---
product: campaign
title: Inserire segmenti Adobe Experience Platform in Campaign
description: Scopri come acquisire il pubblico di Adobe Experience Platform in Campaign Classic
feature: Experience Platform Integration
audience: integrations
content-type: reference
exl-id: 6db8a653-b649-402c-8814-24826edadba7
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---

# Inserire segmenti Adobe Experience Platform in Campaign {#destinations}



Per acquisire i tipi di pubblico di Adobe Experience Platform in Campaign e utilizzarli nei flussi di lavoro, devi innanzitutto collegare Adobe Campaign as a una **destinazione** di Adobe Experience Platform e configurarla con il segmento da esportare.

Una volta configurata la destinazione, i dati verranno esportati nella posizione di archiviazione e sarà necessario creare un flusso di lavoro dedicato in Campaign Classic per acquisirli.

## Connettere Adobe Campaign come destinazione

In Adobe Experience Platform, configura una connessione con Adobe Campaign selezionando una posizione di archiviazione per i segmenti esportati. Questi passaggi ti consentono anche di selezionare i segmenti da esportare e specificare campi XDM aggiuntivi da includere.

Per ulteriori informazioni, consulta la [documentazione sulle destinazioni](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html?lang=it).

Dopo aver configurato la destinazione, Adobe Experience Platform crea un file .txt o .csv delimitato da tabulazioni nel percorso di archiviazione fornito. Questa operazione è pianificata ed eseguita una volta ogni 24 ore.

Ora puoi configurare un flusso di lavoro Campaign Classic per acquisire il segmento in Campaign.

## Creare un flusso di lavoro di importazione in Campaign Classic

Una volta che Campaign Classic è stato configurato come Destinazione, devi creare un flusso di lavoro dedicato per importare il file esportato da Adobe Experience Platform.

A tale scopo, è necessario aggiungere e configurare un&#39;attività **[!UICONTROL File transfer]**. Per ulteriori informazioni su come configurare questa attività, consulta [questa sezione](../../workflow/using/file-transfer.md).

![](assets/rtcdp-file-transfer.png)

Puoi quindi creare il flusso di lavoro in base alle tue esigenze (aggiorna il database utilizzando i dati del segmento, invia consegne cross-channel al segmento, ecc.)

Ad esempio, il flusso di lavoro seguente scarica il file dalla posizione di archiviazione su base giornaliera, quindi aggiorna il database di Campaign con i dati del segmento.

![](assets/rtcdp-workflow.png)
