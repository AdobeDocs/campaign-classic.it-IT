---
product: campaign
title: Configurazione dell’accesso alle risorse
description: Configurazione dell’accesso alle risorse
feature: Asset Sharing
badge-v7: label="v7" type="Informative" tooltip="Applicabile a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
audience: integrations
content-type: reference
topic-tags: asset-sharing
exl-id: f3897a40-b080-47e5-9e31-4d861c1bacd5
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 1%

---

# Configurazione dell’accesso alle risorse{#configuring-access-to-assets}



Questa sezione descrive i passaggi di configurazione necessari in Adobe Campaign per utilizzare le funzionalità di integrazione con il servizio core Assets o la libreria Adobe Experience Manager Assets (AEM Assets).

>[!CAUTION]
>
>Queste integrazioni sono simultanee. Leggi attentamente le seguenti informazioni prima di effettuare qualsiasi configurazione.

* Integrazione con **Experience Cloud Assets**: questa integrazione consente di inserire immagini dalla libreria Adobe Experience Cloud. Questa integrazione deve essere configurata installando il **[!UICONTROL Integration with the Adobe Experience Cloud]** pacchetto integrato in Adobe Campaign.
* Integrazione con **AEM Assets**: questa integrazione ti consente di inserire immagini dalla libreria Adobe Experience Manager Assets. Questa integrazione deve essere configurata installando il **[!UICONTROL AEM Integration]** pacchetto integrato in Adobe Campaign. Questa integrazione non è più disponibile a partire da Adobe Experience Manager 6.4.

>[!NOTE]
>
>Se i due pacchetti (**[!UICONTROL AEM Integration]** e **[!UICONTROL Integration with the Adobe Experience Cloud]** ), è possibile utilizzare solo le risorse disponibili nella libreria Adobe Experience Cloud.

## Integrazione con Experience Cloud Assets {#integrating-with-experience-cloud-assets}

Per utilizzare l’integrazione tra Adobe Campaign e Experience Cloud Assets, è necessario disporre di:

* Un’organizzazione Adobe Experience Cloud
* Modalità di autenticazione Adobe IMS abilitata

Per abilitare la connessione tra Adobe Campaign e Adobe Experience Cloud, configura la connessione tramite IMS (Adobe ID connection service). Questa configurazione è descritta in [Connessione tramite un Adobe ID](../../integrations/using/about-adobe-id.md) documento. Comporta:

* Installazione di **[!UICONTROL Integration with the Adobe Experience Cloud]** pacchetto.
* Configurazione di un account esterno di Adobe Experience Cloud.

>[!NOTE]
>
>Le funzionalità collegate a questa integrazione sono disponibili solo per gli utenti connessi al proprio Adobe ID tramite IMS.

## Integrazione con AEM Assets {#integrating-with-aem-assets}


>[!CAUTION]
>
>Questa funzionalità è stata disattivata a partire da Adobe Experience Manager 6.4. [Ulteriori informazioni](https://experienceleague.adobe.com/docs/experience-manager-64/release-notes/deprecated-removed-features.html#removed-features)

Per integrare AEM Assets con Adobe Campaign, devi prima configurare l’integrazione tra Adobe Experience Manager e Adobe Campaign. Questa configurazione richiede principalmente:

* Installazione di **[!UICONTROL AEM Integration]** pacchetto integrato
* Configurazione di un account esterno specifico di Adobe Experience Manager

Scopri come integrare Adobe Campaign e Adobe Experience Manager in [documentazione dettagliata](../../integrations/using/about-adobe-experience-manager.md).

Una volta impostata questa integrazione, puoi configurare un nuovo modello di consegna in Adobe Campaign per l’utilizzo della libreria AEM Assets. A questo scopo, segui la procedura indicata di seguito:

1. Crea un nuovo modello di consegna o duplicane uno esistente. Per ulteriori informazioni sui modelli di consegna, consulta [questa pagina](../../delivery/using/about-templates.md).
1. Modifica il **Proprietà** di questo modello.
1. In **[!UICONTROL Advanced]** , impostare **[!UICONTROL Content editing mode]** a **DCE**.
1. Seleziona il **[!UICONTROL AEM account]** che devi utilizzare per accedere alla libreria AEM Assets.

   ![](assets/dam_aem_assets1.png)

Quando inserisci immagini nel contenuto di una consegna basata su questo modello, il **[!UICONTROL Select a shared asset]** consente di sfogliare le immagini nella libreria AEM Assets. Per ulteriori informazioni, consulta [questa sezione](../../integrations/using/inserting-a-shared-asset.md).

>[!NOTE]
>
>Se il **[!UICONTROL Integration with the Adobe Experience Cloud]** è installato anche nell’istanza di Adobe Campaign; potrai utilizzare solo le risorse disponibili nella libreria Adobe Experience Cloud. Per accedere alle risorse anche nella libreria di AEM Assets, devi sincronizzare AEM Assets e Adobe Experience Cloud. Le risorse in AEM Assets saranno quindi disponibili anche nella libreria Adobe Experience Cloud. In questo caso, non è necessario creare un modello di consegna specifico.
