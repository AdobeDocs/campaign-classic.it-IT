---
product: campaign
title: Utilizzare i diritti denominati per impostare le autorizzazioni
description: Scopri come utilizzare i diritti denominati per impostare le autorizzazioni
feature: Access Management, Permissions
role: User, Admin
level: Beginner
exl-id: 07470a91-d8d2-4c41-9555-05522c8068f0
source-git-commit: f05eefc9945c4ead89eb448b6e28c3523559e055
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 7%

---

# Utilizzare i diritti denominati per impostare le autorizzazioni{#named-rights}

![](../../assets/common.svg)

Per impostazione predefinita, Adobe Campaign propone un set di diritti con nome che ti consente di definire le autorizzazioni assegnate a operatori e gruppi di operatori. Questi diritti possono essere modificati dalla **[!UICONTROL Administration > Access management > Named rights]** nodo dell&#39;albero.

![](assets/s_ncs_admin_named_rights.png)

Tali diritti sono i seguenti:

* **[!UICONTROL ADMINISTRATION]**: Operatori con **[!UICONTROL ADMINISTRATION]** il diritto ha pieno accesso all&#39;istanza. Gli utenti amministratori possono eseguire/creare/modificare/eliminare qualsiasi oggetto, ad esempio flusso di lavoro, consegna, script e così via.

* **[!UICONTROL APPROVAL ADMINISTRATION]**: Puoi impostare più passaggi di approvazione all’interno di flussi di lavoro e consegne per garantire che lo stato corrente sia stato approvato da un operatore o gruppo assegnato. Utenti con **[!UICONTROL APPROVAL ADMINISTRATION]** può impostare i passaggi di approvazione e assegnare anche un operatore o un gruppo di operatori che deve approvare tali passaggi.

* **[!UICONTROL CENTRAL]**: Diritto alla gestione centrale (Distributed Marketing).

* **[!UICONTROL DELETE FOLDER]**: Diritto di eliminare le cartelle. Con questo diritto, gli utenti possono eliminare le cartelle dalla visualizzazione Esplora risorse.

* **[!UICONTROL EDIT FOLDERS]**: Diritto di modificare le proprietà della cartella come nome interno, etichetta, immagine associata, ordine delle sottocartelle, ecc.

* **[!UICONTROL EXPORT]**: Gli utenti possono esportare i dati dalle proprie istanze Adobe Campaign in un file su server o computer locale utilizzando **[!UICONTROL EXPORT]** attività del flusso di lavoro.

* **[!UICONTROL FILES ACCESS]**: Diritto di accesso in lettura e scrittura per i file tramite uno script che può essere scritto nel **[!UICONTROL JavaScript]** attività del flusso di lavoro per leggere/scrivere file su un server.

* **[!UICONTROL IMPORT]**: Diritto all’importazione di dati generici. **[!UICONTROL IMPORT]** consente di importare dati in qualsiasi altra tabella, mentre il **[!UICONTROL RECIPIENT IMPORT]** right consente di importare solo nella tabella dei destinatari.

* **[!UICONTROL INSERT FOLDERS]**: Diritto di inserire cartelle. Utenti con **[!UICONTROL INSERT FOLDERS]** a destra è possibile creare nuove cartelle nella struttura delle cartelle in visualizzazione Esplora risorse.

* **[!UICONTROL LOCAL]**: Diritto alla gestione locale (Distributed Marketing).

* **[!UICONTROL MERGE]**: Diritto di unire i record selezionati in un unico record. Se i destinatari esistono come duplicati, la **[!UICONTROL MERGE]** right consente all’utente di selezionare i duplicati e di unirli in un destinatario principale.

* **[!UICONTROL PREPARE DELIVERIES]**: Diritto di creare, modificare e salvare una consegna. Utenti con **[!UICONTROL PREPARE DELIVERIES]** right può anche avviare il processo di analisi della consegna.

* **[!UICONTROL PRIVACY DATA RIGHT]**: Diritto di raccogliere ed eliminare dati sulla privacy. Per ulteriori informazioni, consulta questa [pagina](https://helpx.adobe.com/it/campaign/kb/acc-privacy.html).

* **[!UICONTROL PROGRAM EXECUTION]**: Diritto di eseguire comandi in vari linguaggi di programmazione.

* **[!UICONTROL RECIPIENT IMPORT]**: Diritto di importare i destinatari. Utenti con **[!UICONTROL RECIPIENT IMPORT]** right può importare un file locale nella tabella dei destinatari.

* **[!UICONTROL SQL SCRIPT EXECUTION]** Diritto di eseguire qualsiasi comando SQL direttamente sul database.

* **[!UICONTROL START DELIVERIES]**: Diritto di approvare le consegne analizzate in precedenza. Dopo l’analisi della consegna, la consegna verrà messa in pausa a vari passaggi di approvazione e dovrà essere approvata per riprendere. Utenti con **[!UICONTROL START DELIVERIES]** sono autorizzati ad approvare le consegne.

* **[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY]**: Diritto di scrivere script SQL personalizzati utilizzando l&#39;attività SQL Data Management per creare e popolare tabelle di lavoro (vedere [questa sezione](../../workflow/using/sql-data-management.md)).

* **[!UICONTROL WORKFLOW]**: Diritto di eseguire flussi di lavoro. Senza questo diritto, gli utenti non possono avviare, arrestare o riavviare i flussi di lavoro.

* **[!UICONTROL WEBAPP]**: Diritto di utilizzare applicazioni web.

>[!NOTE]
>
>Questo elenco può variare a seconda dei componenti aggiuntivi installati sulla piattaforma.

## Matrice dei diritti di accesso {#access-rights-matrix}

I gruppi predefiniti e i diritti denominati consentono agli operatori di accedere a determinate cartelle nella gerarchia di navigazione e di concedere autorizzazioni di lettura, scrittura ed eliminazione.

È disponibile la matrice dei diritti di accesso di Adobe Campaign [qui](/help/platform/using/assets/access-rights-matrix.pdf).

[![immagine](assets/do-not-localize/user_management.png)](https://experienceleague.adobe.com/docs/campaign-classic/assets/access-rights-matrix.pdf?lang=en)
