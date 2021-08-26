---
product: campaign
title: Inviare e-mail transazionali con allegati
description: Scopri come inviare e-mail transazionali con allegati singoli e/o personalizzati utilizzando Adobe Campaign Classic.
audience: message-center
content-type: reference
topic-tags: use-case
exl-id: 755d2364-f6c4-4943-97e8-3ed52a0f2665
source-git-commit: 7f4bbf3e79d6cdaf17987b9307ebf12801abad22
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 2%

---

# Caso di utilizzo: Inviare e-mail transazionali con allegati {#transactional-email-with-attachments}

![](../../assets/v7-only.svg)

Lo scopo di questo caso d’uso è quello di aggiungere al volo allegati e-mail a messaggi in uscita.

## Passaggi chiave {#key-steps}

In questo scenario, imparerai a inviare e-mail transazionali con allegati singoli e/o personalizzati. Gli allegati non verranno precaricati sul server di messaggistica transazionale: invece saranno generate al volo.

Quando acquisisci le interazioni o i dettagli dei clienti, potrebbe essere necessario inviare queste informazioni al cliente al termine del processo, ad esempio in un file PDF allegato a un messaggio e-mail.

Di seguito sono riportati i passaggi principali di questo scenario:

1. Il cliente accede al sito web e trova un prodotto che desidera acquistare.
1. Il cliente seleziona il prodotto e personalizza alcune opzioni.
1. Il cliente completa la transazione.
1. Viene inviata al cliente un’e-mail di conferma della transazione. Poiché si sconsiglia di inviare informazioni PII (personalmente identificabili) nell’e-mail, viene generato un PDF sicuro che viene allegato all’e-mail.
1. Il cliente riceve l’e-mail e il relativo allegato contenente i dati pertinenti.

In questo scenario, gli allegati non vengono pre-creati, ma aggiunti al volo alle e-mail in uscita, il che offre i seguenti vantaggi:

* Questo consente di personalizzare il contenuto dell’allegato.
* Se l&#39;allegato è associato a una transazione (come nello scenario di esempio descritto sopra), potrebbe contenere dati dinamici generati durante il processo del cliente.
* L’allegato a file PDF ottimizza la protezione in quanto è possibile crittografarli e inviarli tramite HTTPS.

>[!NOTE]
>
>Per evitare problemi di prestazioni, se includi al volo immagini scaricate da un URL personalizzato come allegato, ciascuna dimensione immagine non deve superare i 100.000 byte per impostazione predefinita. Questa soglia consigliata può essere configurata dall&#39; [elenco delle opzioni di Campaign Classic](../../installation/using/configuring-campaign-options.md#delivery).

## Raccomandazioni {#important-notes}

Prima di implementare questo scenario, leggi attentamente le linee guida riportate di seguito:

* Le istanze di messaggistica transazionale non devono essere utilizzate per memorizzare, esportare o caricare file o dati. Possono essere utilizzati solo per i dati evento e le relative informazioni. Non devono essere considerati come un sistema di archiviazione file.
* Poiché non esiste un accesso diretto alle istanze o ai server di messaggistica transazionale al di fuori di Adobe, non esiste un modo standard per inviare tali file su questi server (nessun accesso FTP).
* Non è contrattualmente corretto utilizzare lo spazio su disco nelle istanze di messaggistica transazionale per archiviare file di qualsiasi tipo, nemmeno per gli allegati.
* Per ospitare questi file è necessario utilizzare un altro sistema di dischi online. È necessario un accesso FTP a questo sistema e devi essere in grado di scrivere ed eliminare file.

>[!NOTE]
>
>Per evitare problemi di prestazioni, si consiglia di non includere più di un allegato per e-mail. La soglia consigliata può essere configurata da [l&#39;elenco delle opzioni di Campaign Classic](../../installation/using/configuring-campaign-options.md#delivery).

## Implementazione {#implementation}

Il diagramma seguente illustra i diversi passaggi necessari per implementare questo scenario:

![](assets/message-center-uc1.png)

Per aggiungere istantaneamente un allegato e-mail a un messaggio sulle transazioni, effettua le seguenti operazioni:

1. Iniziare progettando l&#39;allegato. Per ulteriori informazioni, consulta [questa sezione](../../delivery/using/attaching-files.md#attach-a-personalized-file).

   Questo ti consente di allegare i file a un’e-mail, anche se non sono in hosting sull’istanza di esecuzione.

1. Puoi inviare e-mail tramite un trigger di messaggio SOAP. Nella chiamata SOAP è presente un parametro URL (attachmentURL).

   Per ulteriori informazioni sulle richieste SOAP, consulta [Descrizione evento](../../message-center/using/event-description.md).

1. Durante la progettazione dell’e-mail, fai clic su **[!UICONTROL Attachment]**.

1. Nella schermata **[!UICONTROL Attachment definition]**, immetti il parametro di attacco SOAP:

   ```
   <%= rtEvent.ctx.attachmentUrl %>
   ```

1. Quando il messaggio viene elaborato, il sistema riceve il file dalla posizione remota (server di terze parti) e lo allega al singolo messaggio.

   Poiché questo parametro può essere una variabile, deve accettare la variabile URL remota completa del file, inviata tramite la chiamata SOAP.

   ![](assets/message-center-uc2.png)
