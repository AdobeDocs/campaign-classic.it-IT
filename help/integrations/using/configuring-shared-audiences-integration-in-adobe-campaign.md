---
product: campaign
title: Configurazione dell’integrazione dei tipi di pubblico condivisi in Adobe Campaign
description: Scopri come configurare l’integrazione dei tipi di pubblico condivisi
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: a3e26cff-9609-4d91-8976-9213a30c3fd2
source-git-commit: 830c4146d72cd5a744d026a499cfe8613a255da7
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 3%

---

# Configurazione dell’integrazione dei tipi di pubblico condivisi in Adobe Campaign{#configuring-shared-audiences-integration-in-adobe-campaign}

![](../../assets/common.svg)

Dopo aver inviato questa richiesta, Adobe procederà al provisioning dell’integrazione per te e ti contatterà per fornire i dettagli e le informazioni necessarie per completare la configurazione:

1. [Passaggio 1: Configurare o controllare gli account esterni in Adobe Campaign](#step-1--configure-or-check-the-external-accounts-in-adobe-campaign)
1. [Passaggio 2: Configurare l&#39;origine dati](#step-2--configure-the-data-source)
1. [Passaggio 3: Configurare il server di tracciamento delle campagne](#step-3--configure-campaign-tracking-server)
1. [Passaggio 4: Configurare il servizio ID visitatori](#step-4--configure-the-visitor-id-service)

>[!IMPORTANT]
>
>Se utilizzi il dominio demdex e segui la sintassi **ftp-out.demdex.com** per l’account esterno di importazione e **ftp-in.demdex.com** per l’account esterno di esportazione, devi adattare di conseguenza la tua implementazione e passare al connettore Amazon Simple Storage Service (S3) per importare o esportare i dati. Per ulteriori informazioni su come configurare gli account esterni con Amazon S3, consulta questa [sezione](../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md#step-1--configure-or-check-the-external-accounts-in-adobe-campaign).

## Passaggio 1: Configurare o controllare gli account esterni in Adobe Campaign {#step-1--configure-or-check-the-external-accounts-in-adobe-campaign}

Innanzitutto, dobbiamo configurare o controllare gli account esterni in Adobe Campaign come segue:

1. Fai clic sull&#39;icona **[!UICONTROL Explorer]** .
1. Vai a **[!UICONTROL Administration > Platform > External accounts]**. Gli account SFTP menzionati avrebbero dovuto essere configurati per Adobe e le informazioni necessarie avrebbero dovuto essere comunicate all&#39;utente.

   * **[!UICONTROL importSharedAudience]**: account dedicato all’importazione di tipi di pubblico.
   * **[!UICONTROL exportSharedAudience]**: account dedicato all’esportazione di tipi di pubblico.

   ![](assets/aam_config_1.png)

1. Seleziona l’account esterno **[!UICONTROL Export audiences to the Adobe Marketing Cloud]**.

1. Dal menu a discesa **[!UICONTROL Type]**, seleziona **[!UICONTROL AWS S3]**.

1. Fornisci i seguenti dettagli:

   * **[!UICONTROL AWS S3 Account Server]**
URL del server, deve essere compilato come segue:

      ```
      <S3bucket name>.s3.amazonaws.com/<s3object path>
      ```

   * **[!UICONTROL AWS access key ID]**
Per sapere dove trovare l’ID chiave di accesso AWS, consulta questa  [pagina](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys) .

   * **[!UICONTROL Secret access key to AWS]**
Per sapere dove trovare la chiave di accesso segreto per AWS, consulta questa  [pagina](https://aws.amazon.com/fr/blogs/security/wheres-my-secret-access-key/).

   * **[!UICONTROL AWS Region]**
Per ulteriori informazioni sull’area geografica AWS, consulta questa  [pagina](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/).
   ![](assets/aam_config_2.png)

1. Fai clic su **[!UICONTROL Save]** e configura l&#39;account esterno **[!UICONTROL Import audiences from the Adobe Marketing Cloud]** come descritto nei passaggi precedenti.

Gli account esterni sono ora configurati.

## Passaggio 2: Configurare l&#39;origine dati {#step-2--configure-the-data-source}

Il **Destinatario - ID visitatore** viene creato all&#39;interno di Audience Manager. Si tratta di un’origine dati preconfigurata configurata configurata configurata per l’ID visitatore per impostazione predefinita. I segmenti creati da Campaign faranno parte di questa origine dati.

Per configurare l&#39;origine dati **[!UICONTROL Recipient - Visitor ID]**:

1. Dal nodo **[!UICONTROL Explorer]**, seleziona **[!UICONTROL Administration > Platform > AMC Data sources]**.
1. Seleziona **[!UICONTROL Recipient - Visitor ID]**.
1. Inserisci i valori **[!UICONTROL Data Source ID]** e **[!UICONTROL AAM Destination ID]** forniti dall&#39;Adobe.

   ![](assets/aam_config_3.png)

## Passaggio 3: Configurare il server di tracciamento delle campagne {#step-3--configure-campaign-tracking-server}

Per la configurazione dell’integrazione con il servizio core Persone o Audience Manager, dobbiamo anche configurare il server di tracciamento delle campagne.

Devi accertarti che Campaign Tracking Server sia registrato sul dominio (CNAME). Per ulteriori informazioni sulla delega dei nomi di dominio, consulta [questo articolo](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/setting-up-new-subdomain.html?lang=it).

## Passaggio 4: Configurare il servizio ID visitatori {#step-4--configure-the-visitor-id-service}

Nel caso in cui il servizio ID visitatore non sia mai stato configurato sulle proprietà web o sui siti web, consulta il seguente [documento](https://experienceleague.adobe.com/docs/id-service/using/implementation/setup-aam-analytics.html) per informazioni su come configurare il servizio o il seguente [video](https://helpx.adobe.com/it/marketing-cloud/how-to/email-marketing.html#step-two).

La configurazione e il provisioning sono completati. L’integrazione può ora essere utilizzata per importare ed esportare tipi di pubblico o segmenti.
