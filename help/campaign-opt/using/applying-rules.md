---
product: campaign
title: Applicare le regole di tipologia
description: Scopri come applicare le regole di tipologia
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Typology Rules
exl-id: 09ec0fc0-76ed-4c73-8bdf-c931e2103aa9
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '983'
ht-degree: 9%

---

# Applicare le regole di tipologia{#applying-rules}

## Applicare una tipologia a una consegna {#applying-a-typology-to-a-delivery}

Per applicare le regole di tipologia create, devi associarle a una tipologia e quindi fare riferimento a questa tipologia nella consegna. Per eseguire questa operazione:

1. Creare una tipologia di campagna.

   Le tipologie sono accessibili tramite **[!UICONTROL Administration > Campaign Management > Typology management]** > **[!UICONTROL Typologies]** nodo.

1. Vai a **[!UICONTROL Rules]** fai clic sulla scheda **[!UICONTROL Add]** e seleziona le regole da applicare con questa tipologia.

   ![](assets/campaign_opt_pressure_sample_1_6.png)

1. Salva la tipologia: viene aggiunto all’elenco delle tipologie esistenti.
1. Apri la consegna a cui desideri applicare le regole.
1. Apri le proprietà di consegna e accedi al **[!UICONTROL Typology]** scheda .
1. Seleziona la tipologia nell’elenco a discesa.

   ![](assets/campaign_opt_pressure_sample_1_7.png)

   >[!NOTE]
   >
   >La tipologia può essere definita nel modello di consegna, da applicare automaticamente a tutte le consegne create utilizzando questo modello.

## Definire le condizioni dell&#39;applicazione {#defining-application-conditions}

Puoi limitare il campo di applicazione di una regola in base alle tue esigenze (ad eccezione delle regole di controllo).

È possibile configurare le regole di tipologia in modo che riguardino solo alcune consegne a cui sono collegate o alcuni destinatari tra il target di una consegna.

Per definire le condizioni di applicazione di una regola, fai clic sul pulsante **[!UICONTROL Edit the rule application conditions...]** nel collegamento **[!UICONTROL General]** scheda .

Quindi utilizza l’editor delle query per definire le condizioni di filtro. Nell’esempio seguente, la regola della capacità riguarda solo le consegne con la parola &quot;offerta&quot; nell’etichetta o nelle consegne create prima del 1° aprile 2013.

![](assets/campaign_opt_create_capacity_criterion.png)

