---
product: campaign
title: Script e modelli JavaScript
description: Script e modelli JavaScript
feature: Workflows
exl-id: 4a3647d1-cf8c-4867-871e-472287be7c6a
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '1247'
ht-degree: 2%

---

# Script e modelli JavaScript{#javascript-scripts-and-templates}



Gli script consentono di calcolare i valori, scambiare dati tra diverse attività nel processo ed eseguire operazioni specifiche utilizzando chiamate SOAP.

Gli script sono onnipresenti in un diagramma di flusso di lavoro:

* Tutte le attività dispongono di script di inizializzazione. Uno script di inizializzazione viene eseguito quando l’attività viene attivata e può essere utilizzato per inizializzare le variabili e modificare le proprietà.
* L’attività &quot;Codice JavaScript&quot; viene semplicemente utilizzata per eseguire uno script.
* L’attività &quot;Test&quot; valuta le espressioni JavaScript per attivare la transizione appropriata.
* La maggior parte dei campi di testo sono modelli di JavaScript: le espressioni JavaScript possono essere incluse tra &lt;%= e %>. Questi campi offrono un pulsante che apre un elenco a discesa per facilitare l’immissione di espressioni.

  ![](assets/script-button.png)

## Oggetti esposti {#objects-exposed}

Gli script Java eseguiti nel contesto di un flusso di lavoro accedono a una serie di oggetti globali aggiuntivi.

* **istanza**: rappresenta il flusso di lavoro in esecuzione. Lo schema di questo oggetto è **xtk:workflow**.
* **attività**: rappresenta le attività in esecuzione. Lo schema di questo oggetto è **xtk:workflowTask**.
* **event**: rappresenta gli eventi che hanno attivato l&#39;attività in esecuzione. Lo schema di questo oggetto è **xtk:workflowEvent**. Questo oggetto non è inizializzato per attività di tipo **AND-join** attivate da più transizioni.
* **eventi**: rappresenta l&#39;elenco degli eventi che hanno attivato l&#39;attività corrente. Lo schema di questo oggetto è **xtk:workflowEvent**. Questa tabella contiene in genere un elemento, ma può contenere diverse attività di tipo **AND-join** attivate in base a diverse transizioni.
* **attività**: rappresenta il modello dell&#39;attività in esecuzione. Lo schema di questo oggetto dipende dal tipo di attività. Questo oggetto può essere modificato dallo script di inizializzazione, in altri script, modifiche con effetti indeterminabili.

Le proprietà disponibili per questi oggetti possono essere visualizzate in un elenco a discesa facendo clic sul pulsante a destra della barra degli strumenti dello script.

>[!CAUTION]
>
>Le proprietà di questi oggetti sono di sola lettura, ad eccezione delle sottoproprietà della proprietà vars.
>  
>La maggior parte di queste proprietà viene aggiornata solo dopo l’esecuzione di un’attività elementare o quando l’istanza viene passivata. I valori letti non corrispondono necessariamente allo stato corrente ma a quello precedente.

**Esempio**

In questo esempio e negli esempi seguenti creare un flusso di lavoro che includa un&#39;attività **JavaScript code** e un&#39;attività **End** come illustrato nel diagramma seguente.

![](assets/script-1.png)

Fare doppio clic sull&#39;attività **Codice JavaScript** e inserire lo script seguente:

```
logInfo("Label: " + instance.label)
logInfo("Start date: " + task.creationDate)
```

La funzione **[!UICONTROL logInfo(message)]** inserisce un messaggio nel registro.

Fai clic su **[!UICONTROL OK]** per chiudere l&#39;assistente alla creazione, quindi avvia il flusso di lavoro utilizzando i pulsanti di azione in alto a destra nell&#39;elenco dei flussi di lavoro. Al termine dell’esecuzione, consulta il registro. Dovresti visualizzare due messaggi corrispondenti allo script: uno visualizza l’etichetta del flusso di lavoro, l’altro visualizza la data in cui lo script è stato attivato.

