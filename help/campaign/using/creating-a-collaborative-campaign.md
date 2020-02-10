---
title: Creazione di una campagna collaborativa
seo-title: Creazione di una campagna collaborativa
description: Creazione di una campagna collaborativa
seo-description: null
page-status-flag: never-activated
uuid: 13d8ff65-1480-422a-85b6-40b553a3c151
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: distributed-marketing
discoiquuid: 01d8be92-7312-4386-b5f5-651af31308f7
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d30de91002862b664249c5a704b7c0f521dd30f2

---


# Creazione di una campagna collaborativa{#creating-a-collaborative-campaign-intro}

L&#39;entità centrale crea campagne di collaborazione dai modelli delle campagne **Distributed Marketing** . Fare riferimento a [questa pagina](../../campaign/using/about-distributed-marketing.md#collaborative-campaign).

## Creazione di una campagna collaborativa {#creating-a-collaborative-campaign}

Per configurare una campagna collaborativa, fai clic sul **[!UICONTROL Campaign management > Campaigns]** nodo, quindi sull’ **[!UICONTROL New]** icona .

>[!NOTE]
>
>Oltre a **[!UICONTROL collaborative campaigns (by campaign)]**, queste campagne possono essere configurate ed eseguite tramite un&#39;interfaccia Web.

Il processo di configurazione per un database di campagna collaborativa è simile a quello di un modello di campagna locale. Le specifiche dei diversi tipi di campagne collaborative sono descritte di seguito.

### Per modulo {#by-form}

Per creare una campagna collaborativa (per modulo), è necessario selezionare il **[!UICONTROL Collaborative campaign (by form)]** modello.

![](assets/mkg_dist_mutual_op_form2.png)

Nella **[!UICONTROL Edit]** scheda, fate clic sul **[!UICONTROL Advanced campaign settings...]** collegamento per accedere alla scheda **Distributed Marketing** .

Selezionare l&#39;interfaccia Web **Per modulo** . Questo tipo di interfaccia consente di creare campi di personalizzazione che verranno utilizzati dalle entità locali per ordinare una campagna. Fare riferimento a [Creazione di una campagna locale (per modulo)](../../campaign/using/examples.md#creating-a-local-campaign--by-form-).

Salvate la campagna. Ora puoi utilizzarlo dalla visualizzazione dei pacchetti **** Campaign nell&#39;universo **Campaign** facendo clic sul **[!UICONTROL Create]** pulsante.

La **[!UICONTROL Campaign Package]** vista consente di utilizzare modelli di campagna locali (out-of-the-box o duplicati), nonché campagne di riferimento per campagne collaborative, allo scopo di creare campagne per le diverse entità organizzative.

![](assets/mkg_dist_mutual_op_form1b.png)

### Per campagna {#by-campaign}

Per creare una campagna collaborativa (per campagna), è necessario selezionare il **[!UICONTROL Collaborative campaign (by campaign) (opCollaborativeByCampaign)]** modello.

![](assets/mkg_dist_mutual_op_by_op2.png)

Quando ordinate la campagna, l&#39;entità locale può completare i criteri predefiniti dall&#39;entità centrale e valutare la campagna prima di ordinarla.

Quando un ordine per una campagna **collaborativa (per campagna)** viene approvato dall&#39;entità centrale, viene creata una campagna figlio per l&#39;entità locale. Una volta disponibili, l&#39;entità locale può quindi modificare:

* il flusso di lavoro della campagna,
* regole di tipologia,
* e campi di personalizzazione.

L&#39;entità locale esegue la campagna figlio. L&#39;entità centrale esegue la campagna padre.

L&#39;entità centrale può visualizzare tutte le campagne figlio collegate con una campagna **Collaborative (per campagna)** da questa dashboard (tramite il **[!UICONTROL List of associated campaigns]** collegamento).

![](assets/mkg_dist_mutual_op_by_op.png)

### Per approvazione {#by-target-approval}

Per creare una campagna collaborativa (per approvazione target), è necessario selezionare il **[!UICONTROL Collaborative campaign (by target approval)]** modello.

![](assets/mkg_dist_mutual_op_by_valid.png)

>[!NOTE]
>
>In questa modalità, l&#39;entità centrale non deve specificare le entità locali.

Il flusso di lavoro della campagna deve integrare l&#39;attività relativa al tipo di approvazione **** locale. I parametri dell&#39;attività sono i seguenti:

* **[!UICONTROL Action to perform]** : Notifica di approvazione di destinazione.
* **[!UICONTROL Distribution context]** : Esplicito.
* **[!UICONTROL Data distribution]** : Distribuzione di entità locale.

**È necessario creare la distribuzione dei dati del tipo di distribuzione** dell&#39;entità locale. Il modello di distribuzione dei dati consente di limitare il numero di record da un elenco di valori di raggruppamento. In **[!UICONTROL Resources > Campaign management > Data distribution]**, fate clic sull&#39; **[!UICONTROL New]** icona per creare una nuova **[!UICONTROL Data distribution]**. Per ulteriori informazioni sulla distribuzione dei dati, consultare la guida [Flussi](../../workflow/using/using-the-local-approval-activity.md#step-1--creating-the-data-distribution-template-) di lavoro.

![](assets/mkg_dist_data_distribution.png)

