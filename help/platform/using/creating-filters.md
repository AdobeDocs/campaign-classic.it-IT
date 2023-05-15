---
product: campaign
title: Creazione di filtri
description: Creazione di filtri
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: platform
content-type: reference
topic-tags: filtering-data
exl-id: 58e54f67-dc87-42f1-8426-6f801e8e4fb6
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '1963'
ht-degree: 0%

---

# Creare i filtri{#creating-filters}



Quando navighi nella struttura di Adobe Campaign (dalla **[!UICONTROL Explorer]** nella home page), i dati contenuti nel database vengono visualizzati in elenchi. Questi elenchi possono essere configurati per visualizzare solo i dati richiesti dall’operatore . È quindi possibile avviare azioni sui dati filtrati. La configurazione del filtro consente di selezionare i dati da un elenco **[!UICONTROL dynamically]**. Se i dati vengono modificati, i dati filtrati vengono aggiornati.

>[!NOTE]
>
>Le impostazioni di configurazione dell’interfaccia utente sono definite localmente a livello di dispositivo. A volte può essere necessario pulire questi dati, in particolare se si verificano problemi durante l’aggiornamento dei dati. A questo scopo, utilizza **[!UICONTROL File > Clear the local cache]** menu.

## Tipologia dei filtri disponibili {#typology-of-available-filters}

Adobe Campaign consente di applicare filtri agli elenchi di dati.

Questi filtri possono essere utilizzati una sola volta oppure puoi salvarli per utilizzi futuri. È possibile applicare più filtri contemporaneamente.

In Adobe Campaign sono disponibili i seguenti tipi di filtro:

* **Filtri predefiniti**

   La **filtro predefinito** è accessibile tramite i campi situati sopra gli elenchi. Ti consente di filtrare i campi predefiniti (per i profili dei destinatari, questi sono il nome e l’indirizzo e-mail per impostazione predefinita). È possibile utilizzare i campi per immettere i caratteri per filtrare o selezionare le condizioni del filtro da un elenco a discesa.

   ![](assets/filters_recipient_default_filter.png)
<!--
  >[!NOTE]
  >
  >The **%** character replaces any character string. For example, the string `%@yahoo.com` lets you display all the profiles with an email address in the domain "yahoo.com".
