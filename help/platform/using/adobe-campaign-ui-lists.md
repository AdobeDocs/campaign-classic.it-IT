---
product: campaign
title: Gestire e personalizzare gli elenchi
description: Scopri come sfogliare e configurare gli elenchi
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 21656cc2-15a1-4156-8897-ea4fe3e9b97f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1151'
ht-degree: 2%

---

# Gestire e personalizzare gli elenchi{#manage-and-customize-lists}

![](../../assets/common.svg)

Puoi accedere agli elenchi di record nel database di Campaign utilizzando Explorer. È possibile filtrare gli elenchi, eseguire ricerche, aggiungere informazioni, filtrare e ordinare i dati.

## Record di conteggio {#counting-records}

Per impostazione predefinita, Adobe Campaign carica i primi 200 record di un elenco. Ciò significa che il display non mostra necessariamente tutti i record della tabella che stai visualizzando. È possibile eseguire un conteggio del numero di record nell&#39;elenco e caricare altri record.

Nella parte in basso a destra della schermata dell’elenco, un **[!UICONTROL counter]** mostra quanti record sono stati caricati e il numero totale di record nel database (dopo aver applicato eventuali filtri):

![](assets/s_ncs_user_nb_200_0.png)

Se &quot;**?**&quot; viene visualizzato invece del numero a destra, fare clic sul contatore per avviare il calcolo.

### Carica altri record {#loading-more-records}

Per caricare (e quindi visualizzare) record aggiuntivi (200 righe per impostazione predefinita), fai clic su **[!UICONTROL Continue loading]**.

![](assets/s_ncs_user_load_list.png)

Per caricare tutti i record, fare clic con il pulsante destro del mouse sull&#39;elenco e selezionare **[!UICONTROL Load all]**.

>[!CAUTION]
>
>A seconda del numero di record, il tempo di caricamento dell’elenco completo può essere lungo.

### Modificare il numero predefinito di record {#change-default-number-of-records}

Per modificare il numero predefinito di record caricati, fare clic su **[!UICONTROL Configure list]** nell&#39;angolo in basso a destra dell&#39;elenco.

![](assets/s_ncs_user_configure_list.png)

Nella finestra di configurazione dell’elenco, fai clic su **[!UICONTROL Advanced parameters]** (in basso a sinistra) e modifica il numero di righe da recuperare.

![](assets/s_ncs_user_configurelist_advancedparam.png)

## Configurare gli elenchi {#configuring-lists}

### Aggiungi colonne {#add-columns}

Esistono due modi per aggiungere una colonna a un elenco.

È possibile aggiungere rapidamente una colonna a un elenco dai dettagli di un record. Per eseguire questa operazione:

1. Da una schermata di dettaglio, fare clic con il pulsante destro del mouse sul campo che si desidera visualizzare in una colonna.
1. Seleziona **[!UICONTROL Add in the list]**.

   La colonna viene aggiunta a destra delle colonne esistenti.

![](assets/s_ncs_user_add_in_list.png)

Un altro modo per aggiungere colonne, ad esempio se si desidera visualizzare dati non visualizzati nella schermata di dettaglio, è utilizzare la finestra di configurazione dell’elenco. Per eseguire questa operazione:

1. Fai clic su **[!UICONTROL Configure list]** sotto e a destra dell&#39;elenco.

   ![](assets/s_ncs_user_configure_list.png)

