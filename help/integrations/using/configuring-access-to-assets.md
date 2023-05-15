---
product: campaign
title: Configurazione dell’accesso alle risorse
description: Configurazione dell’accesso alle risorse
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: integrations
content-type: reference
topic-tags: asset-sharing
exl-id: f3897a40-b080-47e5-9e31-4d861c1bacd5
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 2%

---

# Configurazione dell’accesso alle risorse{#configuring-access-to-assets}



Questa sezione descrive i passaggi di configurazione necessari in Adobe Campaign per utilizzare le funzionalità di integrazione con il servizio core Assets o la libreria Adobe Experience Manager Assets (AEM Assets).

>[!CAUTION]
>
>Queste integrazioni sono simultanee. Leggi attentamente le seguenti informazioni prima di eseguire qualsiasi configurazione.

* Integrazione con **Risorse di Experience Cloud**: questa integrazione consente di inserire immagini dalla libreria Adobe Experience Cloud. Questa integrazione deve essere configurata installando il **[!UICONTROL Integration with the Adobe Experience Cloud]** pacchetto integrato in Adobe Campaign.
* Integrazione con **AEM Assets**: questa integrazione consente di inserire immagini dalla libreria di Adobe Experience Manager Assets. Questa integrazione deve essere configurata installando il **[!UICONTROL AEM Integration]** pacchetto integrato in Adobe Campaign. Questa integrazione non è più disponibile a partire da Adobe Experience Manager 6.4.

>[!NOTE]
>
>Se i due colli (**[!UICONTROL AEM Integration]** e **[!UICONTROL Integration with the Adobe Experience Cloud]** ) sono installate, è possibile utilizzare solo le risorse disponibili nella libreria Adobe Experience Cloud.

## Integrazione con Experience Cloud Assets {#integrating-with-experience-cloud-assets}

Per utilizzare l’integrazione tra Adobe Campaign e Experience Cloud Assets, è necessario disporre di:

* Un&#39;organizzazione Adobe Experience Cloud
* Modalità di autenticazione Adobe IMS abilitata

Per abilitare la connessione tra Adobe Campaign e Adobe Experience Cloud, configura la connessione tramite IMS (servizio di connessione Adobe ID). Questa configurazione è descritta in [Collegamento tramite un Adobe ID](../../integrations/using/about-adobe-id.md) documento. Si tratta di:

* Installazione di **[!UICONTROL Integration with the Adobe Experience Cloud]** pacchetto.
* Configurazione di un account esterno Adobe Experience Cloud.

>[!NOTE]
>
>Le funzionalità collegate a questa integrazione sono disponibili solo per gli utenti collegati al proprio Adobe ID tramite IMS.

## Integrazione con AEM Assets {#integrating-with-aem-assets}


>[!CAUTION]
>
>Questa funzionalità è stata ritirata a partire da Adobe Experience Manager 6.4. [Ulteriori informazioni](https://experienceleague.adobe.com/docs/experience-manager-64/release-notes/deprecated-removed-features.html?lang=en#removed-features)

Per integrare AEM Assets con Adobe Campaign, devi prima configurare l’integrazione tra Adobe Experience Manager e Adobe Campaign. Questa configurazione richiede principalmente:

* Installazione di **[!UICONTROL AEM Integration]** pacchetto integrato
* Configurazione di un account esterno specifico per Adobe Experience Manager

Scopri come integrare Adobe Campaign e Adobe Experience Manager nel [documentazione dettagliata](../../integrations/using/about-adobe-experience-manager.md).

Una volta configurata l’integrazione, puoi configurare un nuovo modello di consegna in Adobe Campaign per utilizzare la libreria AEM Assets. A tale scopo, segui la procedura indicata di seguito:

1. Crea un nuovo modello di consegna - o duplicane uno esistente. Per ulteriori informazioni sui modelli di consegna, consulta [questa pagina](../../delivery/using/about-templates.md).
1. Modifica le **Proprietà** di questo modello.
1. In **[!UICONTROL Advanced]** imposta la **[!UICONTROL Content editing mode]** a **DCE**.
1. Seleziona l’esterno **[!UICONTROL AEM account]** che devi utilizzare per accedere alla libreria AEM Assets.

   ![](assets/dam_aem_assets1.png)

Quando inserisci immagini nel contenuto di una consegna in base a questo modello, la **[!UICONTROL Select a shared asset]** in modo da poter sfogliare le immagini nella libreria AEM Assets. Per ulteriori informazioni, consulta [questa sezione](../../integrations/using/inserting-a-shared-asset.md).

>[!NOTE]
>
>Se la **[!UICONTROL Integration with the Adobe Experience Cloud]** Il pacchetto viene installato anche nella tua istanza di Adobe Campaign, potrai utilizzare solo le risorse disponibili nella libreria Adobe Experience Cloud. Per accedere anche alle risorse nella libreria AEM Assets, devi sincronizzare AEM Assets e Adobe Experience Cloud. Le risorse in AEM Assets saranno quindi disponibili anche nella libreria Adobe Experience Cloud. In questo caso, non è necessario creare un modello di consegna specifico.
