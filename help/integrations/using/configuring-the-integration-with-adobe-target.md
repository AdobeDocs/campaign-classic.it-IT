---
product: campaign
title: Configurazione dell’integrazione con Adobe Target
description: Configurazione dell’integrazione con Adobe Target
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: ae8c680f-52a6-4d00-91cd-44d1c3807546
source-git-commit: 94e609f3df94c553e2ec84ee427887a767b9af21
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%

---

# Configurazione dell’integrazione con Adobe Target{#configuring-the-integration-with-adobe-target}

## Prerequisiti {#prerequisites}

Per utilizzare l’integrazione tra Adobe Campaign e Adobe Target, è necessario disporre di:

* Organizzazioni Adobe Experience Cloud e Adobe Target
* Una rawbox Adobe Target specificata per stabilire la connessione con Adobe Campaign

## Configurazione di Adobe Campaign {#configuring-adobe-campaign}

Per configurare Adobe Campaign:

1. Installa il pacchetto standard **[!UICONTROL Integration with the Adobe Experience Cloud]**. L&#39;installazione di un pacchetto di integrazione è la stessa dell&#39;installazione di un pacchetto standard, descritta nella sezione [Importazione pacchetto](../../platform/using/working-with-data-packages.md#importing-packages) . Questo consente di accedere alle risorse condivise tramite Digital Asset Manager.
1. Abilita la connessione tramite IMS (Adobe ID connection service) per utilizzare le immagini condivise tramite Adobe Experience Cloud nelle tue e-mail. Consulta la sezione relativa a [IMS](../../integrations/using/about-adobe-id.md).
1. In **[!UICONTROL Administration > Platform > Options]**, configura le opzioni server e organizzazione (tenant) per Adobe Target:

   * **[!UICONTROL TNT_EdgeServer]** : Server Adobe Target utilizzato per l’integrazione. Questa opzione è già selezionata per impostazione predefinita. Questo valore corrisponde all&#39;Adobe Target **[!UICONTROL Domain Server]**, seguito dal valore **/m2**. Ad esempio: **tt.omtrdc.net/m2**.
   * **[!UICONTROL TNT_TenantName]** : Nome organizzazione Adobe Target. Questo valore corrisponde al nome dell&#39;Adobe Target **[!UICONTROL Client]**.

   ![](assets/tar_options.png)

>[!CAUTION]
>
>Per le architetture ibride e in hosting, queste opzioni devono essere impostate su tutti i server, inclusi il [server di mid-sourcing](../../installation/using/mid-sourcing-server.md) e l&#39; [istanza di esecuzione](../../message-center/using/configuring-instances.md#execution-instance).