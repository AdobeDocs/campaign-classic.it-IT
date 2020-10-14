---
title: Creazione di filtri
seo-title: Creazione di filtri
description: Creazione di filtri
seo-description: null
page-status-flag: never-activated
uuid: 9fa4a80d-8f03-4f24-92a1-44f6ae2a2337
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: filtering-data
discoiquuid: 066e730b-2527-4257-b11f-2e73f746a8a5
translation-type: tm+mt
source-git-commit: 75cbb8d697a95f4cc07768e6cf3585e4e079e171
workflow-type: tm+mt
source-wordcount: '1976'
ht-degree: 0%

---


# Creazione di filtri{#creating-filters}

## Introduzione {#introduction}

Quando vi spostate nella struttura  Adobe Campaign (dal **[!UICONTROL Explorer]** menu nella home page), i dati contenuti nel database vengono visualizzati negli elenchi. Questi elenchi possono essere configurati per visualizzare solo i dati richiesti dall&#39;operatore. È quindi possibile avviare azioni sui dati filtrati. La configurazione del filtro consente di selezionare i dati da un elenco **[!UICONTROL dynamically]**. Se i dati vengono modificati, i dati filtrati vengono aggiornati.

>[!NOTE]
>
>La configurazione dello schermo è definita localmente a livello di workstation. È memorizzato in file nascosti e talvolta può essere necessario pulire questi dati, in particolare se si verificano problemi durante l&#39;aggiornamento dei dati. A questo scopo, utilizzare **[!UICONTROL File > Clear the local cache]** il menu.

## Tipologia dei filtri disponibili {#typology-of-available-filters}

 Adobe Campaign consente di applicare filtri agli elenchi di dati.

Questi filtri possono essere utilizzati una sola volta, oppure potete salvarli per un utilizzo futuro. Potete applicare più filtri contemporaneamente.

In  Adobe Campaign sono disponibili i seguenti tipi di filtro:

* Filtri predefiniti

   Il filtro **** predefinito è accessibile tramite i campi situati sopra gli elenchi. Consente di filtrare i campi predefiniti (per i profili dei destinatari, questi sono per impostazione predefinita il nome e l’indirizzo e-mail). È possibile utilizzare i campi per immettere i caratteri per filtrare o selezionare le condizioni del filtro da un elenco a discesa.

   ![](assets/filters_recipient_default_filter.png)
<!--
  >[!NOTE]
  >
  >The **%** character replaces any character string. For example, the string `%@yahoo.com` lets you display all the profiles with an e-mail address in the domain "yahoo.com".
