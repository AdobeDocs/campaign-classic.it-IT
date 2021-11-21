---
product: campaign
title: Esempi
description: Esempi
audience: campaign
content-type: reference
topic-tags: distributed-marketing
exl-id: 2bef6b5e-887e-4c56-bb4b-3583472ca333
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1296'
ht-degree: 0%

---

# Esempi{#examples}

![](../../assets/v7-only.svg)

## Creazione di una campagna locale (tramite modulo) {#creating-a-local-campaign--by-form-}

La **Per modulo** l&#39;interfaccia web di tipo include l&#39;utilizzo di **applicazione web**. A seconda della configurazione, questa applicazione web può contenere qualsiasi tipo di elementi personalizzati definiti. Ad esempio, puoi suggerire collegamenti per valutare il target, il budget, il contenuto, ecc. tramite API dedicate.

>[!NOTE]
>
>Le API sono descritte in un documento dedicato, il cui accesso dipende dal contratto. Fai riferimento a [API](../../configuration/using/about-web-services.md).
>
>L&#39;applicazione Web utilizzata in questo esempio non è un&#39;app Web preconfigurata con Adobe Campaign. Per utilizzare un modulo in una campagna, è necessario creare l’applicazione Web dedicata.

Quando crei il modello di campagna, fai clic sul pulsante **[!UICONTROL Zoom]** all’interno dell’icona **[!UICONTROL Web interface]** opzione **[!UICONTROL Advanced campaign settings...]** link per accedere ai dettagli dell&#39;applicazione web.

![](assets/mkg_dist_local_op_form1.png)

>[!NOTE]
>
>I parametri dell&#39;applicazione Web sono disponibili solo nel modello della campagna.

In **[!UICONTROL Edit]** seleziona la scheda **Ordine campagna** e aprilo per accedere al relativo contenuto.

![](assets/mkg_dist_web_app1.png)

In questo esempio, la **Ordine campagna** l’attività include:

* campi che l’entità locale deve inserire durante l’ordine,

   ![](assets/mkg_dist_web_app2.png)

* collegamenti che consentiranno all’entità locale di valutare la campagna (ad esempio target, budget, contenuto, ecc.),

   ![](assets/mkg_dist_web_app3.png)

* script che consentono di calcolare e visualizzare il risultato di queste valutazioni.

   ![](assets/mkg_dist_web_app4.png)

In questo esempio vengono utilizzate le seguenti API:

* Per la valutazione dell&#39;obiettivo,

   ```
   var res = nms.localOrder.EvaluateTarget(ctx.localOrder);
   ```

* Per la valutazione del bilancio,

   ```
   var res = nms.localOrder.EvaluateDeliveryBudget(ctx.@deliveryId, NL.XTK.parseNumber(ctx.@compt));
   ```

* Per la valutazione del contenuto,

   ```
   var res = nms.localOrder.EvaluateContent(ctx.localOrder, ctx.@deliveryId, "html", resSeed.@id);
   ```

## Creazione di una campagna collaborativa (tramite approvazione target) {#creating-a-collaborative-campaign--by-target-approval-}

### Introduzione {#introduction}

Sei il responsabile marketing di un grande marchio di abbigliamento che ha un negozio online e diverse boutique in tutti gli Stati Uniti. Ora che la primavera è arrivata, si decide di creare un&#39;offerta speciale che darà ai vostri migliori clienti il 50% di sconto di tutti i vestiti nel vostro catalogo.

Questa offerta è rivolta ai migliori clienti dei vostri negozi degli Stati Uniti, cioè quelli che hanno speso più di $300 dall&#39;inizio dell&#39;anno.

Decidi quindi di utilizzare Distributed Marketing per creare una campagna collaborativa (tramite approvazione target) che ti permetterà di selezionare i migliori clienti dei tuoi negozi (raggruppati per regione), che riceveranno l&#39;e-mail di consegna contenente l&#39;offerta speciale.

La prima parte di questo esempio illustra le entità locali che ricevono la notifica di creazione della campagna e come possono utilizzarla per valutare la campagna e ordinarla.

La seconda parte di questo esempio spiega come creare la campagna.

Le fasi sono le seguenti:

**Per l&#39;entità locale**

1. Utilizza la notifica di creazione della campagna per accedere all’elenco dei contatti selezionati dall’entità centrale.
1. Selezionare i contatti e approvare la partecipazione.

**Per l&#39;entità centrale:**

1. Crea un **[!UICONTROL Data distribution]** attività.
1. Crea la campagna collaborativa.
1. Pubblica la campagna.

