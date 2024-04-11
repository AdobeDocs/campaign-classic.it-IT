---
product: campaign
title: Hook
description: Hook
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: e1d7d7c2-61e7-40d6-a8ce-69bc976f8c73
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 1%

---

# Modificare il comportamento standard del motore{#hooks}



Gli hook nell’interazione consentono di modificare **comportamento standard del motore**.

Il **[!UICONTROL Target loading]** e **[!UICONTROL Proposition post-processing]** Gli hook di sono configurati, in Adobe Campaign, nello spazio dell’offerta:

![](assets/interaction_hooks_1.png)

Il **[!UICONTROL Dynamic offer]** l’hook è configurato con il peso dell’offerta in Adobe Campaign:

![](assets/interaction_hooks_2.png)

## Caricamento di Target {#target-loading}

Questo hook ti consente di arricchire il profilo del contatto (caricato dalla query preconfigurata) con dati aggiuntivi provenienti da un sistema esterno.

I dati raccolti devono essere inseriti nel nodo dei dati della chiamata (nodo di interazione). L’integratore deve aver esteso in precedenza lo schema dei dati della chiamata per definire la struttura dei dati raccolti. L’utente può accedere a questi dati con le stesse modalità dei dati di chiamata standard (a livello di regole di idoneità e personalizzazione).

**Parametri di input:**

* xmlInteraction (tipo xml): nodo di interazione
* aTargetId (tipo di tabella): identificatore di destinazione
* sUuid230 (tipo stringa): valore del cookie permanente uuid230
* Nlid (tipo stringa): valore del cookie di sessione nlid

**Parametri restituiti:**

* Nodo di interazione arricchito (primo parametro di questo hook)

>[!NOTE]
>
>Il **xmlInteraction** Il parametro contiene sia i dati della chiamata che il profilo del contatto caricato dalla query predefinita.

**Esempio:**

```
// Call an external system to get additional data for the target
  var additionalData  = getUrl("https://EXTERNAL_SYSTEM?target=" + encodeURIComponent(aTargetId.join("|")));
  // Enrich the context with this data
  interaction.@additionalData = additionalData;
```

## Post-elaborazione della proposta {#proposition-post-processing-}

Questo hook consente di verificare la coerenza e la compatibilità delle proposte idonee in una determinata interazione. Consente inoltre di definire una nuova funzionalità di calcolo del punteggio o della probabilità.

Esempio di utilizzo delle regole di coerenza:

* Limitare il numero di proposte nella stessa chiamata, collegate allo stesso prodotto o alla stessa categoria.
* Presentare solo offerte relative a un prodotto nella stessa interazione.

La post-elaborazione viene eseguita dopo l’applicazione delle regole di tipologia e l’ordinamento delle proposte idonee e prima del passaggio di definizione delle priorità.

**Parametri di input:**

* Proposta: tabella delle proposte ammissibili. Esempio di struttura di un elemento nella tabella

  ```
  { offer_id:1234,
    weight:2}
  ```

* dicOffer (tipo xml): dizionario di tutti gli attributi delle offerte idonee (codice offerta, id categoria, nome completo categoria, data di inizio, data di fine, etichetta, nome interno, id offerta, campi offerta aggiuntivi). Ad esempio

  ```
  { "1242": <offer category-id="61242" categoryFullName="/FULL/PATH/TO/CATEGORY/" code="CODE" endDate="" id="62473" label="LABEL" name="OFR38_OE4" product-id="43" startDate=""/>,
    "1243": ...}
  ```

* xmlTarget (tipo xml): nodo dati profilo
* xmlInteraction (tipo xml): chiama nodo dati
* iPropNumber (tipo intero): numero di offerte previste

**Parametri restituiti:**

* elenco delle proposte modificate (primo parametro dell&#39;hook)
* nodo interazione modificato

**Esempio:**

```
var aReturnedProps = [];

if( aProposition.length > 0 )
{
  var iReturnedProps = 0;
  for( var iPropIdx = 0; iPropIdx < aProposition.length && iReturnedProps < iPropNumber; iPropIdx ++ )
  {
    // Check a consistency rule for instance
    if( true )
    {
      aReturnedProps.push(aProposition[iPropIdx]);
      iReturnedProps++;
    }
  }
}

return aReturnedProps;
```

## Offerta dinamica {#dynamic-offer}

Questo hook consente di effettuare una chiamata a un motore esterno per selezionare un elenco di prodotti collegati a un’offerta. È configurato nell’offerta dopo le regole di idoneità e prima dell’applicazione delle regole di tipologia.

In anticipo, l’integratore deve estendere le proposte **PropositionRcp** con le informazioni aggiuntive sul prodotto. Per specificare la posizione in cui verranno memorizzati i dati, **[!UICONTROL Proposition being processed]** è disponibile nella sezione **[!UICONTROL Storage]** scheda dello spazio

![](assets/interaction_hooks_3.png)

**Parametri di input:**

* xmlOffer (tipo xml): offerta (codice offerta, ID categoria, nome completo categoria, data di inizio, data di fine, etichetta, nome interno, ID offerta, campi offerta aggiuntivi)
* dWeight: peso contestuale (tipo doppio)
* xmlTarget (tipo xml): nodo dati profilo
* xmlInteraction (tipo xml): chiama nodo dati

**Parametri restituiti:**

Viene restituita una tabella di proposte da generare. Ogni elemento di questa tabella è composto dalle seguenti informazioni:

* identificatore dell’offerta
* dati di prodotto aggiuntivi (ad esempio codice prodotto)
* peso

>[!NOTE]
>
>Il sistema controlla che l’ID offerta sia lo stesso per i parametri di input e di ritorno.

**Esempio:**

```
var product = getUrl("https://EXTERNAL_SYSTEM?offerCode=" + encodeURIComponent(xmlOffer.@code));
if( product )
  return [{offer_id: parseInt(String(xmlOffer.@id)), weight: dWeight, productId: product}];
```
