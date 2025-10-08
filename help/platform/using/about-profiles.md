---
product: campaign
title: Introduzione ai profili
description: Utilizzare i profili in Adobe Campaign
feature: Profiles, Audiences
role: User, Data Architect
level: Beginner
exl-id: 54f1ad6c-54b0-4448-8c38-806dd75c1dae
source-git-commit: 4d8c4ba846148d3df00a76ecc29375b9047c2b20
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 24%

---

# Introduzione ai profili{#about-profiles}



I profili sono centralizzati nel database di Adobe Campaign. Esistono molti possibili meccanismi per l’acquisizione di profili e la creazione di questo database: raccolta on-line tramite moduli web, importazione manuale o automatica di file di testo, replica con database aziendali o altri sistemi di informazioni. Con Adobe Campaign, puoi incorporare la cronologia di marketing, le informazioni di acquisto, le preferenze, i dati di gestione delle relazioni con i clienti ed eventuali dati PI rilevanti in una visualizzazione consolidata per analizzare e intraprendere azioni.

&quot;**Profilo**&quot; indica un record di informazioni (ad esempio un record nella tabella nmsRecipient o una tabella esterna contenente un ID cookie, un ID cliente, un identificatore mobile o altre informazioni relative a un canale specifico) che rappresenta un cliente finale, un potenziale cliente o un lead.

In Adobe Campaign, i destinatari sono i profili target predefiniti per l’invio di consegne (e-mail, SMS, ecc). I dati dei destinatari memorizzati nel database consentono di filtrare il target che riceverà una determinata consegna e di aggiungere dati di personalizzazione al contenuto della consegna. Nel database sono presenti altri tipi di profili. Essi sono progettati per diversi utilizzi. Ad esempio, i profili di seed vengono creati per testare le consegne prima che vengano inviate al target finale.