### Lato entità locale {#local-entity-side}

1. Le entità locali scelte per partecipare alla campagna riceveranno una notifica e-mail.

   ![](assets/mkg_dist_use_case_target_valid8.png)

1. Facendo clic sul pulsante **[!UICONTROL Access your contact list and approve targeting]** l’entità locale ha accesso (tramite browser web) all’elenco dei client selezionati per la campagna.

   ![](assets/mkg_dist_use_case_target_valid9.png)

1. L&#39;entità locale deseleziona dall&#39;elenco alcuni contatti perché sono già stati contattati per un&#39;offerta simile dall&#39;inizio dell&#39;anno.

   ![](assets/mkg_dist_use_case_target_valid10.png)

Una volta approvati i controlli, la campagna può essere avviata automaticamente.

### Lato centrale dell&#39;entità {#central-entity-side}

#### Creazione di un’attività di distribuzione dati {#creating-a-data-distribution-activity}

1. Per impostare una campagna collaborativa (per approvazione target), devi prima creare un **[!UICONTROL Data distribution activity]**. Fai clic sul pulsante **[!UICONTROL New]** nella **[!UICONTROL Resources > Campaign management > Data distribution]** nodo.

   ![](assets/mkg_dist_use_case_target_valid3.png)

1. In **[!UICONTROL General]** è necessario specificare:

   * la **[!UICONTROL Targeting dimension]**. Qui **Distribuzione dei dati** è effettuato **Destinatari**.
   * la **[!UICONTROL Distribution type]**. Puoi scegliere una **Dimensione fissa** o **Dimensioni in percentuale**.
   * la **[!UICONTROL Assignment type]**. Seleziona la **Entità locale** opzione .
   * la **[!UICONTROL Distribution type]**. Qui, è il **[!UICONTROL Origin (@origin)]** campo presente nella tabella Destinatario che consente di identificare il rapporto tra il contatto e l’entità locale.
   * La **[!UICONTROL Approval storage]** campo . Seleziona la **Approvazione locale del destinatario** opzione .

1. In **[!UICONTROL Breakdown]** scheda , specifica:

   * la **[!UICONTROL Distribution field value]**, che corrisponde alle entità locali coinvolte nella prossima campagna.
   * entità locale **[!UICONTROL label]**.
   * la **[!UICONTROL Size]** (fisso o in percentuale). La **0 valore predefinito** comporta la selezione di tutti i destinatari collegati all’entità locale.

   ![](assets/mkg_dist_use_case_target_valid4.png)

1. Salva la nuova distribuzione dati.

#### Creazione di una campagna collaborativa {#creating-a-collaborative-campaign}

1. Da **[!UICONTROL Campaign management > Campaign]** nodo, creare un nuovo **[!UICONTROL collaborative campaign (by target approval)]**.
1. In **[!UICONTROL Targeting and workflows]** crea un flusso di lavoro per la campagna. Deve contenere un **Divisione** attività in cui **[!UICONTROL Record count limitation]** è definito dal **[!UICONTROL Data distribution]** attività.

   ![](assets/mkg_dist_use_case_target_valid5.png)

1. Aggiungi un **[!UICONTROL Local approval]** in cui è possibile specificare:

   * il contenuto del messaggio che verrà inviato alle entità locali nella notifica,
   * il richiamo all&#39;approvazione,
   * elaborazione prevista per la campagna.

   ![](assets/mkg_dist_use_case_target_valid7.png)

1. Salvare il record.

#### Pubblicazione della campagna {#publishing-the-campaign}

È ora possibile aggiungere un **pacchetto campagna** dal **[!UICONTROL Campaigns]** scheda .

1. Scegli la tua **[!UICONTROL Reference campaign]**. In **[!UICONTROL Edit]** nella scheda del pacchetto, puoi selezionare la **[!UICONTROL Approval mode]** da utilizzare per la campagna:

   * in **Manuale** , le entità locali partecipano alla campagna se accettano l’invito dall’entità centrale. Possono eliminare i contatti preselezionati se lo desiderano e l&#39;approvazione da parte del manager è necessaria per confermare la loro partecipazione alla campagna.
   * in **Automatico** , le entità locali devono partecipare alla campagna, a meno che non si registrino nuovamente. Possono eliminare i contatti senza bisogno di approvazione.

   ![](assets/mkg_dist_use_case_target_valid.png)

1. In **[!UICONTROL Description]** è possibile aggiungere una descrizione per la campagna e tutti i documenti da inviare alle entità locali.

   ![](assets/mkg_dist_use_case_target_valid1.png)

