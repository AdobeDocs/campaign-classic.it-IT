---
solution: Campaign Classic
product: campaign
title: Configurazione dell’integrazione
description: Configurazione dell’integrazione
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 2%

---


# Opzione pipeline NmsPipeline_Config {#nmspipeline_config}

Una volta che l&#39;autenticazione funziona, [!DNL pipelined] può recuperare gli eventi ed elaborarli. Elabora solo attivatori configurati in  Adobe Campaign, ignorando gli altri. Il trigger deve essere stato generato da Analytics e inviato in anticipo alla pipeline.
L&#39;opzione può essere configurata anche con un carattere jolly per intercettare tutti i trigger, indipendentemente dal nome.

La configurazione dei trigger viene eseguita in un&#39;opzione, in **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]**. Il nome dell&#39;opzione è **[!UICONTROL NmsPipeline_Config]**. Il tipo di dati è &quot;testo lungo&quot; in formato JSON.

Questo esempio specifica due attivatori.

Incollate il codice JSON da questo modello nel valore dell&#39;opzione. Assicurarsi di rimuovere i commenti.

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

Questo secondo esempio intercetta tutti i trigger.

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
>Il valore UID [!DNL Trigger] per un nome di attivatore specifico nell&#39;interfaccia di Analytics si trova come parte dei parametri della query URL nell&#39;interfaccia Triggers. L&#39;UID triggerType viene passato nel flusso di dati della pipeline e il codice può essere scritto nella pipeline.JS per mappare l&#39;UID trigger a un&#39;etichetta intuitiva che può essere memorizzata in una colonna Nome trigger nello schema pipelineEvents.

## Il parametro consumer {#consumer-parameter}

La tubazione funziona con un modello &quot;fornitore e consumatore&quot;. Ci possono essere molti consumatori sulla stessa coda. I messaggi vengono &quot;consumati&quot; solo per un singolo consumatore. Ogni consumatore riceve la propria &quot;copia&quot; dei messaggi.

Il parametro &quot;consumer&quot; identifica l’istanza come uno di questi consumatori. È l&#39;identità dell&#39;istanza che chiama la pipeline. Potete riempirlo con il nome dell’istanza. Il servizio pipeline tiene traccia dei messaggi recuperati da ogni consumatore. L&#39;utilizzo di consumatori diversi per istanze diverse garantisce che ogni messaggio venga inviato a ogni istanza.

## Come configurare l&#39;opzione pipeline {#configure-pipeline-option}

Aggiungere o modificare  attivatori di Experience Cloud nell&#39;array &quot;triggers&quot;; non modificare il resto.
Assicurati che il JSON sia valido con l&#39;aiuto di questo [sito Web](http://jsonlint.com/).

* &quot;name&quot; è l&#39;ID attivatore. Un carattere jolly &quot;*&quot; rileva tutti i trigger.
* &quot;Consumer&quot; è una qualsiasi stringa univoca che identifica in modo univoco l&#39;istanza nlserver. In genere può essere il nome dell&#39;istanza stesso. Per più ambienti (dev/stage/prod), accertatevi che sia univoco per ciascuno di essi in modo che ogni istanza ottenga una copia del messaggio.
* [!DNL Pipelined] supporta anche l&#39;argomento &quot;alias&quot;.

Riavviate [!DNL pipelined] dopo aver apportato le modifiche.
