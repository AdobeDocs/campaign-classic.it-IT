---
product: campaign
title: Estensione esemplificativa
description: Estensione esemplificativa
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: d4acf99b-cef4-48f7-b4cd-c032ec12592f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 3%

---

# Estensione esemplificativa{#extension-example}

![](../../assets/v7-only.svg)

Nel caso di un contatto in entrata (call center o sito web), le offerte più rilevanti sono suggerite a un determinato contatto utilizzando una serie di regole di idoneità. Per arricchire i criteri di idoneità delle offerte, espandi lo schema **nms:relation** .

* Per aggiungere un nuovo contesto di interazione, estendi lo schema **nms:relation** e crea tutti gli elementi **attribute** necessari nello schema.

   Nell’esempio seguente, i criteri aggiunti sono il codice del paese e l’ultima pagina visitata.

   ![](assets/s_ncs_configuration_offer_schemas.png)

* È quindi possibile utilizzare gli attributi creati in precedenza al momento della definizione dei criteri di idoneità.

   Nell’esempio seguente, possiamo creare criteri di idoneità per visualizzare un’offerta in base al paese dell’utente o all’ultima pagina web visualizzata.

   ![](assets/s_ncs_configuration_offer_context.png)

* Durante la configurazione delle chiamate SOAP, inserisci l&#39;elemento **context** XML per fare riferimento alle informazioni di contesto aggiunte nello schema di interazione. Per ulteriori informazioni, consulta [Integrazione tramite SOAP (lato server)](../../interaction/using/integration-via-soap--server-side-.md).
