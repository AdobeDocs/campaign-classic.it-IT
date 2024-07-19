---
product: campaign
title: Opzione pipeline NmsPipeline_Config
description: Opzione pipeline NmsPipeline_Config
feature: Triggers
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
audience: integrations
content-type: reference
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---


# Opzione pipeline NmsPipeline_Config {#nmspipeline_config}



Una volta completata l&#39;autenticazione, [!DNL pipelined] può recuperare gli eventi ed elaborarli. Elabora solo i trigger configurati in Adobe Campaign, ignorando gli altri. Il trigger deve essere stato generato da Analytics e inviato in precedenza alla pipeline.
È inoltre possibile configurare l’opzione con un carattere jolly per acquisire tutti i trigger, indipendentemente dal nome.

La configurazione dei trigger viene eseguita in un&#39;opzione, in **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]**. Nome opzione: **[!UICONTROL NmsPipeline_Config]**. Il tipo di dati è &quot;testo lungo&quot; in formato JSON.

Questo esempio specifica due trigger.

Incolla il codice JSON da questo modello nel valore dell’opzione. Assicurati di rimuovere i commenti.

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

Questo secondo esempio rileva tutti i trigger.

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
>Il valore UID [!DNL Trigger] per un nome trigger specifico nell&#39;interfaccia di Analytics può essere trovato come parte dei parametri querystring dell&#39;URL nell&#39;interfaccia Triggers. L’UID triggerType viene passato nel flusso di dati della pipeline e il codice può essere scritto nel file pipeline.JS per mappare l’UID del trigger a un’etichetta intuitiva che può essere memorizzata in una colonna Nome trigger nello schema pipelineEvents.

## Il parametro consumer {#consumer-parameter}

La pipeline funziona con un modello &quot;fornitore e consumatore&quot;. Ci possono essere molti consumatori nella stessa coda. I messaggi vengono &quot;utilizzati&quot; solo per un singolo consumatore. Ogni consumatore riceve la propria &quot;copia&quot; dei messaggi.

Il parametro &quot;consumer&quot; identifica l’istanza come uno di questi consumatori. È l’identità dell’istanza che chiama la pipeline. Potete riempirlo con il nome dell&#39;istanza. Il servizio pipeline tiene traccia dei messaggi recuperati da ciascun consumatore. L’utilizzo di consumer diversi per istanze diverse garantisce che ogni messaggio venga inviato a ogni istanza.

## Come configurare l’opzione Pipeline {#configure-pipeline-option}

Aggiungi o modifica i trigger di Experience Cloud sotto l’array &quot;triggers&quot;; non modificare gli altri.
Verifica che il JSON sia valido con l&#39;aiuto di questo [sito Web](https://jsonlint.com/).

* &quot;name&quot; è l&#39;ID del trigger. Un carattere jolly &quot;*&quot; acquisisce tutti i trigger.
* &quot;Consumer&quot; è una stringa univoca che identifica in modo univoco l’istanza nlserver. In genere può essere il nome dell’istanza stessa. Per più ambienti (dev/stage/prod), assicurati che sia univoco per ciascuno di essi, in modo che ogni istanza riceva una copia del messaggio.
* [!DNL Pipelined] supporta anche l&#39;argomento &quot;alias&quot;.

Riavvia [!DNL pipelined] dopo aver apportato modifiche.
