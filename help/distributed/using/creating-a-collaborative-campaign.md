---
product: campaign
title: Creare una campagna collaborativa
description: Scopri come creare una campagna collaborativa
feature: Distributed Marketing
exl-id: 17313fe5-ad42-45ca-a35a-1e7aa89380ef
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '915'
ht-degree: 3%

---

# Creare una campagna collaborativa{#creating-a-collaborative-campaign-intro}

![](../../assets/v7-only.svg)

L&#39;entità centrale crea campagne di collaborazione da **Marketing distribuito** modelli di campagna. Consulta [questa pagina](about-distributed-marketing.md#collaborative-campaign).

## Creare una campagna collaborativa {#creating-a-collaborative-campaign}

Per configurare una campagna collaborativa, fai clic sul pulsante **[!UICONTROL Campaign management > Campaigns]** nodo, quindi **[!UICONTROL New]** icona.

>[!NOTE]
>
>A parte **[!UICONTROL collaborative campaigns (by campaign)]**, queste campagne possono essere configurate ed eseguite tramite un’interfaccia web.

Il processo di configurazione per un database di campagne collaborative è simile a quello di un modello di campagna locale. Di seguito sono illustrate le specifiche dei diversi tipi di campagne collaborative.

### Per modulo {#by-form}

Per creare una campagna collaborativa (per modulo), la **[!UICONTROL Collaborative campaign (by form)]** il modello deve essere selezionato.

![](assets/mkg_dist_mutual_op_form2.png)

In **[!UICONTROL Edit]** fai clic sulla scheda **[!UICONTROL Advanced campaign settings...]** per accedere al **Marketing distribuito** scheda .

