---
title: Applicazione delle regole
seo-title: Applicazione delle regole
description: Applicazione delle regole
seo-description: null
page-status-flag: never-activated
uuid: 4472fc0d-d717-4603-8472-bdaf2835a02a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: campaign-optimization
discoiquuid: a0e76d27-bedd-4f81-b4d2-1221444e670e
translation-type: tm+mt
source-git-commit: 75cbb8d697a95f4cc07768e6cf3585e4e079e171
workflow-type: tm+mt
source-wordcount: '979'
ht-degree: 10%

---


# Applicazione delle regole{#applying-rules}

## Applicazione di una tipologia a una consegna {#applying-a-typology-to-a-delivery}

Per applicare le regole di tipologia create, è necessario associarle a una tipologia, quindi fare riferimento a questa tipologia nella distribuzione. Per eseguire questa operazione:

1. Creare una tipologia di campagna.

   Le tipologie sono accessibili tramite il nodo **[!UICONTROL Administration > Campaign Management > Typology management]** > **[!UICONTROL Typologies]** .

1. Vai alla **[!UICONTROL Rules]** scheda, fai clic sul **[!UICONTROL Add]** pulsante e seleziona le regole da applicare con questa tipologia.

   ![](assets/campaign_opt_pressure_sample_1_6.png)

1. Salva la tipologia: viene aggiunto all&#39;elenco delle tipologie esistenti.
1. Aprire la consegna a cui si desidera applicare le regole.
1. Aprite le proprietà di consegna e accedete alla **[!UICONTROL Typology]** scheda.
1. Selezionare la tipologia nell&#39;elenco a discesa.

   ![](assets/campaign_opt_pressure_sample_1_7.png)

   >[!NOTE]
   >
   >La tipologia può essere definita nel modello di consegna, da applicare automaticamente a tutte le consegne create utilizzando questo modello.

## Definizione delle condizioni dell&#39;applicazione {#defining-application-conditions}

È possibile limitare il campo applicazione di una regola in base alle proprie esigenze (ad eccezione delle regole di controllo).

È possibile configurare le regole di tipologia in modo che riguardino solo alcune consegne a cui sono collegate, o alcuni destinatari tra le destinazioni di una consegna.

Per definire le condizioni di applicazione di una regola, fare clic sul **[!UICONTROL Edit the rule application conditions...]** collegamento nella **[!UICONTROL General]** scheda.

Quindi utilizzate l&#39;editor di query per definire le condizioni di filtro. Nell&#39;esempio seguente, la regola della capacità riguarda solo le consegne con la parola &quot;offerta&quot; nell&#39;etichetta o nelle consegne create prima del 1° aprile 2013.

![](assets/campaign_opt_create_capacity_criterion.png)

