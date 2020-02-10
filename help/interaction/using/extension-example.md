---
title: Esempio di estensione
seo-title: Esempio di estensione
description: Esempio di estensione
seo-description: null
page-status-flag: never-activated
uuid: 6703b6e8-4eac-4a94-a80a-a7cd71b25cdf
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: advanced-parameters
discoiquuid: 990b6cbc-9b7b-4278-a635-653d5abafe87
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Esempio di estensione{#extension-example}

Nel caso di un contatto in entrata (call center o sito Web), le offerte più rilevanti sono suggerite a un determinato contatto utilizzando una serie di regole di idoneità. Per arricchire i criteri di idoneità delle offerte, estendere lo schema **nms:interactive** .

* Per aggiungere un nuovo contesto di interazione, estendere lo schema **nms:interactive** e creare tutti gli elementi **attributo** necessari nello schema.

   Nell’esempio seguente, i criteri aggiunti sono il codice del paese e l’ultima pagina visitata.

   ![](assets/s_ncs_configuration_offer_schemas.png)

* Potete quindi utilizzare gli attributi creati in precedenza per definire la definizione dei criteri di idoneità.

   Nell&#39;esempio seguente, possiamo creare criteri di idoneità per visualizzare un&#39;offerta in base al paese dell&#39;utente o all&#39;ultima pagina Web visualizzata.

   ![](assets/s_ncs_configuration_offer_context.png)

* Durante la configurazione delle chiamate SOAP, inserire l&#39;elemento **context** XML per fare riferimento alle informazioni di contesto aggiunte nello schema di interazione. Per ulteriori informazioni, vedere [Integrazione tramite SOAP (lato server)](../../interaction/using/integration-via-soap--server-side-.md).

