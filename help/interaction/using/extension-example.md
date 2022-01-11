---
product: campaign
title: Estensione esemplificativa
description: Estensione esemplificativa
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: d4acf99b-cef4-48f7-b4cd-c032ec12592f
source-git-commit: 07a5742c6f142c786ad8ba2f8774e7e90e8cd191
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 3%

---

# Estensione esemplificativa{#extension-example}

![](../../assets/common.svg)

Nel caso di un contatto in entrata (call center o sito web), le offerte più rilevanti sono suggerite a un determinato contatto utilizzando una serie di regole di idoneità. Per arricchire i criteri di idoneità delle offerte, estendi le **nms:interazione** schema.

* Per aggiungere un nuovo contesto di interazione, estendi la **nms:interazione** schema e crea altrettanti **attributo** elementi necessari nello schema.

   Nell’esempio seguente, i criteri aggiunti sono il codice del paese e l’ultima pagina visitata.

   ![](assets/s_ncs_configuration_offer_schemas.png)

* È quindi possibile utilizzare gli attributi creati in precedenza al momento della definizione dei criteri di idoneità.

   Nell’esempio seguente, possiamo creare criteri di idoneità per visualizzare un’offerta in base al paese dell’utente o all’ultima pagina web visualizzata.

   ![](assets/s_ncs_configuration_offer_context.png)

* Durante la configurazione delle chiamate SOAP, inserisci **contesto** Elemento XML per fare riferimento alle informazioni di contesto aggiunte nello schema di interazione. Per ulteriori informazioni, consulta [Integrazione tramite SOAP (lato server)](../../interaction/using/integration-via-soap--server-side-.md).
