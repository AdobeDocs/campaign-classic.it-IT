---
product: campaign
title: Esclusione
description: Ulteriori informazioni sull’attività del flusso di lavoro Esclusione
audience: workflow
content-type: reference
topic-tags: targeting-activities
exl-id: f4fe97d9-6571-4aa5-8022-b0af9d5a6a13
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# Esclusione{#exclusion}

Un&#39;attività di tipo **Esclusione** crea un target basato su un target principale da cui vengono estratti uno o più altri target.

Per configurare questa attività, immetti la relativa etichetta e seleziona il set di destinatari principale: la popolazione del set principale consente di creare il risultato. I profili condivisi dal set principale e almeno una delle attività di accesso saranno esclusi.

![](assets/s_user_segmentation_exclu.png)

>[!NOTE]
>
>Per ulteriori informazioni sulla configurazione e l’utilizzo dell’attività di esclusione, consulta [Esclusione di una popolazione (Esclusione)](../../workflow/using/targeting-data.md#excluding-a-population--exclusion-).

Se desideri sfruttare la popolazione rimanente, seleziona l’opzione **[!UICONTROL Generate complement]** . Il complemento conterrà la popolazione in entrata principale meno la popolazione in uscita. All’attività verrà quindi aggiunta una transizione di output aggiuntiva, come segue:

![](assets/s_user_segmentation_exclu_compl.png)

## Esempi di esclusione {#exclusion-examples}

L&#39;esempio seguente cerca di compilare un elenco di destinatari di età compresa tra i 18 e i 30 anni, escludendo i residenti di Parigi.

1. Inserisci e apri un&#39;attività di tipo **[!UICONTROL Exclusion]** dopo due query. La prima query esegue il targeting dei destinatari che vivono a Parigi. La seconda query riguarda i 18-30 anni.
1. Inserire il set principale. Qui il set principale è la query **18-30 anni** . Gli elementi relativi al secondo gruppo saranno esclusi dal risultato finale.
1. Seleziona l’opzione **[!UICONTROL Generate complement]** se desideri sfruttare i dati che rimangono dopo l’esclusione. In questo caso, il complemento è costituito da beneficiari di età compresa tra i 18 e i 30 anni che vivono a Parigi.
1. Approva la configurazione di esclusione, quindi inserisci un’attività di aggiornamento elenco al risultato. È inoltre possibile inserire un aggiornamento dell’elenco aggiuntivo per il complemento, se necessario.
1. Esegui il flusso di lavoro. In questo esempio, il risultato è composto da beneficiari di età compresa tra i 18 e i 30 anni, ma quelli che vivono a Parigi sono esclusi e inviati al complemento.

   ![](assets/exclusion_example.png)

## Parametri di input {#input-parameters}

* tableName
* schema

Ogni evento in entrata deve specificare un target definito da questi parametri.

## Parametri di output {#output-parameters}

* tableName
* schema
* recCount

Questo insieme di tre valori identifica il target risultante dall’esclusione. **[!UICONTROL tableName]** è il nome della tabella che registra gli identificatori di destinazione,  **[!UICONTROL schema]** è lo schema del gruppo (in genere nms:recipient) ed  **[!UICONTROL recCount]** è il numero di elementi della tabella.

La transizione associata al complemento ha gli stessi parametri.
