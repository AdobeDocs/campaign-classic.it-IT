---
product: campaign
title: Estrazione dati (file)
description: Ulteriori informazioni sull’attività del flusso di lavoro Estrazione dati (file)
feature: Workflows, Data Management Activity
exl-id: 06eafedd-6386-498f-a80d-7f57ddcccad6
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 1%

---

# Estrazione dati (file){#extraction-file}

![](../../assets/common.svg)

Puoi estrarre dati da una tabella di un flusso di lavoro in un file esterno utilizzando **[!UICONTROL Data extraction (file)]** attività.

>[!CAUTION]
>
>Questa attività deve sempre avere una transizione in entrata contenente i dati da estrarre.

Per configurare l’estrazione dei dati, esegui i seguenti passaggi:

1. Specifica il nome del file di output: questo nome può contenere variabili, inserito tramite il pulsante di personalizzazione a destra del campo .
1. Fai clic su **[!UICONTROL Edit the file format...]** per selezionare i dati da estrarre.

   ![](assets/s_advuser_extract_file_param.png)

   La **[!UICONTROL Handle groupings (GROUP BY + HAVING)]** l’opzione aggiunge un passaggio aggiuntivo per filtrare il risultato finale dell’aggregato, ad esempio per un determinato tipo di ordine di acquisto, per i clienti che hanno ordinato più di 10 volte, ecc.

1. Se necessario, è possibile aggiungere nuove colonne al file di output, ad esempio i risultati di elaborazione o elaborazione. A questo scopo, fai clic sul pulsante **[!UICONTROL Add]** icona.

   ![](assets/s_advuser_extract_file_add_col.png)

   Nella riga aggiuntiva, fai clic sul pulsante **[!UICONTROL Edit expression]** per definire il contenuto della nuova colonna.

   ![](assets/s_advuser_extract_file_add_exp.png)

   Accedi quindi alla finestra di selezione. Fai clic su **[!UICONTROL Advanced selection]** per scegliere il processo da applicare ai dati.

   ![](assets/s_advuser_extract_file_advanced_selection.png)

   Scegliere la formula desiderata dall&#39;elenco.

   ![](assets/s_advuser_extract_file_agregate_values.png)

Puoi definire un post-processo da eseguire durante l’estrazione dei dati, consentendoti di comprimere o crittografare i file. A questo scopo, è necessario aggiungere il comando desiderato nel **[!UICONTROL Script]** scheda dell’attività.

Per ulteriori informazioni, consulta questa sezione: [ZIP o cifratura di un file](how-to-use-workflow-data.md#zipping-or-encrypting-a-file).

![](assets/postprocessing_dataextraction.png)

## Elenco delle funzioni aggregate {#list-of-aggregate-functions}

Di seguito è riportato un elenco delle funzioni di aggregazione disponibili:

* **[!UICONTROL Count]** per contare tutti i valori non nulli del campo da aggregare, compresi i valori duplicati (del campo aggregato),

   **[!UICONTROL Distinct]** per contare il numero totale di valori diversi e non nulli del campo da aggregare (i valori duplicati sono esclusi prima del calcolo),

* **[!UICONTROL Sum]** per calcolare la somma dei valori di un campo numerico,
* **[!UICONTROL Minimum value]** calcolare i valori minimi di un campo (numerico o di altro tipo),
* **[!UICONTROL Maximum value]** per calcolare i valori massimi di un campo (numerico o di altro tipo),
* **[!UICONTROL Average]** calcolare la media dei valori di un campo numerico.
