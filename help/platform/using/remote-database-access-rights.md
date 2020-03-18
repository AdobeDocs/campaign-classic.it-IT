---
title: Accesso a un database esterno
seo-title: Accesso a un database esterno
description: Accesso a un database esterno
seo-description: null
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: ae44e38e9d05478e8ebfacb1e063cdfd5d7ff30c

---


# Diritti di accesso al database remoto {#remote-database-access-rights}

Innanzitutto, affinché l&#39;utente possa eseguire operazioni su un database esterno tramite FDA, quest&#39;ultimo deve avere uno specifico diritto denominato in Adobe Campaign.

1. Seleziona il **[!UICONTROL Administration > Access Management > Named Rights]** nodo in Adobe Campaign Explorer.
1. Crea un nuovo diritto specificando l&#39;etichetta scelta.
1. Il **[!UICONTROL Name]** campo deve avere il seguente formato: **utente:base@server**, dove:

   * **l&#39;utente** corrisponde al nome dell&#39;utente nel database esterno.
   * **base** corrisponde al nome del database esterno.
   * **server** corrisponde al nome del server del database esterno.

      >[!NOTE]
      >
      >La parte **:base** è facoltativa in Oracle.

1. Salva il nome a destra e collegalo all&#39;utente scelto dal **[!UICONTROL Administration > Access Management > Operators]** nodo di Adobe Campaign Explorer.

Quindi, per elaborare i dati contenuti in un database esterno, l&#39;utente Adobe Campaign deve avere almeno i diritti di scrittura sul database per poter creare tabelle di lavoro. Questi vengono eliminati automaticamente da Adobe Campaign.

In generale, sono necessari i seguenti diritti:

* **CONNECT**: connessione al database remoto,
* **LEGGI dati**: accesso in sola lettura alle tabelle contenenti i dati dei clienti,
* **LEGGI &#39;MetaData&#39;**: accesso ai cataloghi di dati del server per ottenere la struttura della tabella,
* **CARICA**: carico di massa nelle tabelle di lavoro (richiesto quando si lavora su raccolte e join),
* **CREA/RILASCIA** PER **TABELLA/INDICE/PROCEDURA/FUNZIONE**,
* **EXPLAIN** (consigliato): per monitorare le prestazioni in caso di problemi,
* **SCRIVI dati** (a seconda dello scenario di integrazione).

>[!NOTE]
>
>L&#39;amministratore del database deve far corrispondere questi diritti ai diritti specifici di ciascun motore di database. Per ulteriori informazioni, fare riferimento a diritti [specifici](https://docs.adobe.com/content/help/en/campaign-classic/using/assets/fda_rdbms_rights.pdf)RDBMS.