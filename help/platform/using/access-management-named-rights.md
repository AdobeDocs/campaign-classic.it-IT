---
solution: Campaign Classic
product: campaign
title: Utilizzare i diritti denominati per impostare le autorizzazioni
description: Scopri come utilizzare i diritti denominati per impostare le autorizzazioni
feature: Access Management
role: Business Practitioner, Administrator
level: Beginner
translation-type: tm+mt
source-git-commit: f2bd093d3a010e079b7f5adf3371e21d07a4f3ae
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 4%

---


# Utilizzare i diritti denominati per impostare le autorizzazioni{#named-rights}

Per impostazione predefinita, Adobe Campaign propone un set di diritti con nome che ti consente di definire le autorizzazioni assegnate a operatori e gruppi di operatori. Questi diritti possono essere modificati dal nodo **[!UICONTROL Administration > Access management > Named rights]** della struttura.

![](assets/s_ncs_admin_named_rights.png)

Tali diritti sono i seguenti:

* **[!UICONTROL ADMINISTRATION]**: Gli operatori con  **[!UICONTROL ADMINISTRATION]** diritto hanno pieno accesso all’istanza. Gli utenti amministratori possono eseguire/creare/modificare/eliminare qualsiasi oggetto, ad esempio flusso di lavoro, consegna, script e così via.

* **[!UICONTROL APPROVAL ADMINISTRATION]**: Puoi impostare più passaggi di approvazione all’interno di flussi di lavoro e consegne per garantire che lo stato corrente sia stato approvato da un operatore o gruppo assegnato. Gli utenti con il diritto **[!UICONTROL APPROVAL ADMINISTRATION]** possono impostare i passaggi di approvazione e assegnare anche un operatore o un gruppo di operatori che deve approvarli.

* **[!UICONTROL CENTRAL]**: Diritto alla gestione centrale (Distributed Marketing).

* **[!UICONTROL DELETE FOLDER]**: Diritto di eliminare le cartelle. Con questo diritto, gli utenti possono eliminare le cartelle dalla visualizzazione Esplora risorse.

* **[!UICONTROL EDIT FOLDERS]**: Diritto di modificare le proprietà della cartella come nome interno, etichetta, immagine associata, ordine delle sottocartelle, ecc.

* **[!UICONTROL EXPORT]**: Gli utenti possono esportare i dati dalle istanze Adobe Campaign in un file sul server o sul computer locale utilizzando l’attività del  **[!UICONTROL EXPORT]** flusso di lavoro.

* **[!UICONTROL FILES ACCESS]**: Diritto di accesso in lettura e scrittura per i file tramite uno script che può essere scritto nell&#39;attività del  **[!UICONTROL JavaScript]** flusso di lavoro per leggere e scrivere i file su un server.

* **[!UICONTROL IMPORT]**: Diritto all’importazione di dati generici. **[!UICONTROL IMPORT]** consente di importare i dati in qualsiasi altra tabella, mentre il  **[!UICONTROL RECIPIENT IMPORT]** diritto consente di importarli solo nella tabella dei destinatari.

* **[!UICONTROL INSERT FOLDERS]**: Diritto di inserire cartelle. Gli utenti con il diritto **[!UICONTROL INSERT FOLDERS]** possono creare nuove cartelle nella struttura delle cartelle nella visualizzazione Esplora risorse.

* **[!UICONTROL LOCAL]**: Diritto alla gestione locale (Distributed Marketing).

* **[!UICONTROL MERGE]**: Diritto di unire i record selezionati in un unico record. Se i destinatari esistono come duplicati, il diritto **[!UICONTROL MERGE]** consente all’utente di selezionare i duplicati e di unirli a un destinatario principale.

* **[!UICONTROL PREPARE DELIVERIES]**: Diritto di creare, modificare e salvare una consegna. Anche gli utenti con il diritto **[!UICONTROL PREPARE DELIVERIES]** possono avviare il processo di analisi della consegna.

* **[!UICONTROL PRIVACY DATA RIGHT]**: Diritto di raccogliere ed eliminare dati sulla privacy. Per ulteriori informazioni, consulta questa [pagina](https://helpx.adobe.com/it/campaign/kb/acc-privacy.html).

* **[!UICONTROL PROGRAM EXECUTION]**: Diritto di eseguire comandi in vari linguaggi di programmazione.

* **[!UICONTROL RECIPIENT IMPORT]**: Diritto di importare i destinatari. Gli utenti con il diritto **[!UICONTROL RECIPIENT IMPORT]** possono importare un file locale nella tabella dei destinatari.

* **[!UICONTROL SQL SCRIPT EXECUTION]** Diritto di eseguire qualsiasi comando SQL direttamente sul database.

* **[!UICONTROL START DELIVERIES]**: Diritto di approvare le consegne analizzate in precedenza. Dopo l’analisi della consegna, la consegna verrà messa in pausa a vari passaggi di approvazione e dovrà essere approvata per riprendere. Gli utenti con il diritto **[!UICONTROL START DELIVERIES]** possono approvare le consegne.

* **[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY]**: Diritto di scrivere script SQL personalizzati utilizzando l&#39;attività SQL Data Management per creare e popolare tabelle di lavoro (vedere  [questa sezione](../../workflow/using/sql-data-management.md)).

* **[!UICONTROL WORKFLOW]**: Diritto di eseguire flussi di lavoro. Senza questo diritto, gli utenti non possono avviare, arrestare o riavviare i flussi di lavoro.

* **[!UICONTROL WEBAPP]**: Diritto di utilizzare applicazioni web.

>[!NOTE]
>
>Questo elenco può variare a seconda dei componenti aggiuntivi installati sulla piattaforma.

## Matrice dei diritti di accesso {#access-rights-matrix}

I gruppi predefiniti e i diritti denominati consentono agli operatori di accedere a determinate cartelle nella gerarchia di navigazione e di concedere autorizzazioni di lettura, scrittura ed eliminazione.

La matrice dei diritti di accesso Adobe Campaign è disponibile [qui](/help/platform/using/assets/access-rights-matrix.pdf).

[![immagine](assets/do-not-localize/user_management.png)](https://experienceleague.adobe.com/docs/campaign-classic/assets/access-rights-matrix.pdf?lang=en)
