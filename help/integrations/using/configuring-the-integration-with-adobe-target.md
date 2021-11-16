---
product: campaign
title: Configurazione dell’integrazione con Adobe Target
description: Configurazione dell’integrazione con Adobe Target
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: ae8c680f-52a6-4d00-91cd-44d1c3807546
source-git-commit: b6e24c63ece12f25b7dafe3fede9e38b3aab2427
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 2%

---

# Configurazione dell’integrazione con Adobe Target{#configuring-the-integration-with-adobe-target}

![](../../assets/common.svg)


>[!CAUTION]
>
> In qualità di cliente in hosting o ibrido, contatta il tuo rappresentante di Adobe per configurare questa integrazione. I passaggi seguenti si applicano solo ai clienti on-premise.

## Prerequisiti {#prerequisites}

Per utilizzare l’integrazione tra Adobe Campaign e Adobe Target, è necessario disporre di:

* Organizzazioni Adobe Experience Cloud e Adobe Target
* Una rawbox Adobe Target specificata per stabilire la connessione con Adobe Campaign

## Configurazione di Adobe Campaign {#configuring-adobe-campaign}

Per configurare Adobe Campaign:

1. Installa il **[!UICONTROL Integration with the Adobe Experience Cloud]** pacchetto integrato. [Ulteriori informazioni](../../platform/using/working-with-data-packages.md#importing-packages)

   Questo pacchetto consente di accedere alle risorse condivise tramite Digital Asset Manager.

1. Abilita la connessione tramite IMS (Adobe ID connection service) per utilizzare le immagini condivise tramite Adobe Experience Cloud nelle tue e-mail. [Ulteriori informazioni](../../integrations/using/about-adobe-id.md)
1. Sfoglia per **[!UICONTROL Administration > Platform > Options]** per configurare le opzioni server e organizzazione (tenant) per Adobe Target:

   ![](assets/tar_options.png)

   * **[!UICONTROL TNT_EdgeServer]** : Server Adobe Target utilizzato per l’integrazione. Questa opzione è già selezionata per impostazione predefinita. Questo valore corrisponde ad Adobe Target **[!UICONTROL Domain Server]**, seguito dal valore **/m2**. Ad esempio: **tt.omtrdc.net/m2**.
   * **[!UICONTROL TNT_TenantName]** : Nome organizzazione Adobe Target. Questo valore corrisponde al nome dell’Adobe Target **[!UICONTROL Client]**.


>[!CAUTION]
>
>Per le architetture ibride e in hosting, queste opzioni devono essere impostate su tutti i server, compresi i [server di mid-sourcing](../../installation/using/mid-sourcing-server.md) e [istanza di esecuzione](../../message-center/using/configuring-instances.md#execution-instance).