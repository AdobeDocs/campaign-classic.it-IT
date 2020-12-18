---
solution: Campaign Classic
product: campaign
title: Estrazione dati (file)
description: Ulteriori informazioni sull'attività del flusso di lavoro di estrazione dei dati (file)
audience: workflow
content-type: reference
topic-tags: action-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 1%

---


# Estrazione dati (file){#extraction-file}

È possibile estrarre dati da una tabella di workflow in un file esterno utilizzando l&#39;attività **[!UICONTROL Data extraction (file)]**.

>[!CAUTION]
>
>Questa attività deve sempre avere una transizione in entrata che contenga i dati da estrarre.

Per configurare l&#39;estrazione dei dati, effettua i seguenti passaggi:

1. Specificate il nome del file di output: questo nome può contenere variabili, inserite tramite il pulsante di personalizzazione a destra del campo.
1. Fare clic su **[!UICONTROL Edit the file format...]** per selezionare i dati da estrarre.

   ![](assets/s_advuser_extract_file_param.png)

   L&#39;opzione **[!UICONTROL Handle groupings (GROUP BY + HAVING)]** aggiunge un passaggio aggiuntivo per filtrare il risultato finale dell&#39;aggregazione, ad esempio per un determinato tipo di ordine di acquisto, per i clienti che hanno ordinato più di 10 volte e così via.

1. Se necessario, è possibile aggiungere nuove colonne al file di output, ad esempio calcoli o risultati di elaborazione. A tale scopo, fare clic sull&#39;icona **[!UICONTROL Add]**.

   ![](assets/s_advuser_extract_file_add_col.png)

   Nella riga aggiuntiva, fate clic sull&#39;icona **[!UICONTROL Edit expression]** per definire il contenuto della nuova colonna.

   ![](assets/s_advuser_extract_file_add_exp.png)

   Potrete quindi accedere alla finestra di selezione. Fare clic su **[!UICONTROL Advanced selection]** per scegliere il processo da applicare ai dati.

   ![](assets/s_advuser_extract_file_advanced_selection.png)

   Scegliere la formula desiderata dall&#39;elenco.

   ![](assets/s_advuser_extract_file_agregate_values.png)

È possibile definire un post-processo da eseguire durante l&#39;estrazione dei dati, consentendo di comprimere o cifrare i file. A questo scopo, il comando desiderato deve essere aggiunto nella scheda **[!UICONTROL Script]** dell&#39;attività.

Per ulteriori informazioni, consulta questa sezione: [Zipping o cifratura di un file](../../workflow/using/how-to-use-workflow-data.md#zipping-or-encrypting-a-file).

![](assets/postprocessing_dataextraction.png)

## Elenco di funzioni aggregate {#list-of-aggregate-functions}

Di seguito è riportato un elenco delle funzioni di aggregazione disponibili:

* **[!UICONTROL Count]** per contare tutti i valori non-null del campo da aggregare, compresi i valori duplicati (del campo aggregato),

   **[!UICONTROL Distinct]** per calcolare il numero totale di valori diversi e non-null del campo da aggregare (i valori duplicati sono esclusi prima del calcolo),

* **[!UICONTROL Sum]** per calcolare la somma dei valori di un campo numerico,
* **[!UICONTROL Minimum value]** per calcolare i valori minimi di un campo (numerici o di altro tipo),
* **[!UICONTROL Maximum value]** per calcolare i valori massimi di un campo (numerici o di altro tipo),
* **[!UICONTROL Average]** per calcolare la media dei valori di un campo numerico.

