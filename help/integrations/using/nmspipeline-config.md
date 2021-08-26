---
product: campaign
title: Configurazione dell’integrazione
description: Configurazione dell’integrazione
audience: integrations
content-type: reference
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 2%

---


# Opzione pipeline NmsPipeline_Config {#nmspipeline_config}

![](../../assets/common.svg)

Una volta che l&#39;autenticazione funziona, [!DNL pipelined] può recuperare gli eventi ed elaborarli. Elabora solo gli attivatori configurati in Adobe Campaign, ignorando gli altri. Il trigger deve essere stato generato da Analytics e inviato in anticipo alla pipeline.
Puoi anche configurare l’opzione con un carattere jolly per individuare tutti i trigger, indipendentemente dal nome.

La configurazione dei trigger viene eseguita in un’opzione, in **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]**. Il nome dell’opzione è **[!UICONTROL NmsPipeline_Config]**. Il tipo di dati è &quot;testo lungo&quot; in formato JSON.

Questo esempio specifica due attivatori.

Incolla il codice JSON da questo modello nel valore dell’opzione . Assicurati di rimuovere i commenti.

```
{
    "topics": [ // list of "topics" that the pipelined is listening to.
        {
            "name": "triggers", // Name of the first topic: triggers.
            "consumer": "customer_dev", // Name of the instance that listens. 
            "triggers": [ // Array of triggers. 
                {
                    "name": "3e8a2ba7-fccc-49bb-bdac-33ee33cf02bf", // TriggerType ID from Analytics 
                    "jsConnector": "cus:triggers.js" // Javascript library holding the processing function.
                }, {
                    "name": "2da3fdff-13af-4c51-8ed0-05802a572e94", // Second TriggerType ID 
                    "jsConnector": "cus:triggers.js" // Can use the same JS for all.
                },
            ]
        }
    ]
}
```

Questo secondo esempio cattura tutti i trigger.

```
{
 "topics": [
    {
      "name": "triggers",
      "consumer":  "customer_dev",
      "triggers": [
        {
          "name": "*",
          "jsConnector": "cus:pipeline.js"
        }
      ]
    }
 ]
 }
```

>[!NOTE]
>
>Il valore UID [!DNL Trigger] di un nome di trigger specifico nell’interfaccia di Analytics si trova come parte dei parametri della stringa di query URL nell’interfaccia Triggers. L’UID triggerType viene passato nel flusso di dati della pipeline e il codice può essere scritto in pipeline.JS per mappare l’UID trigger su un’etichetta semplice da usare che può essere memorizzata in una colonna Trigger Name nello schema pipelineEvents.

## Il parametro consumer {#consumer-parameter}

La pipeline funziona con un modello &quot;fornitore e consumatore&quot;. Ci possono essere molti consumatori sulla stessa coda. I messaggi vengono &quot;consumati&quot; solo per un singolo consumatore. Ogni consumatore ottiene la propria &quot;copia&quot; dei messaggi.

Il parametro &quot;consumer&quot; identifica l’istanza come uno di questi consumatori. È l’identità dell’istanza che chiama la pipeline. Puoi riempirlo con il nome dell’istanza. Il servizio pipeline tiene traccia dei messaggi recuperati da ogni consumatore. Se utilizzi consumatori diversi per istanze diverse, ogni messaggio viene inviato a ogni istanza.

## Come configurare l’opzione Pipeline {#configure-pipeline-option}

Aggiungere o modificare attivatori di Experience Cloud sotto l&#39;array &quot;triggers&quot;; non modificare il resto.
Assicurati che il JSON sia valido con l&#39;aiuto di questo [sito web](http://jsonlint.com/).

* &quot;name&quot; è l&#39;ID trigger. Un carattere jolly &quot;*&quot; cattura tutti i trigger.
* &quot;Consumer&quot; è una stringa univoca che identifica in modo univoco l&#39;istanza nlserver. Di solito può essere il nome dell&#39;istanza stessa. Per più ambienti (dev/stage/prod), assicurati che sia univoco per ciascuno di essi in modo che ogni istanza ottenga una copia del messaggio.
* [!DNL Pipelined] supporta anche l’argomento &quot;alias&quot;.

Riavvia [!DNL pipelined] dopo aver apportato modifiche.
