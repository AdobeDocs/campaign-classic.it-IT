---
solution: Campaign Classic
product: campaign
title: Estensione esemplificativa
description: Estensione esemplificativa
audience: interaction
content-type: reference
topic-tags: advanced-parameters
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 3%

---


# Estensione esemplificativa{#extension-example}

Nel caso di un contatto in entrata (call center o sito Web), le offerte più rilevanti sono suggerite a un determinato contatto utilizzando una serie di regole di idoneità. Per arricchire i criteri di idoneità delle offerte, estendere lo schema **nms:interactive** .

* Per aggiungere un nuovo contesto di interazione, estendere lo schema **nms:interactive** e creare tutti gli elementi **attributo** necessari nello schema.

   Nell’esempio seguente, i criteri aggiunti sono il codice del paese e l’ultima pagina visitata.

   ![](assets/s_ncs_configuration_offer_schemas.png)

* È quindi possibile utilizzare gli attributi creati in precedenza per definire la definizione dei criteri di idoneità.

   Nell&#39;esempio seguente, possiamo creare criteri di idoneità per visualizzare un&#39;offerta in base al paese dell&#39;utente o all&#39;ultima pagina Web visualizzata.

   ![](assets/s_ncs_configuration_offer_context.png)

* Durante la configurazione delle chiamate SOAP, inserire l&#39;elemento **context** XML per fare riferimento alle informazioni di contesto aggiunte nello schema di interazione. Per ulteriori informazioni, vedere [Integrazione tramite SOAP (lato server)](../../interaction/using/integration-via-soap--server-side-.md).