Selezionate la dimensione **** Targeting (Targeting) e la **[!UICONTROL Distribution field]** dimensione. Per **[!UICONTROL Assignment type]**, selezionate **Entità** locale.

Nella **[!UICONTROL Distribution]** scheda, aggiungere un campo per ogni entità locale e specificare il valore.

![](assets/mkg_dist_data_distribution2.png)

Puoi aggiungere una seconda approvazione **** Target dopo l&#39;attività del tipo **Consegna** per configurare un report su di essa.

Nel messaggio di notifica per la creazione della campagna, l&#39;entità locale riceve un elenco di contatti predefinito dai parametri dell&#39;entità centrale.

![](assets/mkg_dist_mutual_op_by_valid1.png)

L&#39;entità locale può eliminare alcuni contatti in base al contenuto della campagna.

![](assets/mkg_dist_mutual_op_by_valid2.png)

### Semplice {#simple}

Per creare una semplice campagna collaborativa, è necessario selezionare il **[!UICONTROL Collaborative campaign (simple)]** modello.

## Creazione di un pacchetto campagna collaborativo {#creating-a-collaborative-campaign-package}

Per rendere disponibile una campagna alle entità locali, l&#39;entità centrale deve creare un pacchetto di campagna.

Effettuate le seguenti operazioni:

1. Nella **[!UICONTROL Navigation]** sezione della pagina **Campagne** fare clic sul **[!UICONTROL Campaign packages]** collegamento.
1. Fate clic sul **[!UICONTROL Create]** pulsante.
1. La sezione nella parte superiore della finestra consente di selezionare il **[!UICONTROL New collaborative package (mutualizedEmpty)]** modello.
1. Selezionate la campagna di riferimento.
1. Specificate l&#39;etichetta, la cartella e la pianificazione di esecuzione per il pacchetto della campagna.

### Date {#dates}

Le date di inizio e fine definiscono il periodo di visibilità della campagna nell&#39;elenco dei pacchetti della campagna.

Per le campagne **** collaborative, l&#39;entità centrale deve specificare la scadenza di registrazione e personalizzazione.

>[!NOTE]
>
>L&#39;entità centrale **[!UICONTROL Personalization deadline]** può scegliere una scadenza entro la quale le entità locali devono aver consegnato i documenti (fogli di calcolo, immagini) da utilizzare per configurare la campagna. Questa non è un&#39;opzione obbligatoria. L’utilizzo di questa data non influisce sull’implementazione della campagna.

![](assets/s_advuser_mkg_dist_create_mutual_entry.png)

### Audience {#audience}

L&#39;entità centrale deve specificare le entità locali coinvolte per campagna non appena viene creata la campagna collaborativa.

![](assets/s_advuser_mkg_dist_create_mutual_entry2.png)

>[!CAUTION]
>
>**[!UICONTROL Simple, by form and by campaign collaborative campaign kits]** non può essere approvato a meno che non siano stati specificati gli enti locali pertinenti.

### Modalità di approvazione {#approval-modes}

Per le campagne **** collaborative, potete specificare la modalità di approvazione dell&#39;ordine.

![](assets/mkg_dist_edit_kit1.png)

In modalità manuale, l&#39;entità locale deve sottoscrivere la campagna per poter partecipare.

In modalità automatica, l&#39;entità locale viene pre-registrata per la campagna. Può annullare la sottoscrizione alla campagna o modificare i suoi parametri senza richiedere l&#39;approvazione dell&#39;entità centrale.

![](assets/mkg_dist_edit_kit2.png)

### Notifications {#notifications}

La configurazione per le notifiche è identica alle notifiche per un&#39;entità locale. Fare riferimento a [questa sezione](../../campaign/using/creating-a-local-campaign.md#notifications).

## Ordinamento di una campagna {#ordering-a-campaign}

Quando una campagna collaborativa viene aggiunta all&#39;elenco dei pacchetti campagna, le entità locali appartenenti all&#39;audience definita dall&#39;entità centrale ricevono una notifica (le campagne **collaborative (per approvazione target)** non hanno un&#39;audience predefinita). Il messaggio inviato contiene un collegamento che consente di registrarsi per la campagna, come mostrato di seguito:

![](assets/mkg_dist_mutual_op_notification.png)

Questo messaggio consente inoltre alle entità locali di visualizzare la descrizione immessa dall&#39;operatore centrale che ha creato il pacchetto, nonché i documenti collegati alla campagna. Questi non appartengono alla campagna stessa, anche se forniscono informazioni aggiuntive al riguardo.

Dopo aver eseguito l&#39;accesso tramite un&#39;interfaccia Web, gli operatori locali possono inserire informazioni personalizzate nella campagna collaborativa che desiderano ordinare:

![](assets/mkg_dist_mutual_op_command.png)

Dopo che un&#39;entità locale ha completato la registrazione, gli enti centrali ricevono una notifica via e-mail per approvare l&#39;ordine.

![](assets/mkg_dist_mutual_op_valid_command.png)

Per ulteriori informazioni, consulta la sezione [Approvazione](../../campaign/using/creating-a-local-campaign.md#approval-process) .

## Approvazione di un ordine {#approving-an-order}

La procedura per l&#39;approvazione di un ordine di pacchetti per campagne collaborative è la stessa utilizzata per una campagna locale. Fare riferimento a [questa sezione](../../campaign/using/creating-a-local-campaign.md#approving-an-order).
