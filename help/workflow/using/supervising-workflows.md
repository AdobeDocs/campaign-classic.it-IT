---
product: campaign
title: Supervisione dei flussi di lavoro
description: Scopri come supervisionare i flussi di lavoro di Campaign
feature: Workflows
exl-id: ca6d4bf4-7b3a-4d36-9fc3-0b83531d0132
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '646'
ht-degree: 0%

---

# Caso di utilizzo: supervisionare i flussi di lavoro{#supervising-workflows}

![](../../assets/v7-only.svg)

Questo caso d’uso descrive la creazione di un flusso di lavoro che consente di monitorare lo stato di un set di flussi di lavoro che vengono &quot;messi in pausa&quot;, &quot;interrotti&quot; o &quot;con errori&quot;.

Il suo scopo è:

* Utilizza un flusso di lavoro per monitorare un gruppo di flussi di lavoro aziendali.
* Invia un messaggio a un supervisore tramite un&#39;attività di &quot;consegna&quot;.

Per monitorare lo stato di un set di flussi di lavoro, è necessario seguire questi passaggi:

1. Crea il flusso di lavoro di monitoraggio.
1. Scrivi il JavaScript per determinare se i flussi di lavoro vengono messi in pausa, interrotti o con errori.
1. Crea il **[!UICONTROL Test]** attività.
1. Prepara il modello di consegna.

>[!NOTE]
>
>Oltre al flusso di lavoro, Campaign **Workflow Heatmap** consente di analizzare in dettaglio i flussi di lavoro attualmente in esecuzione. Per ulteriori informazioni, consulta la sezione [sezione dedicata](heatmap.md).
>
>Per ulteriori informazioni su come **monitorare l’esecuzione dei flussi di lavoro**, fare riferimento a [questa sezione](monitoring-workflow-execution.md).

## Passaggio 1: Creazione del flusso di lavoro di monitoraggio {#step-1--creating-the-monitoring-workflow}

La cartella del flusso di lavoro che verrà monitorata è la **&quot;CustomWorkflows&quot;** cartella memorizzata in **Amministrazione > Produzione > Flussi di lavoro tecnici** nodo. Questa cartella contiene un set di flussi di lavoro aziendali.

La **Monitoraggio del flusso di lavoro** viene memorizzato nella directory principale della cartella Flussi di lavoro tecnici. L’etichetta utilizzata è **&quot;Monitoraggio&quot;**.

Lo schema seguente mostra la sequenza di attività:

![](assets/uc_monitoring_workflow_overview.png)

Questo flusso di lavoro è costituito da:

* a **&quot;Start&quot;** attività.
* a **&quot;Codice JavaScript&quot;** attività responsabile dell’analisi della cartella dei flussi di lavoro aziendali.
* a **&quot;Test&quot;** attività per inviare una consegna al supervisore o riavviare il flusso di lavoro.
* a **&quot;Consegna&quot;** attività responsabile del layout dei messaggi.
* a **&quot;Wait&quot;** attività che controlla i lead time tra le iterazioni del flusso di lavoro.

## Passaggio 2: Scrittura di JavaScript {#step-2--writing-the-javascript}

La prima parte del codice JavaScript coincide con un **query (queryDef)** che consente di identificare i flussi di lavoro con uno stato di &quot;pausa&quot; (@state == 13), &quot;error&quot; (@failed == 1) o &quot;stop&quot; (@state == 20).

La **nome interno** della cartella del flusso di lavoro da monitorare è indicata nella seguente condizione:

```
<condition boolOperator="AND" expr="[folder/@name] = 'Folder20'" internalId="1"/>
```

```
var strError = "";
var strPaused = "";
var strStop = "";

var queryWkfError = xtk.queryDef.create(
  <queryDef schema="xtk:workflow" operation="select">
    <select>
      <node expr="@internalName"/>
      <node expr="@state"/>
      <node expr="@label"/>
      <node expr="@failed"/>
      <node expr="@state"/>   
    </select>
    <where id="12837805386">
      <condition boolOperator="AND" expr="[folder/@name] = 'Folder20'" internalId="1"/>
        <condition boolOperator="AND" internalId="2">
          <condition boolOperator="OR" expr="@state = 20" internalId="3"/>
          <condition expr="@state = 13" internalId="4"/>
        </condition>  
    </where>
  </queryDef>
);
var ndWkfError = queryWkfError.ExecuteQuery(); 
```

