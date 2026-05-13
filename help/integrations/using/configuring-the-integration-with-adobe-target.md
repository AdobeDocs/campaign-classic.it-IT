---
product: campaign
title: Configurare l’integrazione con Adobe Target
description: Scopri come configurare l’integrazione con Adobe Target
feature: Target Integration
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: ae8c680f-52a6-4d00-91cd-44d1c3807546
TQID: https://experienceleague.adobe.com/k6TljRgymSefOITPaogJdR7HOrl1BnnZm9jbkemrcyg
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: c5474392-5419-4296-9e41-f6f4ce4f6e9bid: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2: id: b1fd1501-3105-4d6b-b4d4-9af53126df75
topic_v2: id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 198
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

1. Installa il pacchetto integrato **[!UICONTROL Integration with the Adobe Experience Cloud]**. [Ulteriori informazioni](../../platform/using/working-with-data-packages.md#importing-packages)

   Questo pacchetto consente di accedere alle risorse condivise tramite Digital Asset Manager.

1. Abilita la connessione tramite IMS (Adobe ID connection service) per utilizzare le immagini condivise tramite Adobe Experience Cloud nelle e-mail. [Ulteriori informazioni](../../integrations/using/about-adobe-id.md)
1. Passa a **[!UICONTROL Administration > Platform > Options]** per configurare le opzioni server e organizzazione (tenant) per Adobe Target:

   ![](assets/tar_options.png)

   * **[!UICONTROL TNT_EdgeServer]**: server Adobe Target utilizzato per l&#39;integrazione. Questa opzione è già selezionata per impostazione predefinita. Questo valore corrisponde all&#39;Adobe Target **[!UICONTROL Domain Server]**, seguito dal valore **/m2**. Ad esempio: **tt.omtrdc.net/m2**.
   * **[!UICONTROL TNT_TenantName]**: nome organizzazione Adobe Target. Questo valore corrisponde al nome dell&#39;Adobe Target **[!UICONTROL Client]**.


>[!CAUTION]
>
>Per le architetture ibride e in hosting, queste opzioni devono essere impostate su tutti i server, inclusi il [server di mid-sourcing](../../installation/using/mid-sourcing-server.md) e l&#39;[istanza di esecuzione](../../message-center/using/configuring-instances.md#execution-instance).