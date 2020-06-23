---
title: Configurazione dell'integrazione dell'audience condivisa in  Adobe Campaign
seo-title: Configurazione dell'integrazione dell'audience condivisa in  Adobe Campaign
description: Configurazione dell'integrazione dell'audience condivisa in  Adobe Campaign
seo-description: null
page-status-flag: never-activated
uuid: 6ed137e4-027f-4eb0-a0b5-4beb7deef51f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: audience-sharing
discoiquuid: 4443b0ca-80c6-467d-a4df-50864aae8496
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0c3737b22c7bf4e614c5a2fbe8e8fd954d3ece8a
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 1%

---


# Configurazione dell&#39;integrazione dell&#39;audience condivisa in  Adobe Campaign{#configuring-shared-audiences-integration-in-adobe-campaign}

Dopo aver inviato questa richiesta, Adobe procederà al provisioning dell&#39;integrazione e vi contatterà per fornire i dettagli e le informazioni necessari per completare la configurazione:

1. [Passaggio 1: Configurare o controllare gli account esterni in  Adobe Campaign](#step-1--configure-or-check-the-external-accounts-in-adobe-campaign)
1. [Passaggio 2: Configurare l&#39;origine dati](#step-2--configure-the-data-source)
1. [Passaggio 3: Configurare il server di tracciamento campagna](#step-3--configure-campaign-tracking-server)
1. [Passaggio 4: Configurare il servizio ID visitatori](#step-4--configure-the-visitor-id-service)

## Passaggio 1: Configurare o controllare gli account esterni in  Adobe Campaign {#step-1--configure-or-check-the-external-accounts-in-adobe-campaign}

In primo luogo, è necessario configurare o verificare i conti esterni  Adobe Campaign come segue:

1. Fate clic sull&#39; **[!UICONTROL Explorer]** icona.
1. Vai a **[!UICONTROL Administration > Platform > External accounts]**. I suddetti account SFTP dovrebbero essere stati configurati da Adobe e le informazioni necessarie avrebbero dovuto essere comunicate all&#39;utente.

   * **[!UICONTROL importSharedAudience]** : Account SFTP dedicato all&#39;importazione di audience.
   * **[!UICONTROL exportSharedAudience]** : Account SFTP dedicato all&#39;esportazione dei tipi di pubblico.
   ![](assets/aam_config_1.png)

1. Compila il **[!UICONTROL Server]** campo: **dominio ftp-out.demdex.com** per l’account esterno da importare e il dominio **ftp-in.demdex.com** per l’account esterno da esportare.

   Ricorda che un&#39;esportazione da Campaign è un&#39;importazione per  servizio di base Audience Manager o Persone.

   >[!NOTE]
   >
   >Se si utilizza S3, immettere la sintassi **[!UICONTROL AWS S3 Account Server]** seguente:\
   `<S3bucket name>.s3.amazonaws.com/<s3object path>`\
   Per ulteriori informazioni su come configurare il tuo account S3, consulta questa [pagina](../../platform/using/external-accounts.md#amazon-simple-storage-service--s3--external-account).

   ![](assets/aam_config_2.png)

1. Aggiungete il **[!UICONTROL Account]** e **[!UICONTROL Password]** fornito da Adobe.

Gli account esterni sono ora configurati.

## Step 2: Configure the Data Source {#step-2--configure-the-data-source}

Il **Destinatario - ID** visitatore viene creato all&#39;interno  Audience Manager. Si tratta di un&#39;origine dati out-of-the-box configurata per impostazione predefinita per l&#39;ID visitatore. I segmenti creati da Campaign faranno parte di questa origine dati.

Per configurare l&#39;origine **[!UICONTROL Recipient - Visitor ID]** dati:

1. Dal **[!UICONTROL Explorer]** nodo, selezionare **[!UICONTROL Administration > Platform > AMC Data sources]**.
1. Selezionare **[!UICONTROL Recipient - Visitor ID]**.
1. Inserite il testo **[!UICONTROL Data Source ID]** e **[!UICONTROL AAM Destination ID]** fornito da Adobe.

   ![](assets/aam_config_3.png)

## Passaggio 3: Configurare il server di tracciamento campagna {#step-3--configure-campaign-tracking-server}

Per la configurazione dell&#39;integrazione con il servizio di base Persone o Audience Manager, dobbiamo anche configurare il server di tracciamento delle campagne.

Devi accertarti che Campaign Tracking Server sia registrato nel dominio (CNAME). Ulteriori informazioni sulla delega dei nomi di dominio sono disponibili in [questo articolo](https://helpx.adobe.com/it/campaign/kb/domain-name-delegation.html).

## Passaggio 4: Configurare il servizio ID visitatori {#step-4--configure-the-visitor-id-service}

Nel caso in cui il servizio ID visitatore non sia mai stato configurato sulle proprietà Web o sui siti Web, consulta il seguente [documento](https://docs.adobe.com/content/help/en/id-service/using/implementation/setup-aam-analytics.html) per apprendere come configurare il servizio o il seguente [video](https://helpx.adobe.com/marketing-cloud/how-to/email-marketing.html#step-two) .

La configurazione e il provisioning sono completati. L&#39;integrazione ora può essere utilizzata per importare ed esportare audience o segmenti.