La seconda parte del codice JavaScript consente di: **visualizzare un messaggio per ogni flusso di lavoro** in base allo stato recuperato durante la query.

>[!NOTE]
>
>Le stringhe create devono essere caricate nelle variabili evento del flusso di lavoro.

```
for each ( var wkf in ndWkfError.workflow ) 
{
  if ( wkf.@state == 13 )  // Status 13 = paused
  {
    if ( wkf.@failed == 1 )
      strError += "<li>Workflow '" + wkf.@internalName + "' with the label '" + wkf.@label + "'</li>";
    else
      strPaused += "<li>Workflow '" + wkf.@internalName + "' with the label '" + wkf.@label + "'</li>";
  }
  
  if ( wkf.@state == 20 )  // Status 20 = stop
    strStop += "<li>Workflow '" + wkf.@internalName + "' with the label '" + wkf.@label + "'</li>";
}

vars.strWorkflowError = strError;
vars.strWorkflowPaused = strPaused;
vars.strWorkflowStop = strStop;
```

## Passaggio 3: Creazione dell’attività &quot;Test&quot; {#step-3--creating-the--test--activity}

L’attività &quot;Test&quot; ti consente di determinare se una consegna deve essere inviata o se il flusso di lavoro di monitoraggio deve eseguire un altro ciclo in base all’attività &quot;Wait&quot; (Attendi) .

Viene inviata una consegna al supervisore **se almeno una delle tre variabili di evento &quot;vars.strWorkflowError&quot;, &quot;vars.strWorkflowPaused&quot; o &quot;vars.strWorkflowStop&quot; non è nulla.**

![](assets/uc_monitoring_workflow_test.png)

L’attività &quot;Wait&quot; può essere configurata per riavviare il flusso di lavoro di monitoraggio a intervalli regolari. Per questo caso d&#39;uso, **il tempo di attesa è impostato su un&#39;ora**.

![](assets/uc_monitoring_workflow_attente.png)

## Passaggio 4: Preparazione della consegna {#step-4--preparing-the-delivery}

L’attività &quot;Delivery&quot; è basata su un **modello di consegna** memorizzati in **Risorse > Modelli > Modelli di consegna** nodo.

Questo modello deve includere:

* **l&#39;indirizzo e-mail del supervisore**.
* **Contenuto HTML** per l’inserimento di testo personalizzato.

   ![](assets/uc_monitoring_workflow_variables_diffusion.png)

   Le tre variabili dichiarate (WF_Stop, WF_Paused, WF_Error) corrispondono alle tre variabili dell’evento del flusso di lavoro.

   Queste variabili devono essere dichiarate nella variabile **Variabili** scheda delle proprietà del modello di consegna.

   Per recuperare **il contenuto delle variabili dell’evento del flusso di lavoro**, devi dichiarare le variabili specifiche della consegna che verranno inizializzate con i valori restituiti dal codice JavaScript.

   Il modello di consegna ha il seguente contenuto:

   ![](assets/uc_monitoring_workflow_model_diffusion.png)

Una volta creato e approvato il modello, devi configurare il **Consegna** attività per:

* collega l’attività &quot;Consegna&quot; al modello di consegna creato in precedenza.
* collega le variabili evento del flusso di lavoro a quelle specifiche del modello di consegna.

Fai doppio clic sul pulsante **Consegna** e seleziona le seguenti opzioni:

* Consegna: select **Nuovo, creato da un modello**, quindi seleziona il modello di consegna creato in precedenza.
* Per **Destinatari e contenuti** campi, seleziona **Specificato nella consegna**.
* Azione da eseguire: select **Preparare e iniziare**.
* Deseleziona **Errori di processo** opzione .

   ![](assets/uc_monitoring_workflow_optionmodel.png)

* Vai a **Script** della scheda **Consegna** aggiungi tre attività **stringa di caratteri** digita le variabili tramite il menu del campo di personalizzazione.

   ![](assets/uc_monitoring_workflow_selectlinkvariables.png)

   ![](assets/uc_monitoring_workflow_linkvariables.png)

   Le tre variabili dichiarate sono:

   ```
   delivery.variables._var[0].stringValue = vars.strWorkflowError;
   delivery.variables._var[1].stringValue = vars.strWorkflowPaused;
   delivery.variables._var[2].stringValue = vars.strWorkflowStop; 
   ```

Una volta avviato il flusso di lavoro di monitoraggio, invia il seguente riepilogo al destinatario:

![](assets/uc_monitoring_workflow_mailfinal.png)
