---
title: Gestione del fuso orario
seo-title: Gestione del fuso orario
description: Gestione del fuso orario
seo-description: null
page-status-flag: never-activated
uuid: b8926761-65e2-48fd-8689-2ae6b0596e72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: b9846eda-eeca-433e-b961-6dfc2aa2708b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 3522f4f50770dde220610cd5f1c4084292d8f1f5
workflow-type: tm+mt
source-wordcount: '889'
ht-degree: 1%

---


# Gestione del fuso orario{#time-zone-management}

## Principio di funzionamento {#operating-principle}

Adobe Campaign consente di esprimere le date in funzione del relativo fuso orario: questo consente agli utenti internazionali di lavorare in tutto il mondo su diversi fusi orari. Ogni paese che utilizza la stessa istanza può gestire l&#39;esecuzione di campagne, il tracciamento, l&#39;archiviazione, ecc. a seconda dell&#39;ora locale.

Per abilitare l&#39;uso della piattaforma Adobe Campaign su scala internazionale, tutte le date utilizzate dai sistemi devono essere collegabili a un fuso orario. Una data il cui fuso orario è noto può quindi essere importata in qualsiasi altro fuso orario, o a prescindere dal fuso orario.

Adobe Campaign consente di memorizzare le date/ore nel formato UTC (ora universale coordinata). Quando i dati sono esposti, vengono convertiti nella data/ora locale dell&#39;operatore. La conversione viene eseguita automaticamente quando il database è configurato in UTC (vedere [Configurazione](#configuration)). Se il database non è configurato in UTC, le informazioni relative al fuso orario delle date nella piattaforma vengono memorizzate in un&#39;opzione.

Le principali funzionalità della piattaforma per la gestione del fuso orario sono: importazione/esportazione di dati e gestione di operatori e flussi di lavoro. Il concetto **di** ereditarietà è disponibile per le importazioni/esportazioni o per i flussi di lavoro. Per impostazione predefinita, sono configurati per il fuso orario del server del database, tuttavia è possibile ridefinire nuovi fusi orari per un flusso di lavoro e anche per una singola attività.

**Gli operatori** possono modificare i fusi orari durante la configurazione **della** consegna e specificare il fuso orario in cui verrà eseguito il recapito.

>[!IMPORTANT]
>
>Se il database non gestisce più fusi orari, per tutte le manipolazioni dei filtri dati è necessario eseguire query SQL nel fuso orario del server del database.

Ciascun operatore Adobe Campaign è collegato a un fuso orario: queste informazioni sono configurate nel relativo profilo. For more on this, refer to [this document](../../platform/using/access-management.md).

Se la piattaforma Adobe Campaign non richiede la gestione del fuso orario, puoi mantenere una modalità di archiviazione in formato locale con un fuso orario collegato specifico.

## Recommendations {#recommendations}

I fusi orari combinano diverse realtà: l&#39;espressione può descrivere un intervallo di tempo costante con la data UTC o con gli orari di una regione che possono cambiare due volte all&#39;anno (ora legale).

Ad esempio, in postgreSQL, **SET TIME ZONE &#39;Europe/Paris&#39;;** Il comando terrà conto degli orari estivi e invernali: la data sarà espressa in UTC+1 o UTC+2 a seconda dell&#39;ora dell&#39;anno.

Tuttavia, se si utilizza il **SET TIME ZONE 0200,** il ritardo sarà sempre UTC+2.

## Configurazione {#configuration}

La modalità di memorizzazione per le date e le ore è selezionata durante la creazione del database (vedere [Creazione di una nuova istanza](#creating-a-new-instance)). In caso di migrazione, le ore collegate alle date sono convertite in date e ore locali (fare riferimento a [Migrazione](#migration)).

Dal punto di vista tecnico, nel database sono disponibili due modi per memorizzare le informazioni relative al tipo di **data+ora** :

1. TIMESTAMP CON IL FORMATO TIMEZONE: il motore del database memorizza le date in UTC. Ogni sessione aperta avrà un fuso orario e le date verranno convertite in base ad esso.
1. Formato locale + fuso orario locale: tutte le date sono memorizzate nel formato locale (nessuna gestione del time-lag) e viene loro assegnato un unico fuso orario. Il fuso orario è memorizzato nell’opzione **WdbcTimeZone** dell’istanza Adobe Campaign e può essere modificato mediante il **[!UICONTROL Administration > Platform > Options]** menu della struttura.

>[!IMPORTANT]
>
>Tieni presente che questa modifica può causare problemi di coerenza dei dati e sincronizzazione.

### Creazione di una nuova istanza {#creating-a-new-instance}

Affinché diversi utenti internazionali possano lavorare sulla stessa istanza, è necessario configurare i fusi orari al momento della creazione dell&#39;istanza per gestire i periodi di tempo tra i paesi. Durante la creazione dell&#39;istanza, selezionate la modalità di gestione della data e dell&#39;ora nella **[!UICONTROL Time zone]** sezione del passaggio di configurazione del database.

Selezionare l&#39; **[!UICONTROL UTC database (date fields with time zone)]** opzione per memorizzare tutti i dati con date e ore in formato UTC (campi SQL e campi XML).

![](assets/install_wz_select_utc_option.png)

>[!IMPORTANT]
>
>Se si utilizza **Oracle**, i file timezone (.dat) dei livelli client Oracle devono essere compatibili con i file timezones installati sul server.

Se il database non è UTC, è possibile selezionare uno dei fusi orari disponibili nell&#39;elenco a discesa. È inoltre possibile utilizzare il fuso orario del server o selezionare l&#39;opzione UTC (Coordinated Universal Time).

![](assets/install_wz_unselect_utc_option.png)

Quando l&#39; **[!UICONTROL UTC Database (date fields with time zone)]** opzione è selezionata, i campi SQL sono memorizzati in formato TIMESTAMP WITH TIMEZONE.

In caso contrario, vengono memorizzati nel formato locale e sarà necessario selezionare il fuso orario da applicare al database.

### Migrazione {#migration}

Durante la migrazione a una versione precedente (senza gestione del fuso orario), sarà necessario definire la modalità di archiviazione delle date nel database.

Per garantire la compatibilità con gli strumenti esterni che accedono al database di Adobe Campaign, i campi SQL di tipo **Date+time** rimangono memorizzati nel formato locale per impostazione predefinita.

I campi XML contenenti le date sono ora memorizzati in UTC. Durante il caricamento, i campi non in formato UTC vengono convertiti automaticamente utilizzando il fuso orario dei server. Ciò significa che tutti i campi XML verranno progressivamente convertiti in formato UTC.

Per utilizzare un&#39;istanza esistente, aggiungete l&#39;opzione **WdbcTimeZone** e inserite il fuso orario dell&#39;istanza.

>[!IMPORTANT]
>
>Verificate che il valore corretto sia configurato per l&#39;opzione WdbcTimeZone: le modifiche effettuate successivamente possono causare incoerenze.

Esempio di possibili valori:

* Europa/Parigi,
* Europa/Londra,
* America/New_York, ecc.

   Questi valori vengono presi dal database tz (Olson). Per ulteriori informazioni, consultate [https://en.wikipedia.org/wiki/List_of_tz_database_time_zones](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones).

