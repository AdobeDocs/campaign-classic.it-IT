---
title: Informazioni sul tracciamento Web
seo-title: Informazioni sul tracciamento Web
description: Informazioni sul tracciamento Web
seo-description: null
page-status-flag: never-activated
uuid: 59d18ffb-c26e-4571-8364-5e85ec587349
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 38ba9be9-dabc-41d4-878c-d772955301fe
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Informazioni sul tracciamento Web{#about-web-tracking}

Oltre al tracciamento standard che mostra il comportamento di un utente di Internet che fa clic su un collegamento in un messaggio e-mail, la piattaforma Adobe Campaign consente di raccogliere informazioni sul modo in cui gli utenti di Internet consultano il sito Web. Questa raccolta dati viene eseguita dal modulo di tracciamento Web.

Quando un utente di Internet fa clic su un collegamento tracciato in un messaggio e-mail da una data consegna, il server di reindirizzamento ha contattato per depositare un cookie di sessione contenente l’identificatore del registro di trasmissione (BroadlogId) e l’identificatore della consegna (deliveryId).

Il client Web invia quindi questo cookie al server ogni volta che l&#39;utente visita una pagina contenente un tag di tracciamento Web. Questa situazione continua per tutta la sessione, ossia fino alla chiusura del client Web.

Il server di reindirizzamento raccoglie i dati seguenti in questo modo:

* URL della pagina visualizzata, tramite un identificatore inviato come parametro,
* la consegna da cui è stata visitata la pagina Web, tramite il cookie di sessione,
* identificatore dell’utente Internet che ha fatto clic, tramite il cookie di sessione,
* informazioni aggiuntive, ad esempio il volume di business generato.

Il diagramma seguente mostra le fasi della finestra di dialogo tra il client e i vari server.

![](assets/d_ncs_integration_webtracking_structure1.png)