>[!NOTE]
>
>Per le regole di filtro, potete selezionare la condizione di applicazione dei criteri di filtro: possono dipendere dalla consegna o dal profilo di consegna. Per ulteriori informazioni, vedere [Condizionamento di una regola](../../campaign/using/filtering-rules.md#conditioning-a-filtering-rule)di filtro.

## Regolazione della frequenza di calcolo {#adjusting-calculation-frequency}

Gli arbitrati vengono eseguiti automaticamente ogni notte tramite il flusso di lavoro di pulizia del database. Tuttavia, i valori possono essere salvati oltre questo periodo.

In effetti, alcuni calcoli utilizzano valori che non cambiano su base giornaliera. Sarebbe pertanto irrilevante ricalcolare i dati ogni giorno e sovraccaricare il database per nulla. Ad esempio, se un processo arricchisce il database di marketing con punteggi di propensione dei clienti e informazioni di acquisto settimanali, non è necessario ricalcolare i dati basati su questi valori ogni giorno.

A questo scopo, il **[!UICONTROL Frequency]** campo della **[!UICONTROL General]** scheda consente di definire un periodo massimo durante il quale viene salvato il targeting. Per impostazione predefinita, il valore **0** indica che il calcolo rimane valido fino alla successiva esecuzione del nuovo arbitrato giornaliero.

Per salvare i risultati oltre questo periodo, immettere un valore maggiore di 12 nel **[!UICONTROL Frequency]** campo: una volta scaduto tale periodo, tutte le regole vengono applicate di nuovo.

L&#39; **[!UICONTROL Re-apply the rule at the start of personalization]** opzione consente di applicare la regola automaticamente durante la fase di personalizzazione, anche se il periodo indicato nel **[!UICONTROL Frequency]** campo è ancora valido.

## Selezione della fase di applicazione della regola {#selecting-the-rule-application-phase}

Le regole di tipologia vengono applicate in una sequenza specifica durante le fasi di targeting, analisi e personalizzazione delle consegne a cui si riferiscono.

### Ordine di esecuzione {#execution-order}

Nella modalità operativa standard, le regole vengono applicate nella sequenza seguente:

1. Regole di controllo, se applicate all’inizio del targeting.
1. Regole di filtro:

   * Regole di applicazione native per la qualifica degli indirizzi: indirizzo definito / indirizzo / non verificato / indirizzo sul elenco Bloccati / indirizzo messo in quarantena / qualità indirizzo / non verificato.
   * Regole di filtro definite dall’utente.
   * Regola di deduplicazione sull&#39;indirizzo o sull&#39;identificatore (applicata se necessario).

1. Regole di pressione.
1. Regole sulla capacità.
1. Regole di controllo, se applicate alla fine del targeting.
1. Regole di controllo, se applicate all’inizio della personalizzazione. Se le regole dell&#39;utente (filtro / pressione / capacitivo) sono scadute e devono essere ricalcolate, saranno applicate in questa fase.
1. Regole di controllo, se applicate al termine della personalizzazione.

>[!NOTE]
>
>Se state lavorando con il modulo Interazione campagna, le regole di idoneità delle offerte vengono applicate contemporaneamente alle regole di filtraggio (per le offerte trovate nei contorni di consegna) o durante la fase di personalizzazione, durante la chiamata al motore delle offerte.

È possibile adattare la sequenza di esecuzione delle regole che hanno lo stesso tipo utilizzando il campo appropriato nella **[!UICONTROL General]** scheda della regola. Quando più regole vengono eseguite durante la stessa fase di elaborazione dei messaggi, puoi configurarne la sequenza di esecuzione nel **[!UICONTROL Execution sequence]** campo.

Ad esempio, una regola di pressione con un ordine di esecuzione pari a 20 verrà eseguita prima di una regola di pressione con un ordine di esecuzione pari a 30.

### Regole di controllo {#control-rules}

Per **[!UICONTROL Control]** le regole, potete decidere in quale punto del ciclo di vita della distribuzione verrà applicata la regola (prima o dopo il targeting, all&#39;inizio della personalizzazione, alla fine dell&#39;analisi). Selezionare il valore da applicare nell&#39;elenco a discesa del **[!UICONTROL Phase]** campo, nella **[!UICONTROL General]** scheda della regola di tipologia.

![](assets/campaign_opt_define_control_phase.png)

I valori possibili sono:

* **[!UICONTROL At the start of targeting]**

   Per evitare che il passaggio di personalizzazione venga eseguito in caso di errori, puoi applicare la regola di controllo qui.

* **[!UICONTROL After targeting]**

   Se è necessario conoscere il volume del target per applicare la regola di controllo, selezionare questa fase.

   Ad esempio, la regola di **[!UICONTROL Check proof size]** controllo si applica dopo ogni fase di targeting: questa regola impedisce la personalizzazione dei messaggi in presenza di troppi destinatari di prova.

* **[!UICONTROL At the start of personalization]**

   Questa fase deve essere selezionata se il controllo riguarda l&#39;approvazione della personalizzazione dei messaggi. La personalizzazione dei messaggi viene effettuata durante la fase di analisi.

* **[!UICONTROL At the end of the analysis]**

   Quando un controllo richiede il completamento della personalizzazione dei messaggi, seleziona questa fase.

## Configurazioni aggiuntive {#additional-configurations}

### Controllo del traffico SMTP in uscita {#control-outgoing-smtp-traffic}

Come opzione, potete utilizzare il **[!UICONTROL Managing affinities with IP addresses]** campo per collegare le consegne al server di consegna (MTA) questa affinità. Questo consente di limitare il numero di e-mail per consegne specifiche verso computer o indirizzi di output.

![](assets/campaign_opt_select_ip_affinity.png)

>[!NOTE]
>
>La gestione dell&#39;affinità non si applica alle **[!UICONTROL Filtering]** tipologie.\
>Le affinità sono definite nel file di configurazione dell&#39;istanza, sul server Adobe Campaign . Per ulteriori informazioni al riguardo, consulta [questa sezione](../../installation/using/about-initial-configuration.md).

### Ottimizzazione delle campagne e marketing distribuito {#campaign-optimization-and-distributed-marketing}

La **[!UICONTROL Distributed Marketing]** scheda consente di definire la ricompilazione di tipologie e/o regole da applicare quando una campagna condivisa viene ordinata e/o riservata. Le tipologie/regole definite per un&#39;entità locale (collegate a quelle definite per l&#39;entità centrale) sostituiscono le regole/tipologie collegate all&#39;entità centrale. La nuova mappatura consente di adattare le regole di entità centrale alle entità locali che ordinano la campagna.

![](assets/simu_campaign_opti_distrib_mkg.png)

>[!NOTE]
>
>In tipologie e regole di tipologia, la **[!UICONTROL Distributed Marketing]** scheda viene aggiunta se la licenza include questa opzione: controllare il contratto di licenza.\
>Per ulteriori informazioni su Distributed Marketing, consultate [Informazioni sul marketing](../../campaign/using/about-distributed-marketing.md)distribuito.

