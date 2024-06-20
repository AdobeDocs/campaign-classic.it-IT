---
product: campaign
title: Utilizzare i diritti denominati per impostare le autorizzazioni
description: Scopri come utilizzare i diritti denominati per impostare le autorizzazioni
badge: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
feature: Access Management, Permissions
role: User, Admin
level: Beginner
exl-id: 07470a91-d8d2-4c41-9555-05522c8068f0
source-git-commit: 8aceafa362b80f6e34edfd91a71551a58501a3d0
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 5%

---

# Utilizzare i diritti denominati per impostare le autorizzazioni{#named-rights}

>[!NOTE]
>
>Questa pagina si applica solo agli operatori che si connettono a Campaign con autenticazione nativa. Per l’autenticazione Adobe IMS, consulta [questa documentazione](https://helpx.adobe.com/enterprise/using/manage-permissions-and-roles.html).

Per impostazione predefinita, Adobe Campaign propone una serie di diritti denominati che ti consentono di definire le autorizzazioni assegnate agli operatori e ai gruppi di operatori. Questi diritti possono essere modificati da **[!UICONTROL Administration > Access management > Named rights]** dell&#39;albero.

![](assets/s_ncs_admin_named_rights.png)

Tali diritti sono i seguenti:

* **[!UICONTROL ADMINISTRATION]**: operatori con **[!UICONTROL ADMINISTRATION]** right dispone dell’accesso completo all’istanza. Gli utenti amministratori possono eseguire/creare/modificare/eliminare qualsiasi oggetto, ad esempio flusso di lavoro, consegna, script e così via.

* **[!UICONTROL APPROVAL ADMINISTRATION]**: puoi impostare più passaggi di approvazione all’interno di flussi di lavoro e consegne per garantire che lo stato corrente sia stato approvato da un operatore o un gruppo assegnato. Utenti con **[!UICONTROL APPROVAL ADMINISTRATION]** L&#39;autorizzazione può impostare le fasi di approvazione e assegnare un operatore o un gruppo di operatori che deve approvarle.

* **[!UICONTROL CENTRAL]**: diritto alla gestione centrale (Marketing distribuito).

* **[!UICONTROL DELETE FOLDER]**: diritto di eliminare le cartelle. Con questo diritto, gli utenti possono eliminare cartelle dalla visualizzazione Esplora risorse.

* **[!UICONTROL EDIT FOLDERS]**: diritto di modificare le proprietà della cartella come nome interno, etichetta, immagine associata, ordine delle sottocartelle e così via.

* **[!UICONTROL EXPORT]**: gli utenti possono esportare i dati dalle istanze Adobe Campaign in un file sul server o sul computer locale utilizzando **[!UICONTROL EXPORT]** attività del flusso di lavoro.

* **[!UICONTROL FILES ACCESS]**: diritto di accesso in lettura e scrittura per i file tramite uno script che può essere scritto nel **[!UICONTROL JavaScript]** attività del flusso di lavoro per la lettura/scrittura di file su un server.

* **[!UICONTROL IMPORT]**: diritto per l’importazione di dati generici. **[!UICONTROL IMPORT]** consente di importare dati in qualsiasi altra tabella, mentre **[!UICONTROL RECIPIENT IMPORT]** right consente di importare solo nella tabella dei destinatari.

* **[!UICONTROL INSERT FOLDERS]**: diritto di inserire cartelle. Utenti con **[!UICONTROL INSERT FOLDERS]** con il pulsante destro del mouse è possibile creare nuove cartelle nella struttura cartelle in visualizzazione esplora risorse.

* **[!UICONTROL LOCAL]**: diritto alla gestione locale (Marketing distribuito).

* **[!UICONTROL MERGE]**: diritto di unire i record selezionati in uno. Se i destinatari esistono come duplicati, il **[!UICONTROL MERGE]** L’opzione a destra consente all’utente di selezionare i duplicati e unirli in un destinatario primario.

* **[!UICONTROL PREPARE DELIVERIES]**: diritto di creare, modificare e salvare una consegna. Utenti con **[!UICONTROL PREPARE DELIVERIES]** right può anche avviare il processo di analisi della consegna.

* **[!UICONTROL PRIVACY DATA RIGHT]**: diritto di raccogliere ed eliminare dati sulla privacy. Per ulteriori informazioni, consulta questa [pagina](https://helpx.adobe.com/it/campaign/kb/acc-privacy.html).

* **[!UICONTROL PROGRAM EXECUTION]**: diritto di eseguire comandi in vari linguaggi di programmazione.

* **[!UICONTROL RECIPIENT IMPORT]**: diritto di importare i destinatari. Utenti con **[!UICONTROL RECIPIENT IMPORT]** right può importare un file locale nella tabella dei destinatari.

* **[!UICONTROL SQL SCRIPT EXECUTION]** Diritto di eseguire qualsiasi comando SQL direttamente sul database.

* **[!UICONTROL START DELIVERIES]**: diritto di approvare le consegne analizzate in precedenza. Dopo l’analisi della consegna, la consegna viene sospesa in vari passaggi di approvazione e deve essere approvata per riprendere. Utenti con **[!UICONTROL START DELIVERIES]** I diritti di possono approvare le consegne.

* **[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY]**: diritto di scrivere script SQL personalizzati utilizzando l’attività Gestione dati SQL per creare e popolare tabelle di lavoro (consulta [questa sezione](../../workflow/using/sql-data-management.md)).

* **[!UICONTROL WORKFLOW]**: diritto di eseguire flussi di lavoro. Senza questo diritto, gli utenti non possono avviare, arrestare o riavviare i flussi di lavoro.

* **[!UICONTROL WEBAPP]**: diritto di utilizzare le applicazioni web.

>[!NOTE]
>
>Questo elenco può variare a seconda dei componenti aggiuntivi installati sulla piattaforma.

## Matrice dei diritti di accesso {#access-rights-matrix}

I gruppi predefiniti e i diritti denominati consentono agli operatori di accedere a determinate cartelle nella gerarchia di navigazione e di concedere autorizzazioni di lettura, scrittura ed eliminazione.

È disponibile la matrice dei diritti di accesso di Adobe Campaign [qui](/help/platform/using/assets/access-rights-matrix.pdf).

[![immagine](assets/do-not-localize/user_management.png)](https://experienceleague.adobe.com/docs/campaign-classic/assets/access-rights-matrix.pdf)
