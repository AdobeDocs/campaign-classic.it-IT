---
title: Esempi
seo-title: Esempi
description: Esempi
seo-description: null
page-status-flag: never-activated
uuid: bfc9bb13-500b-4435-b56a-550588a240bb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: distributed-marketing
discoiquuid: 7b0aef75-345d-45be-b7d0-a9f6944ee678
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1298'
ht-degree: 0%

---


# Esempi{#examples}

## Creazione di una campagna locale (per modulo) {#creating-a-local-campaign--by-form-}

L&#39;interfaccia **Per tipo di modulo** Web prevede l&#39;uso di un&#39;applicazione **** Web. A seconda della configurazione, questa applicazione Web può contenere qualsiasi tipo di elementi personalizzati definiti. Ad esempio, potete suggerire collegamenti per valutare la destinazione, il budget, il contenuto e così via. tramite API dedicate.

>[!NOTE]
>
>Le API sono dettagliate in un documento dedicato, il cui accesso dipende dal contratto. Fate riferimento a [API](../../configuration/using/about-web-services.md).
>
>L&#39;applicazione Web utilizzata in questo esempio non è un&#39;app Web disponibile con  Adobe Campaign. Per utilizzare un modulo in una campagna, è necessario creare l&#39;applicazione Web dedicata.

Quando create il modello di campagna, fate clic sull&#39; **[!UICONTROL Zoom]** icona all&#39;interno dell&#39; **[!UICONTROL Web interface]** opzione del **[!UICONTROL Advanced campaign settings...]** collegamento per accedere ai dettagli dell&#39;applicazione Web.

![](assets/mkg_dist_local_op_form1.png)

>[!NOTE]
>
>I parametri dell&#39;applicazione Web sono disponibili solo nel modello della campagna.

Nella **[!UICONTROL Edit]** scheda, selezionate l&#39;attività di ordine **** campagna e apritela per accedere al relativo contenuto.

![](assets/mkg_dist_web_app1.png)

In questo esempio, l&#39;attività dell&#39;ordine **** Campaign include:

* campi che devono essere inseriti dall&#39;entità locale durante l&#39;ordine,

   ![](assets/mkg_dist_web_app2.png)

* collegamenti che consentiranno all&#39;entità locale di valutare la campagna (ad esempio target, budget, contenuto, ecc.),

   ![](assets/mkg_dist_web_app3.png)

* script che consentono di calcolare e visualizzare il risultato di tali valutazioni.

   ![](assets/mkg_dist_web_app4.png)

In questo esempio, vengono utilizzate le seguenti API:

* Per la valutazione degli obiettivi,

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

## Creazione di una campagna collaborativa (per approvazione target) {#creating-a-collaborative-campaign--by-target-approval-}

### Introduzione {#introduction}

Sei il responsabile marketing per un grande marchio di abbigliamento che ha un negozio online e diverse boutique in tutti gli Stati Uniti. Ora che la primavera è arrivata, si decide di creare un&#39;offerta speciale che darà ai vostri migliori clienti il 50% di tutti i vestiti nel vostro catalogo.

Questa offerta è rivolta ai migliori clienti dei vostri negozi negli Stati Uniti, vale a dire a quelli che hanno speso più di 300 dollari dall&#39;inizio dell&#39;anno.

Decidete quindi di utilizzare Distributed Marketing per creare una campagna collaborativa (per approvazione target) che vi consentirà di selezionare i migliori clienti dei vostri negozi (raggruppati per regione), che riceveranno la consegna tramite e-mail contenente l&#39;offerta speciale.

La prima parte di questo esempio illustra le entità locali che ricevono la notifica di creazione della campagna e come possono utilizzarla per valutare la campagna e ordinarla.

La seconda parte di questo esempio spiega come creare la campagna.

La procedura è la seguente:

**Per l&#39;entità locale**

1. Utilizzate la notifica di creazione della campagna per accedere all&#39;elenco dei contatti selezionati dall&#39;entità centrale.
1. Selezionate i contatti e accettate la partecipazione.

**Per l&#39;entità centrale:**

1. Create un&#39; **[!UICONTROL Data distribution]** attività.
1. Create la campagna collaborativa.
1. Pubblicate la campagna.

### Lato entità locale {#local-entity-side}

1. Le entità locali che sono state scelte per partecipare alla campagna riceveranno una notifica e-mail.

   ![](assets/mkg_dist_use_case_target_valid8.png)

