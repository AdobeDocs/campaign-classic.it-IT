---
title: '"Casi di utilizzo: moduli web"'
seo-title: '"Casi di utilizzo: moduli web"'
description: '"Casi di utilizzo: moduli web"'
seo-description: null
page-status-flag: never-activated
uuid: b2c3f171-325e-4913-a188-a791bad0df2e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-forms
discoiquuid: cfa22577-0b9e-4eee-900d-214b81256d81
translation-type: tm+mt
source-git-commit: 75cbb8d697a95f4cc07768e6cf3585e4e079e171
workflow-type: tm+mt
source-wordcount: '960'
ht-degree: 2%

---


# Casi di utilizzo: moduli web{#use-cases-web-forms}

## Creare un modulo di iscrizione con doppio consenso {#create-a-subscription--form-with-double-opt-in}

Quando offrite servizi di informazione, i destinatari devono abbonarsi per ricevere tutte le comunicazioni collegate. Per evitare comunicazioni improprie e assicurarsi che il destinatario si sia iscritto intenzionalmente, si consiglia di inviare una richiesta di conferma dell&#39;iscrizione per creare un doppio consenso. L&#39;iscrizione sarà effettiva solo dopo che l&#39;utente farà clic sul collegamento incluso nel messaggio di conferma.

Questo esempio si basa sullo scenario seguente:

1. Creazione di un modulo di iscrizione a una newsletter su un sito Web contenente una casella di controllo per l’iscrizione a un servizio temporaneo. Questo servizio consente di inviare messaggi di conferma dell’iscrizione.
1. Creazione della consegna di conferma dell&#39;iscrizione con un modello di consegna collegato al modulo Web. Contiene il collegamento di conferma che richiama il modulo per l’iscrizione alla newsletter e visualizza un messaggio di approvazione dell’iscrizione.

### Passaggio 1 - Creazione di servizi di informazione {#step-1---creating-information-services}

1. Create il servizio di iscrizione per la newsletter da offrire ai destinatari. Per ulteriori informazioni sulla creazione di una newsletter, consultate [questa sezione](../../delivery/using/about-services-and-subscriptions.md).

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_1.png)

1. Create un secondo servizio informazioni, un servizio temporaneo collegato a un modello di consegna per l&#39;invio di messaggi di conferma dell&#39;iscrizione.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_1c.png)

### Passaggio 2 - Creazione di messaggi di conferma {#step-2---creating-confirmation-messages}

I messaggi di conferma vengono inviati tramite un modello di consegna dedicato a cui viene fatto riferimento a livello di servizio temporaneo.

1. In the **[!UICONTROL Explorer]** , select **[!UICONTROL Resources > Templates > Delivery templates]**.
1. Create un modello di consegna per l&#39;invio dei messaggi di conferma dell&#39;iscrizione.
1. Fate clic sul **[!UICONTROL To]** pulsante in **[!UICONTROL Email parameters]** per associare il modello di consegna alla mappatura di destinazione Iscrizioni anziché ai destinatari.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_1d.png)

1. Poiché i destinatari della consegna non hanno confermato la loro approvazione, si trovano ancora nel elenco Bloccati del database. Affinché ricevano questa comunicazione, è necessario autorizzare le consegne basate su questo modello per i destinatari a elenco Bloccati.

   A tale scopo, fare clic sulla **[!UICONTROL Exclusions]** scheda.

1. Fate clic sul **[!UICONTROL Edit...]** collegamento e deselezionate l’ **[!UICONTROL Exclude recipients who no longer want to be contacted (blacklist)]** opzione.

   <!-- ![](assets/s_ncs_admin_survey_double-opt-in_sample_4d.png)-->

   >[!IMPORTANT]
   >
   >Questa opzione può essere disabilitata solo in questo tipo di contesto.

1. Personalizza la consegna e inserisci il collegamento di conferma nel contenuto del messaggio. Questo collegamento consente di accedere al modulo Web per registrare la conferma dell&#39;iscrizione.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_1b.png)

1. Con DCE, collegare l’URL al modulo Web. Poiché il modulo Web non è ancora stato creato, sostituire il valore non appena lo si crea.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_3.png)

1. Infine, collegate questo modello al servizio temporaneo creato in precedenza.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_3c.png)

### Passaggio 3 - Creazione del modulo di iscrizione {#step-3---creating-the-subscription-form}

Il modulo Web abilita sia l&#39;iscrizione del destinatario che la conferma dell&#39;iscrizione.

Il flusso di lavoro del modulo Web includerà le seguenti attività:

![](assets/s_ncs_admin_survey_double-opt-in_sample_4c.png)

Per farlo, segui la procedura indicata di seguito:

1. Creare un modulo Web e scegliere il modello **[!UICONTROL Newsletter subscription (subNewsletter)]**.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_5a.png)

1. Nella **[!UICONTROL Edit]** scheda, è necessario configurare il flusso di lavoro esistente perché si desidera aggiungere un messaggio di conferma ai destinatari che desiderano iscriversi.

   A tale scopo, fate doppio clic sulla **[!UICONTROL Preloading]** casella e configuratela come segue.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_5b.png)

   Ciò significa che se l&#39;utente accede a questo modulo tramite il collegamento contenuto nel messaggio di conferma, le relative informazioni di profilo verranno caricate. Se accedono al modulo Web tramite una pagina del sito Web, non verrà caricata alcuna informazione.

