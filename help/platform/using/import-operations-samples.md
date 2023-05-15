---
product: campaign
title: Esempi di importazione generica
description: Ulteriori informazioni sulle importazioni generiche eseguibili tramite i processi di importazione
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 4582b524-2b6d-484c-bace-29d2e69f60e9
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '995'
ht-degree: 1%

---

# Esempi di importazione generica {#import-operations-samples}



## Importa da un elenco di destinatari {#example--import-from-a-list-of-recipients}

Per creare e fornire un elenco di destinatari dalla panoramica degli elenchi, effettua le seguenti operazioni:

1. Creazione dell’elenco

   * Fai clic sul pulsante **[!UICONTROL Lists]** nel collegamento **[!UICONTROL Profiles and targets]** menu della home page di Adobe Campaign.
   * Fai clic sul pulsante **[!UICONTROL Create]** e poi **[!UICONTROL Import a list]** pulsante .

1. Selezione del file da importare

   Fai clic sulla cartella a destra del **[!UICONTROL Local file]** e selezionare il file contenente l’elenco da importare.

   ![](assets/s_ncs_user_import_example00_01.png)

1. Nome elenco e archiviazione

   Immettere il nome dell&#39;elenco e selezionare la directory in cui salvare.

   ![](assets/s_ncs_user_import_example00_02.png)

1. Avvio dell’importazione

   Fai clic su **[!UICONTROL Next]** e poi **[!UICONTROL Start]** per iniziare a importare l’elenco.

   ![](assets/s_ncs_user_import_example00_03.png)

## Importare nuovi record da un file di testo {#example--import-new-records-from-a-text-file-}

Per importare nel database Adobe Campaign i nuovi profili dei destinatari memorizzati in un file di testo, procedi come segue:

1. Scelta di un modello

   * Dalla home page di Adobe Campaign, fai clic sul pulsante **[!UICONTROL Profiles and targets]** link, quindi **[!UICONTROL Jobs]**. Sopra l’elenco dei processi, fai clic su **[!UICONTROL New import]**.
   * Mantieni la **[!UICONTROL New text import]** modello selezionato per impostazione predefinita.
   * Modifica l’etichetta e la descrizione.
   * Seleziona **[!UICONTROL Simple import]**.
   * Mantenere la cartella di lavoro predefinita.
   * Fai clic su **[!UICONTROL Advanced parameters]** e seleziona la **[!UICONTROL Tracking mode]** per visualizzare i dettagli dell’importazione durante l’esecuzione.

1. Selezione del file da importare

   Fai clic sulla cartella a destra del **[!UICONTROL Local file]** e selezionare il file da importare.

   ![](assets/s_ncs_user_import_example01_01.png)

1. Associazione dei campi

   Fai clic sul pulsante **[!UICONTROL Guess the destination fields]** per mappare automaticamente gli schemi di origine e di destinazione. Controlla le informazioni in questa finestra prima di fare clic su **[!UICONTROL Next]**.

   ![](assets/s_ncs_user_import_example03_01.png)

1. Attività Reconciliation

   * Vai a **Destinatari (nms:recipient)** tabella.
   * Seleziona la **[!UICONTROL Insertion]** lasciare i valori predefiniti negli altri campi.

      ![](assets/s_ncs_user_import_example04_01.png)

1. Importazione dei destinatari

   * Se necessario, specifica una cartella in cui importare i record.

      ![](assets/s_ncs_user_import_example05_01.png)

1. Avvio dell’importazione

   * Fai clic su **[!UICONTROL Start]**.

      Nell’area centrale dell’editor, puoi verificare che l’operazione di importazione sia riuscita e visualizzare il numero di record elaborati.

      ![](assets/s_ncs_user_import_example06_01.png)

      La **[!UICONTROL Tracking]** consente di tenere traccia dei dettagli dell’importazione per ogni record del file di origine. A questo scopo, dalla home page fai clic su **[!UICONTROL Profiles and Targets]** then **[!UICONTROL Processes]**, seleziona l’importazione rilevante e cerca il **[!UICONTROL General]**, **[!UICONTROL Journal]** e **[!UICONTROL Rejects]** schede.

      * Verifica dell&#39;avanzamento dell&#39;importazione

         ![](assets/s_ncs_user_import_example07_01.png)

      * Visualizzazione del processo per ogni record

         ![](assets/s_ncs_user_import_example07_02.png)

## Aggiornare e inserire i destinatari {#example--update-and-insert-recipients}

Vogliamo aggiornare i record esistenti nel database e crearne di nuovi da un file di testo. Esempio di procedura:

1. Scelta di un modello

   Ripetere i passaggi descritti nell&#39;esempio 2 precedente.

1. File da importare

   Selezionare il file da importare.

   Nel nostro esempio, la panoramica delle prime righe del file mostra che il file contiene aggiornamenti per tre record e la creazione di un record.

   ![](assets/s_ncs_user_import_example02_02.png)

1. Associazione dei campi

   Applicare la procedura di cui all&#39;esempio 2 precedente.

1. Attività Reconciliation

   * Mantieni **[!UICONTROL Update or insert]** selezionato per impostazione predefinita.
   * Mantieni l’opzione **[!UICONTROL Management of duplicates]** in **[!UICONTROL Update]** in modo che i record esistenti nel database vengano modificati con i dati del file di testo.
   * Selezionare i campi **[!UICONTROL Birth date]**, **[!UICONTROL Name]** e **[!UICONTROL Company]** e assegna loro una chiave di riconciliazione.

      ![](assets/s_ncs_user_import_example04_02.png)

