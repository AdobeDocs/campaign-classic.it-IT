---
product: campaign
title: Inviare e-mail transazionali con allegati
description: Scopri come inviare e-mail transazionali con allegati singoli e/o personalizzati utilizzando Adobe Campaign
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Transactional Messaging
exl-id: 755d2364-f6c4-4943-97e8-3ed52a0f2665
source-git-commit: 64a94982ea1eebc30c652e0025eb0aaa0eab1ce9
workflow-type: tm+mt
source-wordcount: '663'
ht-degree: 4%

---

# Caso d’uso: inviare e-mail transazionali con allegati {#transactional-email-with-attachments}



Lo scopo di questo caso d’uso è quello di aggiungere al volo allegati e-mail alle spedizioni in uscita.

## Passaggi chiave {#key-steps}

In questo scenario, imparerai a inviare e-mail transazionali con allegati singoli e/o personalizzati. Gli allegati non verranno precaricati sul server di messaggistica transazionale, ma verranno generati immediatamente.

Quando acquisisci le interazioni o i dettagli del cliente, potrebbe essere necessario inviare nuovamente queste informazioni al cliente alla fine del processo, ad esempio in un file PDF allegato a un messaggio e-mail.

Di seguito sono riportati i passaggi principali di questo scenario:

1. Il cliente accede al sito web e trova un prodotto che desidera acquistare.
1. Il cliente seleziona il prodotto e personalizza alcune opzioni.
1. Il cliente completa la transazione.
1. Al cliente viene inviata un’e-mail di conferma della transazione. Poiché non è consigliabile inviare dati PII (personalmente identificabili) nell’e-mail, viene generato un PDF sicuro, che viene allegato all’e-mail.
1. Il cliente riceve l’e-mail e il relativo allegato contenente i dati rilevanti.

In questo scenario, gli allegati non vengono precreati, ma aggiunti al volo alle e-mail in uscita, il che offre i seguenti vantaggi:

* Ciò ti consente di personalizzare il contenuto dell’allegato.
* Se l&#39;allegato è associato a una transazione (come nell&#39;esempio descritto in precedenza), può contenere dati dinamici generati durante il processo del cliente.
* Allegando i file PDF si ottimizza la sicurezza in quanto è possibile crittografarli e inviarli tramite HTTPS.

## Recommendations e guardrail {#important-notes}

Per evitare problemi di prestazioni, le immagini incluse nelle e-mail non possono superare i 100 MB. Questo limite, impostato per impostazione predefinita, può essere modificato dal `NmsDelivery_MaxDownloadedImageSize` opzione. Tuttavia, Adobe consiglia vivamente di evitare le immagini di grandi dimensioni nelle consegne e-mail.

L&#39;Adobe consiglia inoltre di limitare le dimensioni e il numero di file allegati. Per impostazione predefinita, è possibile aggiungere un solo file come allegato a un messaggio e-mail. Questa soglia può essere configurata dal `NmsDelivery_MaxRecommendedAttachments` opzione.

Ulteriori informazioni in [elenco delle opzioni di Campaign Classic](../../installation/using/configuring-campaign-options.md#delivery).

Prima di implementare questo scenario, leggi attentamente le linee guida seguenti:

* Le istanze di messaggistica transazionale non devono essere utilizzate per archiviare, esportare o caricare file o dati. Possono essere utilizzati solo per i dati evento e le informazioni correlate. Non devono essere considerati come un sistema di storage di file.
* Poiché non esiste un accesso diretto alle istanze di messaggistica transazionale o ai server al di fuori di Adobe, non esiste una modalità standard per inviare tali file a tali server (nessun accesso FTP).
* Non è contrattualmente corretto utilizzare lo spazio su disco nelle istanze di messaggistica transazionale per memorizzare file di qualsiasi tipo, nemmeno per gli allegati.
* Per ospitare questi file è necessario utilizzare un altro sistema di dischi online. È necessario disporre di un accesso FTP al sistema ed essere in grado di scrivere ed eliminare file.

>[!NOTE]
>
>Per evitare problemi di prestazioni, si consiglia di non includere più di un allegato per e-mail. La soglia consigliata può essere configurata da [elenco delle opzioni di Campaign Classic](../../installation/using/configuring-campaign-options.md#delivery).

## Implementazione {#implementation}

Il diagramma seguente mostra i diversi passaggi necessari per implementare questo scenario:

![](assets/message-center-uc1.png)

Per aggiungere al volo un allegato e-mail a un messaggio sulle transazioni, effettua le seguenti operazioni:

1. Iniziare progettando l&#39;allegato. Per ulteriori informazioni, consulta [questa sezione](../../delivery/using/attaching-files.md#attach-a-personalized-file).

   Ciò ti consente di allegare i file a un messaggio e-mail, anche se non sono ospitati nell’istanza di esecuzione.

1. Puoi inviare e-mail tramite un attivatore di messaggi SOAP. Nella chiamata SOAP è presente un parametro URL (attachmentURL).

   Per ulteriori informazioni sulle richieste SOAP, consulta [Descrizione evento](../../message-center/using/event-description.md).

1. Durante la progettazione dell’e-mail, fai clic su **[!UICONTROL Attachment]**.

1. In **[!UICONTROL Attachment definition]** immettere il parametro SOAP attach:

   ```
   <%= rtEvent.ctx.attachmentUrl %>
   ```

1. Quando il messaggio viene elaborato, il sistema riceve il file dalla posizione remota (server di terze parti) e lo allega al singolo messaggio.

   Poiché questo parametro può essere una variabile, deve accettare la variabile URL remota del file completamente formata, inviata tramite la chiamata SOAP.

   ![](assets/message-center-uc2.png)
