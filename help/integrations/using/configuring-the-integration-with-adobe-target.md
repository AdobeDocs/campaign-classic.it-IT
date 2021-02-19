---
solution: Campaign Classic
product: campaign
title: Configurazione dell'integrazione con  Adobe Target
description: Configurazione dell'integrazione con  Adobe Target
audience: integrations
content-type: reference
topic-tags: adobe-target
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Configurazione dell&#39;integrazione con  Adobe Target{#configuring-the-integration-with-adobe-target}

## Prerequisiti {#prerequisites}

Per utilizzare l&#39;integrazione tra  Adobe Campaign e  Adobe Target, è necessario disporre di:

* Adobe Experience Cloud e  organizzazioni Adobe Target
* Una rawbox Adobe Target  specificata per stabilire la connessione con  Adobe Campaign

## Configurazione  Adobe Campaign {#configuring-adobe-campaign}

Per configurare  Adobe Campaign:

1. Installate il pacchetto **[!UICONTROL Integration with the Adobe Experience Cloud]** standard. L&#39;installazione di un pacchetto di integrazione è la stessa dell&#39;installazione di un pacchetto standard, descritta nella sezione [Package Import](../../platform/using/working-with-data-packages.md#importing-packages). Questo consente di accedere alle risorse condivise tramite Digital Asset Manager.
1. Abilita la connessione tramite IMS ( servizio di connessione Adobe ID) per utilizzare le immagini condivise tramite Adobe Experience Cloud nelle e-mail. Consultare la sezione relativa a [IMS](../../integrations/using/about-adobe-id.md).
1. In **[!UICONTROL Administration > Platform > Options]** configurate le opzioni del server e dell&#39;organizzazione (tenant) per  Adobe Target:

   * **[!UICONTROL TNT_EdgeServer]** :  server Adobe Target utilizzato per l&#39;integrazione. Questa opzione è già selezionata per impostazione predefinita. Questo valore corrisponde al  Adobe Target **[!UICONTROL Domain Server]**, seguito dal valore **/m2**. Ad esempio: **tt.omtrdc.net/m2**.
   * **[!UICONTROL TNT_TenantName]** :  Nome organizzazione Adobe Target. Questo valore corrisponde al nome dell&#39;Adobe Target  **[!UICONTROL Client]**.

   ![](assets/tar_options.png)

