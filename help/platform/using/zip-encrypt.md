---
solution: Campaign Classic
product: campaign
title: Zipping o cifratura di un file
description: Scoprite come comprimere o crittografare un file in Campaign Classic prima di elaborarlo.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: 1cde12d33551206da12e03a7e8deb198d427ab3a
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 3%

---


# ZIP o cifratura di un file {#zipping-or-encrypting-a-file}

 Adobe Campaign consente di esportare file compressi o crittografati. Quando si definisce un&#39;esportazione tramite un&#39;attività **[!UICONTROL Data extraction (file)]**, è possibile definire una post-elaborazione per comprimere o cifrare il file.

Per essere in grado di effettuare le seguenti operazioni:

1. Installate una coppia di chiavi GPG per la vostra istanza utilizzando il [Pannello di controllo Campaign](https://docs.adobe.com/content/help/en/control-panel/using/instances-settings/gpg-keys-management.html#encrypting-data).

   >[!NOTE]
   >
   >Il Pannello di controllo Campaign è disponibile per tutti i clienti ospitati su AWS (ad eccezione dei clienti che ospitano le proprie istanze di marketing in sede).

1. Se l&#39;installazione di  Adobe Campaign è ospitata da  Adobe, contatta  Assistenza clienti Adobe per avere installato sul server le utility necessarie.
1. Se l&#39;installazione di  Adobe Campaign è in sede, installate l&#39;utility da utilizzare (ad esempio: GPG, GZIP) e le chiavi necessarie (chiave di crittografia) sul server dell&#39;applicazione.

Potete quindi utilizzare i comandi o il codice nella scheda **[!UICONTROL Script]** dell&#39;attività o in un&#39;attività **[!UICONTROL JavaScript code]**. Un esempio è illustrato nel caso di utilizzo riportato di seguito.

**Argomenti correlati:**

* [Estrazione o decrittografia di un file prima dell&#39;elaborazione](../../platform/using/unzip-decrypt.md)
* [Attività](../../workflow/using/extraction--file-.md) di estrazione dei dati (file).

## Caso di utilizzo: Cifratura ed esportazione di dati utilizzando una chiave installata nel Pannello di controllo Campaign {#use-case-gpg-encrypt}

In questo caso, verrà creato un flusso di lavoro per la cifratura e l&#39;esportazione dei dati tramite una chiave installata sul Pannello di controllo Campaign.

![](assets/do-not-localize/how-to-video.png) [Scopri questa funzione nel video](#video)

Le operazioni da eseguire per questo caso di utilizzo sono le seguenti:

1. Generate una coppia di chiavi GPG (pubblica/privata) utilizzando un&#39;utility GPG, quindi installate la chiave pubblica sul Pannello di controllo Campaign. I passaggi dettagliati sono disponibili nella [documentazione del Pannello di controllo Campaign](https://docs.adobe.com/content/help/en/control-panel/using/instances-settings/gpg-keys-management.html#encrypting-data).

1. In Campaign Classic, creare un flusso di lavoro per esportare i dati e cifrarlo utilizzando la chiave privata installata tramite il Pannello di controllo Campaign. A tal fine, verrà creato un flusso di lavoro come segue:

   ![](assets/gpg-workflow-encrypt.png)

   * **[!UICONTROL Query]** activity: In questo esempio, si desidera eseguire una query per eseguire il targeting dei dati del database che si desidera esportare.
   * **[!UICONTROL Data extraction (file)]** activity: Estrae i dati in un file.
   * **[!UICONTROL JavaScript code]** activity: Cifra i dati da estrarre.
   * **[!UICONTROL File transfer]** activity: Invia i dati a un&#39;origine esterna (in questo esempio, un server SFTP).

1. Configurate l&#39;attività **[!UICONTROL Query]** per eseguire il targeting dei dati desiderati dal database. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../workflow/using/query.md).

1. Apri l&#39;attività **[!UICONTROL Data extraction (file)]**, quindi configurala in base alle tue esigenze. I concetti globali su come configurare l&#39;attività sono disponibili in [questa sezione](../../workflow/using/extraction--file-.md).

   ![](assets/gpg-data-extraction.png)

1. Aprite l&#39;attività **[!UICONTROL JavaScript code]**, quindi copiate e incollate il comando sottostante per cifrare i dati da estrarre.

   >[!IMPORTANT]
   >
   >Assicurarsi di sostituire il valore **impronte digitali** dal comando con l&#39;impronta digitale della chiave pubblica installata nel Pannello di controllo Campaign.

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

1. Aprite l&#39;attività **[!UICONTROL File transfer]**, quindi specificate il server SFTP al quale desiderate inviare il file. I concetti globali su come configurare l&#39;attività sono disponibili in [questa sezione](../../workflow/using/file-transfer.md).

   ![](assets/gpg-file-transfer.png)

1. Ora puoi eseguire il flusso di lavoro. Una volta eseguita, la destinazione dei dati dalla query verrà esportata nel server SFTP in un file .gpg crittografato.

## Video di esercitazione {#video}

Questo video mostra come utilizzare una chiave GPG per cifrare i dati è disponibile anche in

>[!VIDEO](https://video.tv.adobe.com/v/36399?quality=12)

Ulteriori video dimostrativi sui Campaign Classic sono disponibili [qui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=it).