-->
È possibile modificare il filtro predefinito di un elenco. Per ulteriori informazioni, vedere [Modifica del filtro](#altering-the-default-filter)predefinito.

* Filtri semplici

   **I filtri** semplici sono filtri una tantum sulle colonne. Vengono definiti con uno o più criteri di ricerca semplici nelle colonne visualizzate.

   È possibile combinare diversi filtri semplici sullo stesso elenco di dati per perfezionare la ricerca. I campi filtro vengono visualizzati uno sotto l&#39;altro. Possono essere eliminati indipendentemente l&#39;uno dall&#39;altro.

   ![](assets/filters_recipient_simple_filter.png)

   I filtri semplici sono descritti in [Creazione di un filtro](#creating-a-simple-filter)semplice.

* Filtri avanzati

   **I filtri** avanzati vengono creati utilizzando una query o una combinazione di query sui dati.

   Per ulteriori informazioni sulla creazione di un filtro avanzato, consultate [Creazione di un filtro](#creating-an-advanced-filter)avanzato.

   È possibile utilizzare le funzioni per definire il contenuto del filtro. Per ulteriori informazioni, vedere [Creazione di un filtro avanzato con funzioni](#creating-an-advanced-filter-with-functions).

   >[!NOTE]
   >
   >Per ulteriori informazioni sulla creazione di query in  Adobe Campaign, consultare [questa sezione](../../platform/using/about-queries-in-campaign.md).

* Filtri utente

   Un filtro **** dell&#39;applicazione è un filtro avanzato salvato, che consente di utilizzare e condividere la configurazione con gli altri operatori.

   Il **[!UICONTROL Filters]** pulsante situato sopra gli elenchi offre una serie di filtri applicativi che possono essere combinati per perfezionare il filtro. Il metodo per la creazione di questi filtri viene presentato in [Salvataggio di un filtro](#saving-a-filter).

## Modifica del filtro predefinito {#altering-the-default-filter}

Per modificare il filtro predefinito per un elenco di destinatari, fare clic sul **[!UICONTROL Profiles and Targets > Pre-defined filters]** nodo della struttura.

Per tutti gli altri tipi di dati, configura il filtro predefinito tramite il **[!UICONTROL Administration > Configuration > Predefined filters]** nodo.

Effettuate le seguenti operazioni:

1. Selezionate il filtro da usare per impostazione predefinita.
1. Fare clic sulla **[!UICONTROL Parameters]** scheda e selezionare **[!UICONTROL Default filter for the associated document type]**.

   ![](assets/s_ncs_user_default_filter.png)

   >[!CAUTION]
   >
   >Se all’elenco è già applicato un filtro predefinito, è necessario disattivarlo prima di applicare un nuovo filtro. A tale scopo, fare clic sulla croce rossa a destra dei campi di filtraggio.

1. Fate clic **[!UICONTROL Save]** per applicare il filtro.

   >[!NOTE]
   >
   >La finestra di definizione del filtro è dettagliata in [Creazione di un filtro](#creating-an-advanced-filter) avanzato e [salvataggio di un filtro](#saving-a-filter).

## Creazione di un filtro semplice {#creating-a-simple-filter}

Per creare un filtro **** semplice, effettuate le seguenti operazioni:

1. Fare clic con il pulsante destro del mouse sul campo da filtrare e selezionare **[!UICONTROL Filter on this field]**.

   ![](assets/s_ncs_user_sort_this_field.png)

   I campi filtro predefiniti sono visualizzati sopra l’elenco.

1. Selezionate l’opzione filtro dall’elenco a discesa oppure immettete i criteri di filtro da applicare (il metodo per selezionare o immettere i criteri dipende dal tipo di campo: testo, enumerato, ecc.).

   ![](assets/s_ncs_user_sort_fields.png)

1. Per attivare il filtro, premere Invio sulla tastiera oppure fare clic sulla freccia verde a destra dei campi del filtro.

Se il campo sul quale si desidera filtrare i dati non viene visualizzato nel modulo del profilo, è possibile aggiungerlo nelle colonne visualizzate e quindi filtrare su tale colonna. Per eseguire questa operazione,

1. Fate clic sull&#39; **[!UICONTROL Configure the list]** icona.

   ![](assets/s_ncs_user_configure_list.png)

1. Selezionare la colonna da visualizzare, ad esempio l&#39;età dei destinatari.

   ![](assets/s_ncs_user_select_fields_to_display.png)

1. Fare clic con il pulsante destro del mouse sulla colonna **Età** nell&#39;elenco dei destinatari, quindi selezionare **[!UICONTROL Filter on this column]**.

   ![](assets/s_ncs_user_sort_this_column.png)

   Potete quindi selezionare le opzioni di filtro pagina.

   ![](assets/s_ncs_user_delete_filter.png)

## Creazione di un filtro avanzato {#creating-an-advanced-filter}

Per creare un filtro **** avanzato, effettuate le seguenti operazioni:

1. Click the **[!UICONTROL Filters]** button and select **[!UICONTROL Advanced filter...]**.

   ![](assets/filters_recipient_create_adv_filter.png)

   È inoltre possibile fare clic con il pulsante destro del mouse sull&#39;elenco di dati da filtrare e selezionare **[!UICONTROL Advanced filter...]**.

   Viene visualizzata la finestra di definizione della condizione di filtro.

1. Fare clic sulla **[!UICONTROL Expression]** colonna per definire il valore immesso.
1. Fate clic **[!UICONTROL Edit expression]** per selezionare il campo a cui applicare il filtro.

   ![](assets/s_user_filter_choose_field.png)

1. Dall&#39;elenco, selezionare il campo in cui verranno filtrati i dati. Fate clic **[!UICONTROL Finish]** per confermare.
1. Fare clic sulla **[!UICONTROL Operator]** colonna e selezionare l&#39;operatore da applicare dall&#39;elenco a discesa.
1. Selezionare un valore previsto dalla **[!UICONTROL Value]** colonna. Potete combinare diversi filtri per perfezionare la query. Per aggiungere una condizione filtro, fate clic su **[!UICONTROL Add]**.

   ![](assets/s_ncs_user_filter_add_button_alone.png)

1. È possibile assegnare una gerarchia alle espressioni o modificare l&#39;ordine delle espressioni di query utilizzando le frecce della barra degli strumenti.
1. L&#39;operatore predefinito tra le espressioni è **AND**, ma è possibile modificarlo facendo clic sul campo. È possibile selezionare un operatore **OR** .

   ![](assets/s_ncs_user_filter_operator.png)

1. Fate clic **[!UICONTROL OK]** per confermare la creazione del filtro e applicarlo all&#39;elenco.

Il filtro applicato viene visualizzato sopra l’elenco.

![](assets/s_ncs_user_filter_adv_edit.png)

Per modificare o modificare questo filtro, fate clic sulla relativa etichetta.

Per annullare questo filtro, fate clic sull’ **[!UICONTROL Remove this filter]** icona a destra del filtro.

![](assets/s_ncs_user_filter_adv_remove.png)

Potete salvare un filtro avanzato per mantenerlo utilizzabile in futuro. Per ulteriori informazioni su questo tipo di filtro, consultate [Salvataggio di un filtro](#saving-a-filter).

### Creazione di un filtro avanzato con funzioni {#creating-an-advanced-filter-with-functions}

I filtri avanzati possono utilizzare funzioni; **i filtri con funzioni** vengono creati tramite un editor di espressioni che consente di creare formule utilizzando i dati del database e le funzioni avanzate. Per creare un filtro con funzioni, ripetete i passaggi 1, 2 e 3 per la creazione avanzata del filtro, quindi procedete come segue:

1. Nella finestra di selezione del campo fare clic su **[!UICONTROL Advanced selection]**.
1. Selezionare il tipo di formula da utilizzare: aggregazione, filtro utente esistente o espressione.

   ![](assets/s_ncs_user_filter_formula_select.png)

   Sono disponibili le seguenti opzioni:

   * **[!UICONTROL Field only]** per selezionare un campo. Questa è la modalità predefinita.
   * **[!UICONTROL Aggregate]** per selezionare la formula di aggregazione da utilizzare (conteggio, somma, media, massima, minima).
   * **[!UICONTROL User filter]** per selezionare uno dei filtri utente esistenti. I filtri utente sono descritti in [Salvataggio di un filtro](#saving-a-filter).
   * **[!UICONTROL Expression]** per accedere all&#39;editor delle espressioni.

      L&#39;editor di espressioni consente di definire un filtro avanzato. Si presenta così:

      ![](assets/s_ncs_user_create_exp_exple01.png)

      Consente di selezionare i campi nelle tabelle del database e di associare funzioni avanzate: Selezionare la funzione da utilizzare nella **[!UICONTROL List of functions]**. Le funzioni disponibili sono descritte in [Elenco delle funzioni](../../platform/using/defining-filter-conditions.md#list-of-functions). Quindi, selezionare il campo o i campi interessati dalle funzioni e fare clic **[!UICONTROL OK]** per approvare l&#39;espressione.

      >[!NOTE]
      >
      >Per un esempio di creazione di filtri basato su un&#39;espressione, fare riferimento a [Identificazione dei destinatari il cui compleanno è](../../workflow/using/sending-a-birthday-email.md#identifying-recipients-whose-birthday-it-is).

## Salvataggio di un filtro {#saving-a-filter}

I filtri sono specifici di ciascun operatore e vengono reinizializzati ogni volta che l&#39;operatore cancella la cache della propria console client.

Potete creare un filtro **** applicazione salvando un filtro avanzato: può essere riutilizzato facendo clic con il pulsante destro del mouse in un qualsiasi elenco o mediante il **[!UICONTROL Filters]** pulsante situato sopra gli elenchi.

Questi filtri sono accessibili anche direttamente tramite la procedura guidata di consegna, nella fase di selezione della destinazione (per ulteriori informazioni sulla creazione delle consegne, vedere [questa sezione](../../delivery/using/creating-an-email-delivery.md) ). Per creare il filtro dell’applicazione, potete:

* Convertite un filtro avanzato in un filtro applicazione. A questo scopo, fate clic su **[!UICONTROL Save]** prima di chiudere l&#39;editor di filtri avanzato.

   ![](assets/s_ncs_user_filter_save.png)

* Create questo filtro applicazione tramite il nodo **[!UICONTROL Administration > Configuration > Predefined filters]** (o **[!UICONTROL Profiles and targets > Predefined filters]** per i destinatari) della struttura. A questo scopo, fare clic con il pulsante destro del mouse sull&#39;elenco dei filtri e selezionare **[!UICONTROL New...]**. La procedura è la stessa utilizzata per creare filtri avanzati.

   Il **[!UICONTROL Label]** campo consente di denominare questo filtro. Questo nome verrà visualizzato nella casella combinata del **[!UICONTROL Filters...]** pulsante.

   ![](assets/user_filter_apply.png)

Per eliminare tutti i filtri dall’elenco corrente, fate clic con il pulsante destro del mouse e selezionate **[!UICONTROL No filter]** oppure utilizzate l’ **[!UICONTROL Filters]** icona che si trova sopra l’elenco.

Potete combinare i filtri facendo clic sul **[!UICONTROL Filters]** pulsante e utilizzando il **[!UICONTROL And...]** menu.

![](assets/s_ncs_user_filter_combination.png)

## Filtrare i destinatari {#filtering-recipients}

I filtri predefiniti (consultate [Salvataggio di un filtro](#saving-a-filter)) consentono di filtrare i profili dei destinatari contenuti nel database. È possibile modificare i filtri dal **[!UICONTROL Profiles and Targets > Predefined filters]** nodo della struttura ad albero. I filtri sono elencati nella sezione superiore dell&#39;area di lavoro, tramite il **[!UICONTROL Filters]** pulsante .

Selezionare un filtro per visualizzarne la definizione e accedere a un&#39;anteprima dei dati filtrati.

![](assets/s_ncs_user_segment_edit.png)

>[!NOTE]
>
>Per un esempio dettagliato di creazione di filtri predefiniti, consultate [Caso](../../platform/using/use-case.md)d’uso.

I filtri predefiniti sono:

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etichetta</strong><br /> </td> 
   <td> <strong>Query</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Aperto<br /> </td> 
   <td> Seleziona i destinatari che hanno aperto una consegna.<br /> </td> 
  </tr> 
  <tr> 
   <td> Aperto ma senza clic<br /> </td> 
   <td> Seleziona i destinatari che hanno aperto una consegna ma che non hanno fatto clic su un collegamento.<br /> </td> 
  </tr> 
  <tr> 
   <td> Destinatari inattivi<br /> </td> 
   <td> Seleziona i destinatari che non hanno aperto una consegna in X mesi.<br /> </td> 
  </tr> 
  <tr> 
   <td> Ultima attività per tipo di dispositivo<br /> </td> 
   <td> Seleziona i destinatari che hanno fatto clic o aperto la consegna Y utilizzando il dispositivo X negli ultimi giorni Z.<br /> </td> 
  </tr> 
  <tr> 
   <td> Ultima attività per tipo di dispositivo (tracciamento)<br /> </td> 
   <td> Seleziona i destinatari che hanno fatto clic o aperto la consegna Y utilizzando il dispositivo X negli ultimi giorni Z.<br /> </td> 
  </tr> 
  <tr> 
   <td> Destinatari senza targeting<br /> </td> 
   <td> Seleziona i destinatari per i quali non è mai stato eseguito il targeting tramite il canale Y in X mesi.<br /> </td> 
  </tr> 
  <tr> 
   <td> Destinatari molto attivi<br /> </td> 
   <td> Seleziona i destinatari che hanno fatto clic su una consegna almeno X volte negli ultimi Y mesi.<br /> </td> 
  </tr> 
  <tr> 
 <td> Indirizzo e-mail Inserita nell'elenco Bloccati<br /> </td> 
    <td> Seleziona i destinatari il cui indirizzo e-mail è sul elenco Bloccati.<br/> </td>
  </tr> 
  <tr> 
   <td> Indirizzo e-mail in quarantena<br /> </td> 
   <td> Seleziona i destinatari il cui indirizzo e-mail è in quarantena.<br /> </td> 
  </tr> 
  <tr> 
   <td> Indirizzi e-mail duplicati nella cartella<br /> </td> 
   <td> Seleziona i destinatari il cui indirizzo e-mail è duplicato nella cartella.<br /> </td> 
  </tr> 
  <tr> 
   <td> Non aperto né fatto clic<br /> </td> 
   <td> Seleziona i destinatari che non hanno aperto una consegna o che hanno fatto clic su di essa.<br /> </td> 
  </tr> 
  <tr> 
   <td> Nuovi destinatari (giorni)<br /> </td> 
   <td> Seleziona i destinatari creati negli ultimi X giorni.<br /> </td> 
  </tr> 
  <tr> 
   <td> Nuovi destinatari (minuti)<br /> </td> 
   <td> Seleziona i destinatari creati negli ultimi X minuti.<br /> </td> 
  </tr> 
  <tr> 
   <td> Nuovi destinatari (mesi)<br /> </td> 
   <td> Seleziona i destinatari creati negli ultimi X mesi.<br /> </td> 
  </tr> 
  <tr> 
   <td> Per iscrizione<br /> </td> 
   <td> Seleziona i destinatari in base alla sottoscrizione.<br /> </td> 
  </tr> 
  <tr> 
   <td> Facendo clic su un collegamento specifico<br /> </td> 
   <td> Seleziona i destinatari che hanno fatto clic su un particolare URL in una consegna.<br /> </td> 
  </tr> 
  <tr> 
   <td> Per comportamento di post-consegna<br /> </td> 
   <td> Seleziona i destinatari in base al loro comportamento dopo la ricezione della consegna.<br /> </td> 
  </tr> 
  <tr> 
   <td> Per data di creazione<br /> </td> 
   <td> Seleziona i destinatari per data di creazione, in un periodo compreso tra X mesi (data corrente meno n mesi) e Y mesi (data corrente meno n mesi).<br /> </td> 
  </tr> 
  <tr> 
   <td> Per elenco<br /> </td> 
   <td> Seleziona i destinatari per elenco.<br /> </td> 
  </tr> 
  <tr> 
   <td> Per numero di clic<br /> </td> 
   <td> Seleziona i destinatari che hanno fatto clic su una consegna negli ultimi X mesi.<br /> </td> 
  </tr> 
  <tr> 
   <td> Per numero di messaggi ricevuti<br /> </td> 
   <td> Seleziona i destinatari in base al numero di messaggi ricevuti.<br /> </td> 
  </tr> 
  <tr> 
   <td> Per numero di aperture<br /> </td> 
   <td> Seleziona i destinatari che hanno aperto tra le consegne X e Y per un periodo di tempo pari a Z.<br /> </td> 
  </tr> 
  <tr> 
   <td> Per nome o per e-mail<br /> </td> 
   <td> Seleziona i destinatari in base al nome o all’e-mail.<br /> </td> 
  </tr> 
  <tr> 
   <td> Per fascia di età<br /> </td> 
   <td> Seleziona i destinatari in base alla loro età.<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Tutti i confronti relativi al conteggio e ai periodi devono essere intesi nel senso più ampio (i destinatari che corrispondono ai limiti di query sono inclusi nel confronto).

Esempi di come vengono calcolati i dati:

* Seleziona i destinatari con meno di 30 anni di età:

   ![](assets/predefined_filters_01.png)

* Seleziona i destinatari che hanno almeno 18 anni di età:

   ![](assets/predefined_filters_03.png)

* Seleziona i destinatari di età compresa tra 18 e 30 anni:

   ![](assets/predefined_filters_02.png)

## Impostazioni avanzate per i filtri dati {#advanced-settings-for-data-filters}

Fare clic sulla **[!UICONTROL Settings]** scheda per accedere alle seguenti opzioni:

* **[!UICONTROL Default filter for the associated document type]**: questa opzione consente di suggerire questo filtro per impostazione predefinita nell’editor degli elenchi interessati dall’ordinamento.

   Ad esempio, il **[!UICONTROL By name or login]** filtro viene applicato agli operatori. Questa opzione è selezionata e il filtro è sempre disponibile in tutti gli elenchi degli operatori.

* **[!UICONTROL Filter shared with other operators]**: questa opzione consente di rendere disponibile il filtro a tutti gli altri operatori del database corrente.
* **[!UICONTROL Use parameter entry form]**: questa opzione consente di definire i campi filtro da visualizzare sopra l&#39;elenco quando il filtro è selezionato. Questi campi consentono di definire le impostazioni del filtro. Il modulo deve essere immesso in formato XML tramite il **[!UICONTROL Form]** pulsante. Ad esempio, il filtro preconfigurato **[!UICONTROL Recipients who have opened]**, disponibile nell&#39;elenco dei destinatari, visualizza un campo filtro che consente di selezionare la consegna a cui è destinato il filtro.

   Il **[!UICONTROL Preview]** pulsante visualizza il risultato del filtro selezionato.

* Il **[!UICONTROL Advanced parameters]** collegamento consente di definire impostazioni aggiuntive. In particolare, è possibile associare una tabella SQL al filtro per renderla comune a tutti gli editor che condividono la tabella.

   Selezionate l’ **[!UICONTROL Do not restrict the filter]** opzione per impedire all’utente di ignorare il filtro.

   Questa opzione è abilitata per i filtri &quot;Destinatari di una consegna&quot; e &quot;Destinatari di consegne appartenenti a una cartella&quot; offerti nella procedura guidata di consegna che non possono essere sovraccaricati.

   ![](assets/s_ncs_user_filter_advanced_param.png)

