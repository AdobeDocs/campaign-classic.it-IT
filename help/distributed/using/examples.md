---
product: campaign
title: Esempi di marketing distribuito
description: Esempi di marketing distribuito
feature: Distributed Marketing
exl-id: 2bef6b5e-887e-4c56-bb4b-3583472ca333
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1296'
ht-degree: 0%

---

# Esempi di marketing distribuito{#distributed-marketing-samples}



## Creare una campagna locale (tramite modulo) {#creating-a-local-campaign--by-form-}

L&#39;interfaccia Web di tipo **Per modulo** prevede l&#39;utilizzo di una **applicazione Web**. A seconda della configurazione, questa applicazione web può contenere qualsiasi tipo di elementi personalizzati definiti. Ad esempio, puoi suggerire collegamenti per valutare il target, il budget, il contenuto e così via. tramite API dedicate.

>[!NOTE]
>
>Le API sono descritte in dettaglio in un documento dedicato. [Ulteriori informazioni](../../configuration/using/about-web-services.md).
>
>L’applicazione web utilizzata in questo esempio non è un’app web pronta all’uso con Adobe Campaign. Per utilizzare un modulo in una campagna, devi creare l’applicazione web dedicata.

Durante la creazione del modello della campagna, fare clic sull&#39;icona **[!UICONTROL Zoom]** nell&#39;opzione **[!UICONTROL Web interface]** del collegamento **[!UICONTROL Advanced campaign settings...]** per accedere ai dettagli dell&#39;applicazione Web.

![](assets/mkg_dist_local_op_form1.png)

>[!NOTE]
>
>I parametri dell’applicazione web sono disponibili solo nel modello della campagna.

Nella scheda **[!UICONTROL Edit]**, seleziona l&#39;attività **Ordine campagna** e aprila per accedere al relativo contenuto.

![](assets/mkg_dist_web_app1.png)

In questo esempio, l&#39;attività **Ordine campagna** include:

* campi che l’ente locale deve inserire durante l’ordine,

  ![](assets/mkg_dist_web_app2.png)

* collegamenti che consentano all’ente locale di valutare la campagna (ad esempio, target, budget, contenuto, ecc.),

  ![](assets/mkg_dist_web_app3.png)

* script che consentono di calcolare e visualizzare il risultato di queste valutazioni.

  ![](assets/mkg_dist_web_app4.png)

In questo esempio, vengono utilizzate le seguenti API:

* Per la valutazione del target,

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

## Creare una campagna collaborativa (tramite approvazione target) {#creating-a-collaborative-campaign--by-target-approval-}

### Introduzione {#introduction}

Sei il responsabile marketing di un grande marchio di abbigliamento che ha un negozio online e diverse boutique in tutti gli Stati Uniti. Ora che la primavera è arrivata, decidi di creare un&#39;offerta speciale che darà ai tuoi clienti migliori il 50% di sconto su tutti i vestiti nel tuo catalogo.

Questa offerta è rivolta ai migliori clienti dei tuoi negozi negli Stati Uniti, ovvero coloro che hanno speso più di $ 300 dall&#39;inizio dell&#39;anno.

Decidi quindi di utilizzare il Marketing distribuito per creare una campagna collaborativa (per approvazione target) che ti consenta di selezionare i migliori clienti dei tuoi store (raggruppati per regione), che riceveranno la consegna e-mail contenente l’offerta speciale.

La prima parte di questo esempio illustra le entità locali che ricevono la notifica di creazione della campagna e come utilizzarla per valutare la campagna e ordinarla.

La seconda parte di questo esempio spiega come creare la campagna.

I passaggi sono i seguenti:

**Per l&#39;entità locale**

1. Utilizza la notifica di creazione della campagna per accedere all’elenco dei contatti selezionati dall’entità centrale.
1. Seleziona i contatti e approva la partecipazione.

**Per l&#39;entità centrale:**

1. Crea un&#39;attività **[!UICONTROL Data distribution]**.
1. Crea la campagna collaborativa.
1. Publish la campagna.

### Lato entità locale {#local-entity-side}

1. Le entità locali che sono state scelte per partecipare alla campagna riceveranno una notifica e-mail.

   ![](assets/mkg_dist_use_case_target_valid8.png)

