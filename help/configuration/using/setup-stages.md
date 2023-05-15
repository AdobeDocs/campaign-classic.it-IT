---
product: campaign
title: Fasi di configurazione
description: Fasi di configurazione
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
exl-id: a5ae0b61-3377-46d9-a327-6c897eeda770
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 2%

---

# Fasi di configurazione{#setup-stages}

Il principio di base è l&#39;inserimento di tag di web tracking in alcune pagine del sito web.

Esistono due tipi di tag:

* **WEB**: questo tag indica se la pagina è stata visitata,
* **TRANSAZIONE**: funziona come un tag web, ma con la possibilità di aggiungere informazioni sul volume di business generato, ad esempio (importo della transazione, numero di articoli acquistati, ecc.).

Per impostare questi tag, effettua le seguenti operazioni:

1. Identificare le pagine da monitorare e determinarne il tipo (WEB o TRANSAZIONE).
1. Stabilire quali informazioni aggiuntive si desidera raccogliere ed estendere il **nms:webTrackingLog** schema con la descrizione di queste informazioni. Per impostazione predefinita, questo schema può memorizzare gli importi delle transazioni e il numero di elementi per transazione.
1. Creazione di tag di web tracking. Ci sono due modi per farlo:

   * Inserisci gli URL corrispondenti a queste pagine nella tua piattaforma Adobe Campaign, quindi genera ed estrae i tag di web tracking associati (dal **[!UICONTROL Campaign execution>Resources>Web tracking tags]** nodo della console client).
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
