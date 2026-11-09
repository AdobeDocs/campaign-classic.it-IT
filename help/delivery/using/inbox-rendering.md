---
product: campaign
title: Rendering della casella in entrata in Campaign
description: Scopri come acquisire i rendering di e-mail e renderli disponibili in un rapporto dedicato
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Inbox Rendering, Monitoring, Email Rendering
role: User
exl-id: a3294e70-ac96-4e51-865f-b969624528ce
TQID: 'https://experienceleague.adobe.com/d0fFXi4Ma-PwY8vsSBOmvbhRD4631kUoagNXlf4Rmek'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
    internal-label: Campaign Email Designer
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
    internal-label: Prepare and test messages
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
    internal-label: Email messaging
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
    internal-label: Email design
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
    internal-label: A/B testing
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
    internal-label: Manage deliverability
  - id: 2317b1ea-6db4-58c7-851f-717a69c0f5c0
    internal-label: Inbox Rendering
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
    internal-label: Monitoring guidelines
  - id: aef0b685-fc31-54d4-b831-a87fdb9d69de
    internal-label: Email Rendering
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
topic_v2:
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
source-git-commit: 758d5159759b19f7ef32e8cc8f6237547599e727
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 8%
---
# Rendering della casella in entrata{#inbox-rendering}

Adobe Campaign sfrutta la soluzione di test e-mail basato su Web [Litmus](https://litmus.com/email-testing) per acquisire i rendering di e-mail e renderli disponibili in un report dedicato.

>[!NOTE]
>
>Nell’ambito della transizione da Campaign v7 a v8, il set di documentazione di Campaign Classic è stato razionalizzato e riorganizzato. Le funzioni comuni sono ora disponibili esclusivamente nel set di documentazione di Campaign v8. Per ulteriori informazioni sul rendering della casella in entrata, consulta la [documentazione di Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/deliverability-management/inbox-rendering){target=_blank}.
>
>[![immagine](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/deliverability-management/inbox-rendering){target=_blank}

## Attivazione del rendering della casella in entrata {#activating-inbox-rendering}

[!BADGE On-Premise e ibrido]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"}

Per i client in hosting e ibridi, il rendering della casella in entrata è configurato nell’istanza dal supporto tecnico e dai consulenti Adobe. Per ulteriori informazioni, contatta il tuo account executive di Adobe.

Per le installazioni on-premise, segui i passaggi seguenti per configurare il rendering della casella in entrata.

1. Installa il pacchetto **[!UICONTROL Inbox rendering (IR)]** tramite il menu **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]**. Per ulteriori informazioni, vedere [Installazione dei pacchetti standard di Campaign Classic](../../installation/using/installing-campaign-standard-packages.md).
1. Configurare un account esterno del tipo HTTP tramite il nodo **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External Accounts]**. Per ulteriori informazioni, consulta [Creazione di un account esterno](../../installation/using/external-accounts.md#creating-an-external-account).
1. Imposta i parametri dell’account esterno come segue:
   * **[!UICONTROL Label]**: informazioni sul server di recapito messaggi
   * **[!UICONTROL Internal name]**: deliverabilityInstance
   * **[!UICONTROL Type]**: HTTP
   * **[!UICONTROL Server]**: https://deliverability-app.neolane.net/deliverability
   * **[!UICONTROL Encryption]**: nessuna
   * Seleziona l’opzione **[!UICONTROL Enabled]**.

   ![](assets/s_tn_inbox_rendering_external-account.png)

1. Vai al nodo **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]**. Cerca l&#39;opzione **[!UICONTROL DmRendering_cuid]** e contatta l&#39;assistenza per ottenere l&#39;identificatore dei report di consegna che deve essere copiato nel campo **[!UICONTROL Value (text)]**.
1. Modificare il file **serverConf.xml** per consentire una chiamata al server Litmus. Aggiungere la riga seguente alla sezione `<urlPermission>`:

   ```
   <url dnsSuffix="deliverability-app.neolane.net" urlRegEx="https://.*"/>
   ```

1. Ricarica la configurazione utilizzando il comando seguente:

   ```
   nlserver config -reload
   ```

>[!NOTE]
>
>Per poter utilizzare il rendering della casella in entrata, potrebbe essere necessario disconnettersi dalla console ed effettuare nuovamente l’accesso.
