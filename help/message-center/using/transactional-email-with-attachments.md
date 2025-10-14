---
product: campaign
title: Inviare e-mail transazionali con allegati
description: Scopri come inviare e-mail transazionali con allegati singoli e/o personalizzati utilizzando Adobe Campaign
feature: Transactional Messaging, Message Center
exl-id: 755d2364-f6c4-4943-97e8-3ed52a0f2665
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '667'
ht-degree: 1%

---

# Caso d’uso: inviare e-mail transazionali con allegati {#transactional-email-with-attachments}



Lo scopo di questo caso d’uso è quello di aggiungere al volo allegati e-mail alle spedizioni in uscita.

## Passaggi chiave {#key-steps}

In questo scenario, imparerai a inviare e-mail transazionali con allegati singoli e/o personalizzati. Gli allegati non verranno precaricati sul server di messaggistica transazionale, ma verranno generati immediatamente.

Quando acquisisci le interazioni o i dettagli del cliente, potrebbe essere necessario inviare nuovamente tali informazioni al cliente alla fine del processo, ad esempio in un file PDF allegato a un messaggio e-mail.

Di seguito sono riportati i passaggi principali di questo scenario:

1. Il cliente accede al sito web e trova un prodotto che desidera acquistare.
1. Il cliente seleziona il prodotto e personalizza alcune opzioni.
1. Il cliente completa la transazione.
1. Al cliente viene inviata un’e-mail di conferma della transazione. Poiché non è consigliabile inviare dati PII (Personally Identifiable Information) nell’e-mail, viene generato un PDF sicuro, che viene allegato all’e-mail.
1. Il cliente riceve l’e-mail e il relativo allegato contenente i dati rilevanti.

In questo scenario, gli allegati non vengono precreati, ma aggiunti al volo alle e-mail in uscita, il che offre i seguenti vantaggi:

* Ciò ti consente di personalizzare il contenuto dell’allegato.
* Se l&#39;allegato è associato a una transazione (come nell&#39;esempio descritto in precedenza), può contenere dati dinamici generati durante il processo del cliente.
* Allegando i file PDF si ottimizza la sicurezza in quanto è possibile crittografarli e inviarli tramite HTTPS.

## Consigli e guardrail {#important-notes}

Per evitare problemi di prestazioni, le immagini incluse nelle e-mail non possono superare i 100 KB. Questo limite, impostato per impostazione predefinita, può essere modificato dall&#39;opzione `NmsDelivery_MaxDownloadedImageSize`. Tuttavia, Adobe consiglia vivamente di evitare le immagini di grandi dimensioni nelle consegne e-mail.

Adobe consiglia inoltre di limitare le dimensioni e il numero di file allegati. Per impostazione predefinita, è possibile aggiungere un solo file come allegato a un messaggio e-mail. Questa soglia può essere configurata dall&#39;opzione `NmsDelivery_MaxRecommendedAttachments`.

Ulteriori informazioni sono disponibili in [elenco delle opzioni di Campaign Classic](../../installation/using/configuring-campaign-options.md#delivery).

Prima di implementare questo scenario, leggi attentamente le linee guida seguenti:

* Le istanze di messaggistica transazionale non devono essere utilizzate per archiviare, esportare o caricare file o dati. Possono essere utilizzati solo per i dati evento e le informazioni correlate. Non devono essere considerati come un sistema di storage di file.
* Poiché non esiste un accesso diretto alle istanze di messaggistica transazionale o ai server esterni ad Adobe, non esiste un modo standard per inviare tali file su questi server (nessun accesso FTP).
* Non è contrattualmente corretto utilizzare lo spazio su disco nelle istanze di messaggistica transazionale per memorizzare file di qualsiasi tipo, nemmeno per gli allegati.
* Per ospitare questi file è necessario utilizzare un altro sistema di dischi online. È necessario disporre di un accesso FTP al sistema ed essere in grado di scrivere ed eliminare file.

>[!NOTE]
>
>Per evitare problemi di prestazioni, si consiglia di non includere più di un allegato per e-mail. La soglia consigliata può essere configurata da [l&#39;elenco delle opzioni di Campaign Classic](../../installation/using/configuring-campaign-options.md#delivery).

## Implementazione {#implementation}

Il diagramma seguente mostra i diversi passaggi necessari per implementare questo scenario:

![](assets/message-center-uc1.png)

Per aggiungere al volo un allegato e-mail a un messaggio sulle transazioni, effettua le seguenti operazioni:

1. Iniziare progettando l&#39;allegato. Per ulteriori informazioni, consulta la [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/attaching-files.html?lang=it#attach-a-personalized-file){target="_blank"}.

   Ciò ti consente di allegare i file a un messaggio e-mail, anche se non sono ospitati nell’istanza di esecuzione.

1. Puoi inviare e-mail tramite un attivatore di messaggi di SOAP. Nella chiamata SOAP è presente un parametro URL (attachmentURL).

   Per ulteriori informazioni sulle richieste di SOAP, vedere [Descrizione evento](../../message-center/using/event-description.md).

1. Durante la progettazione dell&#39;e-mail, fare clic su **[!UICONTROL Attachment]**.

1. Nella schermata **[!UICONTROL Attachment definition]**, immettere il parametro dell&#39;allegato SOAP:

   ```
   <%= rtEvent.ctx.attachmentUrl %>
   ```

1. Quando il messaggio viene elaborato, il sistema riceve il file dalla posizione remota (server di terze parti) e lo allega al singolo messaggio.

   Poiché questo parametro può essere una variabile, deve accettare la variabile URL remota del file completamente formata, inviata tramite la chiamata SOAP.

   ![](assets/message-center-uc2.png)
