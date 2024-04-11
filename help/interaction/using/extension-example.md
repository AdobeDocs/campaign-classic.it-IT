---
product: campaign
title: Estensione esemplificativa
description: Estensione esemplificativa
feature: Interaction, Offers
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: d4acf99b-cef4-48f7-b4cd-c032ec12592f
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 3%

---

# Estensione esemplificativa{#extension-example}



Nel caso di un contatto in entrata (call center o sito web), le offerte più rilevanti sono suggerite a un determinato contatto utilizzando una serie di regole di idoneità. Per arricchire i criteri di idoneità delle offerte, estendere **nms:interazione** schema.

* Per aggiungere un nuovo contesto di interazione, estendere **nms:interazione** schema e crearne altrettanti **attributo** elementi necessari nello schema.

  Nell’esempio seguente, i criteri aggiunti sono il codice del paese e l’ultima pagina visitata.

  ![](assets/s_ncs_configuration_offer_schemas.png)

* È quindi possibile utilizzare gli attributi creati in precedenza durante la definizione dei criteri di idoneità.

  Nell’esempio seguente, è possibile creare criteri di idoneità per visualizzare un’offerta in base al paese dell’utente o all’ultima pagina web visualizzata.

  ![](assets/s_ncs_configuration_offer_context.png)

* Durante la configurazione delle chiamate SOAP, inserisci **contesto** Elemento XML per fare riferimento alle informazioni di contesto aggiunte nello schema di interazione. Per ulteriori informazioni, fare riferimento a [Integrazione tramite SOAP (lato server)](../../interaction/using/integration-via-soap-server-side.md).
