---
solution: Campaign Classic
product: campaign
title: Configurazione dell’accesso alle risorse
description: Configurazione dell’accesso alle risorse
audience: integrations
content-type: reference
topic-tags: asset-sharing
translation-type: tm+mt
source-git-commit: 5d5d4b87bae44ce0a93458f79179434a5bf315c3
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 1%

---


# Configurazione dell&#39;accesso a Assets{#configuring-access-to-assets}

Questa sezione descrive i passaggi di configurazione necessari in  Adobe Campaign per utilizzare le funzionalità di integrazione con il servizio di base Assets o la libreria delle risorse di Adobe Experience Manager.

>[!CAUTION]
>
>Queste integrazioni sono simultanee. Leggere attentamente le informazioni seguenti prima di eseguire qualsiasi configurazione.

* Integrazione con **risorse Experience Cloud**: questa integrazione consente di inserire immagini dalla libreria Adobe Experience Cloud. A seconda della configurazione e del modello di licenza, questa libreria può essere il servizio di base Risorse o Risorse su richiesta. Questa integrazione deve essere configurata installando il pacchetto **[!UICONTROL Integration with the Adobe Experience Cloud]** integrato in  Adobe Campaign.
* Integrazione con **AEM Assets**: questa integrazione consente di inserire immagini dalla libreria delle risorse Adobe Experience Manager. Questa integrazione deve essere configurata installando il pacchetto **[!UICONTROL AEM Integration]** integrato in  Adobe Campaign.

>[!NOTE]
>
>Se i due pacchetti (**[!UICONTROL AEM Integration]** e **[!UICONTROL Integration with the Adobe Experience Cloud]** ) sono installati, è possibile utilizzare solo le risorse disponibili nella libreria Adobe Experience Cloud. Per accedere alle risorse anche nella libreria  AEM Assets, dovete sincronizzare  AEM Assets e Adobe Experience Cloud. Le risorse in  AEM Assets saranno quindi disponibili anche nella libreria Adobe Experience Cloud. Per ulteriori informazioni sulla sincronizzazione  AEM Assets e Adobe Experience Cloud, consultare la [documentazione dettagliata](https://docs.adobe.com/docs/en/aod/overview/collaborating/aem-assets-aod-sync.html).

## Integrazione con  risorse Experience Cloud {#integrating-with-experience-cloud-assets}

Per utilizzare l&#39;integrazione tra  Adobe Campaign e  risorse Experienci Cloud, è necessario disporre di:

* Un&#39;organizzazione Adobe Experience Cloud
* Modalità di autenticazione IMS del Adobe  attivata

Per abilitare la connessione tra  Adobe Campaign e Adobe Experience Cloud, configurate la connessione tramite IMS ( servizio di connessione Adobe ID). Questa configurazione è descritta in [Collegamento tramite un documento Adobe ID](../../integrations/using/about-adobe-id.md) . Esso comporta:

* Installazione del pacchetto **[!UICONTROL Integration with the Adobe Experience Cloud]**.
* Configurazione di un account Adobe Experience Cloud esterno.

>[!NOTE]
>
>Le funzionalità collegate a questa integrazione sono disponibili solo per gli utenti collegati al proprio Adobe ID  tramite IMS.

## Integrazione con  AEM Assets {#integrating-with-aem-assets}

Per integrare  AEM Assets con  Adobe Campaign, è innanzitutto necessario configurare l&#39;integrazione tra Adobe Experience Manager e  Adobe Campaign. Questa configurazione richiede principalmente:

* Installazione del pacchetto **[!UICONTROL AEM Integration]** incorporato
* Configurazione di un account esterno specifico per Adobe Experience Manager

Scopri come integrare  Adobe Campaign e Adobe Experience Manager nella [documentazione dettagliata](../../integrations/using/about-adobe-experience-manager.md).

Una volta impostata l&#39;integrazione, potete configurare un nuovo modello di consegna in  Adobe Campaign per utilizzare  libreria AEM Assets. Per farlo, segui la procedura indicata di seguito:

1. Create un nuovo modello di consegna o duplicatene uno esistente. Per ulteriori informazioni sui modelli di consegna, consultare [questa pagina](../../delivery/using/about-templates.md).
1. Modificate la **Proprietà** di questo modello.
1. Nella scheda **[!UICONTROL Advanced]**, impostare **[!UICONTROL Content editing mode]** su **DCE**.
1. Selezionate la **[!UICONTROL AEM account]** esterna da utilizzare per accedere alla libreria AEM Assets .

   ![](assets/dam_aem_assets1.png)

Quando si inseriscono immagini nel contenuto di una distribuzione basata su questo modello, l&#39;opzione **[!UICONTROL Select a shared asset]** consentirà di sfogliare le immagini nella libreria AEM Assets . Ulteriori informazioni in [questa sezione](../../integrations/using/inserting-a-shared-asset.md).

>[!NOTE]
>
>Se anche il pacchetto **[!UICONTROL Integration with the Adobe Experience Cloud]** è installato nell&#39;istanza di Adobe Campaign , sarà possibile utilizzare solo le risorse disponibili nella libreria Adobe Experience Cloud. Per accedere alle risorse anche nella libreria  AEM Assets, dovete sincronizzare  AEM Assets e Adobe Experience Cloud. Le risorse in  AEM Assets saranno quindi disponibili anche nella libreria Adobe Experience Cloud. In questo caso, non è necessario creare un modello di consegna specifico. Per ulteriori informazioni sulla sincronizzazione tra  AEM Assets e Adobe Experience Cloud, fare riferimento alla [documentazione dettagliata](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/configure-assets-cc-integration.html#integration).