1. Facendo clic sul collegamento **[!UICONTROL Access your contact list and approve targeting]**, l&#39;entità locale ha accesso (tramite browser web) all&#39;elenco dei client selezionati per la campagna.

   ![](assets/mkg_dist_use_case_target_valid9.png)

1. L’ente locale deseleziona alcuni contatti dall’elenco perché è già stato contattato per un’offerta simile dall’inizio dell’anno.

   ![](assets/mkg_dist_use_case_target_valid10.png)

Una volta approvati i controlli, la campagna può iniziare automaticamente.

### Lato entità centrale {#central-entity-side}

#### Creare un’attività di distribuzione dati {#creating-a-data-distribution-activity}

1. Per impostare una campagna collaborativa (per approvazione target) è necessario innanzitutto creare **[!UICONTROL Data distribution activity]**. Fare clic sull&#39;icona **[!UICONTROL New]** nel nodo **[!UICONTROL Resources > Campaign management > Data distribution]**.

   ![](assets/mkg_dist_use_case_target_valid3.png)

1. Nella scheda **[!UICONTROL General]** è necessario specificare:

   * **[!UICONTROL Targeting dimension]**. Qui la **distribuzione dei dati** viene eseguita sui **destinatari**.
   * **[!UICONTROL Distribution type]**. Puoi scegliere una **dimensione fissa** o una **dimensione in percentuale**.
   * **[!UICONTROL Assignment type]**. Selezionare l&#39;opzione **Entità locale**.
   * **[!UICONTROL Distribution type]**. In questo caso, è il campo **[!UICONTROL Origin (@origin)]** presente nella tabella Destinatario che consente di identificare la relazione tra il contatto e l&#39;entità locale.
   * Il campo **[!UICONTROL Approval storage]**. Selezionare l&#39;opzione **Approvazione locale del destinatario**.

1. Nella scheda **[!UICONTROL Breakdown]**, specificare:

   * **[!UICONTROL Distribution field value]**, che corrisponde alle entità locali coinvolte nella prossima campagna.
   * entità locale **[!UICONTROL label]**.
   * **[!UICONTROL Size]** (fisso o in percentuale). Il valore predefinito **0** comporta la selezione di tutti i destinatari collegati all&#39;entità locale.

   ![](assets/mkg_dist_use_case_target_valid4.png)

1. Salva la nuova distribuzione dei dati.

#### Creare una campagna collaborativa {#creating-a-collaborative-campaign}

1. Creare un nuovo **[!UICONTROL collaborative campaign (by target approval)]** dal nodo **[!UICONTROL Campaign management > Campaign]**.
1. Nella scheda **[!UICONTROL Targeting and workflows]**, crea un flusso di lavoro per la campagna. Deve contenere un&#39;attività **Split** in cui **[!UICONTROL Record count limitation]** è definito dall&#39;attività **[!UICONTROL Data distribution]**.

   ![](assets/mkg_dist_use_case_target_valid5.png)

1. Aggiungi un&#39;azione **[!UICONTROL Local approval]** in cui puoi specificare:

   * il contenuto del messaggio che sarà inviato alle entità locali nella notifica,
   * il promemoria dell’approvazione,
   * elaborazione prevista per la campagna.

   ![](assets/mkg_dist_use_case_target_valid7.png)

1. Salvare il record.

#### Publish la campagna {#publishing-the-campaign}

È ora possibile aggiungere un **pacchetto campagna** dalla scheda **[!UICONTROL Campaigns]**.

1. Scegli **[!UICONTROL Reference campaign]**. Nella scheda **[!UICONTROL Edit]** del pacchetto, puoi selezionare **[!UICONTROL Approval mode]** da utilizzare per la campagna:

   * in modalità **Manuale**, le entità locali partecipano alla campagna se accettano l&#39;invito dall&#39;entità centrale. Se lo desiderano, possono eliminare i contatti preselezionati ed è necessaria l’approvazione del manager per confermare la loro partecipazione alla campagna.
   * in modalità **Automatico**, le entità locali devono partecipare alla campagna, a meno che non si annullino la registrazione. Possono eliminare i contatti senza bisogno di approvazione.

   ![](assets/mkg_dist_use_case_target_valid.png)

1. Nella scheda **[!UICONTROL Description]** puoi aggiungere una descrizione della campagna ed eventuali documenti da inviare alle entità locali.

   ![](assets/mkg_dist_use_case_target_valid1.png)

