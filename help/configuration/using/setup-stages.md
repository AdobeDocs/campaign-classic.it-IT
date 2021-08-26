---
product: campaign
title: Fasi di configurazione
description: Fasi di configurazione
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
exl-id: a5ae0b61-3377-46d9-a327-6c897eeda770
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 2%

---

# Fasi di configurazione{#setup-stages}

![](../../assets/v7-only.svg)

Il principio di base è l&#39;inserimento di tag di web tracking in alcune pagine del sito web.

Esistono due tipi di tag:

* **WEB**: questo tag indica se la pagina è stata visitata,
* **TRANSAZIONE**: funziona come un tag web, ma con la possibilità di aggiungere informazioni sul volume di business generato, ad esempio (importo della transazione, numero di articoli acquistati, ecc.).

Per impostare questi tag, effettua le seguenti operazioni:

1. Identificare le pagine da monitorare e determinarne il tipo (WEB o TRANSAZIONE).
1. Stabilisci quali informazioni aggiuntive desideri raccogliere ed estendere lo schema **nms:webTrackingLog** con la descrizione di queste informazioni. Per impostazione predefinita, questo schema può memorizzare gli importi delle transazioni e il numero di elementi per transazione.
1. Creazione di tag di web tracking. Ci sono due modi per farlo:

   * Inserisci gli URL corrispondenti a queste pagine nella piattaforma Adobe Campaign, quindi genera ed estrae i tag di web tracking associati (dal nodo **[!UICONTROL Campaign execution>Resources>Web tracking tags]** della console client).
   * Crea tu stesso i tag di web tracking in modalità &quot;on-the-fly create&quot;: gli URL corrispondenti a queste pagine verranno inseriti automaticamente nella piattaforma Adobe Campaign.

1. Aggiungi questi tag in modo statico o dinamico nelle pagine da monitorare.

   >[!NOTE]
   >
   >Tutti i tag di tipo WEB possono essere aggiunti così come sono alle pagine del sito. I tag TRANSAZIONE devono essere modificati o aggiunti dinamicamente per contenere le informazioni aggiuntive (quantità, elementi, ecc.).

**Esempio**:

```
<script type="text/javascript">
var _f = "nmsWebTracking"
var _t = window.location.href.match(/.*://[^/]*(/[^?#&]*)/)[1] + "|w|" + _f
document.write("<img height='0' width='0' alt='' src='" +
window.location.protocol + "//tsupport/r/" +
Math.random().toString() + "?tagid=" + escape(_t) + "'/>")
</script>
```
