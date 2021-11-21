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

Le funzionalità principali della piattaforma per la gestione del fuso orario sono: importazione/esportazione di dati, operatore e gestione del flusso di lavoro. La **concetto di eredità** è disponibile per importazioni/esportazioni o flussi di lavoro. Per impostazione predefinita, sono configurati per il fuso orario del server di database, tuttavia è possibile ridefinire nuovi fusi orari per un flusso di lavoro e anche per una singola attività.

**Operatori** può modificare i fusi orari durante **configurazione della consegna** e può specificare il fuso orario specifico in cui verrà eseguita la consegna.

>[!IMPORTANT]
>
>Se il database non gestisce più fusi orari, per tutte le manipolazioni del filtro dati, le query SQL devono essere eseguite nel fuso orario del server di database.

Ogni operatore Adobe Campaign è collegato a un fuso orario: queste informazioni sono configurate nel loro profilo. Per ulteriori informazioni, consulta [presente documento](../../platform/using/access-management.md).

Quando la piattaforma Adobe Campaign non richiede la gestione del fuso orario, è possibile mantenere una modalità di archiviazione in formato locale con un fuso orario collegato specifico.

## Raccomandazioni {#recommendations}

I fusi orari combinano diverse realtà: l&#39;espressione può descrivere un intervallo di tempo costante con la data UTC o gli orari di una regione che possono cambiare due volte all&#39;anno (ora legale).

Ad esempio, in postgreSQL, il **FUSO ORARIO &quot;Europa/Parigi&quot;;** Il comando terrà conto degli orari estivi e invernali: la data sarà espressa in UTC+1 o UTC+2 a seconda dell’ora dell’anno.

Tuttavia, se utilizzi il **IMPOSTA IL FUSO ORARIO 0200;** il ritardo sarà sempre UTC+2.

## Configurazione {#configuration}

La modalità di archiviazione per le date e le ore viene selezionata durante la creazione del database (fare riferimento a [Creazione di una nuova istanza](#creating-a-new-instance)). In caso di migrazione, le ore collegate alle date vengono convertite in date e ore locali (consulta [Migrazione](#migration)).

Da un punto di vista tecnico, esistono due modi per immagazzinare **Data e ora** informazioni di tipo nel database:

1. MARCA TEMPORALE CON formato TIMEZONE: il motore di database memorizza le date in UTC. Ogni sessione aperta avrà un fuso orario e le date verranno convertite in base ad esso.
1. Formato locale + fuso orario locale: tutte le date sono memorizzate nel formato locale (nessuna gestione del ritardo temporale) e viene loro assegnato un singolo fuso orario. Il fuso orario viene memorizzato nella variabile **WdbcTimeZone** dell’istanza di Adobe Campaign e può essere modificata tramite il **[!UICONTROL Administration > Platform > Options]** menu dell&#39;albero.

>[!IMPORTANT]
>
>Tieni presente che questa modifica può causare problemi di coerenza e sincronizzazione dei dati.

### Creazione di una nuova istanza {#creating-a-new-instance}

Affinché diversi utenti internazionali possano lavorare sulla stessa istanza, è necessario configurare i fusi orari durante la creazione dell’istanza per gestire i periodi di tempo tra i vari paesi. Durante la creazione dell’istanza, seleziona la modalità di gestione della data e dell’ora nel **[!UICONTROL Time zone]** della fase di configurazione del database.

Controlla la **[!UICONTROL UTC database (date fields with time zone)]** opzione per memorizzare tutti i dati con date e ore in formato UTC (campi SQL e campi XML).

![](assets/install_wz_select_utc_option.png)

>[!IMPORTANT]
>
>Se utilizzi **Oracle**, i file del fuso orario (.dat) dei livelli client di Oracle devono essere compatibili con i file del fuso orario installati sul server.

Se il database non è UTC, è possibile selezionare uno dei fusi orari disponibili nell&#39;elenco a discesa. Puoi inoltre utilizzare il fuso orario del server o selezionare l’opzione UTC (Coordinated Universal Time).

![](assets/install_wz_unselect_utc_option.png)

Quando il **[!UICONTROL UTC Database (date fields with time zone)]** i campi SQL sono memorizzati in formato TIMESTAMP WITH TIMEZONE.

In caso contrario, verranno memorizzati nel formato locale e sarà necessario selezionare il fuso orario da applicare al database.

### Migrazione {#migration}

Quando esegui la migrazione a una versione precedente (senza gestione del fuso orario), dovrai definire la modalità di archiviazione della data nel database.

Per garantire la compatibilità con gli strumenti esterni che accedono al database Adobe Campaign, la **Data e ora** I campi SQL di tipo rimangono memorizzati per impostazione predefinita nel formato locale.

I campi XML contenenti le date sono ora memorizzati in UTC. Durante il caricamento, i campi non in formato UTC vengono convertiti automaticamente utilizzando il fuso orario dei server. Ciò significa che tutti i campi XML verranno progressivamente convertiti in formato UTC.

Per utilizzare un&#39;istanza esistente, aggiungi la **WdbcTimeZone** e immetti il fuso orario dell&#39;istanza.

>[!IMPORTANT]
>
>Assicurati che il valore corretto sia configurato per l&#39;opzione WdbcTimeZone: le modifiche apportate successivamente possono causare incongruenze.

Esempio di possibili valori:

* Europa/Parigi,
* Europa/Londra,
* America/New_York, ecc.

   Questi valori vengono ricavati dal database tz (Olson). Per ulteriori informazioni, consulta [https://en.wikipedia.org/wiki/List_of_tz_database_time_zones](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones).
