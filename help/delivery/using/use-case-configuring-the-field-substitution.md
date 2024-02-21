---
product: campaign
title: "Caso d’uso: configurare la sostituzione del campo"
description: "Caso d’uso: configurare la sostituzione del campo"
badge-v7: label="v7" type="Informative" tooltip="Applicabile a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Seed Address
exl-id: 3f567b2d-6f98-4831-af84-7db17fd12c6e
source-git-commit: 668cee663890fafe27f86f2afd3752f7e2ab347a
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 3%

---

# Caso d’uso: configurare la sostituzione del campo{#use-case-configuring-the-field-substitution}



La sostituzione casuale dei campi consente di attribuire un valore dall’elenco dei destinatari agli indirizzi iniziali vuoti quando l’utente utilizza tale valore in una consegna (ad esempio: nome, città, ecc.).

Questa sostituzione consente di risparmiare tempo durante la creazione della consegna: anziché aggiungere manualmente il valore desiderato agli indirizzi di seed, la sostituzione recupera in modo casuale questo valore nell’elenco dei destinatari interessati dalla consegna e lo applica agli indirizzi di seed.

## Contesto {#context}

In questo caso d’uso, il sito **La mia libreria online** vorrebbe mandare uno sconto ai suoi clienti, in base al loro genere letterario preferito.

Il responsabile della consegna ha integrato nell’e-mail un campo di personalizzazione collegato al genere preferito. Lo scopo è quello di utilizzare alcuni indirizzi di seed: questi indirizzi di seed hanno il campo di personalizzazione nella loro tabella, ma non viene salvato alcun valore.

Per utilizzare la sostituzione casuale dei campi, è necessario disporre di:

* una consegna con uno o più campi di personalizzazione,
* indirizzi seed il cui **schema dati** viene modificato in base ai campi di personalizzazione utilizzati nella consegna.

## Creare una consegna {#step-1---creating-a-delivery}

I passaggi per creare una consegna sono descritti in [Creare una consegna e-mail](creating-an-email-delivery.md) sezione.

In questo esempio, il responsabile della consegna ha creato la newsletter.

![](assets/dlv_seeds_usecase_24.png)

## Modifica dello schema dei dati degli indirizzi di seed {#editing-the-seed-addresses-data-schema}

Le istruzioni su come modificare uno schema di dati sono descritte in dettaglio nella sezione.

In questo esempio, lo schema dei dati degli indirizzi di seed accetta un valore creato dallo schema dei dati dei destinatari:

```
 <attribute label="Favorite literary genre" length="80" name="favoriteLiteraryGenre"
               type="string" userEnum="favoriteLiteraryGenre"/>
```

Questa enumerazione consente all’utente di specificare il genere letterario preferito dei suoi clienti.

Affinché questa modifica dello schema dati sia visualizzabile negli indirizzi di seed **Modulo di input**, è necessario aggiornarlo. Consulta la sezione [Aggiornare il modulo di input](use-case-selecting-seed-addresses-on-criteria.md#updating-the-input-form) sezione.

## Configurazione della personalizzazione {#configuring-personalization}

1. Apri una consegna.

   In questo esempio, la consegna ha due campi di personalizzazione: quello del destinatario **nome** e del destinatario **genere letterario preferito**.

   ![](assets/dlv_seeds_usecase_25.png)

1. Configura l’elenco di consegna e gli indirizzi seed. Fai riferimento a [Identificare le popolazioni target](steps-defining-the-target-population.md).

   In questo esempio, l’utente seleziona gli utenti il cui **genere letterario preferito** è Sci-Fi come popolazione target principale.

   ![](assets/dlv_seeds_usecase_26.png)

   L’utente aggiunge indirizzi seed alla consegna.

   ![](assets/dlv_seeds_usecase_27.png)

   >[!NOTE]
   >
   >Per ulteriori informazioni su **[!UICONTROL Edit the dynamic condition...]** collegamento, fare riferimento a [Caso d’uso: selezionare gli indirizzi seed in base ai criteri](use-case-selecting-seed-addresses-on-criteria.md).

1. Fai clic su **[!UICONTROL Preview]** , quindi seleziona un indirizzo di seed per testare la personalizzazione.

   ![](assets/dlv_seeds_usecase_28.png)

   Puoi notare che uno dei campi di personalizzazione è vuoto. Poiché l’indirizzo di seed non dispone di dati per questo campo, l’anteprima del contenuto HTML non può visualizzare un valore.

   Viene eseguita la sostituzione casuale dei campi **al momento della consegna**.

1. Fai clic sul pulsante **[!UICONTROL Send]**.
1. Analizza la consegna, quindi **conferma consegna**.

   Gli indirizzi seed ricevono la consegna nella propria casella in entrata.

   La personalizzazione dei campi è efficace.

   ![](assets/dlv_seeds_usecase_08.png)