1. Nella finestra di configurazione dell’elenco, fai doppio clic sul campo da aggiungere nella **[!UICONTROL Available fields]** per aggiungerlo al **[!UICONTROL Output columns]**.

   ![](assets/s_ncs_user_configurelist.png)

   >[!NOTE]
   >
   >Per impostazione predefinita, i campi avanzati non vengono visualizzati. Per visualizzarli, fai clic su **Visualizza campi avanzati** di seguito e a destra dell’elenco dei campi disponibili.
   >
   >Le etichette vengono visualizzate per tabella e quindi in ordine alfabetico.
   >
   >Utilizza la **Ricerca** per eseguire una ricerca nei campi disponibili. Per ulteriori informazioni, consulta [questa sezione](#sorting-a-list).
   >
   >I campi sono identificati da icone specifiche: Campi SQL, tabelle collegate, campi calcolati, ecc. Per ciascun campo selezionato, la descrizione viene visualizzata sotto l’elenco dei campi disponibili. [Ulteriori informazioni](#configuring-lists).
   >
   >Puoi anche ordinare e filtrare i dati. Vedi [questa sezione](../../platform/using/filtering-options.md).

1. Ripetere la procedura per visualizzare ogni colonna.
1. Utilizza le frecce per modificare le **ordine di visualizzazione**. La colonna più alta si trova a sinistra nell’elenco dei record.

   ![](assets/s_ncs_user_columns_order_down.png)

1. Se necessario, puoi fare clic su **[!UICONTROL Distribution of values]** per visualizzare la partizione dei valori per il campo selezionato nella cartella corrente.

   ![](assets/s_ncs_user_configurelist_values.png)

1. Fai clic su **[!UICONTROL OK]** per confermare la configurazione e visualizzare il risultato.

### Crea una nuova colonna {#create-a-new-column}

È possibile creare nuove colonne per visualizzare campi aggiuntivi nell’elenco. Per eseguire questa operazione:

1. Fai clic su **[!UICONTROL Configure the list]** sotto e a destra della lista.
1. Fai clic su **[!UICONTROL Add]** per visualizzare un nuovo campo nell’elenco.

### Rimuovere una colonna {#remove-a-column}

È possibile mascherare una o più colonne in un elenco di record utilizzando **[!UICONTROL Configure list]** situato sotto e a destra dell&#39;elenco.

![](assets/s_ncs_user_configure_list.png)

Nella finestra di configurazione dell’elenco, seleziona la colonna da mascherare dal **[!UICONTROL Output columns]** e fare clic sul pulsante Elimina.

![](assets/s_ncs_user_removecolumn_icon.png)

Ripetere la procedura per nascondere ogni colonna. Fai clic su **[!UICONTROL OK]** per confermare la configurazione e visualizzare il risultato.

### Regolare la larghezza della colonna {#adjust-column-width}

Quando un elenco è attivo, ovvero se è selezionata almeno una riga, è possibile utilizzare F9 per regolare la larghezza delle colonne in modo che tutte le colonne possano essere visualizzate sullo schermo.

### Visualizzazione dei dati nelle sottocartelle {#display-sub-folders-records}

Gli elenchi possono essere visualizzati:

* Solo i record contenuti nella cartella selezionata,
* Oppure i record nella cartella selezionata E nelle relative sottocartelle.

Per passare da una modalità di visualizzazione all&#39;altra, fare clic su **[!UICONTROL Display sub-levels]** nella barra degli strumenti.

![](assets/s_ncs_user_display_children_icon.png)

## Salvare una configurazione di elenco {#saving-a-list-configuration}

Le configurazioni dell’elenco sono definite localmente a livello di workstation. Quando la cache locale viene svuotata, le configurazioni locali vengono disabilitate.

Per impostazione predefinita, i parametri di visualizzazione definiti si applicano a tutti gli elenchi con il tipo di cartella corrispondente. Pertanto, quando modifichi la modalità di visualizzazione dell’elenco dei destinatari da una cartella, questa configurazione verrà applicata a tutte le altre cartelle dei destinatari.

È tuttavia possibile salvare più di una configurazione da applicare a cartelle diverse dello stesso tipo. La configurazione viene salvata con le proprietà della cartella contenente i dati e può essere riapplicata.

Ad esempio, per una cartella di consegna, è possibile configurare la visualizzazione seguente:

![](assets/s_ncs_user_folder_save_config_1.png)

Per salvare la configurazione dell’elenco in modo che possa essere riutilizzata, segui i passaggi seguenti:

1. Fai clic con il pulsante destro del mouse sulla cartella contenente i dati visualizzati.
1. Seleziona **[!UICONTROL Properties]**.
1. Fai clic su **[!UICONTROL Advanced settings]** e quindi specifica un nome nella **[!UICONTROL Configuration]** campo .

   ![](assets/s_ncs_user_folder_save_config_2.png)

1. Fai clic su **[!UICONTROL OK]** quindi fai clic su **[!UICONTROL Save]**.

Puoi quindi applicare questa configurazione a un&#39;altra **Consegna** cartella:

![](assets/s_ncs_user_folder_save_config_3.png)

Fai clic su **[!UICONTROL Save]** nella finestra delle proprietà della cartella. La visualizzazione dell’elenco viene modificata per corrispondere alla configurazione specificata:

![](assets/s_ncs_user_folder_save_config_5.png)

## Esportare un elenco {#exporting-a-list}

Per esportare i dati da un elenco, è necessario utilizzare una procedura guidata di esportazione. Per accedervi, seleziona gli elementi da esportare dall’elenco, fai clic con il pulsante destro del mouse e seleziona **[!UICONTROL Export...]**.

L&#39;uso delle funzioni di importazione ed esportazione è spiegato in [Importazioni ed esportazioni generiche](../../platform/using/about-generic-imports-exports.md).

>[!CAUTION]
>
>Gli elementi di un elenco non devono essere esportati utilizzando la funzione Copia/Incolla .

## Ordinare un elenco {#sorting-a-list}

Gli elenchi possono contenere una grande quantità di dati. Puoi ordinare questi dati o applicare filtri semplici o avanzati. L’ordinamento consente di visualizzare i dati in ordine crescente o decrescente. I filtri ti consentono di definire e combinare criteri per visualizzare solo i dati selezionati.

Fai clic sull’intestazione della colonna per applicare un ordinamento crescente o decrescente o per annullare l’ordinamento dei dati. Lo stato di ordinamento e l’ordine di ordinamento attivi sono indicati da una freccia blu prima dell’etichetta della colonna. Un trattino rosso prima dell’etichetta della colonna indica che l’ordinamento viene applicato ai dati indicizzati dal database. Questo metodo di ordinamento viene utilizzato per ottimizzare i processi di ordinamento.

Puoi anche configurare l’ordinamento o combinare criteri di ordinamento. Per farlo, segui la procedura indicata di seguito:

1. **[!UICONTROL Configure list]** sotto e a destra dell&#39;elenco.

   ![](assets/s_ncs_user_configure_list.png)

1. Nella finestra di configurazione dell’elenco, fai clic su **[!UICONTROL Sorting]** scheda .
1. Selezionare i campi da ordinare e la direzione di ordinamento (crescente o decrescente).

   ![](assets/s_ncs_user_configurelist_sort.png)

1. La priorità di ordinamento è definita dall&#39;ordine delle colonne di ordinamento. Per modificare la priorità, utilizza le icone appropriate per modificare l’ordine delle colonne.

   ![](assets/s_ncs_user_configurelist_move.png)

   La priorità di ordinamento non influisce sulla visualizzazione delle colonne dell’elenco.

1. Fai clic su **[!UICONTROL Ok]** per confermare questa configurazione e visualizzare il risultato nell’elenco.

### Ricerca degli elementi {#running-a-search}

Puoi eseguire una ricerca dei campi disponibili in un editor utilizzando **[!UICONTROL Search]** campo situato sopra l’elenco dei campi. Press **Invio** sulla tastiera o sfogliare l&#39;elenco. I campi che corrispondono alla ricerca avranno etichette in grassetto.

>[!NOTE]
>
>Puoi creare filtri per visualizzare solo alcuni dei dati di un elenco. [Ulteriori informazioni](../../platform/using/creating-filters.md).
