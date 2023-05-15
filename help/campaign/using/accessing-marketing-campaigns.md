---
product: campaign
title: Accedere alle campagne di marketing
description: Accedere alle campagne di marketing
badge: label="v7" type="Informative" tooltip="Si applica a Campaign Classic v7"
feature: Campaigns, Cross Channel Orchestration
exl-id: 1278bda1-f83c-4d38-8042-e6611755cf36
source-git-commit: 517a343011ff313d016638c586867673e406fd88
workflow-type: tm+mt
source-wordcount: '1257'
ht-degree: 3%

---

# Accesso alle campagne di marketing{#accessing-marketing-campaigns}

Adobe Campaign consente di creare, configurare, eseguire e analizzare campagne di marketing. Tutte le campagne di marketing possono essere gestite da un centro di controllo unificato.

## Nozioni di base su Workspace {#workspace-basics}

### Pagina Home {#home-page}

Una volta effettuata la connessione ad Adobe Campaign, verrà visualizzata la home page.

![](assets/campaign_global_view.png)

Fai clic sui collegamenti nella barra di navigazione per accedere alle varie funzionalità.

Gli elementi della campagna si trovano in **[!UICONTROL Campaigns]** scheda: qui puoi vedere una panoramica dei programmi e delle campagne di marketing e dei relativi sottoinsiemi. Un programma di marketing è costituito da campagne, costituite da consegne, attività, risorse collegate, ecc. Nel contesto della gestione delle campagne di marketing tramite Campaign, le informazioni relative a consegne, budget, revisori e documenti collegati si trovano nelle campagne.

La **[!UICONTROL Browsing]** blocco del **[!UICONTROL Campaigns]** tab offre varie voci, a seconda dei moduli installati nell’istanza. Ad esempio, puoi accedere a:

