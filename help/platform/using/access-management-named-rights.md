---
product: campaign
title: Utilizzare i diritti denominati per impostare le autorizzazioni
description: Scopri come utilizzare i diritti denominati per impostare le autorizzazioni
feature: Access Management, Permissions
role: User, Admin
level: Beginner
exl-id: 07470a91-d8d2-4c41-9555-05522c8068f0
source-git-commit: 34f875f583dd81c2229b66f3344f23965532e802
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 4%

---

# Utilizzare i diritti denominati per impostare le autorizzazioni{#named-rights}

Per impostazione predefinita, Adobe Campaign propone una serie di diritti denominati che ti consentono di definire le autorizzazioni assegnate agli operatori e ai gruppi di operatori. Questi diritti possono essere modificati dal nodo **[!UICONTROL Administration > Access management > Named rights]** della struttura.

![](assets/s_ncs_admin_named_rights.png)

Tali diritti sono i seguenti:

* **[!UICONTROL ADMINISTRATION]**: gli operatori con il diritto **[!UICONTROL ADMINISTRATION]** dispongono dell&#39;accesso completo all&#39;istanza. Gli utenti amministratori possono eseguire/creare/modificare/eliminare qualsiasi oggetto, ad esempio flusso di lavoro, consegna, script e così via.

* **[!UICONTROL APPROVAL ADMINISTRATION]**: è possibile impostare più passaggi di approvazione all&#39;interno dei flussi di lavoro e delle consegne per assicurarsi che lo stato corrente sia stato approvato da un operatore o un gruppo assegnato. Gli utenti con il diritto **[!UICONTROL APPROVAL ADMINISTRATION]** possono impostare i passaggi di approvazione e assegnare un operatore o un gruppo di operatori che deve approvare tali passaggi.

* **[!UICONTROL CENTRAL]**: diritto per la gestione centrale (Marketing distribuito).

* **[!UICONTROL DELETE FOLDER]**: diritto di eliminare le cartelle. Con questo diritto, gli utenti possono eliminare cartelle dalla visualizzazione Esplora risorse.

* **[!UICONTROL EDIT FOLDERS]**: diritto di modificare le proprietà della cartella come nome interno, etichetta, immagine associata, ordine delle sottocartelle e così via.

* **[!UICONTROL EXPORT]**: gli utenti possono esportare i dati dalle proprie istanze Adobe Campaign in un file sul server o sul computer locale utilizzando l&#39;attività del flusso di lavoro **[!UICONTROL EXPORT]**.

* **[!UICONTROL FILES ACCESS]**: diritto di accesso in lettura e scrittura per i file tramite uno script che può essere scritto nell&#39;attività del flusso di lavoro **[!UICONTROL JavaScript]** per la lettura/scrittura di file su un server.

* **[!UICONTROL IMPORT]**: diritto per l&#39;importazione di dati generici. **[!UICONTROL IMPORT]** consente di importare dati in qualsiasi altra tabella, mentre il diritto **[!UICONTROL RECIPIENT IMPORT]** consente di importare solo nella tabella dei destinatari.

* **[!UICONTROL INSERT FOLDERS]**: diritto di inserire cartelle. Gli utenti con il diritto **[!UICONTROL INSERT FOLDERS]** possono creare nuove cartelle nella struttura cartelle in visualizzazione Esplora risorse.

* **[!UICONTROL LOCAL]**: diritto per la gestione locale (Marketing distribuito).

* **[!UICONTROL MERGE]**: diritto di unire i record selezionati in uno. Se i destinatari esistono come duplicati, il diritto **[!UICONTROL MERGE]** consente all&#39;utente di selezionare i duplicati e unirli in un destinatario primario.

* **[!UICONTROL PREPARE DELIVERIES]**: diritto di creare, modificare e salvare una consegna. Gli utenti con il diritto **[!UICONTROL PREPARE DELIVERIES]** possono anche avviare il processo di analisi della consegna.

* **[!UICONTROL PRIVACY DATA RIGHT]**: diritto di raccogliere ed eliminare dati sulla privacy. Per ulteriori informazioni, consulta questa [pagina](https://helpx.adobe.com/it/campaign/kb/acc-privacy.html).

* **[!UICONTROL PROGRAM EXECUTION]**: diritto di eseguire comandi in vari linguaggi di programmazione.

* **[!UICONTROL RECIPIENT IMPORT]**: diritto di importare i destinatari. Gli utenti con questo diritto possono importare un file locale nella tabella dei destinatari.**[!UICONTROL RECIPIENT IMPORT]**

* **[!UICONTROL SQL SCRIPT EXECUTION]** Diritto di eseguire qualsiasi comando SQL direttamente sul database.

* **[!UICONTROL START DELIVERIES]**: diritto di approvare le consegne analizzate in precedenza. Dopo l’analisi della consegna, la consegna viene sospesa in vari passaggi di approvazione e deve essere approvata per riprendere. Gli utenti con il diritto **[!UICONTROL START DELIVERIES]** possono approvare le consegne.

* **[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY]**: diritto di scrivere script SQL personalizzati utilizzando l&#39;attività Gestione dati SQL per creare e popolare tabelle di lavoro (vedere [questa sezione](../../workflow/using/sql-data-management.md)).

* **[!UICONTROL WORKFLOW]**: diritto di eseguire flussi di lavoro. Senza questo diritto, gli utenti non possono avviare, arrestare o riavviare i flussi di lavoro.

* **[!UICONTROL WEBAPP]**: diritto all&#39;utilizzo di applicazioni Web.

>[!NOTE]
>
>Questo elenco può variare a seconda dei componenti aggiuntivi installati sulla piattaforma.

## Matrice dei diritti di accesso {#access-rights-matrix}

I gruppi predefiniti e i diritti denominati consentono agli operatori di accedere a determinate cartelle nella gerarchia di navigazione e di concedere autorizzazioni di lettura, scrittura ed eliminazione.

La matrice dei diritti di accesso di Adobe Campaign è disponibile [qui](/help/platform/using/assets/access-rights-matrix.pdf).

[![immagine](assets/do-not-localize/user_management.png)](https://experienceleague.adobe.com/docs/campaign-classic/assets/access-rights-matrix.pdf)