## Variabili {#variables}

Le variabili sono le proprietà libere degli oggetti **[!UICONTROL instance]**, **[!UICONTROL task]** e **[!UICONTROL event]**. I tipi di JavaScript autorizzati per queste variabili sono **[!UICONTROL string]**, **[!UICONTROL number]** e **[!UICONTROL Date]**.

### Variabili dell’istanza {#instance-variables}

Le variabili di istanza (**[!UICONTROL instance.vars.xxx]**) sono paragonabili alle variabili globali. Sono condivise da tutte le attività.

### Variabili attività {#task-variables}

Le variabili dell&#39;attività (**[!UICONTROL task.vars.xxx]**) sono paragonabili alle variabili locali. Vengono utilizzati solo dall&#39;attività corrente. Queste variabili vengono utilizzate dalle attività persistenti per conservare i dati e talvolta vengono utilizzate per scambiare dati tra i diversi script di una stessa attività.

### Variabili di evento {#event-variables}

Le variabili evento (**[!UICONTROL vars.xxx]**) consentono lo scambio di dati tra le attività elementari di un processo di workflow. Queste variabili vengono passate dall&#39;attività che ha attivato l&#39;attività in corso. È possibile modificarli e definirne di nuovi. Vengono quindi passate alle seguenti attività.

>[!CAUTION]
>
>Nel caso di attività di tipo [AND-join](and-join.md), le variabili vengono unite ma se viene definita due volte la stessa variabile, si verifica un conflitto e il valore rimane indeterminato.

Gli eventi sono le variabili utilizzate più di frequente e devono essere utilizzati al posto delle variabili di istanza.

Alcune variabili evento vengono modificate o lette dalle varie attività. Si tratta di tutte variabili di tipo stringa. Ad esempio, un&#39;esportazione imposta la variabile **[!UICONTROL vars.filename]** con il nome completo del file appena esportato. Tutte queste variabili lette o modificate sono documentate in [Informazioni sulle attività](about-activities.md), nelle sezioni **Parametri di input** e **Parametri di output** delle attività.

### Casi d’uso {#example}

>[!NOTE]
>
>Altri casi di utilizzo del flusso di lavoro sono disponibili in [questa sezione](about-workflow-use-cases.md).

**Esempio 1**

In questo esempio, viene utilizzata una variabile di istanza per calcolare dinamicamente la percentuale divisa da applicare a una popolazione.

1. Crea un flusso di lavoro e aggiungi un’attività Start.

1. Aggiungi e configura un’attività di codice JavaScript per definire una variabile di istanza.

   Esempio: `instance.vars.segmentpercent = 10;`

   ![](assets/js_ex1.png)

1. Aggiungi un’attività Query e indirizza i destinatari in base alle tue esigenze.

1. Aggiungi un’attività Split e configurala per eseguire un campionamento casuale della popolazione in ingresso. La percentuale di campionamento può essere qualsiasi cosa a tua scelta. In questo esempio è impostato su 50%.

   È questa percentuale che viene aggiornata dinamicamente grazie alla variabile di istanza definita in precedenza.

   ![](assets/js_ex2.png)

1. All’interno della sezione Script di inizializzazione della scheda Avanzate dell’attività Dividi, definisci una condizione JS. La condizione JS seleziona la percentuale di campionamento casuale della prima transizione proveniente dall’attività Split e la aggiorna a un valore impostato dalla variabile di istanza creata in precedenza.

   ```
   activity.transitions.extractOutput[0].limiter.percent = instance.vars.segmentpercent;
   ```

   ![](assets/js_ex3.png)

1. Assicurati che il complemento sia generato in una transizione separata dell’attività Split e aggiungi le attività End dopo ciascuna delle transizioni in uscita.