1. Approva il pacchetto della campagna, quindi avvia il flusso di lavoro per pubblicare il pacchetto e renderlo disponibile a tutte le entità locali nell’elenco dei pacchetti.

   ![](assets/mkg_dist_use_case_target_valid2.png)

## Creazione di una campagna collaborativa (tramite modulo) {#creating-a-collaborative-campaign--by-form-}

### Introduzione {#introduction-1}

Sei il responsabile marketing per un grande marchio di trucco che ha un negozio online e diverse boutique in tutti gli Stati Uniti. Per scaricare il materiale invernale e fare spazio al nuovo stock, decidi di creare un’offerta speciale destinata a due categorie di clienti: gli over 30, a cui offrirete prodotti per la cura della pelle sensibili all&#39;età, e gli under 30, a cui offrirete i prodotti più basilari per la cura della pelle.

Decidi quindi di utilizzare Distributed Marketing per creare una campagna collaborativa (per modulo) che ti permetterà di selezionare i clienti dai diversi negozi in base alla fascia di età. Questi clienti riceveranno un’e-mail di consegna con un’offerta speciale che sarà stata personalizzata in base alla loro fascia di età.

La prima parte di questo esempio illustra le entità locali che ricevono la notifica di creazione della campagna e come possono utilizzarla per valutare la campagna e ordinarla.

La seconda parte di questo esempio spiega come creare la campagna.

Le fasi sono le seguenti:

**Per l&#39;entità locale**

1. Utilizza la notifica di creazione della campagna per accedere al modulo online.
1. Personalizza la campagna (target, contenuto, volume di consegna).
1. Controlla questi campi e modificali se necessario.
1. Approva la tua partecipazione.
1. Il responsabile dell’entità locale (o dell’entità centrale) approva la configurazione e la partecipazione dell’utente.

**Per l&#39;entità centrale:**

1. Crea la campagna collaborativa.
1. Configura le **[!UICONTROL Advanced campaign settings...]** come per una campagna locale.
1. Configura il flusso di lavoro della campagna e la consegna come faresti per una campagna locale.
1. Aggiornare il modulo web.
1. Crea il pacchetto della campagna e pubblicalo.

### Lato entità locale {#local-entity-side-1}

1. Gli enti locali selezionati per partecipare alla campagna ricevono una notifica e-mail con la quale li informano della loro partecipazione alla campagna.

   ![](assets/mkg_dist_use_case_form_7.png)

1. Le entità locali compilano il modulo personalizzato, quindi:

   * valutare l&#39;obiettivo e il bilancio,
   * visualizzare in anteprima il contenuto della consegna,
   * approvino la loro partecipazione.

      ![](assets/mkg_dist_use_case_form_8.png)

1. L’operatore incaricato di convalidare gli ordini approva la loro partecipazione.

   ![](assets/mkg_dist_use_case_form_9.png)

### Lato centrale dell&#39;entità {#central-entity-side-1}

1. Per implementare una campagna collaborativa (per modulo), è necessario creare una campagna utilizzando **Campagna collaborativa (per modulo)** modello.

   ![](assets/mkg_dist_use_case_form_1.png)

1. Nella campagna **[!UICONTROL Edit]** fai clic sulla scheda **[!UICONTROL Advanced campaign settings...]** per configurarlo come campagna locale. Fai riferimento a [Creazione di una campagna locale (tramite modulo)](#creating-a-local-campaign--by-form-).

   ![](assets/mkg_dist_use_case_form_2.png)

1. Configura il flusso di lavoro della campagna e il modulo web. Fai riferimento a [Creazione di una campagna locale (tramite modulo)](#creating-a-local-campaign--by-form-).
1. Crea il pacchetto della campagna specificando la pianificazione di esecuzione e le entità locali interessate.

   ![](assets/mkg_dist_use_case_form_3.png)

1. Completare la configurazione del pacchetto selezionando la modalità di approvazione nella **[!UICONTROL Edit]** scheda .

   ![](assets/mkg_dist_use_case_form_4.png)

1. Da **[!UICONTROL Description]** scheda , puoi immettere una descrizione del pacchetto della campagna, un messaggio di notifica da inviare alle entità locali quando il pacchetto viene pubblicato e allegare tutti i documenti informativi al pacchetto della campagna.

   ![](assets/mkg_dist_use_case_form_5.png)

1. Approva il pacchetto per pubblicarlo.

   ![](assets/mkg_dist_use_case_form_6.png)
