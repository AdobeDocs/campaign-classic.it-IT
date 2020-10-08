---
title: Raccolta di tutte le visite
seo-title: Raccolta di tutte le visite
description: Raccolta di tutte le visite
seo-description: null
page-status-flag: never-activated
uuid: c2869b3d-33bb-4a22-a8e6-ac037f0665d9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 7f841368-3867-4d6e-9720-c038d9bea0ce
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 4%

---


# Raccolta di tutte le visite{#collecting-all-visits}

Il modulo di monitoraggio Web fornito da  Adobe Campaign consente di raccogliere le visite ad alcune pagine del sito eseguite da un destinatario nel contesto del tracciamento del sito in seguito a un clic in un messaggio.

Tuttavia, potete configurare la piattaforma in modo che raccolga tutte le visite alle pagine con un tag di tracciamento Web da parte di un utente noto alla piattaforma.

Un utente noto alla piattaforma è un destinatario che ha già ricevuto il targeting per una consegna e che ha fatto clic su di essa almeno una volta. Per identificare il destinatario viene utilizzato un cookie permanente.

>[!IMPORTANT]
>
>La piattaforma Adobe Campaign  non è destinata a essere utilizzata come strumento di tracciamento del sito Web oltre al contesto della visita al sito successiva a un clic in un messaggio. Quando questa opzione è attivata, può causare un utilizzo molto elevato delle risorse sui computer in cui sono installati i server (reindirizzamento, applicazione e database). È consigliabile assicurarsi che l&#39;architettura hardware in uso supporti questo carico ed evitare di inserire tag di tracciamento Web nelle pagine visitate più di frequente, come la pagina principale.

## Configurazione server {#server-configuration}

I server sono configurati sovraccaricando alcuni elementi del file **serverConf.xml** . Questi file vengono salvati nella sottodirectory **conf** della directory di installazione di Adobe Campaign .

### Server di reindirizzamento {#redirection-server}

Per il server di reindirizzamento, impostare l&#39;attributo **trackWebVisitors** dell&#39;elemento **redirection** su **true**.

```
<redirection P3PCompactPolicy="CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV"
databaseId="" defLogCount="30" expirationURL="" maxJobsInCache="100"
startRedirection="true" startRedirectionInModule="true" trackWebVisitors="true"
trackingPassword=""
```

## Configurazione di una campagna corrispondente predefinita {#configuring-a-default-matching-campaign}

Per visualizzare le informazioni di tracciamento tramite la console client, è necessario:

* Create una consegna **** fittizia (la mappatura della consegna deve essere identica alla mappatura dello schema di destinazione),
* Immettete il nome **** interno della consegna nell’opzione **NmsTracking_WebTrackingDelivery** .

Tutte le informazioni di tracciamento del sito non direttamente successive a un clic in un messaggio e-mail possono essere visualizzate nel messaggio di consegna creato.
