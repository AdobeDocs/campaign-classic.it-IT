---
product: campaign
title: Decrittografia o decompressione di un file
description: Scopri come decomprimere o decrittografare un file in Campaign Classic prima dell’elaborazione.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 1a79da3b-2abc-4bfc-a0ee-8471c478638d
source-git-commit: 1d32161d60f6b382188012b104c642f504e28645
workflow-type: tm+mt
source-wordcount: '716'
ht-degree: 11%

---

# Decrittografia o decompressione di un file {#unzipping-or-decrypting-a-file-before-processing}

![](../../assets/common.svg)

Adobe Campaign consente di importare file compressi o crittografati. Prima che possano essere letti in un [Caricamento dati (file)](../../workflow/using/data-loading--file-.md) puoi definire una pre-elaborazione per decomprimere o decrittografare il file.

Per poterlo fare:

1. Utilizza la [Pannello di controllo Campaign](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/gpg-keys-management.html#decrypting-data) per generare una coppia di chiavi pubblica/privata.

   >[!NOTE]
   >
   >Il Pannello di controllo Campaign è accessibile a tutti gli utenti amministratori. I passaggi per concedere a un utente l’accesso come amministratore sono descritti in[questa pagina](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=it#discover-control-panel).
   >
   >Tieni presente che l’istanza deve essere ospitata su AWS e aggiornata con [build GA più recente](../../rn/using/rn-overview.md). Scopri come controllare la versione in [questa sezione](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version). Per verificare se l’istanza è ospitata su AWS, segui i passaggi descritti in [questa sezione](https://experienceleague.adobe.com/docs/control-panel/using/faq.html).

1. Se l’installazione di Adobe Campaign è ospitata per Adobe, contatta [Adobe Customer Care](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) per avere le utility necessarie installate sul server.
1. Se l&#39;installazione di Adobe Campaign è on-premise, installare l&#39;utility da utilizzare (ad esempio: GPG, GZIP) e le chiavi necessarie (chiave di crittografia) sul server dell&#39;applicazione.

Puoi quindi utilizzare i comandi di preelaborazione desiderati nei flussi di lavoro:

1. Aggiungi e configura un **[!UICONTROL File transfer]** nel flusso di lavoro.
1. Aggiungi un **[!UICONTROL Data loading (file)]** e definisci il formato del file.
1. Seleziona l’opzione **[!UICONTROL Pre-process the file]**.
1. Specificare il comando di pre-elaborazione che si desidera applicare.
1. Aggiungi altre attività per gestire i dati provenienti dal file .
1. Salva ed esegui il flusso di lavoro.

Un esempio è presentato nel caso d’uso seguente.

**Argomenti correlati:**

* [Attività di caricamento dei dati (file)](../../workflow/using/data-loading--file-.md).
* [ZIP o crittografare un file](../../workflow/using/how-to-use-workflow-data.md#zipping-or-encrypting-a-file).

## Caso di utilizzo: Importa dati crittografati utilizzando una chiave generata dal Pannello di controllo Campaign {#use-case-gpg-decrypt}

In questo caso d’uso, creeremo un flusso di lavoro per importare i dati crittografati in un sistema esterno, utilizzando una chiave generata nel Pannello di controllo Campaign.

![](assets/do-not-localize/how-to-video.png) [Scopri questa funzione nel video](#video)

I passaggi per eseguire questo caso d’uso sono i seguenti:

1. Utilizza il Pannello di controllo Campaign per generare una coppia di chiavi (pubblica/privata). I passaggi dettagliati sono disponibili in [Documentazione del Pannello di controllo Campaign](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/gpg-keys-management.html#decrypting-data).

   * La chiave pubblica verrà condivisa con il sistema esterno, che lo utilizzerà per crittografare i dati da inviare a Campaign.
   * La chiave privata verrà utilizzata da Campaign Classic per decrittografare i dati crittografati in arrivo.

   ![](assets/gpg_generate.png)

1. Nel sistema esterno, utilizza la chiave pubblica scaricata dal Pannello di controllo Campaign per crittografare i dati da importare in Campaign Classic.

1. In Campaign Classic, crea un flusso di lavoro per importare i dati crittografati e decrittografarli utilizzando la chiave privata installata tramite il Pannello di controllo Campaign. A questo scopo, verrà creato un flusso di lavoro come segue:

   ![](assets/gpg_import_workflow.png)

   * **[!UICONTROL File transfer]** attività: Trasferisce il file da un’origine esterna a Campaign Classic. In questo esempio, vogliamo trasferire il file da un server SFTP.
   * **[!UICONTROL Data loading (file)]** attività: Carica i dati dal file nel database e decrittografalo utilizzando la chiave privata generata nel Pannello di controllo Campaign.

1. Apri **[!UICONTROL File transfer]** quindi specifica l’account esterno da cui importare il file .gpg crittografato.

   ![](assets/gpg_key_transfer.png)

   I concetti globali su come configurare l’attività sono disponibili in [questa sezione](../../workflow/using/file-transfer.md).

1. Apri **[!UICONTROL Data loading (file)]** , quindi configuralo in base alle tue esigenze. I concetti globali su come configurare l’attività sono disponibili in [questa sezione](../../workflow/using/data-loading--file-.md).

   Aggiungi una fase di pre-elaborazione all’attività per decrittografare i dati in arrivo. A questo scopo, seleziona la **[!UICONTROL Pre-process the file]** quindi copia e incolla questo comando di decrittografia in **[!UICONTROL Command]** campo :

   `gpg --batch --passphrase passphrase --decrypt <%=vars.filename%>`

   ![](assets/gpg_load.png)

   >[!CAUTION]
   >
   >In questo esempio, utilizziamo la passphrase utilizzata per impostazione predefinita dal Pannello di controllo Campaign, che è &quot;passphrase&quot;.
   >
   >Se in passato hai già installato chiavi GPG nella tua istanza tramite una richiesta dell’Assistenza clienti, la passphrase potrebbe essere stata modificata ed essere diversa da quella di default.

1. Fai clic su **[!UICONTROL OK]** per confermare la configurazione dell’attività.

1. Ora puoi eseguire il flusso di lavoro. Una volta eseguito, puoi controllare nei registri del flusso di lavoro che la decrittografia è stata eseguita e che i dati del file sono stati importati.

   ![](assets/gpg_run.png)

## Video tutorial {#video}

Questo video mostra come utilizzare una chiave GPG per decrittografare i dati.

>[!VIDEO](https://video.tv.adobe.com/v/36482?quality=12)

Sono disponibili ulteriori video dimostrativi su Campaign Classic [qui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=it).
