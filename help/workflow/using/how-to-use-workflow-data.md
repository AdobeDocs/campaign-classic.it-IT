---
title: Come utilizzare i dati del flusso di lavoro
seo-title: Come utilizzare i dati del flusso di lavoro
description: Come utilizzare i dati del flusso di lavoro
seo-description: null
page-status-flag: never-activated
uuid: ed03f14b-1b53-426e-9213-22cb2f3deb19
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: -general-operation
discoiquuid: ec3844ca-8d80-4ddc-b08c-f18a6919bb28
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b369a17fabc55607fc6751e7909e1a1cb3cd4201
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---


# Come utilizzare i dati del flusso di lavoro{#how-to-use-workflow-data}

## Aggiornamento del database {#updating-the-database}

Tutti i dati raccolti possono essere utilizzati per aggiornare il database o nelle consegne. Ad esempio, puoi arricchire le possibilità di personalizzazione dei contenuti dei messaggi (includere il numero di contratti nel messaggio, specificare il carrello medio degli acquisti nell&#39;ultimo anno, ecc.) o targeting dettagliato della popolazione (inviare un messaggio ai co-possessori del contratto, indirizzare i 1000 migliori abbonati ai servizi online, ecc.). Questi dati possono essere esportati o archiviati in un elenco.

### Elenchi e aggiornamenti diretti {#lists-and-direct-updates}

I dati del database Adobe Campaign e degli elenchi esistenti possono essere aggiornati utilizzando due attività dedicate:

* L&#39; **[!UICONTROL List update]** attività consente di memorizzare le tabelle di lavoro in un datalist.

   Potete selezionare un elenco esistente o crearlo. In questo caso, vengono calcolati il nome e, eventualmente, la cartella del record.

   ![](assets/s_user_create_list.png)

   Fare riferimento a Aggiornamento [](../../workflow/using/list-update.md)elenco.

* L&#39; **[!UICONTROL Update data]** attività esegue un aggiornamento di massa dei campi nel database.

   Per ulteriori informazioni, vedere [Aggiornamento dei dati](../../workflow/using/update-data.md).

### Gestione delle iscrizioni/annullamento delle iscrizioni {#subscription-unsubscription-management}

Per informazioni su come iscriversi e annullare l’iscrizione a un servizio di informazioni tramite un flusso di lavoro, consultate Servizi [](../../workflow/using/subscription-services.md)iscrizione.

## Invio tramite un flusso di lavoro {#sending-via-a-workflow}

### Attività di consegna {#delivery-activity}

L&#39;attività di consegna è dettagliata in [Consegna](../../workflow/using/delivery.md).

### Arricchimento e targeting delle consegne {#enriching-and-targeting-deliveries}

Le consegne possono elaborare i dati dai flussi di lavoro per personalizzare i contenuti o nel quadro della selezione della popolazione di destinazione.

Ad esempio, nell’ambito di una consegna diretta per posta, potete includere nel file di estrazione i dati aggiuntivi, tratti dalla manipolazione dei dati eseguita nel flusso di lavoro:

![](assets/s_advuser_add_data_postal_mail.png)

Oltre ai campi di personalizzazione standard, puoi aggiungere campi di personalizzazione dalle fasi del flusso di lavoro ai contenuti per la distribuzione. I dati aggiuntivi definiti nelle attività del flusso di lavoro possono essere conservati e resi accessibili nella procedura guidata di consegna, come illustrato nell&#39;esempio seguente, per definire il nome del file di output nel quadro della consegna diretta:

![](assets/s_advuser_using_additional_data.png)

I dati contenuti nella tabella del flusso di lavoro sono identificati dal relativo nome: è sempre composto dal collegamento **targetData** . Per ulteriori informazioni, fai riferimento ai dati [di](../../workflow/using/data-life-cycle.md#target-data)Target.

Nel quadro della distribuzione delle e-mail, i campi di personalizzazione possono anche utilizzare i dati provenienti dall&#39;estensione di destinazione eseguita nelle fasi del flusso di lavoro di targeting, come illustrato nell&#39;esempio seguente:

![](assets/s_advuser_add_data_email.png)

Se un codice del segmento viene specificato in un&#39;attività di targeting, viene aggiunto a una colonna specifica della tabella del flusso di lavoro e viene offerto insieme ai campi di personalizzazione. Per visualizzare tutti i campi di personalizzazione, fai clic sul **[!UICONTROL Target extension > Other...]** collegamento accessibile tramite il pulsante di personalizzazione.

![](assets/s_advuser_segment_code_select.png)

## Esportazione dei dati {#exporting-data}

### Zipping o cifratura di un file {#zipping-or-encrypting-a-file}

Adobe Campaign consente di esportare file compressi o crittografati. Quando definite un&#39;esportazione attraverso un&#39; **[!UICONTROL Data extraction (file)]** attività, potete definire una post-elaborazione per comprimere o cifrare il file.

Per essere in grado di effettuare le seguenti operazioni:

* Se l&#39;installazione di Adobe Campaign è ospitata da Adobe: inviare una richiesta all&#39; [Assistenza](https://support.neolane.net) per disporre delle utility necessarie installate sul server.
* Se l&#39;installazione di Adobe Campaign è in sede: installare l&#39;utility che si desidera utilizzare (ad esempio: GPG, GZIP) e le chiavi necessarie (chiave di crittografia) sul server dell&#39;applicazione.

Potete quindi utilizzare comandi o codice, ad esempio:

```
function encryptFile(file) {  
  var systemCommand = “gpg --encrypt --recipient  recipientToEncryptTo ” + file;  
  var result = execCommand(systemCommand, true); 
}
```

Quando importate un file, potete anche decomprimerlo o decrittografarlo. Consultate [Estrazione o decrittografia di un file prima dell’elaborazione](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing).
