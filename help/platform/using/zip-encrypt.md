---
product: campaign
title: Compressione o crittografia di un file
description: Scopri come comprimere o crittografare un file in Campaign prima dell’elaborazione
feature: Data Management, Encryption
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 4596638c-d75a-4e07-a2d8-5befcaad3430
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 5%

---

# Comprimere o crittografare un file {#zipping-or-encrypting-a-file}

Adobe Campaign consente di esportare file compressi o crittografati. Quando definisci un&#39;esportazione tramite un&#39;attività **[!UICONTROL Data extraction (file)]**, puoi definire una post-elaborazione da comprimere o crittografare il file.

Per poterlo fare:

1. Installa una coppia di chiavi GPG per l&#39;istanza utilizzando [Pannello di controllo Campaign](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/gpg-keys-management.html?lang=it#encrypting-data).

   >[!NOTE]
   >
   >Il Pannello di controllo Campaign è riservato agli utenti amministratori ed è disponibile solo per alcune versioni di Campaign. [Ulteriori informazioni](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=it)
   >

1. Se l&#39;installazione di Adobe Campaign è ospitata da Adobe, contatta l&#39;[Assistenza clienti Adobe](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) per installare le utility necessarie sul server.
1. Se l’installazione di Adobe Campaign è on-premise, installa l’utility che desideri utilizzare (ad esempio: GPG, GZIP) nonché le chiavi necessarie (chiave di crittografia) sul server applicazioni.

È quindi possibile utilizzare comandi o codice nella scheda **[!UICONTROL Script]** dell&#39;attività o in un&#39;attività **[!UICONTROL JavaScript code]**. Un esempio è presentato nel caso d’uso seguente.

**Argomenti correlati:**

* [Decomprimere o decrittografare un file prima dell’elaborazione](../../platform/using/unzip-decrypt.md)
* [Attività di estrazione dati (file)](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/extraction-file.html?lang=it){target="_blank"}

## Caso d’uso: crittografare ed esportare dati utilizzando una chiave installata sul Pannello di controllo Campaign {#use-case-gpg-encrypt}

In questo caso d’uso, creeremo un flusso di lavoro per crittografare ed esportare i dati utilizzando una chiave installata sul Pannello di controllo Campaign.

![](assets/do-not-localize/how-to-video.png) [Guarda il video su questa funzione](#video)

I passaggi per eseguire questo caso d’uso sono i seguenti:

1. Genera una coppia di chiavi GPG (pubblica/privata) utilizzando un’utility GPG, quindi installa la chiave pubblica sul Pannello di controllo Campaign. I passaggi dettagliati sono disponibili nella [documentazione del Pannello di controllo Campaign](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/gpg-keys-management.html?lang=it#encrypting-data).

1. In Campaign Classic, crea un flusso di lavoro per esportare i dati e crittografarli utilizzando la chiave privata installata tramite il Pannello di controllo Campaign. A tal fine, verrà creato un flusso di lavoro come segue:

   ![](assets/gpg-workflow-encrypt.png)

   * Attività **[!UICONTROL Query]**: in questo esempio, si desidera eseguire una query per eseguire il targeting dei dati del database che si desidera esportare.
   * Attività **[!UICONTROL Data extraction (file)]**: estrae i dati in un file.
   * Attività **[!UICONTROL JavaScript code]**: crittografa i dati da estrarre.
   * Attività **[!UICONTROL File transfer]**: invia i dati a un&#39;origine esterna (in questo esempio, un server SFTP).

1. Configurare l&#39;attività **[!UICONTROL Query]** in modo che esegua il targeting dei dati desiderati dal database. Consulta la [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/query.html?lang=it){target="_blank"}.

1. Apri l&#39;attività **[!UICONTROL Data extraction (file)]** e configurala in base alle tue esigenze. I concetti globali su come configurare l&#39;attività sono disponibili nella [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/extraction-file.html?lang=it){target="_blank"}.

   ![](assets/gpg-data-extraction.png)

1. Apri l&#39;attività **[!UICONTROL JavaScript code]**, quindi copia e incolla il comando seguente per crittografare i dati da estrarre.

   >[!IMPORTANT]
   >
   >Assicurarsi di sostituire il valore **impronta digitale** dal comando con l&#39;impronta digitale della chiave pubblica installata nel Pannello di controllo Campaign.

   ```
   var cmd='gpg ';
   cmd += ' --trust-model always';
   cmd += ' --batch --yes';
   cmd += ' --recipient fingerprint';
   cmd += ' --encrypt --output ' + vars.filename + '.gpg ' + vars.filename;
   execCommand(cmd,true);
   vars.filename=vars.filename + '.gpg'
   ```

   ![](assets/gpg-script.png)

1. Apri l&#39;attività **[!UICONTROL File transfer]**, quindi specifica il server SFTP a cui inviare il file. I concetti globali su come configurare l&#39;attività sono disponibili nella [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/event-activities/file-transfer.html?lang=it){target="_blank"}.

   ![](assets/gpg-file-transfer.png)

1. Ora puoi eseguire il flusso di lavoro. Una volta eseguita, la destinazione dati dalla query verrà esportata sul server SFTP in un file .gpg crittografato.

## Video tutorial {#video}

Questo video mostra come utilizzare una chiave GPG per crittografare i dati è disponibile anche in

>[!VIDEO](https://video.tv.adobe.com/v/36399?quality=12)

Ulteriori video dimostrativi di Campaign Classic sono disponibili [qui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=it).