1. Approva il pacchetto della campagna, quindi avvia il flusso di lavoro per pubblicarlo e renderlo disponibile a tutte le entità locali nell’elenco dei pacchetti.

   ![](assets/mkg_dist_use_case_target_valid2.png)

## Creare una campagna collaborativa (per modulo) {#creating-a-collaborative-campaign--by-form-}

### Introduzione {#introduction-1}

Sei il responsabile marketing per un grande marchio di trucco che ha un negozio online e diverse boutique in tutti gli Stati Uniti. Per scaricare il tuo stock invernale e fare spazio per il tuo nuovo stock, decidi di creare un’offerta speciale che sarà rivolta a due categorie di clienti: gli over 30, ai quali offrirai prodotti per la cura della pelle sensibili all’età, e gli under 30, ai quali offrirai i prodotti per la cura della pelle più semplici.

Decidi quindi di utilizzare il Marketing distribuito per creare una campagna collaborativa (per modulo) che ti consenta di selezionare i clienti dai diversi store in base alle fasce di età. Questi clienti riceveranno una consegna e-mail con un’offerta speciale che sarà stata personalizzata in base alla loro fascia di età.

La prima parte di questo esempio illustra le entità locali che ricevono la notifica di creazione della campagna e come utilizzarla per valutare la campagna e ordinarla.

La seconda parte di questo esempio spiega come creare la campagna.

I passaggi sono i seguenti:

**Per l&#39;entità locale**

1. Utilizza la notifica di creazione della campagna per accedere al modulo online.
1. Personalizza la campagna (target, contenuto, volume di consegna).
1. Controlla questi campi e modificali se necessario.
1. Approva la tua partecipazione.
1. Il manager dell’entità locale (o dell’entità centrale) approva la configurazione e la partecipazione dell’utente.

**Per l&#39;entità centrale:**

1. Crea la campagna collaborativa.
1. Configura **[!UICONTROL Advanced campaign settings...]** come faresti per una campagna locale.
1. Configura il flusso di lavoro della campagna e la consegna come faresti per una campagna locale.
1. Aggiornare il modulo web.
1. Crea il pacchetto della campagna e pubblicalo.

### Lato entità locale {#local-entity-side-1}

1. Le entità locali selezionate per partecipare alla campagna ricevono una notifica via e-mail che le informa della loro partecipazione alla campagna.

   ![](assets/mkg_dist_use_case_form_7.png)

1. Le entità locali completano il modulo personalizzato, quindi:

   * valutare l&#39;obiettivo e il bilancio,
   * visualizzare in anteprima il contenuto della consegna,
   * approvano la loro partecipazione.

     ![](assets/mkg_dist_use_case_form_8.png)

1. L’operatore incaricato di convalidare gli ordini ne approva la partecipazione.

   ![](assets/mkg_dist_use_case_form_9.png)

### Lato entità centrale {#central-entity-side-1}

1. Per implementare una campagna collaborativa (per modulo), è necessario creare una campagna utilizzando il modello **Campagna collaborativa (per modulo)**.

   ![](assets/mkg_dist_use_case_form_1.png)

1. Nella scheda **[!UICONTROL Edit]** della campagna, fai clic sul collegamento **[!UICONTROL Advanced campaign settings...]** per configurarla come campagna locale. Consulta [Creazione di una campagna locale (per modulo)](#creating-a-local-campaign--by-form-).

   ![](assets/mkg_dist_use_case_form_2.png)

1. Configura il flusso di lavoro della campagna e il modulo web. Consulta [Creazione di una campagna locale (per modulo)](#creating-a-local-campaign--by-form-).
1. Crea il pacchetto della campagna specificando la pianificazione di esecuzione e le entità locali coinvolte.

   ![](assets/mkg_dist_use_case_form_3.png)

1. Completare la configurazione del pacchetto selezionando la modalità di approvazione nella scheda **[!UICONTROL Edit]**.

   ![](assets/mkg_dist_use_case_form_4.png)

1. Dalla scheda **[!UICONTROL Description]** è possibile immettere una descrizione del pacchetto della campagna, un messaggio di notifica da inviare alle entità locali quando il pacchetto viene pubblicato e allegare qualsiasi documento informativo al pacchetto della campagna.

   ![](assets/mkg_dist_use_case_form_5.png)

1. Approva il pacchetto per pubblicarlo.

   ![](assets/mkg_dist_use_case_form_6.png)