![Video che mostra quali sono i profili e come funzionano](assets/do-not-localize/how-to-video.png) [Comprendere il concetto di profili nel video](#create-profiles-video)

>[!NOTE]
>
>Per ulteriori informazioni sul profilo, su come crearlo e modificarlo, consulta la documentazione dettagliata nella [documentazione di Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/audience/gs-audiences){target=_blank}.

>[!BEGINTABS]

>[!TAB Documentazione sui profili]

Per ulteriori informazioni sul profilo, su come crearlo e modificarlo, consulta la documentazione dettagliata nella **[documentazione di Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/audience/gs-audiences){target=_blank}**.

[![immagine](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/audience/gs-audiences){target=_blank}

>[!TAB Crea e modifica profili]

Scopri come modificare, gestire e aggiungere profili nella **documentazione di Campaign v8**:

* [Aggiungi profili](https://experienceleague.adobe.com/en/docs/campaign-classic/using/getting-started/profile-management/adding-profiles){target=_blank}: scopri i passaggi chiave per aggiungere e creare nuovi profili.
* [Modifica profili](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/audience/view-profiles?lang=en#_blank){target=_blank}: visualizza e modifica i profili esistenti.
* [Gestisci profili](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/config/configuration/folders-and-views?lang=en#_blank){target=_blank}: accedi e gestisci i profili esistenti utilizzando lo strumento di gestione delle cartelle.

>[!TAB Profili di importazione/esportazione]

Scopri come importare ed esportare profili e dati nella **documentazione di Campaign v8**:

* [Importa profili](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/audience/add-profiles/import-profiles){target=_blank}: è possibile importare profili utilizzando flussi di lavoro.
* [Importa/esporta dati](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/data/import){target=_blank}: scopri come importare o esportare dati e profili utilizzando importazioni/esportazioni generiche.

>[!ENDTABS]

<!--
## Profile types {#profile-types}

Adobe Campaign lets you manage profiles throughout their entire lifecycle: creation, import, targeting, action tracking, updates, etc.

Each profile matches a database entry. They contain all the information required for targeting, qualifying and tracking individuals.

Profiles can be identified based on storage space. This means that a profile can match: a recipient, a visitor, an operator, a subscriber, a prospect, etc.

## Recipient profiles {#recipient-profiles}

Delivery recipients are stored in the database as profiles containing the information linked to them: last name, first name, address, subscriptions, deliveries, etc. When you create campaigns, you can define the target of the deliveries to a selection of the profiles in the base according to simple or advanced criteria.

You can also create campaigns aimed at recipients whose profiles are stored not in the database, but in files. These are known as "external" deliveries. For more information about this type of delivery, refer to [this page](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients).

The main methods for creating recipient profiles are as follows:

* direct input in the graphical interface screens,
* importing recipient lists,
* on-line collection via web forms.

>[!NOTE]
>
>To find out how files and web forms are imported, refer to [Generic imports and exports](../../platform/using/get-started-data-import-export.md).

## Profiles and targets {#profiles-and-targets}

The **[!UICONTROL Profiles and targets]** link lets you display recipients stored in Adobe Campaign database. You can create new recipient, edit an existing recipient and access its profile. For more on this, refer to [this page](../../platform/using/editing-a-profile.md).

![](assets/d_ncs_user_interface_target_link.png)

It also gives you access to:

* lists - [Learn more](../../platform/using/creating-and-managing-lists.md)
* subscription services - [Learn more](../../delivery/using/managing-subscriptions.md)
* web applications - [Learn more](../../web/using/about-web-applications.md)
* imports and exports (jobs) - [Learn more](../../platform/using/about-generic-imports-exports.md)
* targeting workflows - [Learn more](../../workflow/using/building-a-workflow.md#implementation-steps-)

The recipients page lets you perform frequent operations on profiles: edits, updates, adds, deletions, sorts.

For more advanced profile manipulations, you need to edit the Adobe Campaign tree. To do this, click the **[!UICONTROL Explorer]** link on the Adobe Campaign home page.

By default, recipients are stored in the **[!UICONTROL Profiles and Targets > Recipients]** node of the tree. You can create recipients from this view, as well as:

* sort and filter the profiles of the database - [Learn more](../../platform/using/filtering-options.md)
* move, copy or delete profiles from the database - [Learn more](../../platform/using/managing-profiles.md),
* update profiles - [Learn more](../../platform/using/updating-data.md)
* export recipients - [Learn more](../../platform/using/exporting-and-importing-profiles.md)
* create recipient groups - [Learn more](../../platform/using/creating-and-managing-lists.md)

To access advanced functionalities and configurations, you need to click the **[!UICONTROL Explorer]** icon. 

![](assets/d_ncs_user_interface01.png)

The general layout of the Adobe Campaign explorer is presented in [this page](../../platform/using/adobe-campaign-explorer.md).

>[!NOTE]
>
>You can also display an advanced view of this list from the Adobe Campaign tree by clicking the **[!UICONTROL Profiles and targets > Recipients]** link. The list display can be configured to suit your needs. You can add or delete columns, define column order, sort data, etc. List display configuration is described in [this page](../../platform/using/adobe-campaign-ui-lists.md).  
>
>You can also define recipient views. For further information about this functionality, refer to [this section](../../platform/using/access-management-folders.md).

## Active profiles {#active-profiles}

An active profile is a profile that customer has attempted to communicate with during the past 12 months via any channel.

According to your contract, each of your Campaign instances is provisioned with a specific amount of active profiles that are counted for billing purposes. Please refer to your latest contract for reference on number of purchased active profiles. Learn more in [Adobe Campaign product description](https://helpx.adobe.com/legal/product-descriptions/adobe-campaign-managed-cloud-services.html){target="_blank"}.

You can monitor the number of active profiles on your instance directly from Campaign Control Panel. For more on this, refer to the [Control Panel documentation](https://experienceleague.adobe.com/docs/control-panel/using/performance-monitoring/active-profiles-monitoring.html){target="_blank"}.

The following guardrails and limitations apply:

* A profile that has been targeted by several deliveries is counted only once. 
* Profiles targeted in the context of Social marketing on X (Twitter) or Facebook are not taken into account as active profiles.
* The count of active profiles is available for **Marketing instances** only. It is not available for Execution instances, meaning MID (mid sourcing) and RT (Message Center / Real-time messaging) instances.
* The count is based on the recipient primary key. As a consequence, if a profile is present in two different recipient tables, it can be counted twice as an active profile.


## Tutorial video {#create-profiles-video}

Learn how to access profile data, sort and filter profiles and manually create and manage profiles.

This video also explains the compliance of Adobe Campaign Classic with General Data Protection Regulations. 

>[!VIDEO](https://video.tv.adobe.com/v/35611?quality=12)

Additional Campaign Classic how-to videos are available [here](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html).

**See also**

* [Privacy management in Campaign](https://helpx.adobe.com/campaign/kb/acc-privacy.html)

* [Create queries and segment data in workflows](../../workflow/using/targeting-data.md)

* [Select target mapping](../../delivery/using/steps-defining-the-target-population.md#select-a-target-mapping)

-->