---
solution: Campaign Classic
product: campaign
title: Hook
description: Hook
audience: interaction
content-type: reference
topic-tags: advanced-parameters
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 1%

---


# Hook{#hooks}

Gli hooks in Interaction consentono di modificare il comportamento **standard del motore**.

Gli **[!UICONTROL Target loading]** e **[!UICONTROL Proposition post-processing]** ganci sono configurati, in  Adobe Campaign, nello spazio delle offerte:

![](assets/interaction_hooks_1.png)

Il gancio **[!UICONTROL Dynamic offer]** è configurato con il peso dell&#39;offerta in  Adobe Campaign:

![](assets/interaction_hooks_2.png)

## Caricamento destinazione {#target-loading}

Questo gancio consente di arricchire il profilo del contatto (caricato dalla query out-of-the-box) con dati aggiuntivi da un sistema esterno.

I dati raccolti devono essere inseriti nel nodo dati della chiamata (nodo Interaction). L&#39;integratore deve avere già esteso lo schema dei dati della chiamata per definire la struttura dei dati raccolti. L’utente può accedere a questi dati nello stesso modo dei dati delle chiamate standard (a livello di regole di idoneità e personalizzazione).

**Parametri di input:**

* xmlInteraction (tipo xml): Nodo interazione
* aTargetId (tipo di tabella): identificatore target
* sUuid230 (tipo di stringa): valore del cookie permanente uid230
* sNlid (tipo di stringa): valore del cookie di sessione nlid

**Parametri restituiti:**

* nodo Interazione arricchito (primo parametro di questo gancio)

>[!NOTE]
>
>Il parametro **xmlInteraction** contiene sia i dati della chiamata che il profilo del contatto caricato dalla query out-of-the-box.

**Esempio:**

```
// Call an external system to get additional data for the target
  var additionalData  = getUrl("https://EXTERNAL_SYSTEM?target=" + encodeURIComponent(aTargetId.join("|")));
  // Enrich the context with this data
  interaction.@additionalData = additionalData;
```

## Post-elaborazione proposta {#proposition-post-processing-}

Questo gancio consente di verificare la coerenza e la compatibilità delle proposte idonee in una determinata interazione. Consente inoltre di definire una nuova funzionalità di punteggio o calcolo delle probabilità.

Esempio di utilizzo di regole di coerenza:

* Limitazione del numero di proposte nella stessa chiamata, collegate allo stesso prodotto o alla stessa categoria.
* Presentare solo offerte relative a un prodotto nella stessa interazione.

La post-elaborazione viene eseguita dopo l&#39;applicazione delle regole di tipologia e l&#39;ordinamento delle proposte idonee, e prima della fase di definizione delle priorità.

**Parametri di input:**

* Proposta: tabella delle proposte ammissibili. Esempio della struttura di un elemento in questa tabella

   ```
   { offer_id:1234,
     weight:2}
   ```

* dicOffer (tipo xml): dizionario di tutti gli attributi delle offerte idonee (codice offerta, ID categoria, nome completo categoria, data di inizio, data di fine, etichetta, nome interno, ID offerta, campi offerta aggiuntivi). Ad esempio

   ```
   { "1242": <offer category-id="61242" categoryFullName="/FULL/PATH/TO/CATEGORY/" code="CODE" endDate="" id="62473" label="LABEL" name="OFR38_OE4" product-id="43" startDate=""/>,
     "1243": ...}
   ```

* xmlTarget (tipo xml): nodo dati profilo
* xmlInteraction (tipo xml): call data node
* iPropNumber (tipo intero): numero di offerte previste

**Parametri restituiti:**

* elenco di proposte modificate (primo parametro del gancio)
* nodo Interazione modificato

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

Questo gancio consente di effettuare una chiamata a un motore esterno per selezionare un elenco di prodotti collegati a un&#39;offerta. È configurato nell&#39;offerta dopo le regole di idoneità e prima dell&#39;applicazione delle regole di tipologia.

In precedenza, l&#39;integratore dovrebbe estendere lo schema delle proposizioni **PropositionRcp** con le informazioni aggiuntive sul prodotto. Per specificare dove memorizzare i dati, nella scheda **[!UICONTROL Storage]** dello spazio è disponibile un collegamento **[!UICONTROL Proposition being processed]**

![](assets/interaction_hooks_3.png)

**Parametri di input:**

* xmlOffer (tipo xml): offerta (codice offerta, ID categoria, nome completo categoria, data di inizio, data di fine, etichetta, nome interno, ID offerta, campi aggiuntivi per le offerte)
* dWeight: spessore del contesto (tipo doppio)
* xmlTarget (tipo xml): nodo dati profilo
* xmlInteraction (tipo xml): call data node

**Parametri restituiti:**

Viene restituito un indice di proposizioni da generare. Ciascun elemento di questa tabella è costituito dalle seguenti informazioni:

* offer identifier
* dati di prodotto aggiuntivi (ad esempio, codice prodotto)
* weight

>[!NOTE]
>
>Il sistema verifica che l&#39;ID dell&#39;offerta sia lo stesso per i parametri di input e di ritorno.

**Esempio:**

```
var product = getUrl("https://EXTERNAL_SYSTEM?offerCode=" + encodeURIComponent(xmlOffer.@code));
if( product )
  return [{offer_id: parseInt(String(xmlOffer.@id)), weight: dWeight, productId: product}];
```

