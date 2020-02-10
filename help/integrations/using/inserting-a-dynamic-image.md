---
title: Inserimento di un’immagine dinamica
seo-title: Inserimento di un’immagine dinamica
description: Inserimento di un’immagine dinamica
seo-description: null
page-status-flag: never-activated
uuid: 4acc905e-625c-45aa-bb70-7dde22911aa0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-target
discoiquuid: f6e4d22b-4ad3-4a1e-8a6f-3bdfc1da0535
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# Inserimento di un’immagine dinamica{#inserting-a-dynamic-image}

Questa sezione descrive i passaggi da effettuare in Adobe Campaign per integrare un&#39;immagine da Adobe Target in un messaggio e-mail.

In Adobe Target è necessario eseguire in anticipo le azioni seguenti:

* Create una o più offerte [di](https://marketing.adobe.com/resources/help/en_US/tnt/help/t_Creating_a_Redirect_Offer.html)reindirizzamento, nelle quali dovete specificare l&#39;URL dell&#39;immagine che state utilizzando.
* Create una o più [audience](https://marketing.adobe.com/resources/help/en_US/target/target/t_create-audience.html), per definire il target dell&#39;attività.
* Create un&#39;attività di composer [esperienza basata su](https://marketing.adobe.com/resources/help/en_US/tnt/help/t_Creating_an_A_B_Test.html) modulo, in cui dovete selezionare una rawbox e specificare diverse esperienze, a seconda del numero di offerte di reindirizzamento create. Per ogni esperienza, dovete selezionare una delle offerte di reindirizzamento create.

   Per specificare queste esperienze, puoi creare segmenti utilizzando le informazioni di Adobe Campaign. Per utilizzare i dati di Adobe Campaign nelle regole di selezione dell&#39;offerta, devi specificare i dati nella rawbox in Adobe Target.

Per inserire un&#39;immagine Adobe Target in una distribuzione Adobe Campaign:

1. Creare una consegna tramite e-mail.
1. Nei campi di personalizzazione disponibili, selezionate **[!UICONTROL Include > Dynamic image served by Adobe Target]**.

   ![](assets/tar_insert_dynamic_image.png)

1. Nella finestra visualizzata, selezionate l’immagine che verrà visualizzata per impostazione predefinita nel messaggio e-mail. Potete specificare l&#39;URL dell&#39;immagine o utilizzare un&#39;immagine [](../../integrations/using/sharing-assets-with-adobe-experience-cloud.md)condivisa.
1. Immettete il nome della rawbox specificata in Adobe Target.
1. Immettete un URL nel **[!UICONTROL Landing Page]** campo se desiderate che l’immagine predefinita venga reindirizzata a una pagina di destinazione predefinita. Questo URL è solo per i casi in cui l’immagine predefinita viene visualizzata nell’e-mail finale ed è facoltativa.
1. Se utilizzate le autorizzazioni Enterprise nelle impostazioni in Adobe Target, aggiungete la proprietà corrispondente in questo campo. Ulteriori informazioni sulle autorizzazioni di Target Enterprise in [questa pagina](https://marketing.adobe.com/resources/help/en_US/target/target/properties-overview.html). Questo campo è facoltativo e non obbligatorio se non utilizzate le autorizzazioni Enterprise in Target.
1. In **[!UICONTROL Additional decision parameters]**, specificate la mappatura tra i campi definiti nei segmenti di Adobe Target e i campi di Adobe Campaign. I campi di Adobe Campaign utilizzati devono essere stati specificati nella rawbox.

   ![](assets/tar_additional_decisionning_parameters.png)

   La definizione di un parametro in Adobe Target viene eseguita tramite la rawbox creata quando si integra l&#39;immagine Target in Adobe Campaign e l&#39;opzione **Miglioramenti** .

   ![](assets/tar_additional_decisionning_parameters_1.png)

   L’esempio riportato di seguito illustra come definire esperienze diverse per uomini e donne.

Potete anche definire diversi casi in base al dominio e all&#39;indirizzo e-mail dell&#39;utente. I dati vengono recuperati automaticamente dal browser dell&#39;utente all&#39;apertura dell&#39;e-mail.

![](assets/tar_additional_decisionning_parameters_2.png)

Quando visualizzi l&#39;anteprima del messaggio e-mail, puoi vedere, quando selezioni profili diversi, che l&#39;immagine inserita cambia a seconda dei parametri specificati nell&#39;attività Adobe Target e in Adobe Campaign.

Puoi misurare i risultati delle tue invii in Adobe Target.

![](assets/tar_measure_results.png)

