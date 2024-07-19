---
product: campaign
title: Tracciare l’ipotesi
description: Scopri come tracciare le ipotesi in Campaign Response Manager
feature: Campaigns, Monitoring, Reporting
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
audience: campaign
content-type: reference
topic-tags: response-manager
exl-id: 1dc6d03b-698c-4750-9563-0676fcd185df
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 1%

---

# Tracciamento delle ipotesi{#hypothesis-tracking}



Il risultato dei calcoli delle ipotesi è disponibile a vari livelli della piattaforma Adobe Campaign: gli indicatori calcolati dalle ipotesi e le reazioni delle popolazioni target sono visibili tramite l’ipotesi effettiva, nonché nei rapporti sulle ipotesi disponibili tramite campagne e consegne.

## Risultati ipotesi {#hypothesis-results}

### Indicatori {#indicators}

Una volta calcolata l’ipotesi, diversi indicatori di misurazione vengono aggiornati automaticamente. Sono disponibili nella scheda **[!UICONTROL General]** dell’ipotesi.

![](assets/response_hypothesis_delivery_example_010.png)

Tali indicatori sono:

* **Numero di contatti dei partecipanti**: numero di persone contattate che corrispondono all&#39;ipotesi.
* **Percentuale di risposte contattate**: numero di contatti dei partecipanti/numero totale di persone contattate durante la consegna.
* **Numero di contatti del gruppo di controllo dei partecipanti**: numero di gruppi di controllo corrispondenti all&#39;ipotesi.
* **Percentuale di risposte del gruppo di controllo**: numero di gruppi di controllo partecipanti/numero totale di gruppi di controllo di consegna.
* **Numero di reazioni**: numero di record nella tabella che contiene la relazione tra i singoli utenti, l&#39;ipotesi e la tabella delle transazioni.

Per l&#39;elenco completo degli indicatori, fare clic sul collegamento **[!UICONTROL Display the list]**:

![](assets/response_hypothesis_indicators_002.png)

Gli indicatori forniscono le seguenti informazioni:

* **Ricavi totali della popolazione contattata**: importi totali superiori al numero di individui contattati.
* **Ricavi totali del gruppo di controllo**: importi totali rispetto al numero di gruppi di controllo.
* **Ricavi medi per contatto**: importi totali / contattati.
* **Ricavi medi del gruppo di controllo**: importi totali/gruppo di controllo.
* **Margine totale per contatto**: margine totale su contattato.
* **Margine totale del gruppo di controllo**: margine totale sul gruppo di controllo.
* **Margine medio per contatto**: margine totale / contattato.
* **Margine medio dei gruppi di controllo**: margini totali/gruppo di controllo.
* **Ricavi aggiuntivi**: (Ricavi medi dei contatti-Ricavi medi del gruppo di controllo)&#42;Numero di contatti
* **Margine aggiuntivo**: (Margine medio dei contatti-Margine medio del gruppo di controllo) / numero di contatti
* **Costo medio per contatto**: costo di consegna calcolato / Numero di contatti.
* **ROI**: costo calcolato della consegna / Margine totale per contatto
* **ROI effettivo**: costo di consegna calcolato/margine aggiuntivo.
* **Significatività**: contiene i valori da 0 a 3 a seconda della significatività della campagna.

### Reazioni {#reactions}

Puoi visualizzare le reazioni dei destinatari alle ipotesi tramite la scheda **[!UICONTROL Reactions]**.

1. Una volta completato il calcolo dell’ipotesi, passa al nodo **[!UICONTROL Campaign management > Measurement hypotheses]** della struttura Adobe Campaign.
1. Selezionare l&#39;ipotesi desiderata e fare clic sulla scheda **[!UICONTROL Reactions]** per visualizzare l&#39;elenco dei destinatari che probabilmente acquisteranno qualcosa dopo la campagna di marketing.

   ![](assets/response_hypothesis_reactions_001.png)

## Rapporti {#reports}

**[!UICONTROL Hypothesis report]** consente di visualizzare i risultati delle ipotesi eseguite sulle campagne e sulle consegne. Questo report contiene gli indicatori calcolati dall&#39;ipotesi (per ulteriori informazioni, consulta [Indicatori](#indicators)).

* **A livello di campagna**: fai clic sul collegamento **[!UICONTROL Reports]** della campagna pertinente e seleziona **[!UICONTROL Hypothesis report]**. Questo rapporto contiene l’elenco delle consegne delle campagne e le ipotesi calcolate per ciascuna consegna.

  ![](assets/response_hypothesis_campaign_report_001.png)

* **Al livello di consegna**: per accedere al report, aprire la consegna interessata, fare clic su **[!UICONTROL Reports]** nella scheda **[!UICONTROL Summary]** e selezionare **[!UICONTROL Hypothesis report]**. Se sono state calcolate più ipotesi per la stessa consegna, il rapporto conterrà tutte le ipotesi.

  ![](assets/response_hypothesis_delivery_report_001.png)
