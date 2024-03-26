---
product: campaign
title: Rinuncia alla vendita di informazioni personali
description: Scopri come rinunciare alla vendita di dati personali
feature: Privacy, Privacy Tools
badge-v7: label="v7" type="Informative" tooltip="Applicabile a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 8e308a9f-14a4-4a25-9fd0-8d4bdbcf74ce
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 98%

---

# Rinuncia alla vendita di informazioni personali (CCPA) {#sale-of-personal-information-ccpa}



Il **California Consumer Privacy Act** (CCPA) fornisce ai residenti della California nuovi diritti in merito alle loro informazioni personali e impone responsabilità in materia di protezione dei dati a determinate entità che conducono attività commerciali in California.

La configurazione e l’utilizzo delle richieste di accesso ed eliminazione sono comuni sia al GDPR che al CCPA. Questa sezione presenta la rinuncia alla vendita di dati personali, specifica del CCPA.

Oltre a utilizzare gli strumenti di [gestione del consenso](privacy-management.md#consent-management) forniti da Adobe Campaign, puoi verificare se un consumatore ha negato il consenso alla vendita dei suoi dati personali.

I contatti possono decidere, attraverso il sistema, di non consentire la vendita dei propri dati personali a terzi. In Adobe Campaign, potrai archiviare e tenere traccia di questo tipo di informazioni.

Affinché ciò funzioni, devi estendere la tabella dei profili e aggiungere un campo **[!UICONTROL Opt-Out for CCPA]**.

>[!IMPORTANT]
>
>In qualità di titolare del trattamento è tua responsabilità ricevere la richiesta dell’interessato e tenere traccia delle date della richiesta in conformità con il CCPA. In qualità di fornitore di tecnologia, ci limitiamo a offrire un modo per esprimere la rinuncia. Per ulteriori informazioni sul tuo ruolo in quanto titolare del trattamento, consulta [Dati personali e utenti tipo](privacy-and-recommendations.md#personal-data).

## Prerequisito {#ccpa-prerequisite}

Per sfruttare queste informazioni, è necessario creare tale campo in Adobe Campaign Standard. A questo scopo, aggiungi un campo booleano alla tabella **[!UICONTROL Recipient]**. Quando viene creato un nuovo campo, questo viene automaticamente supportato dall’API di Campaign.

Devi eseguire questa operazione anche se utilizzi una tabella dei destinatari personalizzata.

Per informazioni più dettagliate su come creare un nuovo campo, consulta la [documentazione sull’edizione dello schema](../../configuration/using/about-schema-edition.md).

>[!IMPORTANT]
>
>La modifica degli schemi è un’operazione delicata e deve essere eseguita solo da utenti esperti.

1. Passa a **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Add new fields]**, seleziona **[!UICONTROL Recipients]** come **[!UICONTROL Document type]** e fai clic su **[!UICONTROL Next]**. Per ulteriori informazioni sull’aggiunta di campi a una tabella, consulta [questa sezione](../../configuration/using/new-field-wizard.md).

   ![](assets/privacy-ccpa-1.png)

1. Per **[!UICONTROL Field type]**, seleziona **[!UICONTROL SQL field]**. Per l’etichetta, utilizza **[!UICONTROL Opt-Out for CCPA]**. Seleziona il tipo **[!UICONTROL 8-bit integer (boolean)]** e definisci il seguente **[!UICONTROL Relative path]** univoco: @OPTOUTCCPA. Fai clic su **[!UICONTROL Finish]**.

   ![](assets/privacy-ccpa-2.png)

   Questo estenderà o creerà lo schema **[!UICONTROL Recipient (cus)]**. Fai clic su di esso per verificare che il campo sia stato aggiunto correttamente.

   ![](assets/privacy-ccpa-3.png)

1. Fai clic sul nodo **[!UICONTROL Configuration]** > **[!UICONTROL Input forms]** dell’Explorer. In **[!UICONTROL Recipient (nms)]**, in “General Package” (Pacchetto generale), aggiungi un elemento `<input>` e per il valore xpath utilizz, il percorso relativo definito nel passaggio 2. Per ulteriori informazioni sulla pubblicazione di una risorsa, consulta [questa sezione](../../configuration/using/identifying-a-form.md).

   ```
   <input  colspan="2" type="checkbox" xpath="@OPTOUTCCPA"/>
   ```

   ![](assets/privacy-ccpa-4.png)

1. Disconnettiti e riconnettiti. Segui i passaggi descritti nella sezione successiva per verificare che il campo sia disponibile nei dettagli di un destinatario.

## Utilizzo {#usage}

Compilare il valore del campo e seguire le linee guida e le regole del CCPA relative alla vendita dei dati è responsabilità del titolare del trattamento.

Sono disponibili diversi metodi per compilare i valori:

* Mediante l’interfaccia di Campaign, modificando i dettagli del destinatario
* Mediante l’API
* Mediante un flusso di lavoro di importazione dati

Accertati di non vendere mai a terzi le informazioni personali dei profili che hanno espresso la rinuncia.

1. Per modificare lo stato di rinuncia, passa a **[!UICONTROL Profiles and Target]** > **[!UICONTROL Recipients]** e seleziona un destinatario. Nella scheda **[!UICONTROL General]** viene visualizzato il campo configurato nella sezione precedente.

   ![](assets/privacy-ccpa-5.png)

1. Configura l’elenco dei destinatari affinché venga visualizzata la colonna della rinuncia. Per informazioni su come configurare gli elenchi, consulta la [documentazione dettagliata](../../platform/using/adobe-campaign-workspace.md#configuring-lists).

   ![](assets/privacy-ccpa-6.png)

1. Fai clic sulla colonna per ordinare i destinatari in base alle informazioni di rinuncia. Puoi anche creare un filtro per visualizzare solo i destinatari che hanno rinunciato. Per ulteriori informazioni sulla creazione di filtri, consulta [questa sezione](../../platform/using/creating-filters.md).

   ![](assets/privacy-ccpa-7.png)
