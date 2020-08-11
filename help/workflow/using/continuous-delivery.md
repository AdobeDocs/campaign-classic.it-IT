---
title: Consegna continua
seo-title: Consegna continua
description: Consegna continua
seo-description: null
page-status-flag: never-activated
uuid: af8b4582-299e-47f9-9819-987b35db94ab
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 9d80be19-8dde-4278-ab5f-23f364fe422e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 3566f42b92cc1b7280bf9b6e9e0b4da7a54f61db
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---


# Consegna continua{#continuous-delivery}

Un&#39;azione per il tipo di consegna **** continua consente di aggiungere nuovi destinatari a una consegna esistente. Questo tipo di consegna evita di dover creare una nuova consegna ogni volta: Questa modalità è spesso più efficiente, in particolare per gli avvisi di volume ridotto o le notifiche inviate come e quando necessario. A livello di modello di consegna, potete specificare uno script per calcolare l&#39;etichetta (e la cartella della campagna) della consegna associata. Se lo script calcola una consegna che non esiste ancora, viene creata immediatamente.

![](assets/edit_diffusion_fil.png)

L&#39; **[!UICONTROL Process errors]** opzione visualizza una transizione specifica che verrà attivata se viene generato un errore. In questo caso, il flusso di lavoro non passa alla modalità di errore e continua con l&#39;esecuzione.

Gli errori presi in considerazione sono errori del file system (file non può essere spostato, directory non è stato accessibile, ecc.).

Questa opzione non elabora gli errori relativi alla configurazione dell&#39;attività, ovvero i valori non validi.

## Parametri di input {#input-parameters}

* tableName
* schema

Ogni evento in ingresso deve specificare una destinazione definita da questi parametri.

Solo quando l’ **[!UICONTROL Specified by the inbound event]** opzione è selezionata.

## Parametri di output {#output-parameters}

* tableName
* schema
* recCount

Questo insieme di tre valori identifica il target risultante dalla consegna al volo. **[!UICONTROL tableName]** è il nome della tabella che memorizza gli identificatori del target, **[!UICONTROL schema]** è lo schema della popolazione (in genere nms:destinatario) ed **[!UICONTROL recCount]** è il numero di elementi nella tabella.

La transizione associata al complemento ha gli stessi parametri.

## Come impostare una consegna continua

In questa sezione viene illustrato come impostare una consegna continua.

La consegna **** continua consente di aggiungere nuovi destinatari a una consegna esistente ed evita di dover creare una nuova consegna ogni volta che viene aggiunto un nuovo destinatario. Potete aggiornare il creativo direttamente nel flusso di lavoro della campagna e il modello verrà aggiornato nella cartella delle risorse del modello di consegna.

Una consegna continua creerà un singolo log di consegna e consegna (wideLog) e registri di tracciamento che fanno riferimento al fatto che una consegna viene aggiunta ogni volta che viene eseguita.

![Consegna continua](assets/delivery_continuous.jpg)

Questo video mostra come configurare una consegna continua con una query incrementale.

>[!VIDEO](https://video.tv.adobe.com/v/25039?quality=12)