1. Facendo clic sul **[!UICONTROL Access your contact list and approve targeting]** collegamento, all&#39;entità locale viene fornito l&#39;accesso (tramite browser Web) all&#39;elenco dei client selezionati per la campagna.

   ![](assets/mkg_dist_use_case_target_valid9.png)

1. L&#39;entità locale annulla alcuni contatti dall&#39;elenco perché sono già stati contattati per un&#39;offerta simile dall&#39;inizio dell&#39;anno.

   ![](assets/mkg_dist_use_case_target_valid10.png)

Una volta approvati i controlli, la campagna può essere avviata automaticamente.

### Parte centrale {#central-entity-side}

#### Creazione di un&#39;attività di distribuzione dei dati {#creating-a-data-distribution-activity}

1. Per impostare una campagna collaborativa (per approvazione di destinazione), dovete innanzitutto creare una **[!UICONTROL Data distribution activity]**. Fare clic sull&#39; **[!UICONTROL New]** icona nel **[!UICONTROL Resources > Campaign management > Data distribution]** nodo.

   ![](assets/mkg_dist_use_case_target_valid3.png)

1. Nella **[!UICONTROL General]** scheda, è necessario specificare:

   * the **[!UICONTROL Targeting dimension]**. Qui la distribuzione **dei** dati viene eseguita sui **destinatari**.
   * the **[!UICONTROL Distribution type]**. È possibile scegliere una dimensione **** fissa o una **dimensione come percentuale**.
   * the **[!UICONTROL Assignment type]**. Selezionate l&#39;opzione **Entità** locale.
   * the **[!UICONTROL Distribution type]**. Qui è il **[!UICONTROL Origin (@origin)]** campo presente nella tabella Destinatario che consente di identificare la relazione tra il contatto e l&#39;entità locale.
   * Il **[!UICONTROL Approval storage]** campo. Selezionare l&#39;opzione di approvazione **locale del destinatario** .

1. In the **[!UICONTROL Breakdown]** tab, specify:

   * , **[!UICONTROL Distribution field value]** che corrisponde alle entità locali coinvolte nella prossima campagna.
   * l&#39;entità locale **[!UICONTROL label]**.
   * il valore **[!UICONTROL Size]** (fisso o percentuale). Il valore **predefinito** 0 prevede la selezione di tutti i destinatari collegati all&#39;entità locale.

   ![](assets/mkg_dist_use_case_target_valid4.png)

1. Salva la nuova distribuzione dei dati.

#### Creazione di una campagna collaborativa {#creating-a-collaborative-campaign}

1. Dal **[!UICONTROL Campaign management > Campaign]** nodo, crea un nuovo **[!UICONTROL collaborative campaign (by target approval)]**.
1. Nella **[!UICONTROL Targeting and workflows]** scheda, create un flusso di lavoro per la campagna. Deve contenere un&#39;attività **Split** in cui l&#39; **[!UICONTROL Record count limitation]** attività è definita dall&#39; **[!UICONTROL Data distribution]** attività.

   ![](assets/mkg_dist_use_case_target_valid5.png)

1. Aggiungi un’ **[!UICONTROL Local approval]** azione per specificare:

   * il contenuto del messaggio che verrà inviato alle entità locali nella notifica,
   * il promemoria di approvazione,
   * l&#39;elaborazione prevista per la campagna.

   ![](assets/mkg_dist_use_case_target_valid7.png)

1. Salvare i record.

#### Pubblicazione della campagna {#publishing-the-campaign}

È ora possibile aggiungere un pacchetto **di** campagna dall&#39;universo **Campagne** .

1. Scegli la tua **[!UICONTROL Reference campaign]**. Nella **[!UICONTROL Edit]** scheda del pacchetto, potete selezionare l&#39;opzione **[!UICONTROL Approval mode]** da utilizzare per la campagna:

   * in modalità **Manuale** , le entità locali partecipano alla campagna se accettano l&#39;invito dall&#39;entità centrale. Possono eliminare i contatti preselezionati se lo desiderano e l&#39;approvazione da parte del manager è necessaria per confermare la loro partecipazione alla campagna.
   * in modalità **Automatica** , le entità locali devono partecipare alla campagna, a meno che non si disconnettano da essa. Possono eliminare i contatti senza bisogno di approvazione.

   ![](assets/mkg_dist_use_case_target_valid.png)

1. Nella **[!UICONTROL Description]** scheda, potete aggiungere una descrizione per la campagna e tutti i documenti da inviare alle entità locali.

   ![](assets/mkg_dist_use_case_target_valid1.png)

