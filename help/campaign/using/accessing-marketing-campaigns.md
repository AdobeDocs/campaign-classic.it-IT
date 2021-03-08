---
solution: Campaign Classic
product: campaign
title: Accesso alle campagne di marketing
description: Accesso alle campagne di marketing
audience: campaign
content-type: reference
topic-tags: about-marketing-campaigns
translation-type: tm+mt
source-git-commit: 278dec636373b5ccd3b631bd29607ebe894d53c3
workflow-type: tm+mt
source-wordcount: '1045'
ht-degree: 1%

---


# Accesso alle campagne di marketing{#accessing-marketing-campaigns}

Adobe Campaign consente di creare, configurare, eseguire e analizzare campagne di marketing. Tutte le campagne di marketing possono essere gestite da un centro di controllo unificato.

## Nozioni di base su Workspace {#workspace-basics}

### Pagina Home {#home-page}

Una volta effettuata la connessione ad Adobe Campaign, verrà visualizzata la home page.

![](assets/campaign_global_view.png)

Fai clic sui collegamenti nella barra di navigazione per accedere alle varie funzionalità.

Gli elementi della campagna si trovano nella scheda **[!UICONTROL Campaigns]** : qui puoi vedere una panoramica dei programmi e delle campagne di marketing e dei relativi sottoinsiemi. Un programma di marketing è costituito da campagne, costituite da consegne, attività, risorse collegate, ecc. Nel contesto della gestione delle campagne di marketing tramite Campaign, le informazioni relative a consegne, budget, revisori e documenti collegati si trovano nelle campagne.

Il blocco **[!UICONTROL Browsing]** della scheda **[!UICONTROL Campaigns]** offre varie voci, a seconda dei moduli installati nell’istanza. Ad esempio, puoi accedere a:

