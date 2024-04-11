---
product: campaign
title: Creare una campagna collaborativa
description: Scopri come creare una campagna collaborativa
feature: Distributed Marketing
exl-id: 17313fe5-ad42-45ca-a35a-1e7aa89380ef
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '915'
ht-degree: 3%

---

# Creare una campagna collaborativa{#creating-a-collaborative-campaign-intro}



L’entità centrale crea campagne collaborative da **Marketing distribuito** modelli di campagna. Consulta [questa pagina](about-distributed-marketing.md#collaborative-campaign).

## Creare una campagna collaborativa {#creating-a-collaborative-campaign}

Per configurare una campagna collaborativa, fai clic su **[!UICONTROL Campaign management > Campaigns]** , quindi il **[!UICONTROL New]** icona.

>[!NOTE]
>
>A parte **[!UICONTROL collaborative campaigns (by campaign)]**, queste campagne possono essere configurate ed eseguite tramite un’interfaccia web.

Il processo di configurazione per un database di campagne collaborative è simile a quello di un modello di campagna locale. Le specifiche dei diversi tipi di campagne di collaborazione sono descritte di seguito.

### Per modulo {#by-form}

Per creare una campagna collaborativa (per modulo), **[!UICONTROL Collaborative campaign (by form)]** deve essere selezionato.

![](assets/mkg_dist_mutual_op_form2.png)

In **[!UICONTROL Edit]** , fare clic sulla scheda **[!UICONTROL Advanced campaign settings...]** collegamento per accedere a **Marketing distribuito** scheda.

Seleziona la **Per modulo** interfaccia web. Questo tipo di interfaccia consente di creare campi di personalizzazione che verranno utilizzati dalle entità locali durante l’ordine di una campagna. Fai riferimento a [Creazione di una campagna locale (per modulo)](examples.md#creating-a-local-campaign--by-form-).

Salva la campagna. Ora puoi utilizzarlo dalla sezione **Pacchetti campagne** visualizzare in **Campagna** , facendo clic sulla scheda **[!UICONTROL Create]** pulsante.

Il **[!UICONTROL Campaign Package]** visualizzazione consente di utilizzare modelli di campagna locali (preconfigurati o duplicati), nonché campagne di riferimento per campagne collaborative, allo scopo di creare campagne per le diverse entità organizzative.

![](assets/mkg_dist_mutual_op_form1b.png)

### Per campagna {#by-campaign}

Per creare una campagna collaborativa (per campagna), il **[!UICONTROL Collaborative campaign (by campaign) (opCollaborativeByCampaign)]** deve essere selezionato.

![](assets/mkg_dist_mutual_op_by_op2.png)

Quando ordina la campagna, l’entità locale può completare i criteri predefiniti dall’entità centrale e valutare la campagna prima di ordinarla.

Una volta effettuato un ordine per un **Campagna collaborativa (per campagna)** è approvato dall’entità centrale, viene creata una campagna figlio per l’entità locale. Una volta disponibile, l’entità locale può quindi modificare:

* il flusso di lavoro della campagna,
* regole di tipologia,
* e di personalizzazione.

L’entità locale esegue la campagna figlio. L’entità centrale esegue la campagna principale.

L’entità centrale può visualizzare tutte le campagne secondarie collegate a un **Campagna collaborativa (per campagna)** da questa dashboard (tramite **[!UICONTROL List of associated campaigns]** link).

![](assets/mkg_dist_mutual_op_by_op.png)

### Per approvazione target {#by-target-approval}

Per creare una campagna collaborativa (tramite approvazione target), **[!UICONTROL Collaborative campaign (by target approval)]** deve essere selezionato.

![](assets/mkg_dist_mutual_op_by_valid.png)

>[!NOTE]
>
>In questa modalità, l’entità centrale non deve specificare le entità locali.

Il flusso di lavoro della campagna deve essere integrato **Approvazione locale** attività di tipo. I parametri di attività sono i seguenti:

* **[!UICONTROL Action to perform]** : notifica di approvazione di Target.
* **[!UICONTROL Distribution context]** : Esplicito.
* **[!UICONTROL Data distribution]** : distribuzione di entità locali.

**Distribuzione di entità locali** è necessario creare la distribuzione dei dati del tipo. Il modello di distribuzione dati consente di limitare il numero di record da un elenco di valori di raggruppamento. In entrata **[!UICONTROL Resources > Campaign management > Data distribution]**, fare clic su **[!UICONTROL New]** per creare un nuovo **[!UICONTROL Data distribution]**. Per ulteriori informazioni sulla distribuzione dei dati, consulta [Flussi di lavoro](../../workflow/using/using-the-local-approval-activity.md#step-1--creating-the-data-distribution-template-) guida.

![](assets/mkg_dist_data_distribution.png)

Seleziona la **Dimensione targeting** e **[!UICONTROL Distribution field]**. Per **[!UICONTROL Assignment type]**, seleziona **Entità locale**.

In **[!UICONTROL Distribution]** , aggiungi un campo per ogni entità locale e specifica il valore.

![](assets/mkg_dist_data_distribution2.png)

Puoi aggiungere un secondo **Approvazione target** dopo il **Consegna** digita attività per configurare un rapporto su di essa.

Nel messaggio di notifica per la creazione della campagna, l’entità locale riceve un elenco di contatti predefinito dai parametri dell’entità centrale.

![](assets/mkg_dist_mutual_op_by_valid1.png)

L’entità locale può eliminare alcuni contatti in base al contenuto della campagna.

![](assets/mkg_dist_mutual_op_by_valid2.png)

### Semplice {#simple}

Per creare una semplice campagna collaborativa, **[!UICONTROL Collaborative campaign (simple)]** deve essere selezionato.

## Creazione di un pacchetto di campagne collaborative {#creating-a-collaborative-campaign-package}

Per rendere una campagna disponibile alle entità locali, l’entità centrale deve creare un pacchetto di campagna.

Applica i seguenti passaggi:

1. In **[!UICONTROL Navigation]** sezione sul **Campagne** , fare clic su **[!UICONTROL Campaign packages]** collegamento.
1. Fai clic sul pulsante **[!UICONTROL Create]**.
1. La sezione nella parte superiore della finestra consente di selezionare **[!UICONTROL New collaborative package (mutualizedEmpty)]** modello.
1. Seleziona la campagna di riferimento.
1. Specifica l’etichetta, la cartella e la pianificazione di esecuzione per il pacchetto della campagna.

### Date {#dates}

Le date di inizio e di fine definiscono il periodo di visibilità della campagna nell’elenco dei pacchetti della campagna.

Per **campagne collaborative**, l’entità centrale deve specificare il termine di registrazione e personalizzazione.

>[!NOTE]
>
>Il **[!UICONTROL Personalization deadline]** consente all’entità centrale di scegliere una scadenza entro la quale le entità locali devono aver consegnato i documenti (fogli di calcolo, immagini) da utilizzare per configurare la campagna. Questa non è un’opzione obbligatoria. Il passaggio secondario di questa data non influirà sull’implementazione della campagna.

![](assets/s_advuser_mkg_dist_create_mutual_entry.png)

### Pubblico {#audience}

L’entità centrale deve specificare le entità locali coinvolte per campagna non appena viene creata la campagna collaborativa.

![](assets/s_advuser_mkg_dist_create_mutual_entry2.png)

>[!CAUTION]
>
>**[!UICONTROL Simple, by form and by campaign collaborative campaign kits]** non può essere approvata a meno che non siano state specificate le entità locali pertinenti.

### Modalità di approvazione {#approval-modes}

Per **campagne collaborative**, è possibile specificare la modalità di approvazione dell’ordine.

![](assets/mkg_dist_edit_kit1.png)

In modalità manuale, l’entità locale deve abbonarsi alla campagna per poter partecipare.

In modalità automatica, l’entità locale è preabbonata alla campagna. Può annullare l’abbonamento alla campagna o modificarne i parametri senza aver bisogno dell’approvazione dell’entità centrale.

![](assets/mkg_dist_edit_kit2.png)

### Notifiche {#notifications}

La configurazione per le notifiche è identica alle notifiche per un’entità locale. Fai riferimento a [questa sezione](creating-a-local-campaign.md#notifications).

## Ordinare una campagna {#ordering-a-campaign}

Quando una campagna collaborativa viene aggiunta all’elenco dei pacchetti di campagne, vengono notificate le entità locali appartenenti al pubblico definito dall’entità centrale (il **campagne collaborative (per approvazione target)** non hanno un pubblico predefinito). Il messaggio inviato contiene un collegamento che consente di registrarsi alla campagna, come illustrato di seguito:

![](assets/mkg_dist_mutual_op_notification.png)

Questo messaggio consente inoltre alle entità locali di visualizzare la descrizione immessa dall’operatore centrale che ha creato il pacchetto, nonché i documenti collegati alla campagna. Questi non appartengono alla campagna stessa, anche se forniscono informazioni aggiuntive su di essa.

Dopo aver effettuato l’accesso tramite un’interfaccia web, gli operatori locali possono immettere informazioni personalizzate per la campagna collaborativa che desiderano ordinare:

![](assets/mkg_dist_mutual_op_command.png)

Dopo che un ente locale ha completato la registrazione, gli enti centrali ricevono una notifica via e-mail per approvare l’ordine.

![](assets/mkg_dist_mutual_op_valid_command.png)

Per ulteriori informazioni, consulta [Processo di approvazione](creating-a-local-campaign.md#approval-process) sezione.

## Approvare un ordine {#approving-an-order}

Il processo di approvazione di un ordine di pacchetti di campagne collaborative è lo stesso utilizzato per una campagna locale. Fai riferimento a [questa sezione](creating-a-local-campaign.md#approving-an-order).
