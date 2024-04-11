---
product: campaign
title: Configurare l’integrazione con Adobe Target
description: Scopri come configurare l’integrazione con Adobe Target
feature: Target Integration
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: ae8c680f-52a6-4d00-91cd-44d1c3807546
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 2%

---

# Configurare l’integrazione con Adobe Target{#configuring-the-integration-with-adobe-target}




>[!CAUTION]
>
> In qualità di cliente in hosting o ibrido, contatta il tuo rappresentante Adobe per configurare questa integrazione. I passaggi seguenti sono applicabili solo ai clienti on-premise.

Questa integrazione richiede:

* Organizzazioni Adobe Experience Cloud e Adobe Target
* Un rawbox Adobe Target specificato per stabilire la connessione con Adobe Campaign

Per configurare questa integrazione in Adobe Campaign, effettua le seguenti operazioni:

1. Installare **[!UICONTROL Integration with the Adobe Experience Cloud]** pacchetto incorporato. [Ulteriori informazioni](../../platform/using/working-with-data-packages.md#importing-packages)

   Questo pacchetto consente di accedere alle risorse condivise tramite Digital Asset Manager.

1. Abilita la connessione tramite IMS (Adobe ID connection service) per utilizzare le immagini condivise tramite Adobe Experience Cloud nelle e-mail. [Ulteriori informazioni](../../integrations/using/about-adobe-id.md)
1. Sfoglia per **[!UICONTROL Administration > Platform > Options]** per configurare le opzioni server e organizzazione (tenant) per Adobe Target:

   ![](assets/tar_options.png)

   * **[!UICONTROL TNT_EdgeServer]** : server Adobe Target utilizzato per l’integrazione. Questa opzione è già selezionata per impostazione predefinita. Questo valore corrisponde all’Adobe Target **[!UICONTROL Domain Server]**, seguito dal valore **/m2**. Ad esempio: **tt.omtrdc.net/m2**.
   * **[!UICONTROL TNT_TenantName]** : nome dell’organizzazione Adobe Target. Questo valore corrisponde al nome dell’Adobe Target **[!UICONTROL Client]**.


>[!CAUTION]
>
>Per le architetture ibride e in hosting, queste opzioni devono essere impostate su tutti i server, incluso [server di mid-sourcing](../../installation/using/mid-sourcing-server.md) e [istanza di esecuzione](../../message-center/using/configuring-instances.md#execution-instance).