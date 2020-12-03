---
solution: Campaign Classic
product: campaign
title: Fasi di configurazione
description: Fasi di configurazione
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
translation-type: tm+mt
source-git-commit: c625b4109e2cb47446331cd009ff9827c8267c93
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 2%

---


# Fasi di configurazione{#setup-stages}

Il principio di base è l’inserimento di tag di tracciamento Web in alcune pagine del sito Web.

Esistono due tipi di tag:

* **WEB**: questo tag indica se la pagina è stata visitata,
* **TRANSAZIONE**: funziona come un tag Web, ma con la possibilità di aggiungere informazioni sul volume di business generato, ad esempio (importo della transazione, numero di articoli acquistati, ecc.).

Per impostare questi tag, effettuate le seguenti operazioni:

1. Identificare le pagine da monitorare e determinarne il tipo (WEB o TRANSAZIONE).
1. Determinare quali informazioni aggiuntive si desidera raccogliere ed estendere lo schema **nms:webTrackingLog** con la descrizione di queste informazioni. Per impostazione predefinita, questo schema può memorizzare gli importi delle transazioni e il numero di articoli per transazione.
1. Creazione di tag di tracciamento Web. Esistono due modi per farlo:

   * Inserite gli URL corrispondenti a queste pagine nella piattaforma Adobe Campaign , quindi generate ed estraete i tag di tracciamento Web associati (dal nodo **[!UICONTROL Campaign execution>Resources>Web tracking tags]** della console client).
   * Create i tag di tracciamento Web in modalità &quot;creazione rapida&quot;: gli URL corrispondenti a queste pagine verranno inseriti automaticamente nella piattaforma Adobe Campaign .

1. Aggiungete questi tag in modo statico o dinamico nelle pagine da monitorare.

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

