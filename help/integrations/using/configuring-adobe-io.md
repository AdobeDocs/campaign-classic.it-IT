---
product: campaign
title: Configurazione di Adobe I/O per i trigger Adobe Experience Cloud
description: Scopri come configurare Adobe I/O per Adobe Experience Cloud Triggers
audience: integrations
content-type: reference
index: y
internal: n
snippet: y
exl-id: ab30f697-3022-4a29-bbdb-14ca12ec9c3e
source-git-commit: 8e18a3633e6b806a971678d985c55c123854438e
workflow-type: tm+mt
source-wordcount: '673'
ht-degree: 4%

---

# Configurazione di Adobe I/O per i trigger Adobe Experience Cloud {#configuring-adobe-io}

>[!CAUTION]
>
>Se utilizzi una versione precedente dell&#39;integrazione Triggers tramite autenticazione oAuth, **devi passare all&#39;Adobe I/O come descritto di seguito**. La modalità di autenticazione oAuth legacy con Campaign con verrà ritirata il 30 novembre 2021. [Ulteriori informazioni](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411)
>
>Durante questo passaggio a [!DNL Adobe I/O], alcuni trigger in arrivo potrebbero andare persi.

## Prerequisiti {#adobe-io-prerequisites}

Questa integrazione si applica solo a partire da **Campaign Classic 20.3, 20.2.4, 19.1.8 e [!DNL Gold Standard] 11 versioni**.

Prima di avviare questa implementazione, controlla di avere:

* un **identificatore organizzazione** valido: l’identificatore dell’organizzazione IMS (Identity Management System) è l’identificatore univoco all’interno di Adobe Experience Cloud, utilizzato ad esempio per il servizio VisitorID e per l’accesso singolo IMS (SSO). [Ulteriori informazioni](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/organizations.html)
* a **Accesso sviluppatore** alla tua organizzazione. L’amministratore di sistema dell’organizzazione IMS deve seguire **Aggiungi gli sviluppatori a un singolo profilo di prodotto**
procedura dettagliata [in questa pagina](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/manage-developers.ug.html) per fornire agli sviluppatori l&#39;accesso per il profilo di prodotto `Analytics - {tenantID}` del prodotto Adobe Analytics associato a Triggers.

## Passaggio 1: Crea/aggiorna progetto di Adobe I/O {#creating-adobe-io-project}

1. Accedi a [!DNL Adobe I/O] e accedi con l’accesso per sviluppatori dell’organizzazione IMS.

   >[!NOTE]
   >
   > Assicurati di aver effettuato l&#39;accesso al portale organizzazione corretto.

1. Estrai l&#39;identificatore client esistente (ID client) dal file di configurazione dell&#39;istanza ims/authIMSTAClientId. L&#39;attributo non esistente o vuoto indica che l&#39;identificatore client non è configurato.

   >[!NOTE]
   >
   >Se l&#39;identificatore client è vuoto, puoi direttamente **[!UICONTROL Create a New project]** in Adobe I/O.

1. Identifica il progetto esistente utilizzando l’identificatore client estratto. Cerca progetti esistenti con lo stesso ID client di quello estratto nel passaggio precedente.

   ![](assets/do-not-localize/adobe_io_8.png)

1. Seleziona **[!UICONTROL + Add to Project]** e scegli **[!UICONTROL API]**.

   ![](assets/do-not-localize/adobe_io_1.png)

1. Nella finestra **[!UICONTROL Add an API]**, selezionare **[!UICONTROL Adobe Analytics]**.

   ![](assets/do-not-localize/adobe_io_2.png)

1. Scegli **[!UICONTROL Service Account (JWT)]** come tipo di autenticazione.

   ![](assets/do-not-localize/adobe_io_3.png)

1. Se l’ID client era vuoto, selezionare **[!UICONTROL Generate a key pair]** per creare una coppia di chiavi pubblica e privata.

   Le chiavi vengono quindi scaricate automaticamente con una data di scadenza predefinita di 365 giorni. Una volta scaduta, dovrai creare una nuova coppia di chiavi e aggiornare l’integrazione nel file di configurazione. Utilizzando l&#39;opzione 2, puoi scegliere di creare e caricare manualmente il **[!UICONTROL Public key]** con una data di scadenza più lunga.

   >[!CAUTION]
   >
   >È necessario salvare il file config.zip quando viene visualizzato il prompt di download, poiché non sarà più possibile scaricarlo di nuovo.

   ![](assets/do-not-localize/adobe_io_4.png)

1. Fai clic su **[!UICONTROL Next]**.

   ![](assets/do-not-localize/adobe_io_5.png)

1. Scegli un **[!UICONTROL Product profile]** esistente o creane uno nuovo, se necessario. Non è richiesta alcuna autorizzazione per questo **[!UICONTROL Product profile]**. Per ulteriori informazioni su [!DNL Analytics] **[!UICONTROL Product Profiles]**, consulta la [documentazione di Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html#admin-console).

   Quindi, fai clic su **[!UICONTROL Save configured API]**.

   ![](assets/do-not-localize/adobe_io_6.png)

1. Dal progetto, seleziona **[!UICONTROL Adobe Analytics]** e copia le seguenti informazioni in **[!UICONTROL Service Account (JWT)]**:

   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

   ![](assets/do-not-localize/adobe_io_7.png)

>[!CAUTION]
>
>Il certificato di Adobe I/O scade dopo 12 mesi. Devi generare una nuova coppia di chiavi ogni anno.

## Passaggio 2: Aggiungere le credenziali del progetto in Adobe Campaign {#add-credentials-campaign}

>[!NOTE]
>
>Questo passaggio non è necessario se l&#39;identificatore client non è vuoto nel [passaggio 1: Crea/aggiorna progetto Adobe I/O](#creating-adobe-io-project).

La chiave privata deve essere codificata in formato UTF-8 base64. Per eseguire questa operazione:

1. Utilizza la chiave privata generata nel [Passaggio 1: Crea/aggiorna la sezione Progetto Adobe I/O](#creating-adobe-io-project). La chiave privata deve essere la stessa utilizzata per creare l’integrazione.

1. Codifica la chiave privata utilizzando il seguente comando: `base64 ./private.key > private.key.base64`. In questo modo il contenuto base64 verrà salvato in un nuovo file `private.key.base64`.

   >[!NOTE]
   >
   >Talvolta è possibile aggiungere automaticamente righe extra quando si copia/incolla la chiave privata. Ricorda di rimuoverlo prima di codificare la chiave privata.

1. Copia il contenuto dal file `private.key.base64`.

1. Accedi tramite SSH a ciascun contenitore in cui è installata l’istanza Adobe Campaign e aggiungi le credenziali Progetto in Adobe Campaign eseguendo il seguente comando come utente `neolane`. Questo inserirà le credenziali **[!UICONTROL Technical Account]** nel file di configurazione dell&#39;istanza.

   ```
   nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID/<Client_Secret>/<Base64_encoded_Private_Key>
   ```

## Passaggio 3: Aggiorna tag pipeline {#update-pipelined-tag}

>[!NOTE]
>
>Questo passaggio non è necessario se l&#39;identificatore client non è vuoto nel [passaggio 1: Crea/aggiorna progetto Adobe I/O](#creating-adobe-io-project).

Per aggiornare il tag [!DNL pipelined], è necessario aggiornare il tipo di autenticazione al progetto di Adobe I/O nel file di configurazione **config-&lt; instance-name >.xml** come segue:

```
<pipelined ... authType="imsJwtToken"  ... />
```

Quindi, esegui un `config -reload` e un riavvio del [!DNL pipelined] per tenere conto delle modifiche.
