---
product: campaign
title: Gestire le richieste di accesso ai dati personali
description: Scopri di più sulle richieste di accesso ai dati personali
feature: Privacy, Privacy Tools
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: c7688c2a-f0a7-4c51-a4cf-bf96fe8bf9b6
TQID: https://experienceleague.adobe.com/R1VZbFXdU7rq0MZh5qDxDtY89C718vORDpj31UjO-wQ
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
feature_v2:
  - id: afa4204e-6d08-4e29-bc35-26aafb656d48
subfeature_v2:
  - id: f529d0bd-1401-4c88-9833-43228cc1d40f
  - id: d6330382-c886-4f7a-a4f7-74e3f36c0d9c
  - id: f5293531-9312-4099-bfa3-9e67df6a8750
  - id: efa38731-2723-4334-8d8b-a778af834835
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 198
ht-degree: 88%

---

# Informazioni sulle richieste di accesso a dati personali {#privacy-requests}



Per una presentazione generale sulla gestione della privacy, consulta [questa sezione](privacy-management.md).

Queste informazioni si applicano alle normative GDPR, CCPA, PDPA e LGPD. Per ulteriori informazioni su tali normative, consulta [questa sezione](privacy-management.md#privacy-management-regulations).

>[!NOTE]
>
>La rinuncia alla vendita di informazioni personali, specifica del CCPA, è spiegata in [questa sezione](#sale-of-personal-information-ccpa).

<!--Installation procedures described in this document are applicable starting Campaign Classic 18.4 (build 8931+). If you are running on a previous version, refer to this [technote](https://helpx.adobe.com/campaign/kb/how-to-install-gdpr-package-on-legacy-versions.html).-->

Per aiutarti a garantire l’idoneità alle normative sulla privacy, Adobe Campaign consente di gestire le richieste di accesso ed eliminazione. Il **diritto di accesso** e il **diritto all’oblio** (richiesta di eliminazione) sono illustrati in [questa sezione](privacy-management.md#right-access-forgotten).

Adobe Campaign offre ai titolari del trattamento dei dati due possibilità per eseguire le richieste di accesso e cancellazione dei dati personali:

* Tramite l’**interfaccia di Adobe Campaign**: per ogni richiesta di accesso a dati personali, il titolare del trattamento dei dati crea una nuova richiesta di accesso ai dati personali in Adobe Campaign. Vedi [questa sezione](privacy-requests-ui.md).
* Tramite **API**: Adobe Campaign fornisce un’API che consente il processo automatico delle richieste di accesso a dati personali utilizzando SOAP. Vedi [questa sezione](privacy-requests-api.md).

>[!NOTE]
>
>* Per ulteriori informazioni sui dati personali e sulle diverse entità che gestiscono i dati (titolare del trattamento, responsabile del trattamento e interessato), consulta [Dati personali e utenti tipo](privacy-and-recommendations.md#personal-data).
>* Per ulteriori informazioni sulle richieste di accesso a dati personali, consulta la [documentazione di Campaign v8](https://experienceleague.adobe.com/it/docs/campaign/campaign-v8/privacy/privacy){target=_blank}.

<!--
## Prerequisites {#prerequesites}

Adobe Campaign offers Data Controllers tools to create and process Privacy requests for data stored in Adobe Campaign. However, it is the Data Controller's responsibility to handle the relationship with the Data Subject (email, customer care or a web portal).

It is therefore your responsibility as a Data Controller to confirm the identity of the Data Subject making the request and to confirm that the data returned to the requester is about the Data Subject.

## Installing the Privacy package {#install-privacy-package}

In order to use this feature, you need to install the **[!UICONTROL Privacy Data Protection Regulation]** package via the **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** > **[!UICONTROL Adobe Campaign Package]** menu. For more information on how to install packages, refer to the [detailed documentation](../../installation/using/installing-campaign-standard-packages.md).

Two new folders, specific to Privacy, are created under **[!UICONTROL Administration]** > **[!UICONTROL Platform]**:

* **[!UICONTROL Privacy Requests]**: this is where you will create your Privacy requests and track their evolution.
* **[!UICONTROL Namespaces]**: this is where you will define the field that will be used to identify the Data Subject in the Adobe Campaign database.

![](assets/privacy-folders.png)

In **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**, three technical workflows run every day to process Privacy requests.

![](assets/privacy-workflows.png)

* **[!UICONTROL Collect privacy requests]**: this workflow generates the recipient's data stored in Adobe Campaign and makes it available for download in the privacy request's screen.
* **[!UICONTROL Delete privacy requests data]**: this workflow deletes the recipient's data stored in Adobe Campaign.
* **[!UICONTROL Privacy request cleanup]**: this workflow erases the access request files that are older than 90 days.

In **[!UICONTROL Administration]** > **[!UICONTROL Access Management]** > **[!UICONTROL Named rights]**, the **[!UICONTROL Privacy Data Right]** named right has been added. This named right is required for Data Controllers in order for them to use privacy tools. This allows them to create new requests, track their evolution, use the API, etc.

![](assets/privacy-right.png)

## Namespaces {#namesspaces}

Before creating Privacy requests, you need to define the namespace you will use. This is the key that will be used to identify the Data Subject in the Adobe Campaign database.

Three namespaces are available out-of-the-box: email, phone and mobile phone. If you need a different namespace (a recipient custom field, for example), you can create a new one from **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Namespaces]**.

>[!NOTE]
>
>For optimal performance, it is recommended to use out-of-the-box namespaces.
-->