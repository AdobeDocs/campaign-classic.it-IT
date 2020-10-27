---
title: Configurazione  I/O Adobe per Adobe Experience Cloud Triggers
seo-title: Configurazione  I/O Adobe per Adobe Experience Cloud Triggers
description: Configurazione  I/O Adobe per Adobe Experience Cloud Triggers
seo-description: null
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d15e953740b0a4dd8073b36fd59b4c4e44906340
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---


# Configurazione  I/O Adobe per Adobe Experience Cloud Triggers {#configuring-adobe-io}

Le configurazioni preliminari sono:

* Adobe Campaign Classic build ACC-19.1.9 o ACC-20.2.1 e versioni successive.
* un IMSOrgID valido.
* un accesso sviluppatore all’organizzazione IMS. È necessario richiedere i privilegi di amministratore di sistema dell&#39;organizzazione IMS per seguire la procedura descritta in questa [pagina](https://helpx.adobe.com/ca/enterprise/admin-guide.html/ca/enterprise/using/manage-developers.ug.html) per fornire questo accesso a tutti i profili di prodotto.

## Passaggio 1: Crea/aggiorna  progetto IO Adobe {#creating-adobe-io-project}

1. Accedete  I/O Adobe ed effettuate l&#39;accesso con il diritto di amministratore di sistema per IMSorg.

   >[!NOTE]
   >
   > Assicurati di aver effettuato l’accesso al portale IMSorg corretto.

1. Estrarre l&#39;ID client di integrazione esistente dal file di configurazione dell&#39;istanza ims/authIMSTAClientId. Attributo non esistente o vuoto che indica che l&#39;ID client non è configurato.

   >[!NOTE]
   >
   >Se l&#39;ID cliente è vuoto, puoi accedere direttamente **[!UICONTROL Create a New project]** all&#39;I/O  Adobe.

1. È ora necessario identificare il progetto esistente utilizzando l&#39;ID client estratto. Cercate progetti esistenti con lo stesso ID client estratto nel passaggio precedente.

   ![](assets/adobe_io_8.png)

1. Selezionate **[!UICONTROL + Add to Project]** e scegliete **[!UICONTROL API]**.

   ![](assets/adobe_io_1.png)

1. Nella finestra **[!UICONTROL Add an API]**, selezionare **[!UICONTROL Adobe Analytics]**.

   ![](assets/adobe_io_2.png)

1. Scegliere **[!UICONTROL Service Account (JWT)]** come tipo di autenticazione.

   ![](assets/adobe_io_3.png)

1. Se l&#39;ID client è vuoto, selezionate **[!UICONTROL Generate a key pair]** per creare una coppia di chiavi Pubblica e Privata.

   ![](assets/adobe_io_4.png)

1. Caricate la chiave pubblica e fate clic su **[!UICONTROL Next]**.

   ![](assets/adobe_io_5.png)

1. Scegliete il profilo di prodotto denominato **Analytics-&lt; Nome organizzazione >** e fate clic su **[!UICONTROL Save configured API]**.

   ![](assets/adobe_io_6.png)

1. Dal progetto, selezionate **[!UICONTROL Service Account (JWT)]** e copiate le seguenti informazioni:
   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

   ![](assets/adobe_io_7.png)

## Passaggio 2: Aggiungere le credenziali del progetto in  Adobe Campaign {#add-credentials-campaign}

Per aggiungere le credenziali di progetto in  Adobe Campaign, eseguite il comando seguente come utente neolane su tutti i contenitori dell&#39;istanza Adobe Campaign  per inserire le **[!UICONTROL Technical Account]** credenziali nel file di configurazione dell&#39;istanza.

```
nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID[/Client_Secret[/Base64_encoded_Private_Key]]
```

>[!NOTE]
>
>È necessario codificare la chiave privata in formato base64 UTF-8. Ricordare di rimuovere la nuova riga dalla chiave prima di codificarla, ad eccezione della chiave privata. La chiave privata deve essere la stessa utilizzata per creare l&#39;integrazione.

## Passaggio 3: Aggiorna tag pipeline {#update-pipelined-tag}

Per aggiornare [!DNL pipelined] il tag, è necessario aggiornare il tipo di autenticazione a  progetto IO Adobe nel file di configurazione **config-&lt; instance-name >.xml** come segue:

```
<pipelined ... authType="imsJwtToken"  ... />
```

>[!NOTE]
>
>Se utilizzi una versione precedente di Triggers Integration tramite token JWT legacy, devi anche aggiungere l&#39;API IO  Adobe per [!DNL Adobe Analytics] informazioni dettagliate nel primo passaggio per eseguire automaticamente la migrazione alla nuova autenticazione Triggers.
