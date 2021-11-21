---
product: campaign
title: Guida introduttiva al modello dati di Campaign Classic
description: Scopri come estendere il modello dati di Campaign, modificare gli schemi, utilizzare le API e altro ancora
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 655b5928-b005-442f-b026-2f1b0c1abb99
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '980'
ht-degree: 6%

---

# Introduzione al modello dati di Campaign {#about-data-model}

![](../../assets/v7-only.svg)

Il modello dati concettuale del database di Adobe Campaign è costituito da una serie di tabelle integrate e dalla loro interazione. Le tabelle principali e i concetti sono elencati in questa pagina.

## Panoramica {#data-model-overview}

Adobe Campaign si basa su un database relazionale contenente tabelle collegate tra loro. La struttura di base del modello dati Adobe Campaign può essere descritta come segue.

### Tabella destinatari {#recipient-table}

Il modello dati si basa su una tabella principale che per impostazione predefinita è la tabella Destinatario (**NmsRecipient**). Questa tabella consente di memorizzare tutti i profili di marketing.

Per ulteriori informazioni sulla tabella Destinatario, consulta [questa sezione](#default-recipient-table).

### Tabella di consegna {#delivery-table}

Il modello dati include anche una parte dedicata all’archiviazione di tutte le attività di marketing. Di solito si tratta della tabella Consegna (**NmsDelivery**). Ogni record in questa tabella rappresenta un&#39;azione di consegna o un modello di consegna. Contiene tutti i parametri necessari per eseguire consegne quali target, contenuto e così via.

### Tabelle dei registri {#log-tables}

Un’altra parte del modello dati consente di memorizzare temporaneamente tutti i registri associati all’esecuzione delle campagne.

I registri di consegna sono tutti i messaggi inviati a destinatari o dispositivi su tutti i canali. La tabella dei registri di consegna principale (**NmsBroadLog**) contiene i registri di consegna per tutti i destinatari.
Tabella dei registri di tracciamento principali (**NmsTrackingLog**) memorizza i registri di tracciamento per tutti i destinatari. I registri di tracciamento si riferiscono alle reazioni dei destinatari, ad esempio aperture e clic delle e-mail. Ogni reazione corrisponde a un registro di tracciamento.
I registri di consegna e di tracciamento vengono eliminati dopo un certo periodo, che viene specificato in Adobe Campaign e può essere modificato. Pertanto, si raccomanda vivamente di esportare i registri su base regolare.

### Tabelle tecniche {#technical-tables}

Infine, una parte del modello di dati consiste in dati tecnici utilizzati per il processo applicativo, compresi gli operatori e i diritti degli utenti (**NmsGroup**), cartelle (**XtkFolder**).

## Utilizzo della tabella Destinatario incorporata {#default-recipient-table}

La tabella Destinatario incorporata in Adobe Campaign fornisce un buon punto di partenza per la creazione del modello dati. Dispone di una serie di campi predefiniti e di collegamenti alle tabelle che possono essere facilmente estesi. Questa funzione è particolarmente utile quando esegui principalmente il targeting dei destinatari, perché si adatta a un semplice modello dati incentrato sui destinatari.

I vantaggi dell’utilizzo della tabella Destinatario incorporata sono i seguenti:

* Utilizzo di funzionalità integrate quali abbonamenti, elenchi di seed e altro ancora.
* Fornire un database di marketing con un modello dati incentrato sul destinatario.
* Implementazione più rapida.
* Manutenzione semplice grazie al supporto e ai partner.

Tuttavia, è possibile estendere la tabella Destinatario, ma non ridurre il numero di campi o collegamenti nella tabella.

>[!IMPORTANT]
>
>Si consiglia di non eliminare i campi (anche se inutili) nella tabella dei destinatari, in quanto ciò potrebbe causare errori nei moduli incorporati.

Inoltre, poiché la tabella Destinatario fa parte del prodotto, sia la tabella che il modulo associato si evolvono man mano che il prodotto cambia. Pertanto, è necessaria una manutenzione aggiuntiva per verificare che eventuali estensioni siano ancora valide al momento dell’aggiornamento.

## Estensione del modello dati {#extending-data-model}

Quando inizi con Adobe Campaign, devi valutare il modello dati predefinito per verificare quale tabella è la più adatta per memorizzare i dati di marketing.

Se necessario, puoi utilizzare la tabella Destinatario predefinita con i campi predefiniti, come descritto in [questa sezione](#default-recipient-table).

Se necessario, puoi estenderlo con due meccanismi:

* Estende una tabella esistente con nuovi campi. Ad esempio, puoi aggiungere un nuovo campo &quot;Fedeltà&quot; alla tabella Destinatario.
* Crea una nuova tabella, ad esempio una tabella &quot;Acquisto&quot; in cui sono elencati tutti gli acquisti effettuati da ciascun profilo del database e collegalo alla tabella Destinatario.

Per ulteriori informazioni sulla configurazione degli schemi di estensione per estendere il modello dati concettuale, consulta [Informazioni sulla modifica degli schemi](../../configuration/using/about-schema-edition.md).

>[!IMPORTANT]
>
>L’estensione del modello dati è riservata agli utenti avanzati.

## Utilizzo di una tabella dei destinatari personalizzata {#custom-recipient-table}

Durante la progettazione del modello dati Adobe Campaign, puoi utilizzare la funzione [tabella dei destinatari predefinita](#default-recipient-table)o decidere di creare un [tabella dei destinatari personalizzata](../../configuration/using/about-custom-recipient-table.md) per memorizzare i profili di marketing.

In effetti, se il modello dati non si adatta alla struttura incentrata sul destinatario, puoi impostare altre tabelle come dimensione di targeting all’interno di Adobe Campaign. Ad esempio, questo può essere rilevante quando devi rivolgerti a famiglie, account (come telefoni cellulari) e aziende/siti invece che semplicemente a destinatari.

>[!NOTE]
>
>In questo caso, dovrai creare una nuova [mappatura target](../../configuration/using/target-mapping.md).

Tutti i principi e i passaggi necessari quando si utilizza una tabella dei destinatari personalizzata sono descritti in [questa sezione](../../configuration/using/about-custom-recipient-table.md).

I vantaggi dell’utilizzo di una tabella Destinatario personalizzata sono i seguenti:

* **Modello dati flessibile** - La tabella dei destinatari predefinita è inutile se non hai bisogno della maggior parte dei campi della tabella dei destinatari o se il modello dati non è incentrato sul destinatario.

* **Scalabilità** - I grandi volumi richiedono una tabella semplificata con pochi campi per una progettazione efficiente. La tabella Destinatario predefinita avrebbe troppi campi inutili, che potrebbero influire sulle prestazioni e non essere efficiente.

* **Posizione dati** - Se i dati si trovano in un database di marketing esistente esterno, potrebbe essere necessario troppo impegno per utilizzare la tabella Destinatario preconfigurata. Creare un nuovo modello basato su una struttura esistente è più semplice.

* **Migrazione semplice** - Non è necessaria alcuna manutenzione per verificare che tutte le estensioni siano ancora valide al momento dell&#39;aggiornamento.

>[!IMPORTANT]
>
>L’utilizzo di una tabella dei destinatari personalizzata è riservato agli utenti avanzati ed è soggetto a alcune limitazioni. Per ulteriori informazioni, consulta [questa sezione](../../configuration/using/about-custom-recipient-table.md).

## Argomenti correlati

Ulteriori informazioni sul modello dati di Campaign sono disponibili nelle sezioni seguenti:

* **Descrizione delle principali tabelle** - Per ulteriori informazioni sulla descrizione predefinita del modello dati di Campaign Classic, consulta [questa sezione](../../configuration/using/data-model-description.md).

* **Descrizione completa di ciascuna tabella** - Per accedere alla descrizione completa di ogni tabella, vai a **[!UICONTROL Admin > Configuration > Data schemas]**, seleziona una risorsa dall’elenco e fai clic sul pulsante **[!UICONTROL Documentation]** scheda .

   ![](assets/data-model_documentation-tab.png)


* **Schemi di Campaign** - La struttura fisica e logica dei dati trasferiti nell&#39;applicazione è descritta in XML. Essa obbedisce a una grammatica specifica ad Adobe Campaign, denominata schema. Per ulteriori informazioni sugli schemi Adobe Campaign, consulta [questa sezione](../../configuration/using/about-schema-reference.md).

* **Best practice per i modelli di dati** - Scopri l’architettura del modello dati Campaign e le relative best practice, in [questa sezione](../../configuration/using/data-model-best-practices.md#data-model-architecture).
