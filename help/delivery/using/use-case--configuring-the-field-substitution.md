---
title: '"Caso di utilizzo: configurazione della sostituzione del campo"'
seo-title: '"Caso di utilizzo: configurazione della sostituzione del campo"'
description: '"Caso di utilizzo: configurazione della sostituzione del campo"'
seo-description: null
page-status-flag: never-activated
uuid: 7f083dc6-e6d7-4eea-ac66-87674716515c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
discoiquuid: a104fcab-75e6-4d73-bc3d-88570de6df7f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 003bac4c5d89290b9d3653d6ddfab7284b68642d

---


# Caso di utilizzo: configurazione della sostituzione del campo{#use-case-configuring-the-field-substitution}

La sostituzione casuale dei campi consente di attribuire un valore dall&#39;elenco dei destinatari agli indirizzi iniziali vuoti quando l&#39;utente utilizza questo valore in una consegna (ad esempio: nome, città, ecc.).

Questa sostituzione consente di risparmiare tempo durante la creazione della consegna: invece di aggiungere manualmente il valore desiderato agli indirizzi iniziali, la sostituzione recupera in modo casuale questo valore nell’elenco dei destinatari destinatari a cui viene assegnata la consegna e lo applica agli indirizzi iniziali.

## Contesto {#context}

In questo caso d&#39;uso, il sito **My online library** vorrebbe inviare uno sconto ai suoi clienti, in base al loro genere letterario preferito.

Il manager della distribuzione ha integrato nella sua e-mail un campo di personalizzazione collegato al genere preferito. Vorrebbe usare alcuni indirizzi di seme. Questi indirizzi iniziali contengono il campo di personalizzazione nella tabella, ma non viene salvato alcun valore.

Per utilizzare la sostituzione casuale dei campi è necessario disporre di:

* una consegna con uno o più campi di personalizzazione,
* indirizzi iniziali il cui schema **di** dati viene modificato in base ai campi di personalizzazione utilizzati nella consegna.

## Creating a delivery {#step-1---creating-a-delivery}

I passaggi per la creazione di una consegna sono descritti in dettaglio nella sezione [Creazione di una consegna](../../delivery/using/creating-an-email-delivery.md) e-mail.

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

Affinché la modifica dello schema di dati possa essere visualizzata negli indirizzi iniziali Modulo **di** input, è necessario aggiornarla. Fare riferimento alla sezione [Aggiornamento del modulo](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md#updating-the-input-form) di input.

## Configurazione della personalizzazione {#configuring-personalization}

1. Aprite una consegna.

   In questo esempio, la distribuzione ha due campi di personalizzazione: il **nome** del destinatario e il genere letterario **preferito** del destinatario.

   ![](assets/dlv_seeds_usecase_25.png)

1. Configura l&#39;elenco di consegna e i tuoi indirizzi iniziali. Fare riferimento a [Identificazione delle popolazioni](../../delivery/using/steps-defining-the-target-population.md)bersaglio.

   In questo esempio, l&#39;utente seleziona gli utenti il cui genere letterario **preferito** è Sci-Fi come popolazione di destinazione principale.

   ![](assets/dlv_seeds_usecase_26.png)

   L&#39;utente aggiunge gli indirizzi iniziali alla consegna.

   ![](assets/dlv_seeds_usecase_27.png)

   >[!NOTE]
   >
   >Per ulteriori informazioni sul **[!UICONTROL Edit the dynamic condition...]** collegamento, consulta Caso di [utilizzo: selezione degli indirizzi iniziali sui criteri](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md).

1. Fate clic sulla **[!UICONTROL Preview]** scheda, quindi selezionate un indirizzo e-mail per verificare la personalizzazione.

   ![](assets/dlv_seeds_usecase_28.png)

   Uno dei campi di personalizzazione è vuoto. Poiché l&#39;indirizzo seed non contiene dati per questo campo, l&#39;anteprima del contenuto HTML non può visualizzare un valore.

   La sostituzione casuale dei campi viene effettuata **al momento della consegna**.

1. Fate clic sul **[!UICONTROL Send]** pulsante.
1. Analizzare la consegna e **confermare la consegna**.

   Gli indirizzi iniziali ricevono la consegna nella loro casella in entrata.

   La personalizzazione dei campi è efficace.

   ![](assets/dlv_seeds_usecase_08.png)
