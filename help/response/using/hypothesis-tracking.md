---
product: campaign
title: Tracciare l’ipotesi
description: Scopri come tracciare le ipotesi in Campaign Response Manager
feature: Campaigns, Monitoring, Reporting
badge-v7: label="v7" type="Informative" tooltip="Applicabile a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
audience: campaign
content-type: reference
topic-tags: response-manager
exl-id: 1dc6d03b-698c-4750-9563-0676fcd185df
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 1%

---

# Tracciamento delle ipotesi{#hypothesis-tracking}



Il risultato dei calcoli delle ipotesi è disponibile a vari livelli della piattaforma Adobe Campaign: gli indicatori calcolati dalle ipotesi e le reazioni delle popolazioni target sono visibili tramite l’ipotesi effettiva, nonché nei rapporti sulle ipotesi disponibili tramite campagne e consegne.

## Risultati ipotesi {#hypothesis-results}

### Indicatori {#indicators}

Una volta calcolata l’ipotesi, diversi indicatori di misurazione vengono aggiornati automaticamente. Questi sono disponibili nel **[!UICONTROL General]** dell’ipotesi.

![](assets/response_hypothesis_delivery_example_010.png)

Tali indicatori sono:

* **Numero di contatti dei partecipanti**: numero di individui contattati che corrispondono all’ipotesi.
* **Percentuale di risposte contattate**: numero di contatti dei partecipanti/totale delle persone contattate durante la consegna.
* **Numero di contatti del gruppo di controllo dei partecipanti**: numero di gruppi di controllo che corrispondono all’ipotesi.
* **Tasso di risposta del gruppo di controllo**: numero di gruppi di controllo dei partecipanti/numero totale di gruppi di controllo della consegna.
* **Numero di reazioni**: numero di record nella tabella che contiene la relazione tra i singoli utenti, l’ipotesi e la tabella delle transazioni.

Per l’elenco completo degli indicatori, fai clic su **[!UICONTROL Display the list]** collegamento:

![](assets/response_hypothesis_indicators_002.png)

Gli indicatori forniscono le seguenti informazioni:

* **Ricavi totali della popolazione contattata**: importi totali superiori al numero di persone contattate.
* **Ricavi totali del gruppo di controllo**: importi totali rispetto al numero di gruppi di controllo.
* **Ricavi medi per contatto**: importi totali / contattati.
* **Ricavi medi del gruppo di controllo**: importi totali/gruppo di controllo.
* **Margine totale per contatto**: margine totale su contattato.
* **Margine totale del gruppo di controllo**: margine totale sul gruppo di controllo.
* **Margine medio per contatto**: margine totale / contattato.
* **Margine medio dei gruppi di controllo**: margini totali/gruppo di controllo.
* **Ricavi aggiuntivi**: (Ricavi medi dei contatti - Ricavi medi del gruppo di controllo)&#42;Numero di contatti
* **Margine aggiuntivo**: (Margine medio di contattato-Margine medio del gruppo di controllo) / numero di contattati
* **Costo medio per contatto**: costo di consegna calcolato / numero di contatti.
* **ROI**: costo calcolato della consegna / Margine totale per contatto
* **ROI effettivo**: costo di consegna calcolato/margine aggiuntivo.
* **Significatività**: contiene i valori da 0 a 3 a seconda del significato della campagna.

### Reazioni {#reactions}

Puoi visualizzare le reazioni dei destinatari alle ipotesi tramite **[!UICONTROL Reactions]** scheda.

1. Una volta completato il calcolo dell’ipotesi, vai al **[!UICONTROL Campaign management > Measurement hypotheses]** della struttura Adobe Campaign.
1. Seleziona l’ipotesi desiderata e fai clic su **[!UICONTROL Reactions]** per visualizzare l’elenco dei destinatari che potrebbero acquistare qualcosa dopo la campagna di marketing.

   ![](assets/response_hypothesis_reactions_001.png)

## Rapporti {#reports}

Il **[!UICONTROL Hypothesis report]** consente di visualizzare i risultati delle ipotesi eseguite sulle campagne e sulle consegne. Questo rapporto contiene gli indicatori calcolati dall’ipotesi (per ulteriori informazioni, consulta [Indicatori](#indicators)).

* **A livello di campagna**: fai clic su **[!UICONTROL Reports]** collegamento della campagna in questione e seleziona la **[!UICONTROL Hypothesis report]**. Questo rapporto contiene l’elenco delle consegne delle campagne e le ipotesi calcolate per ciascuna consegna.

  ![](assets/response_hypothesis_campaign_report_001.png)

* **A livello di consegna**: per accedere al rapporto, apri la consegna interessata, fai clic su **[!UICONTROL Reports]** nel **[!UICONTROL Summary]** e seleziona la scheda **[!UICONTROL Hypothesis report]**. Se sono state calcolate più ipotesi per la stessa consegna, il rapporto conterrà tutte le ipotesi.

  ![](assets/response_hypothesis_delivery_report_001.png)
