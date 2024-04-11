---
product: campaign
title: Regole di presentazione
description: Regole di presentazione
feature: Interaction, Offers
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
audience: interaction
content-type: reference
topic-tags: case-study
exl-id: f9dd9ad6-48da-4a80-9405-109a433a1ed5
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 1%

---

# Regole di presentazione{#presentation-rules}



## Creazione di una regola di presentazione {#creating-a-presentation-rule}

Nel nostro database, ci sono diverse offerte di viaggio per Europa, Africa, Stati Uniti e Canada. Vogliamo inviare offerte per un viaggio in Canada, ma se il destinatario rifiuta questo tipo di offerta, non vogliamo inviarle di nuovo

Stiamo per configurare la nostra regola in modo che il viaggio in Canada venga offerto solo una volta per destinatario e non nuovamente se rifiutato.

1. Nella struttura Adobe Campaign, vai al **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Typology management]** > **[!UICONTROL Typology rules]** nodo.
1. Crea un nuovo **[!UICONTROL Offer presentation]** regola di tipo.

   ![](assets/offer_typology_example_001.png)

1. Se necessario, modifica l’etichetta e la descrizione.

   ![](assets/offer_typology_example_002.png)

1. Scegli la **[!UICONTROL All channels]** per estendere la regola a tutti i canali.

   ![](assets/offer_typology_example_003.png)

1. Fai clic su **[!UICONTROL Edit expression]** e scegli il **[!UICONTROL Category]** come espressione.

   ![](assets/offer_typology_example_004.png)

1. Scegli la categoria che corrisponde alla tua offerta di viaggio per il Canada e fai clic su **[!UICONTROL OK]** per chiudere la finestra della query.

   ![](assets/offer_typology_example_005.png)

1. In **[!UICONTROL Offer presentation]** , scegli le stesse dimensioni configurate nell’ambiente.

   ![](assets/offer_typology_example_006.png)

1. Specifica il periodo durante il quale la regola verrà applicata.

   ![](assets/offer_typology_example_007.png)

1. Limita la proposta a uno in modo che i destinatari che hanno già rifiutato un viaggio in Canada non ricevano un’altra offerta simile.

   ![](assets/offer_typology_example_008.png)

1. Seleziona la **[!UICONTROL Offers for the same category]** filtro per escludere tutte le offerte dal **Canada** categoria.

   ![](assets/offer_typology_example_020.png)

1. Seleziona la **[!UICONTROL Rejected propositions]** per tenere conto solo delle proposte rifiutate dal destinatario.

   ![](assets/offer_typology_example_021.png)

1. Scegli i destinatari per i quali applicare questa regola.

   Nel nostro esempio, sceglieremo il **Viaggiatori frequenti** destinatari.

   ![](assets/offer_typology_example_009.png)

1. Fai riferimento alla regola in una tipologia di offerta.

   ![](assets/offer_typology_example_013.png)

1. Vai all’ambiente dell’offerta, (**Ambiente - Destinatario** in questo caso) e fare riferimento alla nuova tipologia appena creata utilizzando l’elenco a discesa nel **[!UICONTROL Eligibility]** scheda.

   ![](assets/offer_typology_example_014.png)

## Applicazione della regola di presentazione {#applying-the-presentation-rule}

Esempio di applicazione della regola di tipologia creata in precedenza.

Desideriamo inviare una proposta di prima offerta appartenente alla categoria Canada. Se l’offerta viene rifiutata una volta da uno dei destinatari, non verrà più offerta loro.

1. In **Viaggiatori frequenti** cartella dei destinatari, scegli uno dei profili per verificare le offerte per le quali sono idonei: fai clic su **[!UICONTROL Propositions]** , quindi la scheda **[!UICONTROL Preview]** scheda.

   Nel nostro esempio, **Tim Ramsey** è idoneo per un’offerta che fa parte del **Americhe** categoria.

   ![](assets/offer_typology_example_015.png)

1. Per iniziare, crea una consegna e-mail destinata al tuo **Viaggiatori frequenti** destinatari con offerte.
1. Seleziona i parametri di richiamo del motore di offerta.

   Nel nostro esempio, il **Viaggi in America** viene scelta la categoria, che contiene **Canada** e **Stati Uniti** sottocategorie.

   ![](assets/offer_typology_example_016.png)

1. Inserisci le offerte nel corpo del messaggio e invia la consegna. Per ulteriori informazioni, consulta [Informazioni sui canali in uscita](../../interaction/using/about-outbound-channels.md).

   Il destinatario ha ricevuto l’offerta per la quale è idoneo.

1. Il destinatario ha rifiutato l’offerta canadese, come mostrato nella cronologia delle proposte.

   ![](assets/offer_typology_example_018.png)

1. Controlla le offerte per le quali sono ora idonee.

   Possiamo vedere che non viene scelta alcuna offerta per il Canada.

   ![](assets/offer_typology_example_019.png)