1. Avvio dell’importazione

   * Fai clic su **[!UICONTROL Start]**.

      Nella finestra di tracciamento, puoi verificare che l’importazione sia riuscita e visualizzare il numero di record elaborati.

      ![](assets/s_ncs_user_import_example06_02.png)

   * Consultare la tabella dei destinatari per verificare che i record siano stati modificati da questa operazione.

      ![](assets/s_ncs_user_import_example06_03.png)

## Arricchisci i valori con quelli di un file esterno {#example--enrich-the-values-with-those-of-an-external-file}

Vogliamo modificare alcuni campi di una tabella di database da un file di testo, dando priorità ai valori contenuti nel database.

In questo esempio, è possibile vedere che alcuni campi nel file di testo hanno un valore, mentre i campi corrispondenti nel database sono vuoti. Altri campi contengono un valore diverso da quello contenuto nel database.

* Contenuto del file di testo da importare.

   ![](assets/s_ncs_user_import_example02_03.png)

* Stato del database prima dell&#39;importazione

   ![](assets/s_ncs_user_import_example06_04.png)

Applica i seguenti passaggi:

1. Scelta di un modello

   Applicare la procedura di cui all&#39;esempio 2 precedente.

1. File da importare

   Selezionare il file da importare.

1. Associazione dei campi

   Applicare la procedura di cui all&#39;esempio 2 precedente.

   Nell&#39;anteprima delle prime righe del file, puoi vedere che il file contiene aggiornamenti per alcuni record.

1. Attività Reconciliation

   * Vai alla tabella e seleziona la **[!UICONTROL Update]** funzionamento.
   * Seleziona l’opzione **[!UICONTROL Reject entity]** per **[!UICONTROL Management of doubles]** campo .
   * Mantieni l’opzione **[!UICONTROL Management of duplicates]** in **[!UICONTROL Update]** in modo che i record esistenti nel database vengano modificati con i dati del file di testo.
   * Posizionare il cursore sul **[!UICONTROL Last name (@lastName)]** e seleziona il **[!UICONTROL Update only if destination is empty]** opzione .
   * Ripeti questa operazione per **[!UICONTROL Company (@company)]** nodo.
   * Assegnare una chiave di riconciliazione ai campi **[!UICONTROL Birth date]**, **[!UICONTROL Email]** e **[!UICONTROL First name]**.

      ![](assets/s_ncs_user_import_example04_03.png)

1. Avvio dell’importazione

   Fai clic su **[!UICONTROL Start]**.

   Consultare la tabella dei destinatari per verificare che i record siano stati modificati dall’importazione.

   ![](assets/s_ncs_user_import_example06_05.png)

   Solo i valori vuoti sono stati sostituiti dai valori del file di testo, ma il valore esistente nel database non è stato sovrascritto dal valore del file di importazione.

## Aggiornare e arricchire i valori da quelli in un file esterno {#example--update-and-enrich-the-values-from-those-in-an-external-file}

Vogliamo modificare alcuni campi di una tabella di database da un file di testo, dando priorità ai valori contenuti nel file di testo.

In questo esempio, alcuni campi nel file di testo hanno un valore vuoto, mentre i campi corrispondenti nel database non sono vuoti. Altri campi contengono un valore diverso da quello del database.

* Contenuto del file di testo da importare.

   ![](assets/s_ncs_user_import_example02_04.png)

* Stato del database prima dell&#39;importazione

   ![](assets/s_ncs_user_import_example06_07.png)

1. Scelta di un modello

   Applicare la procedura di cui all&#39;esempio 2 precedente.

1. File da importare

   Selezionare il file da importare.

   Nell’anteprima delle prime righe del file, puoi vedere che il file contiene campi vuoti e aggiornamenti per alcuni record.

1. Associazione dei campi

   Applicare la procedura di cui all&#39;esempio 2 precedente.

1. Attività Reconciliation

   * Vai alla tabella e seleziona **[!UICONTROL Update]**.
   * Seleziona l’opzione **[!UICONTROL Reject entity]** per **[!UICONTROL Management of doubles]** campo .
   * Lascia l’opzione . **[!UICONTROL Management of duplicates]** in **[!UICONTROL Update]** modalità per i record esistenti nel database da modificare con i dati del file di testo.
   * Posizionare il cursore sul **[!UICONTROL Account number (@account)]** e seleziona l’opzione **[!UICONTROL Take empty values into account]**.
   * Selezionare i campi **[!UICONTROL Birth date]**, **[!UICONTROL Email]** e **[!UICONTROL First name]** e assegna loro una chiave di riconciliazione.

      ![](assets/s_ncs_user_import_example04_04.png)

1. Avvio dell’importazione

   * Fai clic su **[!UICONTROL Start]**.
   * Consultare la tabella dei destinatari per verificare che i record siano stati modificati dall&#39;operazione.

      ![](assets/s_ncs_user_import_example06_06.png)

      I valori del file di testo vuoto sono stati sovrascritti nel database. I valori esistenti nel database sono stati aggiornati con quelli presenti nel file di importazione in linea con il **[!UICONTROL Update]** opzione selezionata per i duplicati al passaggio 4.
