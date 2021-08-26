---
product: campaign
title: Informazioni sul tracciamento web
description: Informazioni sul tracciamento web
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
exl-id: 91c31703-75e6-47a4-a877-35682dd687a9
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 4%

---

# Informazioni sul tracciamento web{#about-web-tracking}

![](../../assets/v7-only.svg)

Oltre al tracciamento standard che mostra il comportamento di un utente di Internet che fa clic su un collegamento in un messaggio di posta elettronica, la piattaforma Adobe Campaign ti consente di raccogliere informazioni su come gli utenti di Internet navigano nel tuo sito web. Questa raccolta di dati viene eseguita dal modulo di web tracking.

Quando un utente Internet fa clic su un collegamento tracciato in un messaggio di posta elettronica da una determinata consegna, il server di reindirizzamento contattato deposita un cookie di sessione contenente l&#39;identificatore del registro di trasmissione (broadlogId) e l&#39;identificatore di consegna (deliveryId).

Il client web invia quindi questo cookie al server ogni volta che l&#39;utente visita una pagina contenente un tag di web tracking. Questo continua per tutta la sessione, cioè fino alla chiusura del client web.

Il server di reindirizzamento raccoglie i dati seguenti in questo modo:

* URL della pagina visualizzata tramite un identificatore inviato come parametro,
* la consegna da cui è stata visitata la pagina web, tramite il cookie di sessione,
* identificatore dell’utente Internet che ha fatto clic, tramite il cookie di sessione,
* informazioni aggiuntive, ad esempio il volume di business generato.

Il diagramma seguente mostra le fasi della finestra di dialogo tra il client e i vari server.

![](assets/d_ncs_integration_webtracking_structure1.png)
