---
solution: Campaign Classic
product: campaign
title: Come utilizzare i dati dei flussi di lavoro
description: Scopri come utilizzare i dati del flusso di lavoro
audience: workflow
content-type: reference
topic-tags: -general-operation
translation-type: tm+mt
source-git-commit: 49f3c123cb8e91b3a2a2a1eb6bd593a242b8bbfe
workflow-type: tm+mt
source-wordcount: '923'
ht-degree: 3%

---


# Come utilizzare i dati dei flussi di lavoro{#how-to-use-workflow-data}

## Aggiornamento del database {#updating-the-database}

Tutti i dati raccolti possono essere utilizzati per aggiornare il database o nelle consegne. Ad esempio, puoi arricchire le possibilità di personalizzazione dei contenuti dei messaggi (includere il numero di contratti nel messaggio, specificare il carrello medio degli acquisti nell&#39;ultimo anno, ecc.) o targeting dettagliato della popolazione (inviare un messaggio ai co-possessori del contratto, indirizzare i 1000 migliori abbonati ai servizi online, ecc.). Questi dati possono essere esportati o archiviati in un elenco.

### Elenchi e aggiornamenti diretti {#lists-and-direct-updates}

I dati del database Adobe Campaign  e gli elenchi esistenti possono essere aggiornati utilizzando due attività dedicate:

* L&#39;attività **[!UICONTROL List update]** consente di memorizzare le tabelle di lavoro in un datalist.

   Potete selezionare un elenco esistente o crearlo. In questo caso, vengono calcolati il nome e, eventualmente, la cartella del record.

   ![](assets/s_user_create_list.png)

   Fare riferimento a [Aggiornamento elenco](../../workflow/using/list-update.md).

* L&#39;attività **[!UICONTROL Update data]** esegue un aggiornamento di massa dei campi nel database.

   Per ulteriori informazioni, fare riferimento a [Aggiorna dati](../../workflow/using/update-data.md).

### Gestione iscrizione/annullamento sottoscrizione {#subscription-unsubscription-management}

Per informazioni su come iscriversi e annullare l&#39;iscrizione a un servizio di informazioni tramite un flusso di lavoro, consultare [Subscription Services](../../workflow/using/subscription-services.md).

## Invio tramite un flusso di lavoro {#sending-via-a-workflow}

### Attività di consegna {#delivery-activity}

L&#39;attività di consegna è dettagliata in [Consegna](../../workflow/using/delivery.md).

### Arricchimento e targeting delle consegne {#enriching-and-targeting-deliveries}

Le consegne possono elaborare i dati dai flussi di lavoro per personalizzare i contenuti o nel quadro della selezione della popolazione di destinazione.

Ad esempio, nell’ambito di una consegna diretta per posta, potete includere nel file di estrazione i dati aggiuntivi, tratti dalla manipolazione dei dati eseguita nel flusso di lavoro:

![](assets/s_advuser_add_data_postal_mail.png)

Oltre ai campi di personalizzazione standard, puoi aggiungere campi di personalizzazione dalle fasi del flusso di lavoro ai contenuti per la distribuzione. I dati aggiuntivi definiti nelle attività del flusso di lavoro possono essere conservati e resi accessibili nella procedura guidata di consegna, come illustrato nell&#39;esempio seguente, per definire il nome del file di output nel quadro della consegna diretta:

![](assets/s_advuser_using_additional_data.png)

I dati contenuti nella tabella del flusso di lavoro sono identificati dal relativo nome: è sempre composto dal collegamento **targetData**. Per ulteriori informazioni, fare riferimento a [Dati di destinazione](../../workflow/using/data-life-cycle.md#target-data).

Nel quadro della distribuzione delle e-mail, i campi di personalizzazione possono anche utilizzare i dati provenienti dall&#39;estensione di destinazione eseguita nelle fasi del flusso di lavoro di targeting, come illustrato nell&#39;esempio seguente:

![](assets/s_advuser_add_data_email.png)

Se un codice del segmento viene specificato in un&#39;attività di targeting, viene aggiunto a una colonna specifica della tabella del flusso di lavoro e viene offerto insieme ai campi di personalizzazione. Per visualizzare tutti i campi di personalizzazione, fai clic sul collegamento **[!UICONTROL Target extension > Other...]** accessibile tramite il pulsante di personalizzazione.

![](assets/s_advuser_segment_code_select.png)

## Esportazione di dati {#exporting-data}

### ZIP o cifratura di un file {#zipping-or-encrypting-a-file}

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

* [Estrazione o decrittografia di un file prima dell&#39;elaborazione](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing)
* [Attività](../../workflow/using/extraction--file-.md) di estrazione dei dati (file).

### Caso di utilizzo: Cifratura ed esportazione di dati utilizzando una chiave installata nel Pannello di controllo Campaign {#use-case-gpg-encrypt}

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

### Video di esercitazione {#video}

Questo video mostra come utilizzare una chiave GPG per cifrare i dati è disponibile anche in

>[!VIDEO](https://video.tv.adobe.com/v/36399?quality=12)

Ulteriori video dimostrativi sui Campaign Classic sono disponibili [qui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=it).
