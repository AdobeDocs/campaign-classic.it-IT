---
solution: Campaign Classic
product: campaign
title: '"Caso di utilizzo: configurazione della sostituzione del campo"'
description: '"Caso di utilizzo: configurazione della sostituzione del campo"'
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 4%

---


# Caso di utilizzo: configurazione della sostituzione del campo{#use-case-configuring-the-field-substitution}

La sostituzione casuale dei campi consente di attribuire un valore dall&#39;elenco dei destinatari agli indirizzi iniziali vuoti quando l&#39;utente utilizza questo valore in una consegna (ad esempio: nome, città, ecc.).

Questa sostituzione consente di risparmiare tempo durante la creazione della consegna: invece di aggiungere manualmente il valore desiderato agli indirizzi iniziali, la sostituzione recupera in modo casuale questo valore nell’elenco dei destinatari destinatari a cui viene assegnata la consegna e lo applica agli indirizzi iniziali.

## Contesto {#context}

In questo caso d&#39;uso, il sito **My online library** vorrebbe inviare uno sconto ai suoi clienti, in base al loro genere letterario preferito.

Il manager della distribuzione ha integrato nella sua e-mail un campo di personalizzazione collegato al genere preferito. Vorrebbe usare alcuni indirizzi di seme. Questi indirizzi iniziali contengono il campo di personalizzazione nella tabella, ma non viene salvato alcun valore.

Per utilizzare la sostituzione casuale dei campi è necessario disporre di:

* una consegna con uno o più campi di personalizzazione,
* indirizzi iniziali i cui **schema di dati** vengono modificati in base ai campi di personalizzazione utilizzati nella distribuzione.

## Creazione di una consegna {#step-1---creating-a-delivery}

I passaggi per la creazione di una consegna sono descritti nella sezione [Creazione di una consegna per e-mail](../../delivery/using/creating-an-email-delivery.md).

In questo esempio, il manager consegna ha creato la newsletter.

![](assets/dlv_seeds_usecase_24.png)

## Modifica dello schema di dati degli indirizzi iniziali {#editing-the-seed-addresses-data-schema}

Le istruzioni su come modificare uno schema di dati sono dettagliate nella sezione.

In questo esempio, lo schema di dati degli indirizzi iniziali prende un valore creato dallo schema di dati dei destinatari:

```
 <attribute label="Favorite literary genre" length="80" name="favoriteLiteraryGenre"
               type="string" userEnum="favoriteLiteraryGenre"/>
```

Questa enumerazione consente all&#39;utente di specificare il genere letterario preferito dei propri client.

Affinché la modifica dello schema di dati possa essere visualizzata negli indirizzi iniziali **Modulo di input**, è necessario aggiornarla. Fare riferimento alla sezione [Aggiornamento del modulo di input](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md#updating-the-input-form).

## Configurazione della personalizzazione {#configuring-personalization}

1. Aprite una consegna.

   In questo esempio, la distribuzione ha due campi di personalizzazione: il nome **del destinatario** e il genere letterario preferito **del destinatario**.

   ![](assets/dlv_seeds_usecase_25.png)

1. Configura l&#39;elenco di consegna e i tuoi indirizzi iniziali. Fare riferimento a [Identificazione delle popolazioni di destinazione](../../delivery/using/steps-defining-the-target-population.md).

   In questo esempio, l&#39;utente seleziona gli utenti il cui **genere letterario preferito** è Sci-Fi come popolazione di destinazione principale.

   ![](assets/dlv_seeds_usecase_26.png)

   L&#39;utente aggiunge gli indirizzi iniziali alla consegna.

   ![](assets/dlv_seeds_usecase_27.png)

   >[!NOTE]
   >
   >Per ulteriori informazioni sul collegamento **[!UICONTROL Edit the dynamic condition...]**, fare riferimento a [Caso di utilizzo: selezione di indirizzi iniziali su criteri](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md).

1. Fate clic sulla scheda **[!UICONTROL Preview]**, quindi selezionate un indirizzo e-mail per verificare la personalizzazione.

   ![](assets/dlv_seeds_usecase_28.png)

   Uno dei campi di personalizzazione è vuoto. Poiché l&#39;indirizzo seed non contiene dati per questo campo, l&#39;anteprima del contenuto HTML non può visualizzare un valore.

   La sostituzione casuale dei campi viene eseguita **al momento della consegna**.

1. Fai clic sul pulsante **[!UICONTROL Send]**.
1. Analizzare la consegna, quindi **confermare la consegna**.

   Gli indirizzi iniziali ricevono la consegna nella loro casella in entrata.

   La personalizzazione dei campi è efficace.

   ![](assets/dlv_seeds_usecase_08.png)
