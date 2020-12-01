---
solution: Campaign Classic
product: campaign
title: Consegna continua
description: Consegna continua
audience: workflow
content-type: reference
topic-tags: action-activities
translation-type: tm+mt
source-git-commit: 20dcdd91d71158bc373db68c3f61f6808b240bd2
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 4%

---


# Consegna continua{#continuous-delivery}

Un&#39;azione di tipo **Consegna continua** consente di aggiungere nuovi destinatari a una consegna esistente. Questo tipo di consegna evita di dover creare una nuova consegna ogni volta: Questa modalità è spesso più efficiente, in particolare per gli avvisi di volume ridotto o le notifiche inviate come e quando necessario.

![](assets/do-not-localize/how-to-video.png) [Scopri questa funzione nel video](#continuous-delivery-video)

A livello di modello di consegna, potete specificare uno script per calcolare l&#39;etichetta (e la cartella della campagna) della consegna associata. Se lo script calcola una consegna che non esiste ancora, viene creata immediatamente.

![](assets/edit_diffusion_fil.png)

L&#39;opzione **[!UICONTROL Process errors]** visualizza una transizione particolare che verrà attivata se viene generato un errore. In questo caso, il flusso di lavoro non passa alla modalità di errore e continua con l&#39;esecuzione.

Gli errori presi in considerazione sono errori del file system (file non può essere spostato, directory non è stato accessibile, ecc.).

Questa opzione non elabora gli errori relativi alla configurazione dell&#39;attività, ovvero i valori non validi.

## Parametri di input {#input-parameters}

* tableName
* schema

Ogni evento in ingresso deve specificare una destinazione definita da questi parametri.

Solo quando l&#39;opzione **[!UICONTROL Specified by the inbound event]** è selezionata.

## Parametri di output {#output-parameters}

* tableName
* schema
* recCount

Questo insieme di tre valori identifica il target risultante dalla consegna al volo. **[!UICONTROL tableName]** è il nome della tabella che memorizza gli identificatori del target,  **[!UICONTROL schema]** è lo schema della popolazione (in genere nms:destinatario) ed  **[!UICONTROL recCount]** è il numero di elementi nella tabella.

La transizione associata al complemento ha gli stessi parametri.

## Come impostare una consegna continua

In questa sezione viene illustrato come impostare una consegna continua.

La **consegna continua** consente di aggiungere nuovi destinatari a una consegna esistente ed evita di dover creare una nuova consegna ogni volta che viene aggiunto un nuovo destinatario. Potete aggiornare il creativo direttamente nel flusso di lavoro della campagna e il modello verrà aggiornato nella cartella delle risorse del modello di consegna.

Una consegna continua creerà un singolo log di consegna e consegna (wideLog) e registri di tracciamento che fanno riferimento al fatto che una consegna viene aggiunta ogni volta che viene eseguita.

![Consegna continua](assets/delivery_continuous.jpg)

## Video di esercitazione {#continuous-delivery-video}

Questo video mostra come configurare una consegna continua con una query incrementale.

>[!VIDEO](https://video.tv.adobe.com/v/25039?quality=12)

Ulteriori video dimostrativi sui Campaign Classic sono disponibili [qui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html).