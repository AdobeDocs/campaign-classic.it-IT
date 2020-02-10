---
title: Configurazione dell’accesso alle risorse
seo-title: Configurazione dell’accesso alle risorse
description: Configurazione dell’accesso alle risorse
seo-description: null
page-status-flag: never-activated
uuid: dc8c0016-92c8-41ab-98c6-d0fe0bfd6c41
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: asset-sharing
discoiquuid: df1b6ead-3471-404a-b43f-a68fb86cb14c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# Configurazione dell’accesso alle risorse{#configuring-access-to-assets}

Questa sezione descrive i passaggi di configurazione necessari in Adobe Campaign per utilizzare le funzionalità di integrazione con il servizio di base Assets o la libreria delle risorse di Adobe Experience Manager.

>[!CAUTION]
>
>Queste integrazioni sono simultanee. Leggere attentamente le informazioni seguenti prima di eseguire qualsiasi configurazione.

* Integrazione con **Experience Cloud Assets**: questa integrazione consente di inserire immagini dalla libreria Adobe Experience Cloud. A seconda della configurazione e del modello di licenza, questa libreria può essere il servizio di base Risorse o Risorse su richiesta. Questa integrazione deve essere configurata installando il pacchetto **[!UICONTROL Integration with the Adobe Experience Cloud]** incorporato in Adobe Campaign.
* Integrazione con **AEM Assets**: questa integrazione consente di inserire immagini dalla libreria delle risorse di Adobe Experience Manager. Questa integrazione deve essere configurata installando il pacchetto **[!UICONTROL AEM Integration]** incorporato in Adobe Campaign.

>[!NOTE]
>
>Se i due pacchetti (**[!UICONTROL AEM Integration]** e **[!UICONTROL Integration with the Adobe Experience Cloud]** ) sono installati, è possibile utilizzare solo le risorse disponibili nella libreria Adobe Experience Cloud. Per accedere alle risorse anche nella libreria Risorse AEM, devi sincronizzare Risorse AEM e Adobe Experience Cloud. Le risorse in Risorse AEM saranno quindi disponibili anche nella libreria Adobe Experience Cloud. Per ulteriori informazioni sulla sincronizzazione di Risorse AEM e Adobe Experience Cloud, consulta la documentazione [](https://docs.adobe.com/docs/en/aod/overview/collaborating/aem-assets-aod-sync.html)dettagliata.

## Integrazione con Experience Cloud Assets {#integrating-with-experience-cloud-assets}

Per utilizzare l&#39;integrazione tra Adobe Campaign e Experience Cloud Assets, devi disporre di:

* Un&#39;organizzazione Adobe Experience Cloud
* Modalità di autenticazione Adobe IMS attivata

Per abilitare la connessione tra Adobe Campaign e Adobe Experience Cloud, configura la connessione tramite IMS (servizio di connessione Adobe ID). Questa configurazione è dettagliata nella [connessione tramite un documento Adobe ID](../../integrations/using/about-adobe-id.md) . Esso comporta:

* Installazione del **[!UICONTROL Integration with the Adobe Experience Cloud]** pacchetto.
* Configurazione di un account esterno Adobe Experience Cloud.

>[!NOTE]
>
>Le funzionalità collegate a questa integrazione sono disponibili solo per gli utenti connessi con il loro Adobe ID tramite IMS.

## Integrazione con AEM Assets {#integrating-with-aem-assets}

Per integrare AEM Assets con Adobe Campaign, devi prima configurare l&#39;integrazione tra Adobe Experience Manager e Adobe Campaign. Questa configurazione richiede principalmente:

* Installazione del pacchetto **[!UICONTROL AEM Integration]** incorporato
* Configurazione di un account esterno specifico per Adobe Experience Manager

Scopri come integrare Adobe Campaign e Adobe Experience Manager nella documentazione [](../../integrations/using/about-adobe-experience-manager.md)dettagliata.

Una volta configurata questa integrazione, puoi configurare un nuovo modello di consegna in Adobe Campaign per utilizzare la libreria Risorse AEM. A questo scopo, effettuate le seguenti operazioni:

1. Create un nuovo modello di consegna o duplicatene uno esistente. Per ulteriori informazioni sui modelli di consegna, consulta [questa pagina](../../delivery/using/about-templates.md).
1. Modificate le **proprietà** del modello.
1. Nella **[!UICONTROL Advanced]** scheda, impostare **[!UICONTROL Content editing mode]** su **DCE**.
1. Seleziona l’esterno **[!UICONTROL AEM account]** da utilizzare per accedere alla libreria Risorse AEM.

   ![](assets/dam_aem_assets1.png)

Quando si inseriscono immagini nel contenuto di una distribuzione basata su questo modello, l&#39; **[!UICONTROL Select a shared asset]** opzione consentirà di sfogliare le immagini nella libreria Risorse AEM. Ulteriori informazioni in [questa sezione](../../integrations/using/inserting-a-shared-asset.md).

>[!NOTE]
>
>Se il **[!UICONTROL Integration with the Adobe Experience Cloud]** pacchetto è installato anche nell&#39;istanza di Adobe Campaign, potrai utilizzare solo le risorse disponibili nella libreria Adobe Experience Cloud. Per accedere alle risorse anche nella libreria Risorse AEM, devi sincronizzare Risorse AEM e Adobe Experience Cloud. Le risorse in Risorse AEM saranno quindi disponibili anche nella libreria Adobe Experience Cloud. In questo caso, non è necessario creare un modello di consegna specifico. Per ulteriori informazioni sulla sincronizzazione tra Risorse AEM e Adobe Experience Cloud, consulta la documentazione [](https://docs.adobe.com/docs/en/aod/overview/collaborating/aem-assets-aod-sync.html)dettagliata.

