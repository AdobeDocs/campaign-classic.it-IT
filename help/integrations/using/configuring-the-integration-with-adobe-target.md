---
title: Configurazione dell'integrazione con  Adobe Target
seo-title: Configurazione dell'integrazione con  Adobe Target
description: Configurazione dell'integrazione con  Adobe Target
seo-description: null
page-status-flag: never-activated
uuid: b9337e92-e4e5-4cba-a559-75db7460d5c5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-target
discoiquuid: 378d5ff9-88c0-43f1-beb8-454701e9f1d1
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---


# Configuring the integration with Adobe Target{#configuring-the-integration-with-adobe-target}

## Prerequisiti {#prerequisites}

Per utilizzare l&#39;integrazione tra  Adobe Campaign e  Adobe Target, è necessario disporre di:

* Adobe Experience Cloud e  organizzazioni Adobe Target
* Una rawbox Adobe Target  specificata per stabilire la connessione con  Adobe Campaign

## Configurazione  Adobe Campaign {#configuring-adobe-campaign}

Per configurare  Adobe Campaign:

1. Installate il pacchetto **[!UICONTROL Integration with the Adobe Experience Cloud]** standard. L’installazione di un pacchetto di integrazione è la stessa dell’installazione di un pacchetto standard, descritta dettagliatamente nella sezione Importazione [](../../platform/using/working-with-data-packages.md#importing-packages) pacchetto. Questo consente di accedere alle risorse condivise tramite Digital Asset Manager.
1. Abilita la connessione tramite IMS ( servizio di connessione Adobe ID) per utilizzare le immagini condivise tramite Adobe Experience Cloud nelle e-mail. Consultate la sezione su [IMS](../../integrations/using/about-adobe-id.md).
1. In **[!UICONTROL Administration > Platform > Options]**, configurate le opzioni del server e dell&#39;organizzazione (tenant) per  Adobe Target:

   * **[!UICONTROL TNT_EdgeServer]** :  server Adobe Target utilizzato per l&#39;integrazione. Questa opzione è già selezionata per impostazione predefinita. Questo valore corrisponde al  Adobe Target **[!UICONTROL Domain Server]**, seguito dal valore **/m2**. Ad esempio: **tt.omtrdc.net/m2**.
   * **[!UICONTROL TNT_TenantName]** :  Nome organizzazione Adobe Target. Questo valore corrisponde al nome dell&#39;Adobe Target  **[!UICONTROL Client]**.

   ![](assets/tar_options.png)

