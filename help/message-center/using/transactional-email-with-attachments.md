---
solution: Campaign Classic
product: campaign
title: Aggiunta di allegati ai messaggi transazionali con Adobe Campaign Classic
description: Informazioni sull'invio di e-mail transazionali con allegati singoli e/o personalizzati tramite Adobe Campaign Classic
audience: message-center
content-type: reference
topic-tags: use-case
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 1%

---


# Caso di utilizzo: Invio di e-mail transazionali con allegati{#transactional-email-with-attachments}

Lo scopo di questo caso d’uso è quello di aggiungere al volo allegati e-mail a messaggi in uscita.

## Passaggi chiave {#key-steps}

In questo scenario verrà illustrato come inviare e-mail transazionali con allegati singoli e/o personalizzati. Gli allegati non verranno precaricati nel server di messaggistica transazionale: invece saranno generate al volo.

Quando acquisite informazioni sui clienti o informazioni dettagliate, potrebbe essere necessario inviarle nuovamente al cliente al termine del processo, ad esempio in un file PDF allegato a un messaggio e-mail.

Di seguito sono riportati i passaggi principali di questo scenario:

1. Il cliente accede al sito Web e trova un prodotto che desidera acquistare.
1. Il cliente seleziona il prodotto e personalizza alcune opzioni.
1. Il cliente completa la transazione.
1. Al cliente viene inviato un messaggio e-mail di conferma della transazione. Poiché non si consiglia di inviare PII (Informazioni personali) all’indirizzo e-mail, viene generato un PDF protetto e allegato al messaggio e-mail.
1. Il cliente riceve l&#39;e-mail e il relativo allegato contenente i dati pertinenti.

In questo scenario, gli allegati non vengono pre-creati, ma aggiunti al volo alle e-mail in uscita, il che offre i seguenti vantaggi:

* Questo consente di personalizzare il contenuto dell&#39;allegato.
* Se l&#39;allegato è associato a una transazione (come nello scenario di esempio sopra descritto), potrebbe contenere dati dinamici generati durante il processo del cliente.
* L’associazione di file PDF ottimizza la protezione e consente di cifrarli e inviarli mediante il protocollo HTTPS.

>[!NOTE]
>
>Per evitare problemi di prestazioni, se includete come allegati immagini scaricate al volo da un URL personalizzato, per impostazione predefinita ciascuna dimensione non deve superare i 100.000 byte. Questa soglia consigliata può essere configurata da [l&#39;elenco di opzioni Campaign Classic](../../installation/using/configuring-campaign-options.md#delivery).

## Raccomandazioni {#important-notes}

Prima di implementare questo scenario, leggi attentamente le linee guida seguenti:

* Le istanze di Messaggi transazionali non devono essere utilizzate per memorizzare, esportare o caricare file o dati. Possono essere utilizzati solo per i dati dell&#39;evento e le relative informazioni. Non devono essere considerati come un sistema di archiviazione file.
* Poiché non esiste un accesso diretto alle istanze o ai server di Messaggistica transnazionale al di fuori  Adobe, non esiste un modo standard per inviare tali file in push su tali server (nessun accesso FTP).
* Non è invece corretto utilizzare lo spazio su disco nelle istanze dei messaggi transazionali per archiviare file di qualsiasi tipo, nemmeno per gli allegati.
* Per ospitare questi file è necessario utilizzare un altro sistema di dischi online. Hai bisogno di un accesso FTP a questo sistema e devi essere in grado di scrivere ed eliminare file.

>[!NOTE]
>
>Per evitare problemi di prestazioni, si consiglia di non includere più di un allegato per e-mail. La soglia consigliata può essere configurata da [l&#39;elenco di opzioni Campaign Classic](../../installation/using/configuring-campaign-options.md#delivery).

## Implementazione {#implementation}

Il diagramma seguente mostra i diversi passaggi per implementare questo scenario:

![](assets/message-center-uc1.png)

Per aggiungere al volo un allegato e-mail a un messaggio transazionale, effettua le operazioni seguenti:

1. Iniziate progettando l&#39;allegato. Per ulteriori informazioni, consulta [questa sezione](../../delivery/using/attaching-files.md#attach-a-personalized-file).

   Questo consente di allegare i file a un&#39;e-mail, anche se non sono ospitati nell&#39;istanza di esecuzione.

1. Potete inviare le e-mail tramite un trigger di messaggio SOAP. Nella chiamata SOAP è presente un parametro URL (attachmentURL).

   Per ulteriori informazioni sulle richieste SOAP, vedere [Descrizione evento](../../message-center/using/event-description.md).

1. Durante la progettazione del messaggio e-mail, fate clic su **[!UICONTROL Attachment]**.

1. Nella schermata **[!UICONTROL Attachment definition]**, immettete il parametro SOAP attachment:

   ```
   <%= rtEvent.ctx.attachementUrl %>
   ```

1. Quando il messaggio viene elaborato, il sistema riceve il file dalla posizione remota (server di terze parti) e lo allega al singolo messaggio.

   Poiché questo parametro può essere una variabile, deve accettare la variabile URL remota completa del file, inviata tramite la chiamata SOAP.

   ![](assets/message-center-uc2.png)