* **Calendario** campagna: calendario di piani, programmi di marketing, consegne e campagne. Fai riferimento a [Calendario delle campagne](#campaign-calendar).
* **Campagne**: accesso alle campagne contenute in tutti i programmi di marketing.
* **Consegne**: accesso alle consegne collegate alle campagne.
* **Applicazioni** Web: accesso alle applicazioni web (moduli, sondaggi, ecc.).

>[!NOTE]
>
>Per ulteriori informazioni sull&#39;ergonomia, le autorizzazioni e le funzionalità di gestione dei profili di Adobe Campaign, consulta [questa sezione](../../platform/using/adobe-campaign-workspace.md).
>
>Tutte le funzionalità relative ai canali e alle consegne sono descritte in [questa sezione](../../delivery/using/steps-about-delivery-creation-steps.md).

### Calendario delle campagne {#campaign-calendar}

Ogni campagna appartiene a un programma che a sua volta appartiene a un piano. I piani, i programmi e le campagne sono accessibili tramite il menu **[!UICONTROL Campaign calendar]** nella scheda **Campagne** .

Per modificare un piano, un programma, una campagna o una consegna, fai clic sul nome corrispondente nel calendario, quindi fai clic su **[!UICONTROL Open...]**. Viene quindi visualizzato in una nuova scheda, come illustrato di seguito:

![](assets/d_ncs_user_interface_hierar.png)

Puoi filtrare le informazioni visualizzate nel calendario della campagna. A questo scopo, fai clic sul collegamento **[!UICONTROL Filter]** e seleziona i criteri di filtro.

![](assets/campaign_planning_filter.png)

>[!NOTE]
>
>Quando si filtra una data, vengono visualizzate tutte le campagne con una data di inizio successiva alla data specificata e/o con una data di fine precedente alla data specificata. Le date devono essere selezionate utilizzando i calendari a destra di ciascun campo.

Puoi inoltre utilizzare il campo **[!UICONTROL Search]** per filtrare gli elementi visualizzati.

Le icone collegate a ciascun elemento consentono di visualizzarne lo stato: finito, in corso, in corso, in corso di modifica, ecc.

### Navigazione in un programma di marketing {#browsing-in-a-marketing-program}

Campaign ti consente di gestire un set di programmi composti da varie campagne di marketing. Ogni campagna contiene consegne, processi e risorse associati.

#### Navigazione in un programma {#browsing-a-program}

Quando modifichi un programma, utilizza le schede descritte di seguito per sfogliare e configurarlo.

* La scheda **Pianificazione** visualizza il calendario dei programmi per un mese, una settimana o un giorno, a seconda della scheda su cui fai clic nell’intestazione del calendario.

   Se necessario, puoi creare una campagna, un programma o un’attività tramite questa pagina.

   ![](assets/s_ncs_user_interface_campaign02.png)

* La scheda **Modifica** consente di personalizzare il programma: nome, date di inizio e fine, budget, documenti collegati, ecc.

   ![](assets/s_ncs_user_interface_campaign05.png)

#### Campagne di navigazione {#browsing-campaigns}

Le campagne sono accessibili tramite il calendario della campagna, la scheda **[!UICONTROL Schedule]** del programma o l’elenco delle campagne.

1. Tramite il calendario della campagna, seleziona la campagna da visualizzare, quindi fai clic sul collegamento **[!UICONTROL Open]** .

   ![](assets/campaign_planning_edit_op.png)

   La campagna viene modificata in una nuova scheda, come illustrato di seguito:

   ![](assets/campaign_op_edit.png)

1. Tramite la scheda **[!UICONTROL Schedule]** del programma, la modalità di modifica è la stessa del calendario della campagna.
1. Tramite il collegamento **[!UICONTROL Campaigns]** della scheda **[!UICONTROL Campaigns]**, fai clic sul nome della campagna da modificare.

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

Per ulteriori informazioni, consulta [Forum di discussione](../../campaign/using/discussion-forums.md).

#### Rapporti {#reports}

Il collegamento **[!UICONTROL Reports]** ti consente di accedere ai rapporti della campagna.

![](assets/campaign_reporting_tab.png)

>[!NOTE]
>
>I rapporti sono descritti in [questa sezione](../../reporting/using/about-adobe-campaign-reporting-tools.md).

#### Configurazione {#configuration}

Le campagne vengono create tramite modelli di campagna. Puoi configurare modelli riutilizzabili per i quali sono selezionate alcune opzioni e altre impostazioni già salvate. Per ogni campagna, è disponibile la seguente funzionalità:

* Riferimento a documenti e risorse: puoi associare i documenti alla campagna (breve, rapporto, immagini, ecc.). Sono supportati tutti i formati di documento. Vedere [Gestione dei documenti associati](../../campaign/using/marketing-campaign-deliveries.md#managing-associated-documents).
* Definizione dei costi: per ogni campagna, Adobe Campaign ti consente di definire voci di costo e strutture di calcolo dei costi che possono essere utilizzate durante la creazione della campagna di marketing. Ad esempio: costi di stampa, utilizzo di un&#39;agenzia esterna, noleggio di camere, ecc. Vedere [Definizione delle categorie di costi](../../campaign/using/providers--stocks-and-budgets.md#defining-cost-categories).
* Definizione degli obiettivi: puoi definire obiettivi quantificabili per una campagna, ad esempio numero di abbonati, volume di affari, ecc. Queste informazioni vengono successivamente utilizzate nei rapporti delle campagne.
* Gestione degli indirizzi di seed (per ulteriori informazioni, consulta [questa sezione](../../delivery/using/about-seed-addresses.md)) e dei gruppi di controllo (consulta [Definizione di un gruppo di controllo](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group)).
* Gestione delle approvazioni: è possibile selezionare i trattamenti da approvare e, se necessario, selezionare gli operatori di revisione o i gruppi di operatori. Consulta [Controllo e approvazione delle consegne](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries).

>[!NOTE]
>
>Per accedere alle configurazioni della campagna e apportare loro modifiche, fai clic sul collegamento **[!UICONTROL Advanced campaign parameters...]** nella scheda **[!UICONTROL Edit]** . Per ulteriori informazioni sull’impostazione dei parametri a livello di campagna in modo che le consegne ereditino automaticamente i valori, consulta [la nostra nota tecnica](https://helpx.adobe.com/campaign/kb/simplifying-campaign-management-acc.html#Setparametersatthecampaignlevelsodeliveriesinheritvaluesautomatically).

## Utilizzo dell&#39;interfaccia Web {#using-the-web-interface-}

Puoi accedere alle schermate della console Adobe Campaign tramite un browser Internet per visualizzare tutte le campagne e le consegne, nonché i rapporti e le informazioni sui profili nel database. L&#39;accesso non consente la creazione di record. A seconda dei diritti dell’operatore, è possibile visualizzare e/o intervenire sui dati nel database. Ad esempio, puoi approvare il contenuto e il targeting della campagna, riavviare o interrompere una consegna, ecc.

1. Accedi come di consueto tramite https://`<your instance>:<port>/view/home`.
1. Utilizza i menu per accedere alle panoramiche.

   ![](assets/s_ncs_user_interface_web_campaign_01.png)

Le approvazioni (di un target o di un contenuto di consegna, ad esempio) possono essere eseguite tramite accesso web.

![](assets/campaign_web_interface_validation.png)

Puoi anche utilizzare il collegamento contenuto nei messaggi di notifica. Per ulteriori informazioni, consulta [Controllo e approvazione delle consegne](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries).
