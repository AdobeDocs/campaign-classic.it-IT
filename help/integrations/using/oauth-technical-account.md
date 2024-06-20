---
product: campaign
title: Creazione e configurazione dell’account tecnico Adobe per le API
description: Ulteriori informazioni su come creare l’account API Adobe
role: User, Admin
level: Beginner
source-git-commit: efd09fd71069878a5096bfa3592e6ebbaa9dd4e4
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 1%

---

# Crea il tuo account tecnico Adobe {#create-service-account}

Le credenziali di autenticazione server-to-server consentono al server dell&#39;applicazione di generare token di accesso e di effettuare chiamate API per conto dell&#39;applicazione stessa. [Ulteriori informazioni](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/)

## Migrare le integrazioni esistenti {#migrate-jwt}

Le credenziali dell’account di servizio (JWT) sono diventate obsolete da Adobe. Le integrazioni di Campaign con le soluzioni e le app Adobe ora devono basarsi sulle credenziali server-to-server di OAuth.

Se hai implementato integrazioni in entrata o in uscita con Campaign prima di giugno 2024, devi aggiornare l’ambiente Campaign alla versione v7.4.1 e migrare l’account tecnico a oAuth come descritto [in questa documentazione](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration){target="_blank"}. Le credenziali dell’account di servizio (JWT) esistenti continueranno a funzionare fino al **27 gennaio 2025**.

Al termine della migrazione, devi associare le nuove credenziali a Campaign come descritto in [questa sezione](#add-credentials).

## Crea un nuovo account tecnico OAuth per le nuove integrazioni {#oauth-service}

Per creare l’account tecnico OAuth per le nuove integrazioni, segui questi passaggi:

1. Accedi alla console di Adobe Developer e accedi come **Amministratore di sistema** della tua organizzazione.

   Per ulteriori informazioni sui ruoli di amministratore, consulta questa [pagina](https://helpx.adobe.com/enterprise/using/admin-roles.html).

1. Fai clic su **[!UICONTROL Create a new project]**.

   ![](assets/api-account-1.png)

1. Clic **[!UICONTROL Add to Project]** e seleziona **[!UICONTROL API]**.

   ![](assets/api-account-2.png)

1. Seleziona il prodotto da integrare con Campaign e fai clic su **[!UICONTROL Next]**.

1. Scegli **[!UICONTROL OAuth Server-to-Server]** come tipo di autenticazione e fai clic su **[!UICONTROL Next]**.

   ![](assets/api-account-3.png)

1. Seleziona la **[!UICONTROL Product profile]** collegamento al progetto.

   Se necessario, puoi crearne una nuova. [Ulteriori informazioni](https://helpx.adobe.com/enterprise/using/manage-product-profiles.html)

1. Quindi, fai clic su **[!UICONTROL Save Configured API]**.

   ![](assets/api-account-4.png)

1. Dal progetto, in Credenziali seleziona [!DNL OAuth Server-to-Server] e copia le seguenti informazioni:

   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

## Aggiungere le credenziali del progetto OAuth in Adobe Campaign {#add-credentials}

Per aggiungere le credenziali del progetto OAuth in Adobe Campaign, segui i passaggi seguenti:

1. Accedi tramite SSH a ogni contenitore in cui è installata l’istanza di Adobe Campaign.

1. Aggiungi le credenziali del progetto OAuth in Adobe Campaign eseguendo il seguente comando come `neolane` utente. Verrà inserito il **[!UICONTROL Technical Account]** credenziali nel file di configurazione dell’istanza.

   ```
   nlserver config -instance:<instance_name> -setimsoauth:ims-org-id/client-id/technical-account-id/client-secret
   ```
