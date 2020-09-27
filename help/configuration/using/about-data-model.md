---
title: Informazioni sul modello dati Adobe Campaign Classic
description: Scopri come estendere il modello dati di Campaign, modificare gli schemi, utilizzare le API e altro ancora.
page-status-flag: never-activated
uuid: faddde15-59a1-4d2c-8303-5b3e470a0c51
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5957b39e-c2c6-40a2-b81a-656e9ff7989c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: eccf0e9899426c2517748c7a72611ff098291cd2
workflow-type: tm+mt
source-wordcount: '971'
ht-degree: 5%

---


# About the Campaign data model{#about-data-model}

Questa sezione descrive le basi del modello dati Adobe Campaign Classic, per una migliore comprensione delle tabelle integrate di Campaign e della loro interazione.

Il modello dati concettuale del database di Adobe Campaign è costituito da una serie di tabelle integrate e dalla loro interazione.

Per accedere alla descrizione di ciascuna tabella, passare a **[!UICONTROL Admin > Configuration > Data schemas]**, selezionare una risorsa dall&#39;elenco e fare clic sulla **[!UICONTROL Documentation]** scheda.

![](assets/data-model_documentation-tab.png)

Per ulteriori informazioni sulla descrizione del modello dati Campaign Classic predefinito, consultare [questa sezione](../../configuration/using/data-model-description.md).

La struttura fisica e logica dei dati trasferiti nell’applicazione è descritta in XML. Essa obbedisce a una grammatica specifica ad Adobe Campaign, denominata schema. For more on Adobe Campaign schemas, read out [this section](../../configuration/using/about-schema-reference.md).

## Panoramica {#data-model-overview}

 Adobe Campaign si basa su un database relazionale contenente tabelle collegate tra loro. La struttura di base del modello dati Adobe Campaign  può essere descritta come segue.

>[!NOTE]
>
>Per ulteriori informazioni sull&#39;architettura del modello dati Campaign e sulle relative best practice, consulta [questa sezione](../../configuration/using/data-model-best-practices.md#data-model-architecture).

### Tabella destinatari {#recipient-table}

Il modello dati si basa su una tabella principale che per impostazione predefinita è la tabella Recipient (**NmsRecipient**). Questa tabella consente di archiviare tutti i profili di marketing.