1. Aggiungete un&#39; **[!UICONTROL Test]** attività al flusso di lavoro.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_6e.png)

   L&#39; **[!UICONTROL Test]** attività può riguardare l&#39;e-mail del destinatario. In questo caso, configuratelo come segue:

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_6d.png)

1. Aggiungi due **[!UICONTROL Script]** attività al flusso di lavoro.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_6f.png)

   La prima **[!UICONTROL Script]** attività aggiungerà i destinatari al elenco Bloccati fino a quando non avranno confermato la loro iscrizione alla newsletter. Il contenuto deve essere il seguente:

   ```
   ctx.recipient.@blackList=1
   ```

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_6bbis.png)

   La seconda **[!UICONTROL Script]** attività autorizza l&#39;invio agli utenti e la sottoscrizione alla newsletter. Le ultime due righe dello script consentiranno di trasferire i destinatari dalla cartella temp a un&#39;altra cartella e di riconciliarsi con i profili esistenti non appena avranno confermato l&#39;iscrizione.

   ```
   ctx.recipient.@blackList=0
   nms.subscription.Subscribe("INTERNAL_NAME_OF_THE_NEWSLETTER", ctx.recipient, false)
   ctx.recipient.folder = <folder name="nmsRootRecipient"/>
   nms.subscription.Unsubscribe("TEMP", ctx.recipient)
   ```

   >[!NOTE]
   >
   >La **[!UICONTROL Temp]** partizione può anche essere eliminata regolarmente utilizzando un flusso di lavoro.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_6b.png)

1. Fate doppio clic sull&#39; **[!UICONTROL Subscription]** attività per personalizzare il modulo di iscrizione e collegate una casella di controllo con il servizio temporaneo creato in precedenza.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_5c.png)

1. Configurare l&#39; **[!UICONTROL Storage]** attività per salvare le informazioni immesse nella pagina del modulo.

   Questa attività consente di creare i profili dei destinatari in un temporaneo dedicato per impostarli separatamente dai profili nel database a cui possono essere inviate le comunicazioni.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_5g.png)

   >[!NOTE]
   >
   >Non è necessario definire opzioni di riconciliazione.

1. Aggiungete due **[!UICONTROL End]** attività per visualizzare un messaggio per l&#39;utente.

   La seconda **[!UICONTROL End]** casella visualizza il messaggio di conferma al termine dell&#39;iscrizione.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_5h.png)

1. Una volta creato e configurato il modulo Web, è ora possibile farvi riferimento nel modello di consegna per inviare messaggi di conferma.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_7b.png)

### Passaggio 4 - Pubblicazione e verifica del modulo {#step-4---publishing-and-testing-the-form}

È ora possibile pubblicare il modulo per renderlo accessibile agli utenti.

![](assets/s_ncs_admin_survey_double-opt-in_sample_8b.png)

L’iscrizione alla newsletter prevede i seguenti passaggi:

1. L’utente del sito Web accede alla pagina di iscrizione e approva il modulo.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_8c.png)

   Gli viene comunicato tramite un messaggio nel loro browser che la loro richiesta è stata presa in considerazione.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_8d.png)

   L’utente viene aggiunto al database Adobe Campaign  nella **[!UICONTROL Temp]** cartella e il suo profilo è elenco Bloccati fino a quando non conferma la propria iscrizione tramite e-mail.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_8f.png)

1. Viene loro inviato un messaggio di conferma contenente un collegamento per l’approvazione della sottoscrizione.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_8e.png)

1. Quando fanno clic su questo collegamento, la pagina di approvazione viene visualizzata nel browser.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_8.png)

   In  Adobe Campaign, il profilo utente viene aggiornato:

   * non sono più elenco Bloccati,
   * sono iscritti al servizio informazioni.

      ![](assets/s_ncs_admin_survey_double-opt-in_sample_9.png)

## Visualizzazione di opzioni diverse a seconda dei valori selezionati {#displaying-different-options-depending-on-the-selected-values}

Nell&#39;esempio seguente, all&#39;utente viene chiesto di selezionare un tipo di veicolo. È possibile visualizzare le categorie di veicoli disponibili in base al tipo selezionato. Ciò significa che gli elementi visualizzati nella colonna di destra dipendono dalla selezione dell&#39;utente:

![](assets/s_ncs_admin_survey_condition_sample0.png)

* Quando l&#39;utente seleziona &quot;veicolo privato&quot;, viene offerta la scelta tra &quot;compatto&quot; e &quot;Minivan&quot;.

   ![](assets/s_ncs_admin_survey_condition_sample2.png)

* Quando l&#39;utente seleziona &quot;veicolo commerciale&quot;, una selezione viene visualizzata in un elenco a discesa:

   ![](assets/s_ncs_admin_survey_condition_sample1.png)

In questo esempio, il tipo di veicolo non è memorizzato nel database. L&#39;elenco a discesa è configurato come segue:

![](assets/s_ncs_admin_survey_condition_config1.png)

Queste informazioni vengono memorizzate in una variabile locale.

La visualizzazione condizionale della colonna di destra è configurata nei contenitori:

![](assets/s_ncs_admin_survey_condition_config1bis.png)

* Visibilità condizionale dei campi per un veicolo privato:

   ![](assets/s_ncs_admin_survey_condition_config2.png)

* Visibilità condizionata dei campi per un veicolo commerciale:

   ![](assets/s_ncs_admin_survey_condition_config3.png)

