---
solution: Campaign Classic
product: campaign
title: Configurazione di Adobe I/O per i trigger Adobe Experience Cloud
description: Scopri come configurare  Adobe I/O per Adobe Experience Cloud Triggers
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 5639f08ad709597d5f5c9e6bbd6932cffcbde40f
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 4%

---


# Configurazione di Adobe I/O per i trigger Adobe Experience Cloud {#configuring-adobe-io}

>[!CAUTION]
>
>Se utilizzi una versione precedente dell&#39;integrazione Triggers tramite autenticazione, **devi passare a  Adobe I/O come descritto di seguito**. La modalità di autenticazione legacy verrà ritirata il 30 aprile 2021. [Ulteriori informazioni](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411)

## Prerequisiti {#adobe-io-prerequisites}

Questa integrazione si applica solo a partire dalle versioni **Campaign Classic 20.3 e Gold Standard 11**.

Prima di avviare l&#39;implementazione, verifica di avere:

* un IMSOrgID valido: l’identificatore dell’organizzazione  Identity Management System (IMS) è l’identificatore univoco all’interno dell’Adobe Experience Cloud, utilizzato ad esempio per il servizio VisitorID e per l’SSO (IMS Single-Sign On),
* un accesso sviluppatore all’organizzazione IMS.

>[!NOTE]
>
>Per richiedere i privilegi di amministratore di sistema dell&#39;organizzazione IMS, seguite la procedura dettagliata [in questa pagina](https://helpx.adobe.com/ca/enterprise/admin-guide.html/ca/enterprise/using/manage-developers.ug.html) per fornire questo accesso a tutti i profili di prodotto.


## Passaggio 1: Creare/aggiornare  progetto Adobe I/O {#creating-adobe-io-project}

1. Accedete  Adobe I/O ed effettuate l&#39;accesso con il diritto di amministratore di sistema per IMSorg.

   >[!NOTE]
   >
   > Assicurati di aver effettuato l’accesso al portale IMSorg corretto.

1. Estrarre l&#39;ID client di integrazione esistente dal file di configurazione dell&#39;istanza ims/authIMSTAClientId. Attributo non esistente o vuoto che indica che l&#39;ID client non è configurato.

   >[!NOTE]
   >
   >Se l&#39;ID client è vuoto, è possibile **[!UICONTROL Create a New project]** direttamente in  Adobe I/O.

1. Identificate il progetto esistente utilizzando l&#39;ID client estratto. Cercate progetti esistenti con lo stesso ID client estratto nel passaggio precedente.

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

## Passaggio 2: Aggiungere le credenziali del progetto in  Adobe Campaign {#add-credentials-campaign}

Per aggiungere le credenziali di progetto in  Adobe Campaign, eseguite il comando seguente come utente &quot;neolano&quot; su tutti i contenitori dell&#39;istanza Adobe Campaign  per inserire le credenziali **[!UICONTROL Technical Account]** nel file di configurazione dell&#39;istanza.

```
nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID[/Client_Secret[/Base64_encoded_Private_Key]]
```

>[!NOTE]
>
>È necessario codificare la chiave privata in formato base64 UTF-8. Ricordare di rimuovere la nuova riga dalla chiave prima di codificarla, ad eccezione della chiave privata. La chiave privata deve essere la stessa utilizzata per creare l&#39;integrazione.

## Passaggio 3: Aggiorna tag pipeline {#update-pipelined-tag}

Per aggiornare il tag [!DNL pipelined], è necessario aggiornare il tipo di autenticazione per  progetto Adobe I/O nel file di configurazione **config-&lt; instance-name >.xml** come segue:

```
<pipelined ... authType="imsJwtToken"  ... />
```
