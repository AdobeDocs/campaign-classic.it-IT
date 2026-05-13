---
product: campaign
title: Creare e configurare l’account tecnico Adobe per le API
description: Scopri come creare il tuo account API di Adobe
role: User, Admin
level: Intermediate, Experienced
exl-id: 5d830ea0-a0a3-4b35-8dc4-e955380431fb
TQID: https://experienceleague.adobe.com/cZi5LdGtTnT8wMtI8nmg3Ue5LPfTkn3OKFZkxxdg3F0
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: b12f6872-9271-4369-85e5-86969a0b99a2
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2:
  - id: c3bf7e1e-1db5-4c72-9293-e2f0b1ab73d0
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 366
ht-degree: 6%

---

# Creare un account tecnico Adobe personale {#create-service-account}

Le credenziali di autenticazione server-to-server consentono al server dell&#39;applicazione di generare token di accesso e di effettuare chiamate API per conto dell&#39;applicazione stessa. [Ulteriori informazioni](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/)

## Migrare le integrazioni esistenti {#migrate-jwt}

Le credenziali dell’account di servizio (JWT) sono diventate obsolete da Adobe. Le integrazioni di Campaign con le soluzioni e le app Adobe ora devono basarsi sulle credenziali server-to-server OAuth.

Se hai implementato integrazioni in entrata o in uscita con Campaign prima di giugno 2024, devi aggiornare l’ambiente Campaign alla versione v7.4.1 e migrare l’account tecnico a oAuth come descritto [in questa documentazione](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration){target="_blank"}. Le credenziali dell’account di servizio (JWT) esistenti continueranno a funzionare fino al **martedì 30 giugno 2025**.

Al termine della migrazione, devi associare le nuove credenziali a Campaign come descritto in [questa sezione](#add-credentials).

## Crea un nuovo account tecnico OAuth per le nuove integrazioni {#oauth-service}

Per creare l’account tecnico OAuth per le nuove integrazioni, segui questi passaggi:

1. Accedi alla console Adobe Developer e accedi come **Amministratore di sistema** della tua organizzazione.

   Per ulteriori informazioni sui ruoli di amministratore, consulta questa [pagina](https://helpx.adobe.com/enterprise/using/admin-roles.html).

1. Fai clic su **[!UICONTROL Create a new project]**.

   ![](assets/api-account-1.png)

1. Fare clic su **[!UICONTROL Add to Project]** e selezionare **[!UICONTROL API]**.

   ![](assets/api-account-2.png)

1. Selezionare il prodotto da integrare con Campaign e fare clic su **[!UICONTROL Next]**.

1. Scegliere **[!UICONTROL OAuth Server-to-Server]** come tipo di autenticazione e fare clic su **[!UICONTROL Next]**.

   ![](assets/api-account-3.png)

1. Seleziona il collegamento **[!UICONTROL Product profile]** al progetto.

   Se necessario, puoi crearne una nuova. [Ulteriori informazioni](https://helpx.adobe.com/enterprise/using/manage-product-profiles.html)

1. Quindi fare clic su **[!UICONTROL Save Configured API]**.

   ![](assets/api-account-4.png)

1. Nel progetto, in Credenziali, selezionare [!DNL OAuth Server-to-Server] e copiare le seguenti informazioni:

   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

## Aggiungere le credenziali del progetto OAuth in Campaign {#add-credentials}

Una volta eseguiti i passaggi precedenti, aggiungi le credenziali del progetto OAuth in Adobe Campaign.

>[!NOTE]
>
>In qualità di cliente di Cloud Services in hosting o gestito, questo passaggio non è necessario: Adobe ha già aggiunto le credenziali del progetto OAuth al tuo ambiente.
>

In qualità di cliente on-premise o ibrido, segui questi passaggi:

1. Accedi tramite SSH a ogni contenitore in cui è installata l’istanza di Adobe Campaign.

1. Aggiungi le credenziali del progetto OAuth in Adobe Campaign eseguendo il seguente comando come utente `neolane`. Verranno inserite le credenziali **[!UICONTROL Technical Account]** nel file di configurazione dell&#39;istanza.

   ```
   nlserver config -instance:<instance_name> -setimsoauth:ims-org-id/client-id/technical-account-id/client-secret
   ```

   >[!NOTE]
   >
   > Per le versioni precedenti alla versione 7.4.1, utilizzare `setimsauth` o `setimsjwtauth` anziché `setimsoauth`.


