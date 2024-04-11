---
product: campaign
title: Gestire le richieste di accesso ai dati personali
description: Scopri di più sulle richieste di accesso ai dati personali
feature: Privacy, Privacy Tools
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: c7688c2a-f0a7-4c51-a4cf-bf96fe8bf9b6
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 100%

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
>Per ulteriori informazioni sui dati personali e sulle diverse entità che gestiscono i dati (titolare del trattamento, responsabile del trattamento e interessato), consulta [Dati personali e utenti tipo](privacy-and-recommendations.md#personal-data).

## Prerequisiti {#prerequesites}

 Adobe Campaign offre ai titolari del trattamento strumenti per creare ed elaborare richieste di accesso a dati personali per i dati memorizzati in Adobe Campaign. La gestione del rapporto con l’interessato (tramite e-mail, assistenza clienti o un portale web) rimane tuttavia responsabilità del titolare del trattamento.

In qualità di titolare del trattamento, avrai pertanto la responsabilità di confermare l’identità dell’interessato che presenta la richiesta e confermare che i dati restituiti al richiedente riguardano l’interessato.

## Installazione del pacchetto Privacy {#install-privacy-package}

Per utilizzare questa funzione, è necessario installare il pacchetto **[!UICONTROL Privacy Data Protection Regulation]** tramite il menu **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** > **[!UICONTROL Adobe Campaign Package]**. Per ulteriori informazioni su come installare i pacchetti, consulta la [documentazione dettagliata](../../installation/using/installing-campaign-standard-packages.md).

Due nuove cartelle, specifiche di Privacy, vengono create in **[!UICONTROL Administration]** > **[!UICONTROL Platform]**:

* **[!UICONTROL Privacy Requests]**: qui puoi creare le richieste di Privacy e tracciarne l’evoluzione.
* **[!UICONTROL Namespaces]**: questo campo verrà utilizzato per identificare l’interessato nel database di Adobe Campaign.

![](assets/privacy-folders.png)

In **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**, tre flussi di lavoro tecnici vengono eseguiti ogni giorno per elaborare le richieste relative ai dati personali.

![](assets/privacy-workflows.png)

* **[!UICONTROL Collect privacy requests]**: questo flusso di lavoro genera i dati del destinatario memorizzati in Adobe Campaign e li rende disponibili per il download nella schermata della richiesta di accesso a dati personali.
* **[!UICONTROL Delete privacy requests data]**: questo flusso di lavoro elimina i dati del destinatario memorizzati in Adobe Campaign.
* **[!UICONTROL Privacy request cleanup]**: questo flusso di lavoro cancella i file di richiesta di accesso che sono stati creati da più di 90 giorni.

In **[!UICONTROL Administration]** > **[!UICONTROL Access Management]** > **[!UICONTROL Named rights]** è stata aggiunta l’autorizzazione denominata **[!UICONTROL Privacy Data Right]**. Questa autorizzazione denominata è necessaria per i titolari del trattamento dei dati affinché possano utilizzare gli strumenti per la privacy. Consente loro di creare nuove richieste, tracciare la loro evoluzione, utilizzare l’API, ecc.

![](assets/privacy-right.png)

## Spazi dei nomi {#namesspaces}

Prima di creare le richieste di accesso a dati personali, è necessario definire lo spazio dei nomi che verrà utilizzato. Questa chiave verrà utilizzata per identificare l’interessato nel database di Adobe Campaign.

Sono disponibili tre namespace predefiniti: e-mail, telefono e cellulare. Se hai bisogno di un namespace diverso (ad esempio un campo destinatario personalizzato), puoi crearne uno nuovo da **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Namespaces]**.

>[!NOTE]
>
>Per ottenere prestazioni ottimali, si consiglia di utilizzare gli spazi dei nomi predefiniti.
