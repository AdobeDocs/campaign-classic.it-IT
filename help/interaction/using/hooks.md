---
product: campaign
title: Hook
description: Hook
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: e1d7d7c2-61e7-40d6-a8ce-69bc976f8c73
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 1%

---

# Hook{#hooks}

I blocchi in Interazione consentono di modificare il comportamento **del motore standard**.

Gli hook **[!UICONTROL Target loading]** e **[!UICONTROL Proposition post-processing]** sono configurati, in Adobe Campaign, nello spazio dell’offerta:

![](assets/interaction_hooks_1.png)

Il gancio **[!UICONTROL Dynamic offer]** è configurato con il peso dell&#39;offerta in Adobe Campaign:

![](assets/interaction_hooks_2.png)

## Caricamento della destinazione {#target-loading}

Questo gancio ti consente di arricchire il profilo del contatto (caricato dalla query preconfigurata) con dati aggiuntivi provenienti da un sistema esterno.

I dati raccolti devono essere inseriti nel nodo di dati della chiamata (nodo di interazione). L’integratore deve aver precedentemente esteso lo schema dei dati di chiamata per definire la struttura dei dati raccolti. L’utente può accedere a questi dati nello stesso modo in cui si trovano per i dati delle chiamate standard (a livello di regole di idoneità e personalizzazione).

**Parametri di input:**

* xmlInteraction (tipo xml): Nodo di interazione
* aTargetId (tipo di tabella): identificatore target
* sUid230 (tipo di stringa): valore del cookie permanente uuid230
* sNlid (tipo di stringa): valore del cookie di sessione nlid

**Parametri di ritorno:**

* nodo di interazione arricchito (primo parametro di questo gancio)

>[!NOTE]
>
>Il parametro **xmlInteraction** contiene sia i dati della chiamata che il profilo del contatto caricato dalla query preconfigurata.

**Esempio:**

```
// Call an external system to get additional data for the target
  var additionalData  = getUrl("https://EXTERNAL_SYSTEM?target=" + encodeURIComponent(aTargetId.join("|")));
  // Enrich the context with this data
  interaction.@additionalData = additionalData;
```

## Post-elaborazione della proposta {#proposition-post-processing-}

Questo gancio consente di verificare la coerenza e la compatibilità delle proposte idonee in una determinata interazione. Consente inoltre di definire una nuova funzionalità di calcolo del punteggio o della probabilità.

Esempio di utilizzo delle regole di coerenza:

* Limitazione del numero di proposte nella stessa chiamata, collegate allo stesso prodotto o alla stessa categoria.
* Presentare solo offerte relative a un prodotto nella stessa interazione.

Il processo di post-elaborazione viene eseguito dopo l’applicazione delle regole di tipologia e l’ordinamento delle proposte idonee, e prima della fase di definizione delle priorità.

**Parametri di input:**

* Proposta: tabella delle proposte ammissibili. Ecco un esempio della struttura di un elemento in questa tabella

   ```
   { offer_id:1234,
     weight:2}
   ```

* dicOffer (tipo xml): dizionario di tutti gli attributi delle offerte idonee (codice offerta, ID categoria, nome completo categoria, data di inizio, data di fine, etichetta, nome interno, id offerta, campi di offerta aggiuntivi). Ad esempio

   ```
   { "1242": <offer category-id="61242" categoryFullName="/FULL/PATH/TO/CATEGORY/" code="CODE" endDate="" id="62473" label="LABEL" name="OFR38_OE4" product-id="43" startDate=""/>,
     "1243": ...}
   ```

* xmlTarget (tipo xml): nodo dati profilo
* xmlInteraction (tipo xml): nodo dati di chiamata
* iPropNumber (tipo intero): numero di offerte previste

**Parametri di ritorno:**

* elenco delle proposte modificate (primo parametro del gancio)
* nodo di interazione modificato

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

Questo gancio consente di effettuare una chiamata a un motore esterno per selezionare un elenco di prodotti collegati a un’offerta. Viene configurato nell’offerta dopo le regole di idoneità e prima dell’applicazione delle regole di tipologia.

In precedenza, l&#39;integratore dovrebbe estendere lo schema delle proposte **PropositionRcp** con le informazioni aggiuntive sul prodotto. Per specificare dove memorizzare questi dati, nella scheda **[!UICONTROL Storage]** dello spazio è disponibile un collegamento **[!UICONTROL Proposition being processed]**

![](assets/interaction_hooks_3.png)

**Parametri di input:**

* xmlOffer (tipo xml): offerta (codice offerta, id categoria, nome completo categoria, data di inizio, data di fine, etichetta, nome interno, id offerta, campi offerta aggiuntivi)
* dPeso: peso contestuale (doppio tipo)
* xmlTarget (tipo xml): nodo dati profilo
* xmlInteraction (tipo xml): nodo dati di chiamata

**Parametri di ritorno:**

Viene restituita una tabella di proposte da generare. Ogni elemento di questa tabella è costituito dalle seguenti informazioni:

* identificatore di offerta
* dati di prodotto aggiuntivi (ad esempio, codice prodotto)
* weight

>[!NOTE]
>
>Il sistema controlla che l’id dell’offerta sia lo stesso per i parametri di input e di ritorno.

**Esempio:**

```
var product = getUrl("https://EXTERNAL_SYSTEM?offerCode=" + encodeURIComponent(xmlOffer.@code));
if( product )
  return [{offer_id: parseInt(String(xmlOffer.@id)), weight: dWeight, productId: product}];
```