>[!NOTE]
>
>Per filtrare le regole, puoi selezionare la condizione di applicazione dei criteri di filtro: possono dipendere dalla consegna o dal profilo di consegna. Per ulteriori informazioni, consulta [Condizionamento di una regola di filtro](filtering-rules.md#conditioning-a-filtering-rule).

## Regola frequenza di calcolo {#adjusting-calculation-frequency}

Gli arbitrati vengono rieseguiti automaticamente ogni notte tramite il flusso di lavoro di pulizia del database. Tuttavia, i valori possono essere salvati oltre questo periodo.

In effetti, alcuni calcoli utilizzano valori che non cambiano su base giornaliera. Sarebbe quindi irrilevante ricalcolare i dati ogni giorno e sovraccaricare il database per nulla. Ad esempio, se un processo arricchisce il database di marketing con i punteggi di propensione del cliente e le informazioni di acquisto settimanalmente, i dati basati su questi valori non devono essere ricalcolati ogni giorno.

Per eseguire questa operazione, **[!UICONTROL Frequency]** campo **[!UICONTROL General]** La scheda ti consente di definire un periodo massimo durante il quale viene salvato il targeting. Per impostazione predefinita, il valore **0** indica che il calcolo rimane valido fino alla successiva esecuzione del ri-arbitrato giornaliero.

Per salvare i risultati oltre questo periodo, immetti un valore maggiore di 12 nel **[!UICONTROL Frequency]** campo: una volta scaduto questo periodo, tutte le regole vengono nuovamente applicate.

La **[!UICONTROL Re-apply the rule at the start of personalization]** consente di applicare la regola automaticamente durante la fase di personalizzazione, anche se il periodo indicato in **[!UICONTROL Frequency]** campo ancora valido.

## Selezione della fase di applicazione della regola {#selecting-the-rule-application-phase}

Le regole di tipologia vengono applicate in una sequenza specifica durante le fasi di targeting, analisi e personalizzazione delle consegne interessate.

### Ordine di esecuzione {#execution-order}

Nella modalità operativa standard, le regole vengono applicate nella sequenza seguente:

1. Regole di controllo, se applicate all’inizio del targeting.
1. Regole di filtro:

   * Regole di applicazione native per la qualifica degli indirizzi: indirizzo definito / indirizzo non verificato / indirizzo sul  elenco Bloccati / indirizzo messo in quarantena / qualità indirizzo.
   * Regole di filtro definite dall’utente.
   * Regola di deduplicazione sull’indirizzo o sull’identificatore (applicata se necessario).

1. Regole di pressione.
1. Regole sulla capacità.
1. Regole di controllo, se applicate alla fine del targeting.
1. Regole di controllo, se applicate all’inizio della personalizzazione. Se le regole dell&#39;utente (filtro / pressione / capacitivo) sono scadute e devono essere ricalcolate, verranno applicate durante questo passaggio.
1. Regole di controllo, se applicate al termine della personalizzazione.

>[!NOTE]
>
>Se lavori con il modulo di interazione di Campaign, le regole di idoneità delle offerte vengono applicate contemporaneamente alle regole di filtro (per le offerte che si trovano nei contorni di consegna) o durante la fase di personalizzazione, durante la chiamata al motore di offerta.

È possibile adattare la sequenza di esecuzione delle regole che hanno lo stesso tipo utilizzando il campo appropriato nella sezione **[!UICONTROL General]** scheda della regola. Quando più regole vengono eseguite durante la stessa fase di elaborazione dei messaggi, puoi configurarne la sequenza di esecuzione nel **[!UICONTROL Execution sequence]** campo .

Ad esempio, una regola di pressione con un ordine di esecuzione di 20 verrà eseguita prima di una regola di pressione con un ordine di esecuzione di 30.

### Regole di controllo {#control-rules}

Per **[!UICONTROL Control]** regole, puoi decidere in quale punto del ciclo di vita della consegna verrà applicata la regola (prima o dopo il targeting, all’inizio della personalizzazione, alla fine dell’analisi). Seleziona il valore da applicare nell’elenco a discesa della **[!UICONTROL Phase]** nel campo **[!UICONTROL General]** scheda della regola di tipologia.

![](assets/campaign_opt_define_control_phase.png)

I valori possibili sono:

* **[!UICONTROL At the start of targeting]**

   Per evitare che il passaggio di personalizzazione venga eseguito in caso di errori, puoi applicare la regola di controllo qui.

* **[!UICONTROL After targeting]**

   Se devi conoscere il volume del target per applicare la regola di controllo, seleziona questa fase.

   Ad esempio, il **[!UICONTROL Check proof size]** la regola di controllo si applica dopo ogni fase di targeting: questa regola impedisce la personalizzazione dei messaggi se sono presenti troppi destinatari di bozza.

* **[!UICONTROL At the start of personalization]**

   Questa fase deve essere selezionata se il controllo riguarda l’approvazione della personalizzazione dei messaggi. La personalizzazione dei messaggi viene eseguita durante la fase di analisi.

* **[!UICONTROL At the end of the analysis]**

   Quando un controllo richiede il completamento della personalizzazione dei messaggi, seleziona questa fase.

## Configurazioni aggiuntive {#additional-configurations}

### Controllo del traffico SMTP in uscita {#control-outgoing-smtp-traffic}

Come opzione, puoi utilizzare la funzione **[!UICONTROL Managing affinities with IP addresses]** per collegare le consegne al server di consegna (MTA) questa affinità. Ciò ti consente di limitare il numero di e-mail per consegne specifiche a computer o indirizzi di output.

![](assets/campaign_opt_select_ip_affinity.png)

>[!NOTE]
>
>La gestione dell’affinità non è applicabile per **[!UICONTROL Filtering]** tipologie.\
>Le affinità sono definite nel file di configurazione dell’istanza, sul server Adobe Campaign. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../installation/using/about-initial-configuration.md).

### Ottimizzazione delle campagne e marketing distribuito {#campaign-optimization-and-distributed-marketing}

La **[!UICONTROL Distributed Marketing]** La scheda ti consente di definire la ricompilazione di tipologie e/o regole che si applicano quando una campagna condivisa viene ordinata e/o riservata. Le tipologie/regole definite per un’entità locale (collegate a quelle definite per l’entità centrale) sostituiscono le regole/tipologie collegate all’entità centrale. La nuova mappatura consente di adattare le regole di entità centrale alle entità locali che ordinano la campagna.

![](assets/simu_campaign_opti_distrib_mkg.png)

>[!NOTE]
>
>Nelle tipologie e nelle regole di tipologia, il **[!UICONTROL Distributed Marketing]** viene aggiunta una scheda se la licenza include questa opzione: controlla il contratto di licenza.\
>Per ulteriori informazioni su Marketing distribuito, consulta [Informazioni sul marketing distribuito](../../distributed/using/about-distributed-marketing.md).
