---
product: campaign
title: Fasi di configurazione
description: Fasi di configurazione
feature: Configuration
role: Developer
exl-id: a5ae0b61-3377-46d9-a327-6c897eeda770
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 2%

---

# Fasi di configurazione{#setup-stages}

Il principio di base è l’inserimento di tag di tracciamento web in determinate pagine del sito web.

Esistono due tipi di tag:

* **WEB**: questo tag indica se la pagina è stata visitata,
* **TRANSAZIONE**: funziona come un tag Web, ma con la possibilità di aggiungere informazioni sul volume di business generato, ad esempio (importo della transazione, numero di elementi acquistati, ecc.).

Per impostare questi tag, effettua le seguenti operazioni:

1. Identifica le pagine da tracciare e determinane il tipo (WEB o TRANSACTION).
1. Determina quali informazioni aggiuntive desideri raccogliere ed estendi lo schema **nms:webTrackingLog** con la descrizione di queste informazioni. Per impostazione predefinita, questo schema può memorizzare gli importi delle transazioni e il numero di elementi per transazione.
1. Creazione dei tag di tracciamento web. Esistono due modi per farlo:

   * Inserisci gli URL corrispondenti a queste pagine nella piattaforma Adobe Campaign, quindi genera ed estrai i tag di tracciamento web associati (dal nodo **[!UICONTROL Campaign execution>Resources>Web tracking tags]** della console client).
   * Crea tu stesso i tag di web-tracking in modalità &quot;creazione immediata&quot;: gli URL corrispondenti a queste pagine verranno inseriti automaticamente nella tua piattaforma Adobe Campaign.

1. Aggiungi questi tag in modo statico o dinamico nelle pagine che desideri tracciare.

   >[!NOTE]
   >
   >Tutti i tag di tipo WEB possono essere aggiunti così come sono alle pagine del sito. I tag TRANSACTION devono essere modificati o aggiunti in modo dinamico per contenere le informazioni aggiuntive (importo, elementi, ecc.).

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
