---
solution: Campaign Classic
product: campaign
title: Supervisione dei flussi di lavoro
description: Scopri come supervisionare i flussi di lavoro di Campaign
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 11ff62238a8fb73658f2263c25dbeb27d2e0fb23
workflow-type: tm+mt
source-wordcount: '646'
ht-degree: 0%

---


# Caso di utilizzo: supervisiona i tuoi flussi di lavoro{#supervising-workflows}

Questo caso d’uso descrive la creazione di un flusso di lavoro che consente di monitorare lo stato di un set di flussi di lavoro che vengono &quot;messi in pausa&quot;, &quot;interrotti&quot; o &quot;con errori&quot;.

Il suo scopo è:

* Utilizza un flusso di lavoro per monitorare un gruppo di flussi di lavoro aziendali.
* Invia un messaggio a un supervisore tramite un&#39;attività di &quot;consegna&quot;.

Per monitorare lo stato di un set di flussi di lavoro, è necessario seguire questi passaggi:

1. Crea il flusso di lavoro di monitoraggio.
1. Scrivi il JavaScript per determinare se i flussi di lavoro vengono messi in pausa, interrotti o con errori.
1. Crea l’attività **[!UICONTROL Test]** .
1. Prepara il modello di consegna.

>[!NOTE]
>
>Oltre al flusso di lavoro, Campaign **Workflow Heatmap** ti consente di analizzare in dettaglio i flussi di lavoro attualmente in esecuzione. Per ulteriori informazioni, consulta la sezione [dedicata](../../workflow/using/heatmap.md).
>
>Per ulteriori informazioni su come **monitorare l&#39;esecuzione dei flussi di lavoro**, consulta [questa sezione](../../workflow/using/monitoring-workflow-execution.md).

## Passaggio 1: Creazione del flusso di lavoro di monitoraggio {#step-1--creating-the-monitoring-workflow}

La cartella del flusso di lavoro che stiamo per monitorare è la cartella **&quot;CustomWorkflows&quot;** memorizzata nel nodo **Amministrazione > Produzione > Flussi di lavoro tecnici**. Questa cartella contiene un set di flussi di lavoro aziendali.

Il **flusso di lavoro di monitoraggio** viene memorizzato nella directory principale della cartella Flussi di lavoro tecnici. L&#39;etichetta utilizzata è **&quot;Monitoring&quot;**.

Lo schema seguente mostra la sequenza di attività:

![](assets/uc_monitoring_workflow_overview.png)

Questo flusso di lavoro è costituito da:

* un&#39;attività **&quot;Start&quot;**.
* un&#39;attività **&quot;JavaScript code&quot;** responsabile dell&#39;analisi della cartella dei flussi di lavoro aziendali.
* un&#39;attività **&quot;Test&quot;** per inviare una consegna al supervisore o riavviare il flusso di lavoro.
* un&#39;attività **&quot;Delivery&quot;** responsabile del layout dei messaggi.
* un&#39;attività **&quot;Wait&quot;** che controlla i lead time tra le iterazioni del flusso di lavoro.

## Passaggio 2: Scrittura di JavaScript {#step-2--writing-the-javascript}

La prima parte del codice JavaScript coincide con una **query (queryDef)** che consente di identificare i flussi di lavoro con uno stato di &quot;pausa&quot; (@state == 13), &quot;error&quot; (@failed == 1) o &quot;stop&quot; (@state == 20).

Il **nome interno** della cartella del flusso di lavoro da monitorare è indicato nella seguente condizione:

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

La seconda parte del codice JavaScript ti consente di **visualizzare un messaggio per ogni flusso di lavoro** in base allo stato recuperato durante la query.

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

## Passaggio 3: Creazione dell&#39;attività &quot;Test&quot; {#step-3--creating-the--test--activity}

L’attività &quot;Test&quot; ti consente di determinare se una consegna deve essere inviata o se il flusso di lavoro di monitoraggio deve eseguire un altro ciclo in base all’attività &quot;Wait&quot; (Attendi) .

Una consegna viene inviata al supervisore **se almeno una delle tre variabili di evento &quot;vars.strWorkflowError&quot;, &quot;vars.strWorkflowPaused&quot; o &quot;vars.strWorkflowStop&quot; non è nulla.**

![](assets/uc_monitoring_workflow_test.png)

L’attività &quot;Wait&quot; può essere configurata per riavviare il flusso di lavoro di monitoraggio a intervalli regolari. Per questo caso d&#39;uso, **il tempo di attesa è impostato su un&#39;ora**.

![](assets/uc_monitoring_workflow_attente.png)

## Passaggio 4: Preparazione della consegna {#step-4--preparing-the-delivery}

L&#39;attività &quot;Delivery&quot; è basata su un **modello di consegna** memorizzato nel nodo **Risorse > Modelli > Modelli di consegna** .

Questo modello deve includere:

* **l&#39;indirizzo e-mail del supervisore**.
* **Contenuto HTML** per l’inserimento di testo personalizzato.

   ![](assets/uc_monitoring_workflow_variables_diffusion.png)

   Le tre variabili dichiarate (WF_Stop, WF_Paused, WF_Error) corrispondono alle tre variabili dell’evento del flusso di lavoro.

   Queste variabili devono essere dichiarate nella scheda **Variabili** delle proprietà del modello di consegna.

   Per recuperare **il contenuto delle variabili dell&#39;evento del flusso di lavoro**, è necessario dichiarare le variabili specifiche della consegna che verranno inizializzate con i valori restituiti dal codice JavaScript.

   Il modello di consegna ha il seguente contenuto:

   ![](assets/uc_monitoring_workflow_model_diffusion.png)

Una volta creato e approvato il modello, devi configurare l&#39;attività **Delivery** per:

* collega l’attività &quot;Consegna&quot; al modello di consegna creato in precedenza.
* collega le variabili evento del flusso di lavoro a quelle specifiche del modello di consegna.

Fai doppio clic sull&#39;attività **Consegna** e seleziona le seguenti opzioni:

* Consegna: seleziona **Nuovo, creato da un modello**, quindi seleziona il modello di consegna creato in precedenza.
* Per i campi **Destinatari e Contenuto**, seleziona **Specificato nella consegna**.
* Azione da eseguire: selezionare **Prepare and start**.
* Deseleziona l&#39;opzione **Elabora errori** .

   ![](assets/uc_monitoring_workflow_optionmodel.png)

* Vai alla scheda **Script** dell&#39;attività **Consegna** e aggiungi tre variabili di tipo **stringa di caratteri** tramite il menu del campo di personalizzazione.

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