* **Calendario delle campagne**: calendario di piani, programmi di marketing, consegne e campagne. Fai riferimento a [Calendario delle campagne](#campaign-calendar).
* **Campagne**: accesso alle campagne contenute in tutti i programmi di marketing.
* **Consegne**: accesso alle consegne collegate alle campagne.
* **Applicazioni Web**: accesso ad applicazioni web (moduli, pagine di destinazione, ecc.).

>[!NOTE]
>
>Per ulteriori informazioni sull’ergonomia generale di Adobe Campaign, sulle autorizzazioni e sulle funzionalità di gestione dei profili, consulta [questa sezione](../../platform/using/adobe-campaign-workspace.md).
>
>Tutte le funzionalità relative ai canali e alle consegne sono descritte in [questa sezione](../../delivery/using/steps-about-delivery-creation-steps.md).

### Calendario delle campagne {#campaign-calendar}

Ogni campagna appartiene a un programma che a sua volta appartiene a un piano. I piani, i programmi e le campagne sono accessibili tramite **[!UICONTROL Campaign calendar]** nel menu **Campagne** scheda .

Per modificare un piano, un programma, una campagna o una consegna, fare clic sul relativo nome nel calendario, quindi fare clic su **[!UICONTROL Open...]**. Viene quindi visualizzato in una nuova scheda, come illustrato di seguito:

![](assets/d_ncs_user_interface_hierar.png)

Puoi filtrare le informazioni visualizzate nel calendario della campagna. A questo scopo, fai clic sul pulsante **[!UICONTROL Filter]** collega e seleziona i criteri di filtro.

![](assets/campaign_planning_filter.png)

>[!NOTE]
>
>Quando si filtra una data, vengono visualizzate tutte le campagne con una data di inizio successiva alla data specificata e/o con una data di fine precedente alla data specificata. Le date devono essere selezionate utilizzando i calendari a destra di ciascun campo.

È inoltre possibile utilizzare **[!UICONTROL Search]** per filtrare gli elementi visualizzati.

Le icone collegate a ciascun elemento consentono di visualizzarne lo stato: finito, in corso, in corso, in corso di modifica, ecc.

### Esplorazione di un programma di marketing {#browsing-in-a-marketing-program}

Campaign ti consente di gestire un set di programmi composti da varie campagne di marketing. Ogni campagna contiene consegne, processi e risorse associati.

#### Navigazione in un programma {#browsing-a-program}

Quando modifichi un programma, utilizza le schede descritte di seguito per sfogliare e configurarlo.

* La **Pianificazione** Visualizza il calendario dei programmi per un mese, una settimana o un giorno a seconda della scheda su cui fai clic nell’intestazione del calendario.

   Se necessario, puoi creare una campagna, un programma o un’attività tramite questa pagina.

   ![](assets/s_ncs_user_interface_campaign02.png)

* La **Modifica** consente di personalizzare il programma: nome, date di inizio e fine, budget, documenti collegati, ecc.

   ![](assets/s_ncs_user_interface_campaign05.png)

#### Campagne di navigazione {#browsing-campaigns}

È possibile accedere alle campagne tramite il calendario della campagna, **[!UICONTROL Schedule]** scheda del programma o elenco delle campagne.

1. Tramite il calendario della campagna, seleziona la campagna da visualizzare, quindi fai clic sul **[!UICONTROL Open]** link.

   ![](assets/campaign_planning_edit_op.png)

   La campagna viene modificata in una nuova scheda, come illustrato di seguito:

   ![](assets/campaign_op_edit.png)

1. Tramite il **[!UICONTROL Schedule]** la modalità di modifica è la stessa del calendario della campagna.
1. Tramite il **[!UICONTROL Campaigns]** collegamento **[!UICONTROL Campaigns]** , fai clic sul nome della campagna da modificare.

   ![](assets/campaign_edit_from_list.png)

### Controllo di una campagna {#controlling-a-campaign}

#### Dashboard {#dashboard}

Per ogni campagna, processi, risorse e consegne sono centralizzati in un’unica schermata, ovvero il dashboard, che consente di gestire le azioni di marketing in collaborazione con altri.

Il dashboard di una campagna viene utilizzato come interfaccia di controllo. Accede direttamente alle principali fasi di creazione e gestione della campagna: consegne, file di estrazione, notifiche, budget, ecc.

![](assets/s_ncs_user_op_board_start_del.png)

Con Adobe Campaign puoi impostare processi collaborativi per la creazione e l’approvazione delle varie fasi delle campagne di marketing e comunicazione: approvazione del bilancio, dell&#39;obiettivo, del contenuto, ecc.

![](assets/s_ncs_user_op_board_validate.png)

>[!NOTE]
>
>La configurazione dei modelli di campagna è presentata in [Modelli di campagna](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

#### Pianificazione {#schedule}

Una campagna centralizza un insieme di consegne. Per ogni campagna, la pianificazione offre una visualizzazione globale di tutti i componenti: questo ti consente di visualizzare le attività e le consegne e di accedervi facilmente.

![](assets/campaign_planning_tab.png)

#### Forum {#forum}

Per ogni campagna, gli operatori possono scambiare messaggi tramite un forum dedicato.

Per ulteriori informazioni, consulta [Forum di discussione](../../mrm/using/discussion-forums.md).

#### Rapporti {#reports}

La **[!UICONTROL Reports]** link ti consente di accedere ai report della campagna.

![](assets/campaign_reporting_tab.png)

>[!NOTE]
>
>I rapporti sono descritti in [questa sezione](../../reporting/using/about-adobe-campaign-reporting-tools.md).

#### Configurazione {#configuration}

Le campagne vengono create tramite modelli di campagna. Puoi configurare modelli riutilizzabili per i quali sono selezionate alcune opzioni e altre impostazioni già salvate. Per ogni campagna, è disponibile la seguente funzionalità:

* Riferimento a documenti e risorse: puoi associare i documenti alla campagna (breve, rapporto, immagini, ecc.). Sono supportati tutti i formati di documento. Vedi [Gestione dei documenti associati](../../campaign/using/marketing-campaign-deliveries.md#managing-associated-documents).
* Definizione dei costi: per ogni campagna, Adobe Campaign ti consente di definire voci di costo e strutture di calcolo dei costi che possono essere utilizzate durante la creazione della campagna di marketing. Ad esempio: costi di stampa, utilizzo di un&#39;agenzia esterna, noleggio di camere, ecc. Vedi [Definizione delle categorie di costi](../../campaign/using/providers--stocks-and-budgets.md#defining-cost-categories).
* Definizione degli obiettivi: puoi definire obiettivi quantificabili per una campagna, ad esempio numero di abbonati, volume di affari, ecc. Queste informazioni vengono successivamente utilizzate nei rapporti delle campagne.
* Gestione degli indirizzi di seed (per ulteriori informazioni, consulta [questa sezione](../../delivery/using/about-seed-addresses.md)) e gruppi di controllo (consulta [Definizione di un gruppo di controllo](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group)).
* Gestione delle approvazioni: è possibile selezionare i trattamenti da approvare e, se necessario, selezionare gli operatori di revisione o i gruppi di operatori. Vedi [Controllo e approvazione delle consegne](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries).

>[!NOTE]
>
>Per accedere alle configurazioni della campagna e apportare loro modifiche, fai clic sul pulsante **[!UICONTROL Advanced campaign parameters...]** nel collegamento **[!UICONTROL Edit]** scheda .

## Utilizzo dell’interfaccia web {#using-the-web-interface-}

Puoi accedere alle schermate della console Adobe Campaign tramite un browser Internet per visualizzare tutte le campagne e le consegne, nonché i rapporti e le informazioni sui profili nel database. L&#39;accesso non consente la creazione di record. A seconda dei diritti dell’operatore, è possibile visualizzare e/o intervenire sui dati nel database. Ad esempio, puoi approvare il contenuto e il targeting della campagna, riavviare o interrompere una consegna, ecc.

1. Accedi come di consueto tramite https://`<your instance>:<port>/view/home`.
1. Utilizza i menu per accedere alle panoramiche.

   ![](assets/s_ncs_user_interface_web_campaign_01.png)

Oltre a navigare tra le campagne e visualizzarle, è possibile eseguire i seguenti tipi di attività:

* Monitorare l’attività su un’istanza
* Partecipa ai processi di convalida, ad esempio per approvare o rifiutare un contenuto di consegna
* Eseguire altre azioni rapide, ad esempio sospendere un flusso di lavoro
* Accedere a tutte le funzioni di reporting
* Partecipare alle discussioni del forum

In questa tabella sono riepilogate le azioni che è possibile eseguire sulle campagne da un browser:

| Pagina  | Azione |
| --- | --- |
| Elenco di campagne, consegne, offerte, ecc. | Eliminare una voce dell’elenco |
| Campaign | Annullare una campagna |
| Consegna | Approvare il contenuto e la destinazione della consegna<br/>Inviare il contenuto della consegna<br/>Conferma di una consegna<br/>Sospendi e interrompi una consegna |
| Applicazione web | Creare un’applicazione web<br/>Modifica del contenuto e delle proprietà dell&#39;applicazione<br/>Salva il contenuto dell’applicazione come modello<br/>Pubblicare l’applicazione |
| Offerta | Approvare il contenuto dell’offerta e l’idoneità<br/>Disattiva un’offerta online |
| Attività Task | Completare un&#39;attività<br/>Annullare un’attività |
| Risorse di marketing | Approvare una risorsa<br/>Bloccare e sbloccare una risorsa |
| Pacchetto campagne | Invia un pacchetto per l&#39;approvazione<br/>Approvare o rifiutare un pacchetto<br/>Annullare un pacchetto |
| Ordine delle campagne | Creare un ordine<br/>Accettare o rifiutare un ordine <!-- Je n'ai pas pu créer de campaign order pour vérifier cela. Peut-on accéder à ces fonctionnalités depuis l'accès web ? --> |
| Magazzino | Elimina una linea di magazzino |
| Simulazione dell’offerta | Avviare e arrestare una simulazione |
| Flusso di lavoro di targeting | Avviare, mettere in pausa e interrompere un flusso di lavoro |
| Rapporto | Salva i dati correnti nella cronologia del report |
| Forum | Aggiungi una discussione<br/>Risposta a un messaggio in una discussione<br/>Seguire una discussione e cancellarla |

### Approvazioni

Le approvazioni (di un target o di un contenuto di consegna, ad esempio) possono essere eseguite tramite accesso web.

![](assets/campaign_web_interface_validation.png)

Puoi anche utilizzare il collegamento contenuto nei messaggi di notifica. Per ulteriori informazioni, consulta [Controllo e approvazione delle consegne](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries).