-->
È possibile modificare il filtro predefinito di un elenco. Per ulteriori informazioni, consulta [Modificare il filtro predefinito](#altering-the-default-filter).

* **Filtri semplici**

   **Filtri semplici** sono filtri una tantum nelle colonne. Sono definiti con uno o più criteri di ricerca semplici nelle colonne visualizzate.

   È possibile combinare diversi filtri semplici nello stesso elenco di dati per perfezionare la ricerca. I campi filtro vengono visualizzati uno sotto l’altro. Possono essere cancellati indipendentemente l&#39;uno dall&#39;altro.

   ![](assets/filters_recipient_simple_filter.png)

   I filtri semplici sono descritti in [Creare un filtro semplice](#creating-a-simple-filter).

* **Filtri avanzati**

   **Filtri avanzati** vengono create utilizzando una query o una combinazione di query sui dati.

   Per ulteriori informazioni sulla creazione di un filtro avanzato, consulta [Creare un filtro avanzato](#creating-an-advanced-filter).

   Puoi utilizzare le funzioni per definire il contenuto del filtro. Per ulteriori informazioni, consulta [Creare un filtro avanzato con funzioni](#creating-an-advanced-filter-with-functions).

   >[!NOTE]
   >
   >Per ulteriori informazioni sulla creazione di query in Adobe Campaign, consulta [questa sezione](../../platform/using/about-queries-in-campaign.md).

* **Filtri utente**

   Un **filtro dell&#39;applicazione** è un filtro avanzato salvato, che consente di utilizzare e condividere la configurazione con gli altri operatori.

   La **[!UICONTROL Filters]** il pulsante situato sopra gli elenchi offre un set di filtri dell’applicazione che possono essere combinati per perfezionare il filtro. Il metodo per creare questi filtri viene presentato in [Salvare un filtro](#saving-a-filter).

## Modificare il filtro predefinito {#altering-the-default-filter}

Per modificare il filtro predefinito per un elenco di destinatari, fai clic sul pulsante **[!UICONTROL Profiles and Targets > Pre-defined filters]** nodo dell&#39;albero.

Per tutti gli altri tipi di dati, configura il filtro predefinito tramite il **[!UICONTROL Administration > Configuration > Predefined filters]** nodo.

Applica i seguenti passaggi:

1. Seleziona il filtro da utilizzare per impostazione predefinita.
1. Fai clic sul pulsante **[!UICONTROL Parameters]** e seleziona **[!UICONTROL Default filter for the associated document type]**.

   ![](assets/s_ncs_user_default_filter.png)

   >[!CAUTION]
   >
   >Se all’elenco è già applicato un filtro predefinito, è necessario disattivarlo prima di applicare un nuovo filtro. A questo scopo, fai clic sulla croce rossa a destra dei campi di filtraggio.

1. Fai clic su **[!UICONTROL Save]** per applicare il filtro.

   >[!NOTE]
   >
   >La finestra di definizione del filtro è descritta in [Creare un filtro avanzato](#creating-an-advanced-filter) e [Salvare un filtro](#saving-a-filter).

## Creare un filtro semplice {#creating-a-simple-filter}

Per creare una **filtro semplice**, applica i seguenti passaggi:

1. Fai clic con il pulsante destro del mouse sul campo da filtrare e seleziona **[!UICONTROL Filter on this field]**.

   ![](assets/s_ncs_user_sort_this_field.png)

   I campi di filtro predefiniti vengono visualizzati sopra l’elenco.

1. Seleziona l’opzione filtro dall’elenco a discesa oppure immetti i criteri di filtro da applicare (il metodo per selezionare o immettere i criteri dipende dal tipo di campo: testo, enumerato, ecc.).

   ![](assets/s_ncs_user_sort_fields.png)

1. Per attivare il filtro, premere Invio sulla tastiera oppure fare clic sulla freccia verde a destra dei campi del filtro.

Se il campo sul quale desideri filtrare i dati non viene visualizzato sotto forma di profilo, puoi aggiungerlo nelle colonne visualizzate, quindi filtrare la colonna. Per eseguire questa operazione,

1. Fai clic sul pulsante **[!UICONTROL Configure the list]** icona.

   ![](assets/s_ncs_user_configure_list.png)

1. Seleziona la colonna da visualizzare, ad esempio l’età dei destinatari.

   ![](assets/s_ncs_user_select_fields_to_display.png)

1. Fai clic con il pulsante destro del mouse sul pulsante **Età** nell’elenco dei destinatari e seleziona **[!UICONTROL Filter on this column]**.

   ![](assets/s_ncs_user_sort_this_column.png)

   Puoi quindi selezionare le opzioni di filtro della pagina.

   ![](assets/s_ncs_user_delete_filter.png)

## Creare un filtro avanzato {#creating-an-advanced-filter}

Per creare un **filtro avanzato**, applica i seguenti passaggi:

1. Fai clic sul pulsante **[!UICONTROL Filters]** e seleziona **[!UICONTROL Advanced filter...]**.

   ![](assets/filters_recipient_create_adv_filter.png)

   Puoi anche fare clic con il pulsante destro del mouse sull’elenco di dati da filtrare e selezionare **[!UICONTROL Advanced filter...]**.

   Viene visualizzata la finestra di definizione della condizione di filtro.

1. Fai clic sul pulsante **[!UICONTROL Expression]** per definire il valore immesso.
1. Fai clic su **[!UICONTROL Edit expression]** per selezionare il campo a cui applicare il filtro.

   ![](assets/s_user_filter_choose_field.png)

1. Dall’elenco, seleziona il campo in cui verranno filtrati i dati. Fai clic su **[!UICONTROL Finish]** per confermare.
1. Fai clic sul pulsante **[!UICONTROL Operator]** e seleziona l’operatore da applicare dall’elenco a discesa.
1. Seleziona un valore previsto dal **[!UICONTROL Value]** colonna. Puoi combinare diversi filtri per perfezionare la query. Per aggiungere una condizione di filtro, fai clic su **[!UICONTROL Add]**.

   ![](assets/s_ncs_user_filter_add_button_alone.png)

1. È possibile assegnare una gerarchia alle espressioni o modificare l’ordine delle espressioni di query utilizzando le frecce della barra degli strumenti.
1. L&#39;operatore predefinito tra le espressioni è **E**, ma puoi modificarlo facendo clic sul campo . Puoi selezionare un **Oppure** operatore.

   ![](assets/s_ncs_user_filter_operator.png)

1. Fai clic su **[!UICONTROL OK]** per confermare la creazione del filtro e applicarlo all’elenco.

Il filtro applicato viene visualizzato sopra l’elenco.

![](assets/s_ncs_user_filter_adv_edit.png)

Per modificare o modificare questo filtro, fai clic sulla relativa etichetta.

Per annullare questo filtro, fai clic sul pulsante **[!UICONTROL Remove this filter]** a destra del filtro.

![](assets/s_ncs_user_filter_adv_remove.png)

Puoi salvare un filtro avanzato per conservarlo per utilizzi futuri. Per ulteriori informazioni su questo tipo di filtro, consulta [Salvare un filtro](#saving-a-filter).

### Creare un filtro avanzato con funzioni {#creating-an-advanced-filter-with-functions}

I filtri avanzati possono utilizzare funzioni; **filtri con funzioni** vengono create tramite un editor di espressioni che consente di creare formule utilizzando i dati del database e le funzioni avanzate. Per creare un filtro con funzioni, ripeti i passaggi 1, 2 e 3 della creazione del filtro avanzato, quindi procedi come segue:

1. Nella finestra di selezione del campo, fai clic su **[!UICONTROL Advanced selection]**.
1. Selezionare il tipo di formula da utilizzare: aggregato, filtro utente esistente o espressione.

   ![](assets/s_ncs_user_filter_formula_select.png)

   Sono disponibili le seguenti opzioni:

   * **[!UICONTROL Field only]** per selezionare un campo. Questa è la modalità predefinita.
   * **[!UICONTROL Aggregate]** per selezionare la formula aggregata da utilizzare (conteggi, somma, media, massima, minima).
   * **[!UICONTROL User filter]** per selezionare uno dei filtri utente esistenti. I filtri utente sono descritti in [Salvare un filtro](#saving-a-filter).
   * **[!UICONTROL Expression]** per accedere all’editor espressioni.

      L’editor di espressioni ti consente di definire un filtro avanzato. Si presenta così:

      ![](assets/s_ncs_user_create_exp_exple01.png)

      Consente di selezionare i campi nelle tabelle del database e di allegare funzioni avanzate: Seleziona la funzione da utilizzare nel **[!UICONTROL List of functions]**. Le funzioni disponibili sono descritte in [Elenco delle funzioni](../../platform/using/defining-filter-conditions.md#list-of-functions). Quindi, seleziona il campo o i campi interessati dalle funzioni e fai clic su **[!UICONTROL OK]** per approvare l’espressione.

      >[!NOTE]
      >
      >Per un esempio di creazione di un filtro basato su un&#39;espressione, fare riferimento a [questa sezione](../../workflow/using/sending-a-birthday-email.md#identifying-recipients-whose-birthday-it-is).

## Salvare un filtro {#saving-a-filter}

I filtri sono specifici per ogni operatore e vengono reinizializzati ogni volta che l’operatore cancella la cache della console client.

Puoi creare un **filtro dell&#39;applicazione** salvando un filtro avanzato: può essere riutilizzato facendo clic con il pulsante destro del mouse su qualsiasi elenco o tramite il **[!UICONTROL Filters]** sopra gli elenchi.

Questi filtri sono inoltre accessibili direttamente tramite la procedura guidata di consegna, nella fase di selezione del target (consulta [questa sezione](../../delivery/using/creating-an-email-delivery.md) per ulteriori informazioni sulla creazione di consegne). Per creare il filtro dell&#39;applicazione, puoi:

* Converti un filtro avanzato in un filtro dell’applicazione. A questo scopo, fai clic su **[!UICONTROL Save]** prima di chiudere l’editor di filtri avanzati.

   ![](assets/s_ncs_user_filter_save.png)

* Crea questo filtro applicazione tramite **[!UICONTROL Administration > Configuration > Predefined filters]** o **[!UICONTROL Profiles and targets > Predefined filters]** per destinatari) nodo della struttura. A questo scopo, fai clic con il pulsante destro del mouse sull’elenco dei filtri e seleziona **[!UICONTROL New...]**. La procedura è la stessa per la creazione di filtri avanzati.

   La **[!UICONTROL Label]** consente di denominare questo filtro. Questo nome verrà visualizzato nella casella combinata del **[!UICONTROL Filters...]** pulsante .

   ![](assets/user_filter_apply.png)

Per eliminare tutti i filtri nell’elenco corrente, fai clic con il pulsante destro del mouse e seleziona **[!UICONTROL No filter]** o tramite **[!UICONTROL Filters]** sopra l’elenco.

Per combinare i filtri, fai clic sul pulsante **[!UICONTROL Filters]** e utilizzando **[!UICONTROL And...]** menu.

![](assets/s_ncs_user_filter_combination.png)

## Filtrare i destinatari {#filtering-recipients}

Filtri predefiniti (vedi [Salvare un filtro](#saving-a-filter)) ti consente di filtrare i profili dei destinatari contenuti nel database. Puoi modificare i filtri dalla **[!UICONTROL Profiles and Targets > Predefined filters]** nodo dell&#39;albero. I filtri sono elencati nella sezione superiore dell’area di lavoro tramite il **[!UICONTROL Filters]** pulsante .

Seleziona un filtro per visualizzarne la definizione e per accedere a un’anteprima dei dati filtrati.

![](assets/s_ncs_user_segment_edit.png)

>[!NOTE]
>
>Per un esempio dettagliato della creazione di filtri predefiniti, consulta [Caso d’uso](../../platform/using/use-case.md).

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
   <td> Aperto ma non cliccato<br /> </td> 
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
   <td> Seleziona destinatari che non sono mai stati oggetto di targeting tramite il canale Y in X mesi.<br /> </td> 
  </tr> 
  <tr> 
   <td> Destinatari molto attivi<br /> </td> 
   <td> Seleziona i destinatari che hanno fatto clic su in una consegna almeno X volte negli ultimi Y mesi.<br /> </td> 
  </tr> 
  <tr> 
 <td> Indirizzo e-mail Inserita nell'elenco Bloccati<br /> </td> 
    <td> Seleziona i destinatari il cui indirizzo e-mail si trova sul elenco Bloccati.<br/> </td>
  </tr> 
  <tr> 
   <td> Indirizzo e-mail in quarantena<br /> </td> 
   <td> Seleziona i destinatari il cui indirizzo e-mail viene messo in quarantena.<br /> </td> 
  </tr> 
  <tr> 
   <td> Indirizzi e-mail duplicati nella cartella<br /> </td> 
   <td> Seleziona i destinatari il cui indirizzo e-mail è duplicato nella cartella.<br /> </td> 
  </tr> 
  <tr> 
   <td> Nessuna apertura né clic<br /> </td> 
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
   <td> Per abbonamento<br /> </td> 
   <td> Seleziona i destinatari per abbonamento.<br /> </td> 
  </tr> 
  <tr> 
   <td> Facendo clic su un collegamento specifico<br /> </td> 
   <td> Seleziona i destinatari che hanno fatto clic su un particolare URL in una consegna.<br /> </td> 
  </tr> 
  <tr> 
   <td> Per comportamento di consegna post<br /> </td> 
   <td> Seleziona i destinatari in base al loro comportamento dopo la ricezione di una consegna.<br /> </td> 
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
   <td> Per nome o e-mail<br /> </td> 
   <td> Seleziona i destinatari in base al loro nome o al loro indirizzo e-mail.<br /> </td> 
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

Esempi di calcolo dei dati:

* Seleziona i destinatari che hanno meno di 30 anni:

   ![](assets/predefined_filters_01.png)

* Seleziona i destinatari che hanno 18 anni o più:

   ![](assets/predefined_filters_03.png)

* Seleziona destinatari di età compresa tra i 18 e i 30 anni:

   ![](assets/predefined_filters_02.png)

## Impostazioni avanzate per i filtri dati {#advanced-settings-for-data-filters}

Fai clic sul pulsante **[!UICONTROL Settings]** per accedere alle seguenti opzioni:

* **[!UICONTROL Default filter for the associated document type]**: questa opzione ti consente di suggerire questo filtro per impostazione predefinita nell’editor degli elenchi interessati dall’ordinamento.

   Ad esempio, il **[!UICONTROL By name or login]** Il filtro viene applicato agli operatori. Questa opzione è selezionata e quindi il filtro viene sempre offerto su tutti gli elenchi degli operatori.

* **[!UICONTROL Filter shared with other operators]**: questa opzione ti consente di rendere il filtro disponibile a tutti gli altri operatori del database corrente.
* **[!UICONTROL Use parameter entry form]**: questa opzione ti consente di definire i campi filtro da visualizzare sopra l’elenco quando questo filtro è selezionato. Questi campi consentono di definire le impostazioni del filtro. Questo modulo deve essere immesso in formato XML tramite **[!UICONTROL Form]** pulsante . Ad esempio, il filtro preconfigurato **[!UICONTROL Recipients who have opened]**, disponibile dall’elenco dei destinatari, visualizza un campo filtro che consente di selezionare la consegna a cui è destinato il filtro.

   La **[!UICONTROL Preview]** visualizza il risultato del filtro selezionato.

* La **[!UICONTROL Advanced parameters]** link ti consente di definire impostazioni aggiuntive. In particolare, è possibile associare una tabella SQL al filtro per renderla comune a tutti gli editor che condividono la tabella.

   Seleziona la **[!UICONTROL Do not restrict the filter]** per impedire all’utente di ignorare il filtro.

   Questa opzione è abilitata per i filtri &quot;Destinatari di una consegna&quot; e &quot;Destinatari di consegne appartenenti a una cartella&quot; offerti nella procedura guidata di consegna che non possono essere sovraccaricati.

   ![](assets/s_ncs_user_filter_advanced_param.png)
