---
product: campaign
title: Estrazione o decrittografia di un file
description: Scopri come decomprimere o decrittografare un file in Campaign prima dell’elaborazione
feature: Workflows, Encryption
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 1a79da3b-2abc-4bfc-a0ee-8471c478638d
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '709'
ht-degree: 10%

---


# Decomprimere o decrittografare un file {#unzipping-or-decrypting-a-file-before-processing}

Adobe Campaign consente di importare file compressi o crittografati. Prima di poter essere letti in un&#39;attività [Caricamento dati (file)](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/data-loading-file.html){target="_blank"}), puoi definire una pre-elaborazione per decomprimere o decrittografare il file.

>[!IMPORTANT]
>
>Non è possibile decomprimere file compressi di dimensioni superiori a 4 Gb.

Per poterlo fare:

1. Utilizza il [Pannello di controllo Campaign](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/gpg-keys-management.html#decrypting-data) per generare una coppia di chiavi pubblica/privata per consentire la decrittografia del file.

   >[!NOTE]
   >
   >Il Pannello di controllo è accessibile a tutti gli utenti amministratori. I passaggi per concedere a un utente l’accesso come amministratore sono descritti in[questa pagina](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=it#discover-control-panel).
   >
   >Tieni presente che l&#39;istanza deve essere ospitata su AWS e aggiornata con la [build GA più recente](../../rn/using/rn-overview.md). Scopri come controllare la versione in [questa sezione](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version). Per verificare se l’istanza è ospitata su AWS, segui i passaggi descritti in [questa sezione](https://experienceleague.adobe.com/docs/control-panel/using/faq.html?lang=it).

1. Se l’installazione di Adobe Campaign è on-premise, installa l’utility che desideri utilizzare (ad esempio: GPG, GZIP) nonché le chiavi necessarie (chiave di crittografia) sul server applicazioni.

   Se l&#39;installazione di Adobe Campaign è ospitata da Adobe, contatta l&#39;[Assistenza clienti Adobe](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) per installare le utility necessarie sul server.

Puoi quindi utilizzare nei flussi di lavoro i comandi di pre-elaborazione desiderati:

1. Aggiungi e configura un&#39;attività **[!UICONTROL File transfer]** nel flusso di lavoro.
1. Aggiungi un&#39;attività **[!UICONTROL Data loading (file)]** e definisci il formato del file.
1. Seleziona l’opzione **[!UICONTROL Pre-process the file]**.
1. Selezionare il comando di pre-elaborazione da applicare.
1. Aggiungi altre attività per gestire i dati provenienti dal file.
1. Salva ed esegui il flusso di lavoro.

Un esempio è presentato nel caso d’uso seguente.

**Argomenti correlati:**

* [Attività caricamento dati (file)](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/data-loading-file.html){target="_blank"}.
* [Comprimere o crittografare un file](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/extraction-file.html){target="_blank"}.

## Caso d’uso: importare dati crittografati utilizzando una chiave generata dal Pannello di controllo Campaign {#use-case-gpg-decrypt}

In questo caso d’uso, creeremo un flusso di lavoro per importare dati che sono stati crittografati in un sistema esterno, utilizzando una chiave generata nel Pannello di controllo Campaign.

![](assets/do-not-localize/how-to-video.png) [Guarda il video su questa funzione](#video)

I passaggi per eseguire questo caso d’uso sono i seguenti:

1. Utilizza il Pannello di controllo Campaign per generare una coppia di chiavi (pubblica/privata). I passaggi dettagliati sono disponibili nella [documentazione del Pannello di controllo Campaign](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/gpg-keys-management.html#decrypting-data).

   * La chiave pubblica verrà condivisa con il sistema esterno, che la utilizzerà per crittografare i dati da inviare a Campaign.
   * La chiave privata verrà utilizzata da Campaign Classic per decrittografare i dati crittografati in arrivo.

   ![](assets/gpg_generate.png)

1. Nel Pannello di controllo Campaign esterno, utilizzare la chiave pubblica scaricata dal sistema per crittografare i dati da importare in Campaign Classic.

1. In Campaign Classic, crea un flusso di lavoro per importare i dati crittografati e decrittografarli utilizzando la chiave privata installata tramite il Pannello di controllo Campaign. A tal fine, verrà creato un flusso di lavoro come segue:

   ![](assets/gpg_import_workflow.png)

   * Attività **[!UICONTROL File transfer]**: trasferisce il file da un&#39;origine esterna a Campaign Classic. In questo esempio, vogliamo trasferire il file da un server SFTP.
   * Attività **[!UICONTROL Data loading (file)]**: carica i dati dal file nel database e li decrittografa utilizzando la chiave privata generata nel Pannello di controllo Campaign.

1. Aprire l&#39;attività **[!UICONTROL File transfer]**, quindi specificare l&#39;account esterno da cui si desidera importare il file .gpg crittografato.

   ![](assets/gpg_key_transfer.png)

   I concetti globali su come configurare l&#39;attività sono disponibili nella [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/event-activities/file-transfer.html){target="_blank"}.


1. Apri l&#39;attività **[!UICONTROL Data loading (file)]**, quindi configurala in base alle tue esigenze. I concetti globali su come configurare l&#39;attività sono disponibili nella [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/data-loading-file.html){target="_blank"}.

   Aggiungi una fase di pre-elaborazione all’attività per decrittografare i dati in arrivo. A tale scopo, selezionare l&#39;opzione **[!UICONTROL Pre-process the file]**, quindi selezionare **[!UICONTROL Decrypt]** dall&#39;elenco a discesa **[!UICONTROL Command]**:

   ![](assets/gpg_load.png)

   >[!NOTE]
   >
   >Se sono necessarie modifiche ai comandi disponibili, puoi contattare l&#39;[Assistenza clienti Adobe](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) per modificare le impostazioni di preProcessCommand.
   >
   >Se si utilizza una distribuzione ibrida, è possibile configurare questi comandi direttamente dal file di configurazione del server (serverConf.xml). [Scopri come configurare i comandi di pre-elaborazione nel file di configurazione del server](../../installation/using/the-server-configuration-file.md#preprocesscommand)

1. Fare clic su **[!UICONTROL OK]** per confermare la configurazione dell&#39;attività.

1. Ora puoi eseguire il flusso di lavoro. Una volta eseguita, puoi verificare nei registri del flusso di lavoro che la decrittografia è stata eseguita e che i dati del file sono stati importati.

   ![](assets/gpg_run.png)

## Video tutorial {#video}

Questo video mostra come utilizzare una chiave GPG per decrittografare i dati.

>[!VIDEO](https://video.tv.adobe.com/v/36482?quality=12)

Ulteriori video dimostrativi di Campaign Classic sono disponibili [qui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=it).
