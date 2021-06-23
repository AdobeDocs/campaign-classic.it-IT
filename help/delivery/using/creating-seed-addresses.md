---
product: campaign
title: Creazione di indirizzi di seed
description: Scopri come creare e utilizzare gli indirizzi di seed
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
exl-id: f7dc97f0-3423-4b6f-88e2-08180f9adf8a
source-git-commit: a129f49d4f045433899fd7fdbd057fb16d0ed36a
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 1%

---

# Creazione di indirizzi di seed{#creating-seed-addresses}

Gli indirizzi di seed non vengono gestiti tramite profili e destinazioni standard, ma in un nodo dedicato della gerarchia Adobe Campaign **[!UICONTROL Resources > Campaign management > Seed addresses]**.

Puoi creare sottocartelle per organizzare gli indirizzi di seed. A questo scopo, fai clic con il pulsante destro del mouse sul nodo **[!UICONTROL Seed addresses]** e seleziona **[!UICONTROL Create a new 'Seed addresses' folder]**. Denomina la sottocartella e premi **[!UICONTROL Enter]** per eseguire la convalida. Ora puoi creare o copiare gli indirizzi di seed in questa sottocartella. Per ulteriori informazioni, consulta [Definizione degli indirizzi](#defining-addresses).

Adobe Campaign consente inoltre di creare modelli di indirizzi di seed importati in consegne o campagne e adattati in base alle esigenze specifiche delle consegne e delle campagne interessate. Fai riferimento a [Creazione di modelli di indirizzi di seed](#creating-seed-address-templates).

## Definizione degli indirizzi {#defining-addresses}

Per creare indirizzi di seed, segui i passaggi seguenti:

1. Fai clic sul pulsante **[!UICONTROL New]** sopra l’elenco degli indirizzi di seed.
1. Immetti i dati collegati all’indirizzo nei campi corrispondenti dalla scheda **[!UICONTROL Recipient]** . I campi disponibili corrispondono ai campi standard nei profili dei destinatari della consegna (tabella nms:recipient): nome, nome, e-mail, ecc.

   >[!NOTE]
   >
   >L’etichetta dell’indirizzo viene automaticamente compilata con il cognome e il nome definiti.
   >
   >Non è necessario inserire tutti i campi di ciascuna scheda durante la creazione di un indirizzo di seed. Eventuali elementi di personalizzazione mancanti vengono inseriti in modo casuale durante la distribuzione.

   ![](assets/s_ncs_user_seedlist_new_address.png)

1. Nella scheda **[!UICONTROL Seed fields]** , immetti i valori che verranno inseriti nei registri di consegna durante la fase di analisi (nella tabella **[!UICONTROL nms:broadLog]** ).

1. Nella scheda **[!UICONTROL Additional data]** , inserisci i dati di personalizzazione utilizzati per le consegne create nei flussi di lavoro di gestione dei dati a cui desideri assegnare un valore specifico.

   >[!NOTE]
   >
   >Assicurati che i dati di destinazione aggiuntivi siano stati definiti con un alias che inizia con &#39;@&#39; nell&#39;attività **[!UICONTROL Enrichment]**. In caso contrario, non potrai utilizzarli correttamente con gli indirizzi di seed nell’attività di consegna.

## Creazione di modelli di indirizzi di seed {#creating-seed-address-templates}

Per creare modelli di indirizzi da importare e modificare per ogni consegna, il processo è lo stesso di quando si definisce un nuovo indirizzo di seed. L’unica differenza consiste nel fatto che gli indirizzi dei modelli di indirizzo di seed devono essere memorizzati in una cartella di tipo &quot;Modello&quot;.

Per definire una cartella di modelli, applicare il seguente processo:

1. Crea una nuova cartella di tipo **[!UICONTROL Seed addresses]**, fai clic con il pulsante destro del mouse sulla cartella e seleziona **[!UICONTROL Properties...]**.

   ![](assets/s_ncs_user_seedlist_template_folder.png)

1. Fai clic sulla scheda **[!UICONTROL Restriction]** e aggiungi la seguente condizione di filtro: **@isModel = true**.

   ![](assets/s_ncs_user_seedlist_folder_is_model.png)

   Gli indirizzi memorizzati in questa cartella possono ora essere utilizzati come modelli di indirizzo. Puoi importarli in consegne o campagne e adattarli in base alle esigenze specifiche delle consegne e delle campagne interessate (consulta [Aggiunta di indirizzi di seed](adding-seed-addresses.md)).
