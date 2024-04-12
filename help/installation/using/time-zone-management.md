---
product: campaign
title: Gestione del fuso orario
description: Gestione del fuso orario
feature: Installation, Instance Settings
badge-v7-prem: label="Solo on-premise/ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: e5ed96cc-3fc7-4af4-a29e-5a4c81f4fe39
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '951'
ht-degree: 1%

---

# Gestione del fuso orario{#time-zone-management}



## Principio di funzionamento {#operating-principle}

Adobe Campaign consente di esprimere le date in funzione del loro fuso orario: questo consente agli utenti internazionali di lavorare in tutto il mondo su vari fusi orari. Ogni paese che utilizza la stessa istanza può gestire l’esecuzione di campagne, il tracciamento, l’archiviazione, ecc. a seconda dell’ora locale.

Per consentire l’utilizzo della piattaforma Adobe Campaign su scala internazionale, tutte le date utilizzate dai sistemi devono essere collegabili a un fuso orario. Una data il cui fuso orario è noto può quindi essere importata in qualsiasi altro fuso orario, o indipendentemente dal fuso orario.

Adobe Campaign consente di memorizzare date/ore in formato UTC (Coordinated Universal Time). Quando i dati vengono esposti, vengono convertiti nella data/ora locale dell’operatore. La conversione viene eseguita automaticamente quando il database è configurato in UTC (fare riferimento a [Configurazione](#configuration)). Se il database non è configurato in UTC, le informazioni sul fuso orario delle date nella piattaforma vengono memorizzate in un’opzione.

Le principali funzionalità della piattaforma relative alla gestione del fuso orario sono: importazione/esportazione di dati e gestione degli operatori e dei flussi di lavoro. Il **concetto di ereditarietà** è disponibile per importazioni/esportazioni o flussi di lavoro. Per impostazione predefinita, sono configurati per il fuso orario del server di database, tuttavia è possibile ridefinire nuovi fusi orari per un flusso di lavoro e anche per una singola attività.

**Operatori** può modificare i fusi orari durante **configurazione della consegna** e può specificare il particolare fuso orario in cui verrà eseguita la consegna.

>[!IMPORTANT]
>
>Se il database non gestisce più fusi orari, per tutte le manipolazioni del filtro dati è necessario eseguire query SQL nel fuso orario del server database.

Ogni operatore Adobe Campaign è collegato a un fuso orario: queste informazioni sono configurate nel loro profilo. Per ulteriori informazioni, consulta [questo documento](../../platform/using/access-management.md).

Quando la piattaforma Adobe Campaign non richiede la gestione del fuso orario, puoi mantenere una modalità di archiviazione in formato locale con un fuso orario collegato specifico.

## Raccomandazioni {#recommendations}

I fusi orari combinano diverse realtà: l’espressione può descrivere un’attesa costante con la data UTC, oppure le ore di una regione che possono cambiare le ore due volte all’anno (ora legale).

Ad esempio, in postgreSQL, il **SET TIME ZONE &#39;Europa/Parigi&#39;;** Il comando terrà conto dell&#39;ora legale e invernale: la data sarà espressa in UTC+1 o UTC+2 a seconda dell&#39;ora dell&#39;anno.

Tuttavia, se utilizzi il **IMPOSTARE IL FUSO ORARIO 0200;** , l&#39;intervallo di tempo sarà sempre UTC+2.

## Configurazione {#configuration}

La modalità di archiviazione per date e ore viene selezionata durante la creazione del database (fare riferimento a [Creazione di una nuova istanza](#creating-a-new-instance)). In caso di migrazione, le ore collegate alle date vengono convertite in date e ore locali (fare riferimento a [Migrazione](#migration)).

Da un punto di vista tecnico, esistono due modi per archiviare **Data e ora** informazioni sul tipo nel database:

1. TIMESTAMP WITH TIMEZONE format (MARCA TEMPORALE CON FORMATO FUSO ORARIO): il motore di database memorizza le date in UTC. Ogni sessione aperta avrà un fuso orario e le date verranno convertite in base a esso.
1. Formato locale + fuso orario locale: tutte le date vengono memorizzate nel formato locale (nessuna gestione degli intervalli di tempo) e a esse viene assegnato un singolo fuso orario. Il fuso orario viene memorizzato in **WdbcTimeZone** dell&#39;istanza di Adobe Campaign e possono essere modificate tramite il **[!UICONTROL Administration > Platform > Options]** menu dell&#39;albero.

>[!IMPORTANT]
>
>Tieni presente che questa modifica può causare problemi di coerenza e sincronizzazione dei dati.

### Creazione di una nuova istanza {#creating-a-new-instance}

Affinché diversi utenti internazionali possano lavorare sulla stessa istanza, è necessario configurare i fusi orari durante la creazione dell’istanza per gestire gli intervalli tra i paesi. Durante la creazione dell’istanza, seleziona la modalità di gestione data e ora in **[!UICONTROL Time zone]** sezione della fase di configurazione del database.

Controlla la **[!UICONTROL UTC database (date fields with time zone)]** opzione per memorizzare tutti i dati con data e ora in formato UTC (campi SQL e campi XML).

![](assets/install_wz_select_utc_option.png)

>[!IMPORTANT]
>
>Se sta usando **Oracle**, i file del fuso orario (dat) dei livelli client Oracle devono essere compatibili con i file dei fusi orari installati sul server.

Se il database non è UTC, è possibile selezionare uno dei fusi orari disponibili nell&#39;elenco a discesa. È inoltre possibile utilizzare il fuso orario del server o selezionare l&#39;opzione UTC (Coordinated Universal Time).

![](assets/install_wz_unselect_utc_option.png)

Quando **[!UICONTROL UTC Database (date fields with time zone)]** Se l&#39;opzione è selezionata, i campi SQL vengono memorizzati in formato TIMESTAMP WITH TIMEZONE.

In caso contrario, vengono archiviati nel formato locale e sarà necessario selezionare il fuso orario da applicare al database.

### Migrazione {#migration}

Durante la migrazione a una versione precedente (senza la gestione del fuso orario), è necessario definire la modalità di archiviazione della data nel database.

Per garantire la compatibilità con gli strumenti esterni che accedono al database di Adobe Campaign, il **Data e ora** i campi SQL di tipo rimangono memorizzati nel formato locale per impostazione predefinita.

I campi XML contenenti date ora sono memorizzati in formato UTC. Durante il caricamento, i campi non in formato UTC vengono convertiti automaticamente utilizzando il fuso orario dei server. Ciò significa che tutti i campi XML verranno progressivamente convertiti in formato UTC.

Per utilizzare un’istanza esistente, aggiungi **WdbcTimeZone** e immettere il fuso orario dell&#39;istanza.

>[!IMPORTANT]
>
>Verificare che il valore corretto sia configurato per l&#39;opzione WdbcTimeZone: le modifiche eseguite in seguito potrebbero causare incoerenze.

Esempio di valori possibili:

* Europa/Parigi,
* Europa/Londra,
* America/New_York, ecc.

  Questi valori vengono ricavati dal database tz (Olson). Per ulteriori informazioni, consulta [https://en.wikipedia.org/wiki/List_of_tz_database_time_zones](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones).

## Fuso orario del database e del server Oracle

Per il database principale, Campaign utilizza il fuso orario del server per impostare il fuso orario della sessione nella connessione al database. L&#39;opzione &quot;WdbcTimeZone&quot; non ha alcun impatto. Pertanto, il fuso orario del server deve corrispondere a quello del database principale utilizzato da Campaign. Se non è possibile modificare il fuso orario del server, quello utilizzato da Campaign può essere sovrascritto impostando la variabile di ambiente TZ in customer.sh.