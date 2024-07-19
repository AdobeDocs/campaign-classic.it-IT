---
product: campaign
title: Introduzione al modello dati di Campaign Classic
description: Scopri come estendere il modello dati di Campaign, modificare gli schemi, utilizzare le API e altro ancora
feature: Data Model, Configuration
role: Data Engineer, Developer
exl-id: 655b5928-b005-442f-b026-2f1b0c1abb99
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '980'
ht-degree: 5%

---

# Introduzione al modello dati di Campaign{#about-data-model}

Il modello dati concettuale del database di Adobe Campaign è costituito da una serie di tabelle integrate e dalla loro interazione. Le tabelle e i concetti principali sono elencati in questa pagina.

## Panoramica {#data-model-overview}

Adobe Campaign si basa su un database relazionale contenente tabelle collegate tra loro. La struttura di base del modello dati di Adobe Campaign può essere descritta come segue.

### Tabella destinatari {#recipient-table}

Il modello dati si basa su una tabella principale che è per impostazione predefinita la tabella dei destinatari (**NmsRecipient**). Questa tabella consente di memorizzare tutti i profili di marketing.

Per ulteriori informazioni sulla tabella Destinatari, vedere [questa sezione](#default-recipient-table).

### Tabella di consegna {#delivery-table}

Il modello dati include anche una parte dedicata alla memorizzazione di tutte le attività di marketing. Di solito si tratta della tabella di consegna (**NmsDelivery**). Ogni record di questa tabella rappresenta un’azione di consegna o un modello di consegna. Contiene tutti i parametri necessari per eseguire le consegne come destinazione, contenuto, ecc.

### Tabelle dei registri {#log-tables}

Un’altra parte del modello dati consente di memorizzare temporaneamente tutti i registri associati all’esecuzione delle campagne.

I registri di consegna sono tutti messaggi inviati a destinatari o dispositivi su tutti i canali. La tabella principale dei registri di consegna (**NmsBroadLog**) contiene i registri di consegna per tutti i destinatari.
La tabella principale dei registri di tracciamento (**NmsTrackingLog**) memorizza i registri di tracciamento per tutti i destinatari. I registri di tracciamento si riferiscono alle reazioni dei destinatari, ad esempio aperture delle e-mail e clic. Ogni reazione corrisponde a un registro di tracciamento.
I registri di consegna e di tracciamento vengono eliminati dopo un determinato periodo di tempo, specificato in Adobe Campaign, che può essere modificato. Pertanto, si consiglia vivamente di esportare i registri su base regolare.

### Tabelle tecniche {#technical-tables}

Infine, parte del modello dati è costituita da dati tecnici utilizzati per il processo applicativo, inclusi operatori e diritti utente (**NmsGroup**), cartelle (**XtkFolder**).

## Utilizzo della tabella dei destinatari incorporata {#default-recipient-table}

La tabella dei destinatari integrata in Adobe Campaign fornisce un buon punto di partenza per la creazione del modello di dati. Dispone di una serie di campi predefiniti e collegamenti alle tabelle che possono essere facilmente estesi. Questa funzione è particolarmente utile quando esegui il targeting principalmente dei destinatari, in quanto si adatta a un semplice modello di dati incentrato sul destinatario.

Di seguito sono riportati i vantaggi dell&#39;utilizzo della tabella predefinita Destinatario:

* Utilizzo integrato di funzionalità quali abbonamenti, elenchi di seed e altro ancora.
* Fornire a un database di marketing un modello dati incentrato sui destinatari.
* Implementazione più rapida.
* Manutenzione semplice da parte del supporto e dei partner.

Tuttavia, è possibile estendere la tabella Destinatario, ma non ridurre il numero di campi o collegamenti nella tabella.

>[!IMPORTANT]
>
>Si consiglia di non eliminare i campi (anche se sono inutili) nella tabella dei destinatari, in quanto ciò potrebbe causare errori nei moduli incorporati.

Inoltre, poiché la tabella Destinatario fa parte del prodotto, sia la tabella che la relativa forma associata si evolvono con il cambiare del prodotto. Pertanto, è necessaria una manutenzione aggiuntiva per verificare che eventuali estensioni siano ancora valide al momento dell’aggiornamento.

## Estensione del modello dati {#extending-data-model}

Quando si inizia con Adobe Campaign, è necessario valutare il modello dati predefinito per verificare quale tabella è più adatta per memorizzare i dati di marketing.

Se necessario, è possibile utilizzare la tabella Destinatario predefinita con i campi predefiniti, come descritto in [questa sezione](#default-recipient-table).

Se necessario, è possibile estenderlo con due meccanismi:

* Estendere una tabella esistente con nuovi campi. Ad esempio, puoi aggiungere un nuovo campo &quot;Fedeltà&quot; alla tabella Destinatario.
* Crea una nuova tabella, ad esempio una tabella &quot;Purchase&quot; in cui sono elencati tutti gli acquisti effettuati da ciascun profilo del database, quindi collegala alla tabella Recipient.

Per ulteriori informazioni sulla configurazione degli schemi di estensione per estendere il modello dati concettuale, vedere [Informazioni sulla modifica dello schema](../../configuration/using/about-schema-edition.md).

>[!IMPORTANT]
>
>L’estensione del modello dati è riservata agli utenti avanzati.

## Utilizzo di una tabella dei destinatari personalizzata {#custom-recipient-table}

Durante la progettazione del modello dati di Adobe Campaign, puoi utilizzare la [tabella dei destinatari incorporata](#default-recipient-table) oppure decidere di creare una [tabella dei destinatari personalizzata](../../configuration/using/about-custom-recipient-table.md) per archiviare i profili di marketing.

In effetti, se il modello dati non si adatta alla struttura incentrata sul destinatario, puoi impostare altre tabelle come dimensione di targeting in Adobe Campaign. Ad esempio, questo può essere rilevante quando è necessario rivolgersi a famiglie, account (come i telefoni cellulari) e aziende/siti anziché semplicemente ai destinatari.

>[!NOTE]
>
>In questo caso, sarà necessario creare una nuova [mappatura target](../../configuration/using/target-mapping.md).

Tutti i principi e i passaggi necessari quando si utilizza una tabella dei destinatari personalizzata sono descritti in [questa sezione](../../configuration/using/about-custom-recipient-table.md).

L’utilizzo di una tabella dei destinatari personalizzata offre i seguenti vantaggi:

* **Modello dati flessibile** - La tabella dei destinatari incorporata è inutile se non è necessaria la maggior parte dei campi della tabella dei destinatari o se il modello dati non è incentrato sui destinatari.

* **Scalabilità** - Volumi di grandi dimensioni richiedono una tabella semplificata con pochi campi per una progettazione efficiente. La tabella dei destinatari integrata conterrebbe troppi campi inutili, che potrebbero influire sulle prestazioni e sulla mancanza di efficienza.

* **Posizione dati** - Se i dati si trovano in un database di marketing esterno esistente, potrebbe essere necessario uno sforzo eccessivo per utilizzare la tabella dei destinatari incorporata. La creazione di una nuova struttura basata su una struttura esistente è più semplice.

* **Migrazione semplice** - Non è necessaria alcuna manutenzione per verificare che tutte le estensioni siano ancora valide al momento dell&#39;aggiornamento.

>[!IMPORTANT]
>
>L’utilizzo di una tabella dei destinatari personalizzata è riservato agli utenti avanzati ed è soggetto ad alcune limitazioni. Per ulteriori informazioni, consulta [questa sezione](../../configuration/using/about-custom-recipient-table.md).

## Argomenti correlati

Ulteriori informazioni sul modello dati di Campaign sono disponibili nelle sezioni seguenti:

* **Descrizione delle tabelle principali**. Per ulteriori informazioni sulla descrizione predefinita del modello dati di Campaign Classic, fare riferimento a [questa sezione](../../configuration/using/data-model-description.md).

* **Descrizione completa di ogni tabella**. Per accedere alla descrizione completa di ogni tabella, passare a **[!UICONTROL Admin > Configuration > Data schemas]**, selezionare una risorsa dall&#39;elenco e fare clic sulla scheda **[!UICONTROL Documentation]**.

  ![](assets/data-model_documentation-tab.png)


* **Schemi campagna** - La struttura fisica e logica dei dati trasferiti nell&#39;applicazione è descritta in XML. Essa obbedisce a una grammatica specifica ad Adobe Campaign, denominata schema. Per ulteriori informazioni sugli schemi di Adobe Campaign, consulta [questa sezione](../../configuration/using/about-schema-reference.md).

* **Best practice per i modelli di dati** - Scopri l’architettura dei modelli di dati di Campaign e le relative best practice, in [questa sezione](../../configuration/using/data-model-best-practices.md#data-model-architecture).