Per ulteriori informazioni sulla tabella Destinatario, consulta [questa sezione](#default-recipient-table).

### Tabella di consegna {#delivery-table}

Il modello dati include anche una parte dedicata alla memorizzazione di tutte le attività di marketing. Solitamente si tratta della tabella Consegna (**NmsDelivery**). Ogni record in questa tabella rappresenta un&#39;azione di consegna o un modello di consegna. Contiene tutti i parametri necessari per eseguire le consegne, come target, contenuto, ecc.

### Tabelle dei registri {#log-tables}

Un&#39;altra parte del modello dati consente di memorizzare temporaneamente tutti i log associati all&#39;esecuzione delle campagne.

I registri di distribuzione sono tutti i messaggi inviati ai destinatari o ai dispositivi su tutti i canali. La tabella dei registri di consegna principale (**NmsBroadLog**) contiene i registri di consegna per tutti i destinatari.
La tabella dei registri di tracciamento principale (**NmsTrackingLog**) memorizza i registri di tracciamento per tutti i destinatari. I registri di tracciamento fanno riferimento alle reazioni dei destinatari, ad esempio aperture e clic delle e-mail. Ogni reazione corrisponde a un registro di tracciamento.
I registri di consegna e di tracciamento vengono eliminati dopo un certo periodo, specificato in  Adobe Campaign e modificabile. Si raccomanda pertanto vivamente di esportare i tronchi su base regolare.

### Tabelle tecniche {#technical-tables}

Infine, parte del modello di dati è costituita da dati tecnici utilizzati per il processo applicativo, inclusi operatori e diritti utente (**NmsGroup**), cartelle (**XtkFolder**).

## Utilizzo della tabella Destinatario predefinita {#default-recipient-table}

La tabella dei destinatari out-of-the-box in  Adobe Campaign rappresenta un buon punto di partenza per la creazione del modello dati. Dispone di una serie di campi e collegamenti di tabella predefiniti che possono essere facilmente estesi. Questa funzione è particolarmente utile quando si esegue il targeting principalmente dei destinatari, perché si adatta a un semplice modello dati incentrato sui destinatari.

I vantaggi derivanti dall&#39;utilizzo della tabella Destinatario standard sono i seguenti:

* Utilizzo di funzionalità quali abbonamenti, elenchi di sementi, sondaggi, social network e così via.
* Fornitura di un database di marketing con un modello dati incentrato sui destinatari.
* Implementazione più rapida.
* Facile manutenzione da parte del supporto e dei partner.

Tuttavia, è possibile estendere la tabella Destinatario, ma non ridurre il numero di campi o collegamenti nella tabella.

>[!IMPORTANT]
>
>Si consiglia di non eliminare i campi (anche se inutili) nella tabella dei destinatari, in quanto ciò potrebbe causare errori nei moduli incorporati.

Inoltre, poiché la tabella Destinatario fa parte del prodotto, sia la tabella che il modulo associato si evolvono mano a mano che il prodotto cambia. Pertanto, è necessaria ulteriore manutenzione per verificare che eventuali estensioni siano ancora valide al momento dell&#39;aggiornamento.

## Estensione del modello dati {#extending-data-model}

Quando inizi con  Adobe Campaign, devi valutare il modello dati predefinito per verificare quale tabella è la più adatta per memorizzare i dati di marketing.

Se pertinente, puoi utilizzare la tabella dei destinatari predefinita con i campi out-of-the-box, come descritto in [questa sezione](#default-recipient-table).

Se necessario, potete estenderlo con due meccanismi:

* Estende una tabella esistente con nuovi campi. Ad esempio, puoi aggiungere un nuovo campo &quot;Fedeltà&quot; alla tabella Destinatario.
* Create una nuova tabella, ad esempio una tabella &quot;Acquista&quot; in cui sono elencati tutti gli acquisti effettuati da ciascun profilo del database e collegatela alla tabella Destinatario.

Per ulteriori informazioni sulla configurazione degli schemi di estensione per estendere il modello di dati concettuale, vedere [Informazioni sull&#39;edizione](../../configuration/using/about-schema-edition.md)dello schema.

>[!IMPORTANT]
>
>L&#39;estensione del modello dati è riservata agli utenti avanzati.

## Using a custom recipient table {#custom-recipient-table}

Durante la progettazione del modello di dati Adobe Campaign , puoi utilizzare la tabella [](#default-recipient-table)out-of-the-box Recipient o decidere di creare una tabella di destinatari non standard per memorizzare i profili di marketing.

In effetti, se il modello dati non soddisfa la struttura incentrata sui destinatari, è possibile impostare altre tabelle come dimensione di targeting all&#39;interno  Adobe Campaign. Ad esempio, questo può essere rilevante quando è necessario rivolgersi a famiglie, account (come telefoni cellulari) e società/siti invece che semplicemente a destinatari.

>[!NOTE]
>
>In questo caso, dovrete creare una nuova mappatura [di](../../configuration/using/target-mapping.md)destinazione.

Tutti i principi e i passaggi necessari per utilizzare una tabella di destinatari personalizzata sono descritti in [questa sezione](../../configuration/using/about-custom-recipient-table.md).

I vantaggi derivanti dall&#39;utilizzo di una tabella Destinatario personalizzata sono i seguenti:

### Modello dati flessibile {#flexible-data-model}

La tabella del destinatario out-of-the-box è inutile se non hai bisogno della maggior parte dei campi della tabella Recipient o se il modello dati non è incentrato sul destinatario.

### Scalabilità {#scalability}

I grandi volumi richiedono una tabella semplificata con pochi campi per una progettazione efficiente. La tabella dei destinatari out-of-the-box contiene troppi campi inutili, che possono avere un impatto sulle prestazioni e una scarsa efficienza.

### Posizione dati {#data-location}

Se i dati si trovano in un database di marketing esistente esterno, potrebbe essere necessario troppo impegno per utilizzare la tabella dei destinatari out-of-the-box. Creare una nuova struttura basata su una struttura esistente è più semplice.

### Migrazione semplice {#easy-migration}

Non è necessaria alcuna manutenzione per verificare che tutte le estensioni siano ancora valide al momento dell&#39;aggiornamento.

>[!IMPORTANT]
>
>L&#39;utilizzo di una tabella di destinatari personalizzata è riservato agli utenti avanzati ed è soggetto a alcune limitazioni. Per ulteriori informazioni, consulta [questa sezione](../../configuration/using/about-custom-recipient-table.md).
