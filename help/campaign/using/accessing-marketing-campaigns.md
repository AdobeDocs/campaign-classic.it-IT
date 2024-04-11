---
product: campaign
title: Accedere alle campagne di marketing
description: Accedere alle campagne di marketing
role: User
feature: Campaigns, Cross Channel Orchestration
exl-id: 1278bda1-f83c-4d38-8042-e6611755cf36
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1199'
ht-degree: 2%

---

# Accesso alle campagne di marketing{#accessing-marketing-campaigns}

Adobe Campaign consente di creare, configurare, eseguire e analizzare campagne di marketing. Tutte le campagne di marketing possono essere gestite da un centro di controllo unificato.

## Nozioni di base su Workspace {#workspace-basics}

### Home page {#home-page}

Una volta connesso ad Adobe Campaign, sfoglia le varie funzionalità utilizzando i collegamenti nella barra di navigazione.


![](assets/campaign_global_view.png)


Gli elementi della campagna si trovano nel **[!UICONTROL Campaigns]** scheda: qui puoi vedere una panoramica dei programmi di marketing, delle campagne e dei relativi sottoinsiemi. Un programma di marketing è costituito da campagne, che sono costituite da consegne, attività, risorse collegate, ecc. Nel contesto della gestione delle campagne di marketing tramite Campaign, le informazioni relative a consegne, budget, revisori e documenti collegati si trovano nelle campagne.

Il **[!UICONTROL Browsing]** blocco del **[!UICONTROL Campaigns]** La scheda offre diverse voci, a seconda dei moduli installati nell’istanza. Ad esempio, puoi accedere a:

