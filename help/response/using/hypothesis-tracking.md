---
product: campaign
title: Ipotesi di tracciamento
description: Scopri come tracciare le ipotesi in Campaign Response Manager
audience: campaign
content-type: reference
topic-tags: response-manager
exl-id: 1dc6d03b-698c-4750-9563-0676fcd185df
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---

# Tracciamento delle ipotesi{#hypothesis-tracking}

![](../../assets/v7-only.svg)

Il risultato dei calcoli di ipotesi è disponibile a vari livelli della piattaforma Adobe Campaign: gli indicatori calcolati in base alle ipotesi e alle reazioni della popolazione destinataria sono visibili attraverso l&#39;ipotesi effettiva, nonché nei rapporti di ipotesi disponibili tramite campagne e consegne.

## Risultati ipotesi {#hypothesis-results}

### Indicatori {#indicators}

Una volta calcolata l&#39;ipotesi, diversi indicatori di misurazione vengono aggiornati automaticamente. Sono disponibili nella scheda **[!UICONTROL General]** dell’ipotesi.

![](assets/response_hypothesis_delivery_example_010.png)

Questi indicatori sono:

* **Numero di contatti** intervistati: numero di persone contattate che corrispondono all&#39;ipotesi.
* **Tasso** di risposta contattato: numero di contatti intervistati / totale di persone contattate durante la consegna.
* **Numero di contatti** del gruppo di controllo partecipanti: numero di gruppi di controllo che corrispondono all&#39;ipotesi.
* **Tasso di risposta del gruppo** di controllo: numero di gruppi di controllo partecipanti/numero totale di gruppi di controllo della consegna.
* **Numero di reazioni**: numero di registrazioni nella tabella che contiene il rapporto tra individui, l&#39;ipotesi e la tabella delle transazioni.

Per l&#39;elenco completo degli indicatori, fai clic sul collegamento **[!UICONTROL Display the list]**:

![](assets/response_hypothesis_indicators_002.png)

Gli indicatori forniscono le seguenti informazioni:

* **Entrate totali della popolazione contattata**: importi totali sul numero di persone contattate.
* **Entrate totali del gruppo** di controllo: importi totali sul numero di gruppi di controllo.
* **Entrate medie per contatto**: importi totali / contattati.
* **Entrate medie del gruppo** di controllo: importi totali/gruppo di controllo.
* **Margine totale per contatto**: margine totale su contattato.
* **Margine totale del gruppo** di controllo: margine totale sul gruppo di controllo.
* **Margine medio per contatto**: margine totale / contattato.
* **Margine medio dei gruppi** di controllo: margini totali / gruppo di controllo.
* **Entrate** aggiuntive: (Entrate medie del gruppo di controllo contattato-Entrate medie del gruppo di controllo)*Numero di contatti
* **Margine** aggiuntivo: (Margine medio del gruppo di controllo contattato-Margine medio del gruppo di controllo) / numero di contatti
* **Costo medio per contatto**: costo di consegna calcolato / numero di contatti.
* **ROI**: costo calcolato della consegna / margine totale per contatto
* **ROI** effettivo: costo di consegna calcolato / margine aggiuntivo.
* **Significato**: contiene valori da 0 a 3 a seconda del significato della campagna.

### Reazioni {#reactions}

Puoi visualizzare le reazioni dei destinatari alle ipotesi tramite la scheda **[!UICONTROL Reactions]** .

1. Una volta completato il calcolo delle ipotesi, passa al nodo **[!UICONTROL Campaign management > Measurement hypotheses]** della struttura Adobe Campaign.
1. Seleziona l’ipotesi desiderata e fai clic sulla scheda **[!UICONTROL Reactions]** per visualizzare l’elenco dei destinatari che probabilmente acquisteranno qualcosa dopo la campagna di marketing.

   ![](assets/response_hypothesis_reactions_001.png)

## Rapporti {#reports}

Il **[!UICONTROL Hypothesis report]** ti consente di visualizzare i risultati delle ipotesi eseguite su campagne e consegne. Questo rapporto contiene gli indicatori calcolati dall&#39;ipotesi (per ulteriori informazioni, fare riferimento a [Indicatori](#indicators)).

* **A livello** di campagna: fai clic sul  **[!UICONTROL Reports]** collegamento della campagna pertinente e seleziona il  **[!UICONTROL Hypothesis report]**. Questo rapporto contiene l’elenco delle consegne della campagna e le ipotesi calcolate per ogni consegna.

   ![](assets/response_hypothesis_campaign_report_001.png)

* **A livello** di consegna: per accedere al rapporto, apri la consegna interessata, fai clic su  **[!UICONTROL Reports]** nella  **[!UICONTROL Summary]** scheda e seleziona  **[!UICONTROL Hypothesis report]**. Se per la stessa consegna sono state calcolate diverse ipotesi, la relazione conterrà tutte le ipotesi.

   ![](assets/response_hypothesis_delivery_report_001.png)
