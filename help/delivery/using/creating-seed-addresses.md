---
product: campaign
title: Creare indirizzi seed
description: Scopri come creare e utilizzare gli indirizzi di seed
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Seed Address
role: User, Developer
exl-id: f7dc97f0-3423-4b6f-88e2-08180f9adf8a
TQID: https://experienceleague.adobe.com/ya4m8nG7m3DUj-buOZMnd2Nzfx1J6lmIiOuo1VcHjwU
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
  - id: a658c786-869b-4194-a780-2594d663adda
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 426
ht-degree: 1%

---

# Creare indirizzi seed{#creating-seed-addresses}

Gli indirizzi di seed non vengono gestiti tramite profili e destinazioni standard, ma in un nodo dedicato della gerarchia Adobe Campaign **[!UICONTROL Resources > Campaign management > Seed addresses]**.

Puoi creare sottocartelle per organizzare gli indirizzi di seed. A tale scopo, fare clic con il pulsante destro del mouse sul nodo **[!UICONTROL Seed addresses]** e selezionare **[!UICONTROL Create a new 'Seed addresses' folder]**. Assegnare un nome alla sottocartella, quindi premere **[!UICONTROL Enter]** per confermare. Ora puoi creare o copiare gli indirizzi di seed in questa sottocartella. Per ulteriori informazioni, consulta [Definire gli indirizzi](#defining-addresses).

Adobe Campaign consente inoltre di creare modelli di indirizzi seed importati in consegne o campagne e adattati in base alle esigenze specifiche delle consegne e delle campagne in questione. Consulta [Creare modelli di indirizzi seed](#creating-seed-address-templates).

## Definire gli indirizzi {#defining-addresses}

Per creare indirizzi seed, effettua le seguenti operazioni:

1. Fare clic sul pulsante **[!UICONTROL New]** sopra l&#39;elenco degli indirizzi di seed.
1. Immettere i dati collegati all&#39;indirizzo nei campi corrispondenti della scheda **[!UICONTROL Recipient]**. I campi disponibili corrispondono ai campi standard nei profili dei destinatari della consegna (tabella nms:recipient): nome, nome, e-mail, ecc.

   >[!NOTE]
   >
   >L’etichetta dell’indirizzo viene automaticamente compilata con il cognome e il nome definiti.
   >
   >Non è necessario immettere tutti i campi di ciascuna scheda durante la creazione di un indirizzo di seed. Gli elementi di personalizzazione mancanti vengono inseriti in modo casuale durante l’analisi della consegna.

   ![](assets/s_ncs_user_seedlist_new_address.png)

1. Nella scheda **[!UICONTROL Address fields]**, immetti i valori che verranno inseriti nei registri di consegna durante la fase di analisi (nella tabella **[!UICONTROL nms:broadLog]**).

1. Nella scheda **[!UICONTROL Additional data]**, immetti i dati di personalizzazione utilizzati per le consegne create nei flussi di lavoro di gestione dati e a cui desideri assegnare un valore specifico.

   >[!NOTE]
   >
   >Verificare che siano stati definiti dati di destinazione aggiuntivi con un alias che inizia con &#39;@&#39; nell&#39;attività **[!UICONTROL Enrichment]**. In caso contrario, non potrai utilizzarli correttamente con gli indirizzi seed nell’attività di consegna.

## Creazione di modelli di indirizzi seed {#creating-seed-address-templates}

Per creare modelli di indirizzo che verranno importati e che potranno essere modificati per ogni consegna, il processo è lo stesso utilizzato per definire un nuovo indirizzo di seed. L&#39;unica differenza consiste nel fatto che gli indirizzi dei modelli di indirizzi seed devono essere memorizzati in una cartella di tipo &quot;Modello&quot;.

Per definire una cartella di modelli, attenersi alla procedura descritta di seguito.

1. Creare una nuova cartella di tipo **[!UICONTROL Seed addresses]**, fare clic con il pulsante destro del mouse sulla cartella e selezionare **[!UICONTROL Properties...]**.

   ![](assets/s_ncs_user_seedlist_template_folder.png)

1. Fare clic sulla scheda **[!UICONTROL Restriction]** e aggiungere la seguente condizione di filtro: **@isModel = true**.

   ![](assets/s_ncs_user_seedlist_folder_is_model.png)

   Gli indirizzi memorizzati in questa cartella possono ora essere utilizzati come modelli di indirizzi. Puoi importarli in consegne o campagne e adattarli in base alle esigenze specifiche delle consegne e campagne interessate (consulta [Aggiungi indirizzi seed](adding-seed-addresses.md)).