* **Calendario della campagna**: calendario di piani, programmi di marketing, consegne e campagne. Fai riferimento a [Calendario della campagna](#campaign-calendar).
* **Campagne**: accesso alle campagne contenute in tutti i programmi di marketing.
* **Consegne**: accesso alle consegne collegate alle campagne.
* **Applicazioni web**: accesso alle applicazioni web (moduli, pagine di destinazione, ecc.).

>[!NOTE]
>
>Per ulteriori informazioni sull’ergonomia generale di Adobe Campaign, sulle autorizzazioni e sulle funzionalità di gestione dei profili, consulta [questa sezione](../../platform/using/adobe-campaign-workspace.md).
>
>Tutte le funzionalità relative a canali e consegne sono descritte in [questa sezione](../../delivery/using/steps-about-delivery-creation-steps.md).

### Calendario della campagna {#campaign-calendar}

Ogni campagna appartiene a un programma che a sua volta appartiene a un piano. Piani, programmi e campagne sono accessibili tramite **[!UICONTROL Campaign calendar]** menu in **Campagne** scheda.

Per modificare un piano, un programma, una campagna o una consegna, fare clic sul relativo nome nel calendario e quindi su **[!UICONTROL Open...]**. Viene quindi visualizzato in una nuova scheda, come illustrato di seguito:

![](assets/d_ncs_user_interface_hierar.png)

Puoi filtrare le informazioni visualizzate nel calendario della campagna: fai clic sul pulsante **[!UICONTROL Filter]** e selezionare i criteri di filtro.

![](assets/campaign_planning_filter.png)

>[!NOTE]
>
>Quando si applica un filtro in base a una data, vengono visualizzate tutte le campagne con una data di inizio successiva alla data specificata e/o con una data di fine precedente alla data specificata. Selezionare le date utilizzando i calendari a destra di ciascun campo.

È inoltre possibile utilizzare **[!UICONTROL Search]** per filtrare gli elementi visualizzati.

Le icone collegate a ciascun elemento ti consentono di visualizzarne lo stato: completato, in corso, in corso di modifica, ecc.

### Esplorazione in un programma di marketing {#browsing-in-a-marketing-program}

Campaign ti consente di gestire un set di programmi composto da varie campagne di marketing. Ogni campagna contiene consegne e i processi e le risorse associati.

#### Esplorazione di un programma {#browsing-a-program}

Durante la modifica di un programma, utilizza le schede descritte di seguito per sfogliarlo e configurarlo.

* Il **Pianificazione** scheda visualizza il calendario dei programmi per un mese, una settimana o un giorno, a seconda della scheda su cui si fa clic nell&#39;intestazione del calendario.

  Se necessario, puoi creare una campagna, un programma o un’attività tramite questa pagina.

  ![](assets/s_ncs_user_interface_campaign02.png)

* Il **Modifica** Questa scheda ti permette di personalizzare il programma: nome, date di inizio e fine, budget, documenti collegati, ecc.

  ![](assets/s_ncs_user_interface_campaign05.png)

#### Navigazione nelle campagne {#browsing-campaigns}

Le campagne sono accessibili tramite il calendario della campagna, il **[!UICONTROL Schedule]** del programma o dell’elenco delle campagne.

1. Seleziona la campagna da visualizzare tramite il calendario della campagna, quindi fai clic su **[!UICONTROL Open]** collegamento.

   ![](assets/campaign_planning_edit_op.png)

   La campagna viene modificata in una nuova scheda, come illustrato di seguito:

   ![](assets/campaign_op_edit.png)

1. Attraverso il **[!UICONTROL Schedule]** del programma, la modalità di modifica è la stessa del calendario della campagna.
1. Attraverso il **[!UICONTROL Campaigns]** collegamento del **[!UICONTROL Campaigns]** , fai clic sul nome della campagna da modificare.

   ![](assets/campaign_edit_from_list.png)

### Controllo di una campagna {#controlling-a-campaign}

#### Dashboard {#dashboard}

Per ogni campagna, processi, risorse e consegne sono centralizzati in un’unica schermata, la dashboard, che consente di gestire le azioni di marketing in collaborazione con gli altri.

Il dashboard di una campagna viene utilizzato come interfaccia di controllo. Accede direttamente alle fasi principali di creazione e gestione della campagna: consegne, file di estrazione, notifiche, budget, ecc.

![](assets/s_ncs_user_op_board_start_del.png)

Con Adobe Campaign puoi impostare processi collaborativi per la creazione e l’approvazione delle varie fasi delle campagne di marketing e comunicazione: approvazione del budget, target, contenuto, ecc.

![](assets/s_ncs_user_op_board_validate.png)

>[!NOTE]
>
>La configurazione dei modelli di campagna è presentata in [Modelli di campagna](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

#### Pianificazione {#schedule}

Una campagna centralizza una serie di consegne. Per ogni campagna, la pianificazione offre una visualizzazione globale di tutti i componenti: puoi visualizzare le attività e le consegne e accedervi facilmente.

![](assets/campaign_planning_tab.png)

#### Forum {#forum}

Per ogni campagna, gli operatori possono scambiarsi messaggi tramite un forum dedicato.

Ulteriori informazioni in [Forum di discussione](../../mrm/using/discussion-forums.md).

#### Rapporti {#reports}

Il **[!UICONTROL Reports]** consente di accedere ai rapporti della campagna.

![](assets/campaign_reporting_tab.png)

>[!NOTE]
>
>I rapporti sono descritti in [questa sezione](../../reporting/using/about-adobe-campaign-reporting-tools.md).

#### Configurazione {#configuration}

Le campagne vengono create tramite modelli di campagna. Puoi configurare modelli riutilizzabili per i quali sono selezionate alcune opzioni e altre impostazioni sono già salvate. Per ogni campagna sono offerte le seguenti funzionalità:

* Riferimento a [documenti e risorse](../../campaign/using/marketing-campaign-deliveries.md#managing-associated-documents): puoi associare documenti alla campagna (breve, rapporto, immagini, ecc.). Sono supportati tutti i formati di documento.
* Definizione dei costi: per ogni campagna, Adobe Campaign consente di definire [voci di costo e strutture di calcolo dei costi](../../campaign/using/providers-stocks-and-budgets.md#defining-cost-categories) che possono essere utilizzati durante la creazione della campagna di marketing. Ad esempio: spese di stampa, ricorso ad agenzie esterne, affitto di stanze.
* Definizione degli obiettivi: puoi definire obiettivi quantificabili per una campagna, ad esempio numero di abbonati, volume di business, ecc. Queste informazioni vengono successivamente utilizzate nei rapporti delle campagne.
* Gestione [indirizzi seed](../../delivery/using/about-seed-addresses.md) e [gruppi di controllo](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).
* Gestione delle approvazioni: è possibile selezionare i trattamenti da approvare e, se necessario, selezionare gli operatori di revisione o i gruppi di operatori. [Ulteriori informazioni](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries)

>[!NOTE]
>
>Per accedere alle configurazioni della campagna e modificarle, fai clic sul pulsante **[!UICONTROL Advanced campaign parameters...]** collegamento in **[!UICONTROL Edit]** scheda.

## Utilizzo dell’interfaccia web {#using-the-web-interface-}

Puoi accedere alle schermate della console Adobe Campaign tramite un browser Internet per visualizzare tutte le campagne e le consegne, nonché i rapporti e le informazioni sui profili nel database. Questo accesso non consente la creazione di record. A seconda dei diritti degli operatori, è possibile visualizzare e/o agire sui dati nel database. Ad esempio, puoi approvare il contenuto della campagna e il targeting, riavviare o interrompere una consegna, ecc.

1. Accedi come al solito tramite https://`<your instance>:<port>/view/home`.
1. Utilizza i menu per accedere alle panoramiche.

   ![](assets/s_ncs_user_interface_web_campaign_01.png)

Oltre a navigare tra le campagne e visualizzarle, puoi eseguire i seguenti tipi di attività:

* Monitorare l’attività su un’istanza
* Partecipa ai processi di convalida, ad esempio approva o rifiuta un contenuto di consegna
* Eseguire altre azioni rapide, ad esempio sospendere un flusso di lavoro
* Accedere a tutte le funzioni di reporting
* Partecipa alle discussioni del forum

Questa tabella fornisce un riepilogo delle azioni che è possibile eseguire sulle campagne da un browser:

| Pagina  | Azione |
| --- | --- |
| Elenco di campagne, consegne, offerte, ecc. | Eliminare una voce di elenco |
| Campaign | Annullare una campagna |
| Consegna | Approvare il contenuto e la destinazione della consegna<br/>Inviare il contenuto della consegna<br/>Conferma una consegna<br/>Sospendere e interrompere una consegna |
| Applicazione web | Creare un’applicazione web<br/>Modificare il contenuto e le proprietà dell’applicazione<br/>Salvare il contenuto dell’applicazione come modello<br/>Pubblicare l’applicazione |
| Offerta | Approvare il contenuto e l’idoneità dell’offerta<br/>Disattivare un’offerta online |
| Attività Task | Terminare un’attività<br/>Annullare un’attività |
| Risorse di marketing | Approvare una risorsa<br/>Bloccare e sbloccare una risorsa |
| Pacchetto campagna | Inviare un pacchetto per l&#39;approvazione<br/>Approvare o rifiutare un pacchetto<br/>Annullare un pacchetto |
| Ordine delle campagne | Crea un ordine<br/>Accettare o rifiutare un ordine <!-- Je n'ai pas pu créer de campaign order pour vérifier cela. Peut-on accéder à ces fonctionnalités depuis l'accès web ? --> |
| Magazzino | Eliminare una linea di magazzino |
| Simulazione di offerta | Avviare e interrompere una simulazione |
| Flusso di lavoro di destinazione | Avviare, mettere in pausa e interrompere un flusso di lavoro |
| Report | Salva i dati correnti nella cronologia del rapporto |
| Forum | Aggiungere una discussione<br/>Rispondere a un messaggio in una discussione<br/>Segui una discussione e annulla l’iscrizione |

### Approvazioni

Le approvazioni (ad esempio di un target o di un contenuto di consegna) possono essere eseguite tramite accesso web.

![](assets/campaign_web_interface_validation.png)

Puoi anche utilizzare il collegamento contenuto nei messaggi di notifica. Per ulteriori informazioni, consulta [Verifica e approvazione delle consegne](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries).
