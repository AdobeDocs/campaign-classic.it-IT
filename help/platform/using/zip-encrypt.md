---
product: campaign
title: Compressione o crittografia di un file
description: Scopri come comprimere o crittografare un file in Campaign prima dell’elaborazione
feature: Data Management, Encryption
badge-v7: label="v7" type="Informative" tooltip="Applicabile a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 4596638c-d75a-4e07-a2d8-5befcaad3430
source-git-commit: 58998fa2480a33776507a434ed846541ac19e58b
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 5%

---

# Comprimere o crittografare un file {#zipping-or-encrypting-a-file}

Adobe Campaign consente di esportare file compressi o crittografati. Quando si definisce un’esportazione tramite un **[!UICONTROL Data extraction (file)]** attività, puoi definire una post-elaborazione da comprimere o crittografare il file.

Per poterlo fare:

1. Installare una coppia di chiavi GPG per l’istanza utilizzando [Pannello di controllo Campaign](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/gpg-keys-management.html#encrypting-data).

   >[!NOTE]
   >
   >Il Pannello di controllo Campaign è riservato agli utenti amministratori ed è disponibile solo per alcune versioni di Campaign. [Ulteriori informazioni](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=it)
   >

1. Se l’installazione di Adobe Campaign è ospitata da Adobe, contatta [Assistenza clienti Adobe](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) per installare le utility necessarie sul server.
1. Se l’installazione di Adobe Campaign è on-premise, installa l’utility che desideri utilizzare (ad esempio: GPG, GZIP) nonché le chiavi necessarie (chiave di crittografia) sul server applicazioni.

Puoi quindi utilizzare comandi o codice nel **[!UICONTROL Script]** scheda dell’attività o in una **[!UICONTROL JavaScript code]** attività. Un esempio è presentato nel caso d’uso seguente.

**Argomenti correlati:**

* [Decomprimere o decrittografare un file prima dell’elaborazione](../../platform/using/unzip-decrypt.md)
* [Attività di estrazione dati (file)](../../workflow/using/extraction--file-.md).

## Caso d’uso: crittografare ed esportare dati utilizzando una chiave installata sul Pannello di controllo Campaign {#use-case-gpg-encrypt}

In questo caso d’uso, creeremo un flusso di lavoro per crittografare ed esportare i dati utilizzando una chiave installata sul Pannello di controllo Campaign.

![](assets/do-not-localize/how-to-video.png) [Guarda il video su questa funzione](#video)

I passaggi per eseguire questo caso d’uso sono i seguenti:

1. Genera una coppia di chiavi GPG (pubblica/privata) utilizzando un’utility GPG, quindi installa la chiave pubblica sul Pannello di controllo Campaign. I passaggi dettagliati sono disponibili in [Documentazione del Pannello di controllo Campaign](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/gpg-keys-management.html#encrypting-data).

1. In Campaign Classic, crea un flusso di lavoro per esportare i dati e crittografarli utilizzando la chiave privata installata tramite il Pannello di controllo Campaign. A tal fine, verrà creato un flusso di lavoro come segue:

   ![](assets/gpg-workflow-encrypt.png)

   * **[!UICONTROL Query]** attività: in questo esempio, desideri eseguire una query per eseguire il targeting dei dati dal database che desideri esportare.
   * **[!UICONTROL Data extraction (file)]** activity (attività): estrae i dati in un file.
   * **[!UICONTROL JavaScript code]** attività: crittografa i dati da estrarre.
   * **[!UICONTROL File transfer]** attività: invia i dati a un’origine esterna (in questo esempio, un server SFTP).

1. Configurare **[!UICONTROL Query]** per eseguire il targeting dei dati desiderati dal database. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../workflow/using/query.md).

1. Apri **[!UICONTROL Data extraction (file)]** quindi configurarlo in base alle tue esigenze. I concetti globali su come configurare l’attività sono disponibili in [questa sezione](../../workflow/using/extraction--file-.md).

   ![](assets/gpg-data-extraction.png)

1. Apri **[!UICONTROL JavaScript code]** attività, quindi copia e incolla il comando seguente per crittografare i dati da estrarre.

   >[!IMPORTANT]
   >
   >Assicurati di sostituire il **impronta digitale** valore dal comando con l&#39;impronta digitale della chiave pubblica installata sul Pannello di controllo Campaign.

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

1. Apri **[!UICONTROL File transfer]** , quindi specifica il server SFTP a cui inviare il file. I concetti globali su come configurare l’attività sono disponibili in [questa sezione](../../workflow/using/file-transfer.md).

   ![](assets/gpg-file-transfer.png)

1. Ora puoi eseguire il flusso di lavoro. Una volta eseguita, la destinazione dati dalla query verrà esportata sul server SFTP in un file .gpg crittografato.

## Video tutorial {#video}

Questo video mostra come utilizzare una chiave GPG per crittografare i dati è disponibile anche in

>[!VIDEO](https://video.tv.adobe.com/v/36399?quality=12)

Sono disponibili altri video dimostrativi sui Campaign Classic [qui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=it).