1. Salva ed esegui il flusso di lavoro. Il campionamento dinamico viene applicato in base alla variabile dell’istanza.

   ![](assets/js_ex4.png)

**Esempio 2**

1. Prendi il flusso di lavoro dell&#39;esempio precedente e sostituisci lo script dell&#39;attività **Codice JavaScript** con lo script seguente:

   ```
   instance.vars.foo = "bar1"
   vars.foo = "bar2"
   task.vars.foo = "bar3"
   ```

1. Aggiungi lo script seguente allo script di inizializzazione dell&#39;attività **End**:

   ```
   logInfo("instance.vars.foo = " + instance.vars.foo)
   logInfo("vars.foo = " + vars.foo)
   logInfo("task.vars.foo = " + task.vars.foo)
   ```

1. Avvia il flusso di lavoro, quindi controlla il registro.

   ```
   Workflow finished
   task.vars.foo = undefined
   vars.foo = bar2
   instance.vars.foo = bar1
   Starting workflow (operator 'admin')
   ```

Questo esempio mostra che l&#39;attività che segue **JavaScript Code** accede alle variabili di istanza e alle variabili di evento, ma le variabili di attività non sono accessibili dall&#39;esterno (&#39;undefined&#39;).

### Chiamata di una variabile di istanza in una query {#calling-an-instance-variable-in-a-query}

Dopo aver specificato una variabile di istanza in un’attività, puoi riutilizzarla in una query del flusso di lavoro.

Per chiamare una variabile **instance.vars.xxx = &quot;yyyy&quot;** in un filtro, immettere **$(instance/vars/xxx)**.

Ad esempio:

1. Creare una variabile di istanza che definisce il nome interno di una consegna tramite **[!UICONTROL JavaScript code]**: **instance.vars.deliveryIN = &quot;DM42&quot;**.

   ![](assets/wkf_js_activity_1.png)

1. Crea una query le cui dimensioni di targeting e filtro sono i destinatari. Nelle condizioni, specifica che desideri trovare tutti i destinatari a cui è stata inviata la consegna specificata dalla variabile.

   Come promemoria, queste informazioni vengono memorizzate nei registri di consegna.

   Per fare riferimento alla variabile di istanza nella colonna **[!UICONTROL Value]**, immettere **$(instance/vars/@deliveryIN)**.

   Il flusso di lavoro restituirà i destinatari della consegna DM42.

   ![](assets/wkf_var_in_query.png)

## Funzioni avanzate {#advanced-functions}

Oltre alle funzioni standard di JavaScript, sono disponibili funzioni speciali per la manipolazione di file, la lettura o la modifica di dati nel database o l&#39;aggiunta di messaggi al registro.

### Diario {#journal}

**[!UICONTROL logInfo(message)]** è stato descritto negli esempi precedenti. Questa funzione aggiunge un messaggio informativo al giornale di registrazione.

**[!UICONTROL logError(message)]** aggiunge un messaggio di errore al registro. Lo script interrompe l’esecuzione e il flusso di lavoro passa allo stato di errore (per impostazione predefinita, l’istanza viene messa in pausa).

## Script di inizializzazione {#initialization-script}

In determinate condizioni, puoi modificare una proprietà di un’attività al momento dell’esecuzione.

La maggior parte delle proprietà delle attività può essere calcolata dinamicamente utilizzando un modello di JavaScript o perché le proprietà del flusso di lavoro consentono esplicitamente di calcolare il valore tramite uno script.

Per altre proprietà, tuttavia, è necessario utilizzare lo script di inizializzazione. Questo script viene valutato prima dell’esecuzione dell’attività. La variabile **[!UICONTROL activity]** fa riferimento all&#39;attività corrispondente all&#39;attività. Le proprietà di questa attività possono essere modificate e influiranno solo su questa attività.

**Argomenti correlati**
[Esempi di codice JavaScript nei flussi di lavoro](javascript-in-workflows.md)
