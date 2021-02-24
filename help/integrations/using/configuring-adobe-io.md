---
solution: Campaign Classic
product: campaign
title: Configurazione di Adobe I/O per i trigger Adobe Experience Cloud
description: Scoprite come configurare  Adobe I/O per  Adobe Experience Cloud Triggers
audience: integrations
content-type: reference
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 333d2221d4f86fe18232473385653ed8409adf54
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 6%

---


# Configurazione di Adobe I/O per i trigger Adobe Experience Cloud {#configuring-adobe-io}

>[!CAUTION]
>
>Se utilizzi una versione precedente dell&#39;integrazione Triggers tramite autenticazione, **devi passare al Adobe I/O  come descritto di seguito**. La modalità di autenticazione oAuth verrà ritirata il 30 aprile 2021. [Ulteriori informazioni](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411)
>
>Durante questo passaggio al Adobe I/O , alcuni attivatori in arrivo potrebbero andare persi.

## Prerequisiti {#adobe-io-prerequisites}

Questa integrazione si applica solo a partire dalle versioni **Campaign Classic 20.3, 20.2.4, 19.1.8 e Gold Standard 11**.

Prima di avviare l&#39;implementazione, verifica di avere:

* un **identificatore organizzazione** valido: l’identificatore dell’organizzazione  Identity Management System (IMS) è l’identificatore univoco all’interno dell’Adobe Experience Cloud, utilizzato ad esempio per il servizio VisitorID e per l’SSO (IMS Single-Sign On). [Ulteriori informazioni](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/organizations.html)
* **Accesso sviluppatore** all&#39;organizzazione.  Per richiedere i privilegi di amministratore di sistema dell&#39;organizzazione IMS, seguite la procedura dettagliata [in questa pagina](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/manage-developers.ug.html) per fornire questo accesso a tutti i profili di prodotto.

## Passaggio 1: Crea/aggiorna  progetto di Adobe I/O {#creating-adobe-io-project}

1. Accedete  Adobe I/O ed effettuate l&#39;accesso con il diritto di amministratore di sistema per l&#39;organizzazione IMS.

   >[!NOTE]
   >
   > Assicurarsi di aver eseguito l&#39;accesso al portale organizzazione corretto.

1. Estrarre l&#39;identificatore client di integrazione esistente (ID client) dal file di configurazione dell&#39;istanza ims/authIMSTAClientId. Attributo non esistente o vuoto che indica che l&#39;identificatore client non è configurato.

   >[!NOTE]
   >
   >Se l&#39;identificatore client è vuoto, è possibile **[!UICONTROL Create a New project]** direttamente in  Adobe I/O.

1. Identificate il progetto esistente utilizzando l&#39;identificatore client estratto. Cercare progetti esistenti con lo stesso identificatore client estratto nel passaggio precedente.

   ![](assets/do-not-localize/adobe_io_8.png)

1. Selezionare **[!UICONTROL + Add to Project]** e scegliere **[!UICONTROL API]**.

   ![](assets/do-not-localize/adobe_io_1.png)

1. Nella finestra **[!UICONTROL Add an API]**, selezionare **[!UICONTROL Adobe Analytics]**.

   ![](assets/do-not-localize/adobe_io_2.png)

1. Scegliete **[!UICONTROL Service Account (JWT)]** come tipo di autenticazione.

   ![](assets/do-not-localize/adobe_io_3.png)

1. Se l&#39;ID client era vuoto, selezionare **[!UICONTROL Generate a key pair]** per creare una coppia di chiavi pubblica e privata.

   ![](assets/do-not-localize/adobe_io_4.png)

1. Caricate la vostra chiave pubblica e fate clic su **[!UICONTROL Next]**.

   ![](assets/do-not-localize/adobe_io_5.png)

1. Scegliete il profilo di prodotto denominato **Analytics-&lt; Nome organizzazione >** e fate clic su **[!UICONTROL Save configured API]**.

   ![](assets/do-not-localize/adobe_io_6.png)

1. Dal progetto, seleziona **[!UICONTROL Service Account (JWT)]** e copia le informazioni seguenti:
   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

   ![](assets/do-not-localize/adobe_io_7.png)

>[!CAUTION]
>
> certificato di Adobe I/O scade dopo 12 mesi. È necessario generare una nuova coppia di chiavi ogni anno.

## Passaggio 2: Aggiungere le credenziali del progetto in  Adobe Campaign {#add-credentials-campaign}

Per aggiungere le credenziali di progetto in  Adobe Campaign, eseguite il comando seguente come utente &quot;neolano&quot; su tutti i contenitori dell&#39;istanza Adobe Campaign  per inserire le credenziali **[!UICONTROL Technical Account]** nel file di configurazione dell&#39;istanza.

```
nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID/<Client_Secret>/<Base64_encoded_Private_Key>
```

La chiave privata deve essere codificata in formato base64 UTF-8. Per eseguire questa operazione:

1. Utilizzare la chiave privata generata nel [Passaggio 1: Crea/aggiorna  sezione Progetto Adobe I/O](#creating-adobe-io-project). La chiave privata deve essere la stessa utilizzata per creare l&#39;integrazione.

1. Utilizzando questo [sito Web](https://www.base64encode.org/), copiate e incollate la chiave privata nel campo corrispondente.

   >[!NOTE]
   >
   >Talvolta, quando si copia o incolla la chiave privata, è possibile aggiungere automaticamente una riga aggiuntiva. Ricorda di rimuoverlo prima di codificare la chiave privata.

1. Fai clic su **[!UICONTROL Encode]**.

1. Utilizzate la vostra chiave privata appena generata, codificata in formato base64 UTF-8 per eseguire il comando descritto sopra.

## Passaggio 3: Aggiorna tag pipeline {#update-pipelined-tag}

Per aggiornare il tag [!DNL pipelined], è necessario aggiornare il tipo di autenticazione a  progetto di Adobe I/O nel file di configurazione **config-&lt; instance-name >.xml** come segue:

```
<pipelined ... authType="imsJwtToken"  ... />
```
