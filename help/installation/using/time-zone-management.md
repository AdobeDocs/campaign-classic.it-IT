---
product: campaign
title: Gestione del fuso orario
description: Gestione del fuso orario
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: e5ed96cc-3fc7-4af4-a29e-5a4c81f4fe39
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '886'
ht-degree: 1%

---

# Gestione del fuso orario{#time-zone-management}

![](../../assets/v7-only.svg)

## Principio di funzionamento {#operating-principle}

Adobe Campaign consente di esprimere le date in funzione del relativo fuso orario: questo consente agli utenti internazionali di lavorare in tutto il mondo su diversi fusi orari. Ogni paese che utilizza la stessa istanza può gestire l’esecuzione di campagne, il tracciamento, l’archiviazione, ecc. a seconda dell&#39;ora locale.

Per consentire l’utilizzo della piattaforma Adobe Campaign su scala internazionale, tutte le date utilizzate dai sistemi devono essere collegate a un fuso orario. Una data il cui fuso orario è noto può quindi essere importata in qualsiasi altro fuso orario, o indipendentemente dal fuso orario.

Adobe Campaign consente di memorizzare date/ore in formato UTC (Coordinated Universal Time). Quando i dati vengono esposti, vengono convertiti nella data/ora locale dell’operatore. La conversione viene eseguita automaticamente quando il database è configurato in UTC (fare riferimento a [Configurazione](#configuration)). Se il database non è configurato in UTC, le informazioni sul fuso orario delle date nella piattaforma vengono memorizzate in un&#39;opzione.

Le funzionalità principali della piattaforma per la gestione del fuso orario sono: importazione/esportazione di dati, operatore e gestione del flusso di lavoro. Il **concetto di ereditarietà** è disponibile per importazioni/esportazioni o flussi di lavoro. Per impostazione predefinita, sono configurati per il fuso orario del server di database, tuttavia è possibile ridefinire nuovi fusi orari per un flusso di lavoro e anche per una singola attività.

**** Gli operatori possono modificare i fusi orari durante  **la** configurazione della consegna e specificare il fuso orario specifico in cui verrà eseguita la consegna.

>[!IMPORTANT]
>
>Se il database non gestisce più fusi orari, per tutte le manipolazioni del filtro dati, le query SQL devono essere eseguite nel fuso orario del server di database.

Ogni operatore Adobe Campaign è collegato a un fuso orario: queste informazioni sono configurate nel loro profilo. Per ulteriori informazioni, consulta [questo documento](../../platform/using/access-management.md).

Quando la piattaforma Adobe Campaign non richiede la gestione del fuso orario, è possibile mantenere una modalità di archiviazione in formato locale con un fuso orario collegato specifico.

## Raccomandazioni {#recommendations}

I fusi orari combinano diverse realtà: l&#39;espressione può descrivere un intervallo di tempo costante con la data UTC o gli orari di una regione che possono cambiare due volte all&#39;anno (ora legale).

Ad esempio, in postgreSQL, il comando **SET TIME ZONE &#39;Europe/Paris&#39;;** terrà conto degli orari estivi e invernali: la data sarà espressa in UTC+1 o UTC+2 a seconda dell’ora dell’anno.

Tuttavia, se si utilizza il comando **SET TIME ZONE 0200;**, l&#39;intervallo di tempo sarà sempre UTC+2.

## Configurazione {#configuration}

La modalità di archiviazione per date e ore viene selezionata durante la creazione del database (fare riferimento a [Creazione di una nuova istanza](#creating-a-new-instance)). In caso di migrazione, le ore collegate alle date vengono convertite in date e ore locali (consulta [Migrazione](#migration)).

Dal punto di vista tecnico, esistono due modi per memorizzare le informazioni di tipo **Date+time** nel database:

1. MARCA TEMPORALE CON formato TIMEZONE: il motore di database memorizza le date in UTC. Ogni sessione aperta avrà un fuso orario e le date verranno convertite in base ad esso.
1. Formato locale + fuso orario locale: tutte le date sono memorizzate nel formato locale (nessuna gestione del ritardo temporale) e viene loro assegnato un singolo fuso orario. Il fuso orario viene memorizzato nell&#39;opzione **WdbcTimeZone** dell&#39;istanza Adobe Campaign e può essere modificato tramite il menu **[!UICONTROL Administration > Platform > Options]** della struttura.

>[!IMPORTANT]
>
>Tieni presente che questa modifica può causare problemi di coerenza e sincronizzazione dei dati.

### Creazione di una nuova istanza {#creating-a-new-instance}

Affinché diversi utenti internazionali possano lavorare sulla stessa istanza, è necessario configurare i fusi orari durante la creazione dell’istanza per gestire i periodi di tempo tra i vari paesi. Durante la creazione dell&#39;istanza, seleziona la modalità di gestione di data e ora nella sezione **[!UICONTROL Time zone]** del passaggio di configurazione del database.

Selezionare l&#39;opzione **[!UICONTROL UTC database (date fields with time zone)]** per memorizzare tutti i dati con date e ore in formato UTC (campi SQL e campi XML).

![](assets/install_wz_select_utc_option.png)

>[!IMPORTANT]
>
>Se utilizzi **Oracle**, i file del fuso orario (.dat) dei livelli client di Oracle devono essere compatibili con i file timezones installati sul server.

Se il database non è UTC, è possibile selezionare uno dei fusi orari disponibili nell&#39;elenco a discesa. Puoi inoltre utilizzare il fuso orario del server o selezionare l’opzione UTC (Coordinated Universal Time).

![](assets/install_wz_unselect_utc_option.png)

Quando l&#39;opzione **[!UICONTROL UTC Database (date fields with time zone)]** è selezionata, i campi SQL vengono memorizzati in formato TIMESTAMP WITH TIMEZONE.

In caso contrario, verranno memorizzati nel formato locale e sarà necessario selezionare il fuso orario da applicare al database.

### Migrazione {#migration}

Durante la migrazione a una versione precedente (senza gestione del fuso orario), è necessario definire la modalità di archiviazione della data nel database.

Per garantire la compatibilità con gli strumenti esterni che accedono al database Adobe Campaign, i campi SQL di tipo **Date+time** rimangono memorizzati per impostazione predefinita nel formato locale.

I campi XML contenenti le date sono ora memorizzati in UTC. Durante il caricamento, i campi non in formato UTC vengono convertiti automaticamente utilizzando il fuso orario dei server. Ciò significa che tutti i campi XML verranno progressivamente convertiti in formato UTC.

Per utilizzare un&#39;istanza esistente, aggiungi l&#39;opzione **WdbcTimeZone** e immetti il fuso orario dell&#39;istanza.

>[!IMPORTANT]
>
>Assicurati che il valore corretto sia configurato per l&#39;opzione WdbcTimeZone: le modifiche apportate successivamente possono causare incongruenze.

Esempio di possibili valori:

* Europa/Parigi,
* Europa/Londra,
* America/New_York, ecc.

   Questi valori vengono ricavati dal database tz (Olson). Per ulteriori informazioni, consulta [https://en.wikipedia.org/wiki/List_of_tz_database_time_zones](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones).
