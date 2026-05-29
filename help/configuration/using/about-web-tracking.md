---
product: campaign
title: Informazioni sul tracciamento web
feature: Configuration, Instance Settings
description: Informazioni sul tracciamento web
role: User, Developer
exl-id: 91c31703-75e6-47a4-a877-35682dd687a9
TQID: https://experienceleague.adobe.com/FfA6FEH5WP2JJGVR4BhpjO19Yj4mt8irvyJLwuzCThs
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: d3cdead0-685a-4489-9250-4bb709942f66
feature_v2: []
subfeature_v2: []
source-git-commit: bb41e9407ab5853b0194bb325bbf3f17bc3ea232
workflow-type: tm+mt
source-wordcount: 192
ht-degree: 4%

---

# Informazioni sul tracciamento web{#about-web-tracking}

Oltre al tracciamento standard che mostra il comportamento di un utente Internet che fa clic su un collegamento in un messaggio e-mail, la piattaforma Adobe Campaign ti consente di raccogliere informazioni sulle modalità con cui gli utenti Internet navigano sul tuo sito web. Questa raccolta di dati viene eseguita dal modulo di tracciamento web.

Quando un utente di Internet fa clic su un collegamento tracciato in un’e-mail da una determinata consegna, il server di reindirizzamento contattato deposita un cookie di sessione contenente l’identificatore broadlog (broadlogId) e l’identificatore di consegna (deliveryId).

Il client web invia quindi questo cookie al server ogni volta che l’utente visita una pagina contenente un tag di tracciamento web. Questo continua per tutta la sessione, ovvero fino alla chiusura del client web.

Il server di reindirizzamento raccoglie i dati seguenti in questo modo:

* URL della pagina visualizzata, tramite un identificatore inviato come parametro,
* la consegna dalla quale è stata visitata la pagina web, tramite il cookie di sessione,
* identificatore dell’utente di Internet che ha fatto clic su, tramite il cookie di sessione,
* informazioni aggiuntive, ad esempio il volume di affari generato.

Il diagramma seguente mostra le fasi della finestra di dialogo tra il client e i vari server.

![](assets/d_ncs_integration_webtracking_structure1.png)
