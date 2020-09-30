---
title: Creazione di indirizzi di seed
seo-title: Creazione di indirizzi di seed
description: Creazione di indirizzi di seed
seo-description: null
page-status-flag: never-activated
uuid: 0dae107a-7b53-4096-93c3-9517b402cbc9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
discoiquuid: 6dad49af-4818-471b-9df1-057cc6b9a68a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 6483c3e2e9fd3a2951b2bc8bf6d8a3350361e86f
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 2%

---


# Creazione di indirizzi di seed{#creating-seed-addresses}

Gli indirizzi dei semi non vengono gestiti tramite profili e destinazioni standard, ma in un nodo dedicato della gerarchia Adobe Campaign  **[!UICONTROL Resources > Campaign management > Seed addresses]**.

Potete creare sottocartelle per organizzare gli indirizzi iniziali. A tal fine, fare clic con il pulsante destro del mouse sul **[!UICONTROL Seed addresses]** nodo e selezionare **[!UICONTROL Create a new 'Seed addresses' folder]**. Assegnare un nome alla sottocartella, quindi premere **[!UICONTROL Enter]** per eseguire la convalida. È ora possibile creare o copiare gli indirizzi iniziali in questa sottocartella. For more on this, refer to [Defining addresses](#defining-addresses).

 Adobe Campaign consente inoltre di creare modelli di indirizzi di base che vengono importati nelle consegne o nelle campagne e adattati in base alle esigenze specifiche delle consegne e delle campagne interessate. Fare riferimento a [Creazione di modelli](#creating-seed-address-templates)di indirizzi iniziali.

## Definizione degli indirizzi {#defining-addresses}

Per creare indirizzi iniziali, effettuate le seguenti operazioni:

1. Fare clic sul **[!UICONTROL New]** pulsante sopra l&#39;elenco degli indirizzi iniziali.
1. Immettere i dati collegati all&#39;indirizzo nei campi corrispondenti della **[!UICONTROL Recipient]** scheda. I campi disponibili corrispondono ai campi standard nei profili dei destinatari della consegna (tabella nms:destinatario): nome, nome, e-mail, ecc.

   >[!NOTE]
   >
   >L’etichetta dell’indirizzo viene compilata automaticamente con il cognome e il nome definiti dall’utente.
   >
   >Non è necessario immettere tutti i campi di ciascuna scheda al momento della creazione di un indirizzo seed. Eventuali elementi di personalizzazione mancanti vengono inseriti in modo casuale durante la distribuzione.

   ![](assets/s_ncs_user_seedlist_new_address.png)

1. Nella **[!UICONTROL Seed fields]** scheda, immettete i valori che verranno inseriti nei registri di consegna durante la fase di analisi (nella **[!UICONTROL nms:broadLog]** tabella).

1. Nella **[!UICONTROL Additional data]** scheda, immetti i dati di personalizzazione utilizzati per le consegne create nei flussi di lavoro di gestione dei dati a cui vuoi assegnare un valore specifico.

   >[!NOTE]
   >
   >Verificate che siano stati definiti ulteriori dati di destinazione con un alias che inizia con &#39;@&#39; nell&#39; **[!UICONTROL Enrichment]** attività. In caso contrario, non potrai utilizzarli correttamente con i tuoi indirizzi iniziali nell&#39;attività di consegna.

## Creazione di modelli di indirizzi iniziali {#creating-seed-address-templates}

Per creare modelli di indirizzi che verranno importati e che potranno essere modificati per ogni consegna, il processo è lo stesso di quando si definisce un nuovo indirizzo. L&#39;unica differenza è che gli indirizzi dei modelli di indirizzi iniziali devono essere memorizzati in una cartella di tipo &#39;Modello&#39;.

Per definire una cartella di modelli, effettuate le seguenti operazioni:

1. Create una nuova cartella di **[!UICONTROL Seed addresses]** tipo, fate clic con il pulsante destro del mouse sulla cartella e selezionate **[!UICONTROL Properties...]**.

   ![](assets/s_ncs_user_seedlist_template_folder.png)

1. Fate clic sulla **[!UICONTROL Restriction]** scheda e aggiungete la seguente condizione di filtro: **@isModel = true**.

   ![](assets/s_ncs_user_seedlist_folder_is_model.png)

   Gli indirizzi memorizzati in questa cartella possono ora essere utilizzati come modelli di indirizzo. È possibile importarli nelle consegne o nelle campagne e adattarli in base alle esigenze specifiche delle consegne e delle campagne interessate (vedere [Aggiunta di indirizzi](../../delivery/using/adding-seed-addresses.md)iniziali).
