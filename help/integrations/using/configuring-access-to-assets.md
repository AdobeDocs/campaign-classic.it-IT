---
product: campaign
title: Configurazione dell’accesso alle risorse
description: Configurazione dell’accesso alle risorse
audience: integrations
content-type: reference
topic-tags: asset-sharing
exl-id: f3897a40-b080-47e5-9e31-4d861c1bacd5
source-git-commit: eb630b29dba8cc34046e2f14e9ed6ba8c017ea5d
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 1%

---

# Configurazione dell’accesso alle risorse{#configuring-access-to-assets}

Questa sezione descrive i passaggi di configurazione necessari in Adobe Campaign per utilizzare le funzionalità di integrazione con il servizio core Assets o la libreria Adobe Experience Manager Assets (AEM Assets).

>[!CAUTION]
>
>Queste integrazioni sono simultanee. Leggi attentamente le seguenti informazioni prima di eseguire qualsiasi configurazione.

* Integrazione con **risorse di Experience Cloud**: questa integrazione consente di inserire immagini dalla libreria Adobe Experience Cloud. Questa integrazione deve essere configurata installando il pacchetto incorporato **[!UICONTROL Integration with the Adobe Experience Cloud]** in Adobe Campaign.
* Integrazione con **AEM Assets**: questa integrazione consente di inserire immagini dalla libreria di Adobe Experience Manager Assets. Questa integrazione deve essere configurata installando il pacchetto incorporato **[!UICONTROL AEM Integration]** in Adobe Campaign. Questa integrazione non è più disponibile con Adobe Experience Manager 6.5.

>[!NOTE]
>
>Se i due pacchetti (**[!UICONTROL AEM Integration]** e **[!UICONTROL Integration with the Adobe Experience Cloud]** ) sono installati, è possibile utilizzare solo le risorse disponibili nella libreria Adobe Experience Cloud.

## Integrazione con Experience Cloud Assets {#integrating-with-experience-cloud-assets}

Per utilizzare l’integrazione tra Adobe Campaign e Experience Cloud Assets, è necessario disporre di:

* Un&#39;organizzazione Adobe Experience Cloud
* Modalità di autenticazione IMS di Adobe abilitata

Per abilitare la connessione tra Adobe Campaign e Adobe Experience Cloud, configura la connessione tramite IMS (servizio di connessione Adobe ID). Questa configurazione è descritta in [Collegamento tramite un documento Adobe ID](../../integrations/using/about-adobe-id.md). Si tratta di:

* Installazione del pacchetto **[!UICONTROL Integration with the Adobe Experience Cloud]**.
* Configurazione di un account esterno Adobe Experience Cloud.

>[!NOTE]
>
>Le funzionalità collegate a questa integrazione sono disponibili solo per gli utenti collegati al proprio Adobe ID tramite IMS.

## Integrazione con AEM Assets {#integrating-with-aem-assets}


>[!CAUTION]
>
>Questa funzionalità è stata rimossa a partire da Adobe Experience Manager 6.5. [Ulteriori informazioni](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/deprecated-removed-features.html?lang=en#removed-features)

Per integrare AEM Assets con Adobe Campaign, devi prima configurare l’integrazione tra Adobe Experience Manager e Adobe Campaign. Questa configurazione richiede principalmente:

* Installazione del pacchetto incorporato **[!UICONTROL AEM Integration]**
* Configurazione di un account esterno specifico per Adobe Experience Manager

Scopri come integrare Adobe Campaign e Adobe Experience Manager nella [documentazione dettagliata](../../integrations/using/about-adobe-experience-manager.md).

Una volta configurata l’integrazione, puoi configurare un nuovo modello di consegna in Adobe Campaign per utilizzare la libreria AEM Assets. Per farlo, segui la procedura indicata di seguito:

1. Crea un nuovo modello di consegna - o duplicane uno esistente. Per ulteriori informazioni sui modelli di consegna, consulta [questa pagina](../../delivery/using/about-templates.md).
1. Modifica le **Proprietà** di questo modello.
1. Nella scheda **[!UICONTROL Advanced]** , imposta **[!UICONTROL Content editing mode]** su **DCE**.
1. Seleziona la **[!UICONTROL AEM account]** esterna da utilizzare per accedere alla libreria AEM Assets.

   ![](assets/dam_aem_assets1.png)

Quando inserisci immagini nel contenuto di una consegna basato su questo modello, l’opzione **[!UICONTROL Select a shared asset]** ti consentirà di sfogliare le immagini nella libreria AEM Assets. Ulteriori informazioni in [questa sezione](../../integrations/using/inserting-a-shared-asset.md).

>[!NOTE]
>
>Se il pacchetto **[!UICONTROL Integration with the Adobe Experience Cloud]** è installato anche nell’istanza di Adobe Campaign, potrai utilizzare solo le risorse disponibili nella libreria Adobe Experience Cloud. Per accedere anche alle risorse nella libreria AEM Assets, devi sincronizzare AEM Assets e Adobe Experience Cloud. Le risorse in AEM Assets saranno quindi disponibili anche nella libreria Adobe Experience Cloud. In questo caso, non è necessario creare un modello di consegna specifico. Per ulteriori informazioni sulla sincronizzazione tra AEM Assets e Adobe Experience Cloud, consulta la [documentazione dettagliata](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/configure-assets-cc-integration.html#integration).
