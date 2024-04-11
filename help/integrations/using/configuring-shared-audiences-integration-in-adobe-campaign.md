---
product: campaign
title: Configurazione dell’integrazione dei tipi di pubblico condivisi in Adobe Campaign
description: Scopri come configurare l’integrazione dei pubblici condivisi
feature: Audiences, People Core Service Integration
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: a3e26cff-9609-4d91-8976-9213a30c3fd2
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 0%

---

# Configurazione dell’integrazione dei tipi di pubblico condivisi in Adobe Campaign{#configuring-shared-audiences-integration-in-adobe-campaign}



Dopo aver inviato questa richiesta, Adobe procederà al provisioning dell’integrazione per te e ti contatterà per fornire dettagli e informazioni necessari per finalizzare la configurazione:

1. [Passaggio 1: configurare o controllare gli account esterni in Adobe Campaign](#step-1--configure-or-check-the-external-accounts-in-adobe-campaign)
1. [Passaggio 2: configurare l’origine dati](#step-2--configure-the-data-source)
1. [Passaggio 3: configurare il server di tracciamento campagna](#step-3--configure-campaign-tracking-server)
1. [Passaggio 4: configurare il servizio ID visitatori](#step-4--configure-the-visitor-id-service)

>[!IMPORTANT]
>
>Se utilizzi il dominio demdex e segui la sintassi **ftp-out.demdex.com** per l’account esterno import e **ftp-in.demdex.com** per esportare un account esterno, è necessario adattare di conseguenza l’implementazione e passare al connettore Amazon Simple Storage Service (S3) per importare o esportare i dati. Per ulteriori informazioni su come configurare gli account esterni con Amazon S3, consulta questa [sezione](../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md#step-1--configure-or-check-the-external-accounts-in-adobe-campaign).

Il diagramma seguente illustra il funzionamento di questa integrazione. Qui AAM sta per Adobe Audience Manager e AC per Adobe Campaign.

![](assets/aam_diagram.png){align="center"}

## Passaggio 1: configurare o controllare gli account esterni in Adobe Campaign {#step-1--configure-or-check-the-external-accounts-in-adobe-campaign}

Innanzitutto, devi configurare o controllare gli account esterni in Adobe Campaign come segue:

1. Fai clic su **[!UICONTROL Explorer]** icona.
1. Vai a **[!UICONTROL Administration > Platform > External accounts]**. Gli account SFTP menzionati avrebbero dovuto essere configurati da Adobe e le informazioni necessarie avrebbero dovuto essere comunicate all’utente.

   * **[!UICONTROL importSharedAudience]**: account dedicato all’importazione di tipi di pubblico.
   * **[!UICONTROL exportSharedAudience]**: account dedicato all’esportazione dei tipi di pubblico.

   ![](assets/aam_config_1.png)

1. Seleziona la **[!UICONTROL Export audiences to the Adobe Marketing Cloud]** account esterno.

1. Dalla sezione **[!UICONTROL Type]** a discesa, seleziona **[!UICONTROL AWS S3]**.

1. Fornisci i seguenti dettagli:

   * **[!UICONTROL AWS S3 Account Server]**
URL del server, deve essere compilato come segue:

     ```
     <S3bucket name>.s3.amazonaws.com/<s3object path>
     ```

   * **[!UICONTROL AWS access key ID]**
Per sapere dove trovare il tuo ID chiave di accesso ad AWS, consulta questa [pagina](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys) .

   * **[!UICONTROL Secret access key to AWS]**
Per sapere dove trovare la chiave di accesso segreta ad AWS, consulta questa [pagina](https://aws.amazon.com/fr/blogs/security/wheres-my-secret-access-key/).

   * **[!UICONTROL AWS Region]**
Per ulteriori informazioni sull’area geografica di AWS, consulta [pagina](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/).

   ![](assets/aam_config_2.png)

1. Clic **[!UICONTROL Save]** e configurare **[!UICONTROL Import audiences from the Adobe Marketing Cloud]** account esterno come descritto nei passaggi precedenti.

Gli account esterni sono ora configurati.

## Passaggio 2: configurare l’origine dati {#step-2--configure-the-data-source}

Il **Destinatario - ID visitatore** viene creato all’interno di Audienci Manager. Si tratta di un’origine dati predefinita configurata per impostazione predefinita per l’ID visitatore. I segmenti creati da Campaign faranno parte di questa origine dati.

Per configurare **[!UICONTROL Recipient - Visitor ID]** origine dati:

1. Dalla sezione **[!UICONTROL Explorer]** nodo, seleziona **[!UICONTROL Administration > Platform > AMC Data sources]**.
1. Seleziona **[!UICONTROL Recipient - Visitor ID]**.
1. Inserisci il **[!UICONTROL Data Source ID]** e **[!UICONTROL AAM Destination ID]** fornite dall’Adobe.

   ![](assets/aam_config_3.png)

## Passaggio 3: configurare il server di tracciamento campagna {#step-3--configure-campaign-tracking-server}

Per la configurazione dell’integrazione con il servizio core People o Audience Manager, è necessario configurare anche il server di tracciamento di Campaign.

Per consentire ai tipi di pubblico condivisi di funzionare con l’ID visitatore, il dominio del server di tracciamento deve essere un sottodominio dell’URL su cui è stato fatto clic o del sito web principale.

>[!IMPORTANT]
>
>Assicurati che il server di tracciamento di Campaign sia registrato nel dominio (CNAME). Per ulteriori informazioni sulla delega dei nomi di dominio, consulta [questo articolo](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/setting-up-new-subdomain.html?lang=it).

## Passaggio 4: configurare il servizio ID visitatori {#step-4--configure-the-visitor-id-service}

Nel caso in cui il servizio ID visitatore non sia mai stato configurato nelle tue proprietà web o sui tuoi siti web, consulta quanto segue [documento](https://experienceleague.adobe.com/docs/id-service/using/implementation/setup-aam-analytics.html) per informazioni su come configurare il servizio o sui seguenti [video](https://helpx.adobe.com/it/marketing-cloud/how-to/email-marketing.html#step-two).

Sincronizzare gli identificatori dei clienti con l’ID dichiarato utilizzando `setCustomerID` funzione nel servizio ID Experience Cloud con il codice di integrazione: `AdobeCampaignID`. Il `AdobeCampaignID` deve corrispondere al valore della chiave di riconciliazione impostata nell’origine dati del destinatario configurata in [Passaggio 2: configurare le origini dati](#step-2--configure-the-data-sources).

La configurazione e il provisioning sono finalizzati, l’integrazione ora può essere utilizzata per importare ed esportare tipi di pubblico o segmenti.
