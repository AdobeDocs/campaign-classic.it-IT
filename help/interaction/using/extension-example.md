---
product: campaign
title: Estensione esemplificativa
description: Estensione esemplificativa
feature: Interaction, Offers
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: d4acf99b-cef4-48f7-b4cd-c032ec12592f
TQID: 'https://experienceleague.adobe.com/TQZaYrJop03HAw47XPFqgmoxb073iC-xztTp-f-5dEk'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b6fcaf36-3bc4-4604-94f3-81b5d3f41ecf
    internal-label: Offer Management
  - id: 65702805-0026-5ca1-843a-144fa79f0883
    internal-label: Interaction
  - id: ea08db70-4682-59a2-9408-9aedd9548e07
    internal-label: Offers
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: e739ee2b-6228-412e-878f-45de0791417d
    internal-label: Use cases
source-git-commit: 3e213ecc670d5a3cb8299c092ccbb5303858327d
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 3%
---
# Estensione esemplificativa{#extension-example}



Nel caso di un contatto in entrata (call center o sito web), le offerte più rilevanti sono suggerite a un determinato contatto utilizzando una serie di regole di idoneità. Per arricchire i criteri di idoneità delle offerte, estendere lo schema **nms:interaction**.

* Per aggiungere un nuovo contesto di interazione, estendere lo schema **nms:interaction** e creare tutti gli elementi **attribute** necessari nello schema.

  Nell’esempio seguente, i criteri aggiunti sono il codice del paese e l’ultima pagina visitata.

  ![](assets/s_ncs_configuration_offer_schemas.png)

* È quindi possibile utilizzare gli attributi creati in precedenza durante la definizione dei criteri di idoneità.

  Nell’esempio seguente, è possibile creare criteri di idoneità per visualizzare un’offerta in base al paese dell’utente o all’ultima pagina web visualizzata.

  ![](assets/s_ncs_configuration_offer_context.png)

* Durante la configurazione delle chiamate di SOAP, inserisci l&#39;elemento XML **context** per fare riferimento alle informazioni di contesto aggiunte nello schema di interazione. Per ulteriori informazioni, consultare [Integrazione tramite SOAP (lato server)](../../interaction/using/integration-via-soap-server-side.md).