1. Approvare il pacchetto della campagna, quindi avviare il flusso di lavoro per pubblicare il pacchetto e renderlo disponibile a tutte le entità locali nell&#39;elenco dei pacchetti.

   ![](assets/mkg_dist_use_case_target_valid2.png)

## Creazione di una campagna collaborativa (per modulo) {#creating-a-collaborative-campaign--by-form-}

### Introduzione {#introduction-1}

Sei il responsabile marketing per un grande marchio di trucco che ha un negozio online e diverse boutique in tutti gli Stati Uniti. Per scaricare il materiale invernale e fare spazio per il nuovo stock, si decide di creare un&#39;offerta speciale per due categorie di clienti: gli oltre 30, a cui offrirete prodotti per la cura della pelle sensibili all&#39;età, e i meno 30 anni, a cui offrirete i più basilari prodotti per la cura della pelle.

Decidete quindi di utilizzare Distributed Marketing per creare una campagna collaborativa (per modulo) che vi consentirà di selezionare i client dai diversi store per fasce di età. Questi clienti riceveranno un&#39;e-mail di consegna con un&#39;offerta speciale che sarà stata personalizzata in base alla loro fascia di età.

La prima parte di questo esempio illustra le entità locali che ricevono la notifica di creazione della campagna e come possono utilizzarla per valutare la campagna e ordinarla.

La seconda parte di questo esempio spiega come creare la campagna.

La procedura è la seguente:

**Per l&#39;entità locale**

1. Utilizzare la notifica di creazione della campagna per accedere al modulo online.
1. Personalizzare la campagna (target, contenuto, volume di distribuzione).
1. Controllate questi campi e modificateli se necessario.
1. Approva la tua partecipazione.
1. Il manager dell’entità locale (o dell’entità centrale) approva la configurazione e la partecipazione dell’utente.

**Per l&#39;entità centrale:**

1. Create la campagna collaborativa.
1. Configurate le **[!UICONTROL Advanced campaign settings...]** stesse impostazioni per una campagna locale.
1. Configurate il flusso di lavoro della campagna e la distribuzione come fareste per una campagna locale.
1. Aggiornare il modulo Web.
1. Create il pacchetto della campagna e pubblicatelo.

### Lato entità locale {#local-entity-side-1}

1. Le entità locali selezionate per partecipare alla campagna ricevono una notifica via e-mail in cui vengono informate della loro partecipazione alla campagna.

   ![](assets/mkg_dist_use_case_form_7.png)

1. Le entità locali compilano il modulo personalizzato, quindi:

   * valutare l&#39;obiettivo e il bilancio,
   * visualizzare in anteprima il contenuto della distribuzione,
   * approva la loro partecipazione.

      ![](assets/mkg_dist_use_case_form_8.png)

1. L&#39;operatore incaricato di convalidare gli ordini approva la loro partecipazione.

   ![](assets/mkg_dist_use_case_form_9.png)

### Parte centrale {#central-entity-side-1}

1. Per implementare una campagna collaborativa (per modulo), è necessario creare una campagna utilizzando il modello Campagna **Collaborativa (per modulo)** .

   ![](assets/mkg_dist_use_case_form_1.png)

1. Nella **[!UICONTROL Edit]** scheda della campagna, fate clic sul **[!UICONTROL Advanced campaign settings...]** collegamento per configurarlo come campagna locale. Fare riferimento a [Creazione di una campagna locale (per modulo)](#creating-a-local-campaign--by-form-).

   ![](assets/mkg_dist_use_case_form_2.png)

1. Configurare il flusso di lavoro della campagna e il modulo Web. Fare riferimento a [Creazione di una campagna locale (per modulo)](#creating-a-local-campaign--by-form-).
1. Create il pacchetto della campagna specificando la pianificazione di esecuzione e le entità locali interessate.

   ![](assets/mkg_dist_use_case_form_3.png)

1. Per completare la configurazione del pacchetto, selezionate la modalità di approvazione nella **[!UICONTROL Edit]** scheda.

   ![](assets/mkg_dist_use_case_form_4.png)

1. Dalla **[!UICONTROL Description]** scheda, potete immettere una descrizione del pacchetto della campagna, un messaggio di notifica da inviare alle entità locali quando il pacchetto viene pubblicato e allegare eventuali documenti informativi al pacchetto della campagna.

   ![](assets/mkg_dist_use_case_form_5.png)

1. Approvare il pacchetto per pubblicarlo.

   ![](assets/mkg_dist_use_case_form_6.png)