Seleziona la **Per modulo** interfaccia web. Questo tipo di interfaccia consente di creare campi di personalizzazione che verranno utilizzati dalle entità locali per ordinare una campagna. Fai riferimento a [Creazione di una campagna locale (tramite modulo)](examples.md#creating-a-local-campaign--by-form-).

Salva la campagna. È ora possibile utilizzarlo dal **Pacchetti campagna** visualizza in **Campaign** facendo clic sulla scheda **[!UICONTROL Create]** pulsante .

La **[!UICONTROL Campaign Package]** view consente di utilizzare modelli di campagna locali (preconfigurati o duplicati), nonché campagne di riferimento per campagne collaborative, allo scopo di creare campagne per le diverse entità organizzative.

![](assets/mkg_dist_mutual_op_form1b.png)

### Per campagna {#by-campaign}

Per creare una campagna collaborativa (per campagna), il **[!UICONTROL Collaborative campaign (by campaign) (opCollaborativeByCampaign)]** il modello deve essere selezionato.

![](assets/mkg_dist_mutual_op_by_op2.png)

Quando ordinate la campagna, l’entità locale può completare i criteri predefiniti dall’entità centrale e valutare la campagna prima di ordinarla.

Una volta effettuato l&#39;ordine di un **Campagna collaborativa (per campagna)** viene approvata dall’entità centrale, viene creata una campagna figlio per l’entità locale. Una volta disponibili, l’entità locale può quindi modificare:

* il flusso di lavoro della campagna,
* regole di tipologia,
* e campi di personalizzazione.

L’entità locale esegue la campagna figlio. L’entità centrale esegue la campagna padre.

L’entità centrale può visualizzare tutte le campagne figlio collegate a un **Campagna collaborativa (per campagna)** da questo dashboard (tramite **[!UICONTROL List of associated campaigns]** link).

![](assets/mkg_dist_mutual_op_by_op.png)

### Per approvazione target {#by-target-approval}

Per creare una campagna collaborativa (per approvazione target), il **[!UICONTROL Collaborative campaign (by target approval)]** il modello deve essere selezionato.

![](assets/mkg_dist_mutual_op_by_valid.png)

>[!NOTE]
>
>In questa modalità, l’entità centrale non deve specificare le entità locali.

Il flusso di lavoro della campagna deve essere integrato **Approvazione locale** digitare activity. I parametri dell’attività sono i seguenti:

* **[!UICONTROL Action to perform]** : Notifica di approvazione di Target.
* **[!UICONTROL Distribution context]** : Esplicito.
* **[!UICONTROL Data distribution]** : Distribuzione di entità locale.

**Distribuzione di entità locali** è necessario creare la distribuzione dei dati di tipo . Il modello di distribuzione dei dati ti consente di limitare il numero di record da un elenco di valori di raggruppamento. In **[!UICONTROL Resources > Campaign management > Data distribution]**, fai clic su **[!UICONTROL New]** per creare un nuovo **[!UICONTROL Data distribution]**. Per ulteriori informazioni sulla distribuzione dei dati, consulta la [Flussi di lavoro](../../workflow/using/using-the-local-approval-activity.md#step-1--creating-the-data-distribution-template-) guida.

![](assets/mkg_dist_data_distribution.png)

Seleziona la **Dimensione di targeting** e **[!UICONTROL Distribution field]**. Per **[!UICONTROL Assignment type]**, seleziona **Entità locale**.

In **[!UICONTROL Distribution]** , aggiungi un campo per ogni entità locale e specifica il valore .

![](assets/mkg_dist_data_distribution2.png)

Puoi aggiungere un secondo **Approvazione di Target** dopo il **Consegna** digita attività per configurare un rapporto su di essa.

Nel messaggio di notifica della creazione della campagna, l’entità locale riceve un elenco di contatti predefinito dai parametri dell’entità centrale.

![](assets/mkg_dist_mutual_op_by_valid1.png)

L’entità locale può eliminare alcuni contatti in base al contenuto della campagna.

![](assets/mkg_dist_mutual_op_by_valid2.png)

### Semplice {#simple}

Per creare una semplice campagna collaborativa, il **[!UICONTROL Collaborative campaign (simple)]** il modello deve essere selezionato.

## Creazione di un pacchetto di campagna collaborativo {#creating-a-collaborative-campaign-package}

Per rendere una campagna disponibile alle entità locali, l’entità centrale deve creare un pacchetto della campagna.

Applica i seguenti passaggi:

1. In **[!UICONTROL Navigation]** sezione **Campagne** fai clic su **[!UICONTROL Campaign packages]** link.
1. Fai clic sul pulsante **[!UICONTROL Create]**.
1. La sezione nella parte superiore della finestra ti consente di selezionare il **[!UICONTROL New collaborative package (mutualizedEmpty)]** modello.
1. Seleziona la campagna di riferimento.
1. Specifica l’etichetta, la cartella e la pianificazione di esecuzione per il pacchetto della campagna.

### Date {#dates}

Le date di inizio e di fine definiscono il periodo di visibilità della campagna nell’elenco dei pacchetti della campagna.

Per **campagne collaborative**, l’entità centrale deve specificare il termine di registrazione e personalizzazione.

>[!NOTE]
>
>La **[!UICONTROL Personalization deadline]** consente all’entità centrale di scegliere una scadenza entro la quale le entità locali devono aver consegnato i documenti (fogli di calcolo, immagini) da utilizzare per configurare la campagna. Questa non è un&#39;opzione obbligatoria. L’utilizzo graduale di questa data non influirà sull’implementazione della campagna.

![](assets/s_advuser_mkg_dist_create_mutual_entry.png)

### Pubblico {#audience}

L’entità centrale deve specificare le entità locali coinvolte per campagna non appena viene creata la campagna collaborativa.

![](assets/s_advuser_mkg_dist_create_mutual_entry2.png)

>[!CAUTION]
>
>**[!UICONTROL Simple, by form and by campaign collaborative campaign kits]** non possono essere approvati a meno che non siano stati specificati gli enti locali pertinenti.

### Modalità di approvazione {#approval-modes}

Per **campagne collaborative**, puoi specificare la modalità di approvazione dell’ordine.

![](assets/mkg_dist_edit_kit1.png)

In modalità manuale, l’entità locale deve sottoscrivere la campagna per partecipare.

In modalità automatica, l’entità locale viene pre-sottoscritta per la campagna. Può annullare la sottoscrizione della campagna o modificare i suoi parametri senza richiedere l’approvazione da parte dell’entità centrale.

![](assets/mkg_dist_edit_kit2.png)

### Notifiche {#notifications}

La configurazione per le notifiche è identica alle notifiche per un&#39;entità locale. Fai riferimento a [questa sezione](creating-a-local-campaign.md#notifications).

## Ordinare una campagna {#ordering-a-campaign}

Quando una campagna collaborativa viene aggiunta all’elenco dei pacchetti di campagne, le entità locali appartenenti al pubblico definito dall’entità centrale ricevono una notifica (il **campagne collaborative (per approvazione target)** non hanno un pubblico predefinito). Il messaggio inviato contiene un collegamento che consente di registrarsi per la campagna, come illustrato di seguito:

![](assets/mkg_dist_mutual_op_notification.png)

Questo messaggio consente anche alle entità locali di visualizzare la descrizione immessa dall’operatore centrale che ha creato il pacchetto, nonché i documenti collegati alla campagna. Questi non appartengono alla campagna stessa, anche se forniscono informazioni aggiuntive al riguardo.

Dopo aver effettuato l’accesso tramite un’interfaccia web, gli operatori locali possono inserire informazioni personalizzate nella campagna collaborativa che desiderano ordinare:

![](assets/mkg_dist_mutual_op_command.png)

Dopo che un ente locale ha completato la sua registrazione, gli enti centrali ricevono una notifica via e-mail per approvare il loro ordine.

![](assets/mkg_dist_mutual_op_valid_command.png)

Per ulteriori informazioni, consulta la sezione [Processo di approvazione](creating-a-local-campaign.md#approval-process) sezione .

## Approva un ordine {#approving-an-order}

Il processo per l’approvazione di un ordine di pacchetti di campagna collaborativa è lo stesso di quando lo si fa per una campagna locale. Fai riferimento a [questa sezione](creating-a-local-campaign.md#approving-an-order).
