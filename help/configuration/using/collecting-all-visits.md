---
product: campaign
title: Raccolta di tutte le visite
description: Raccolta di tutte le visite
exl-id: cc554d0d-bbab-4f72-b870-5fef5a2fda9d
source-git-commit: 3997412f14666fa61bf71d0f0a0653f5cc042e19
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 3%

---

# Raccolta di tutte le visite{#collecting-all-visits}

![](../../assets/v7-only.svg)

Il modulo di web tracking fornito da Adobe Campaign consente di raccogliere le visite a determinate pagine del sito eseguite da un destinatario nel contesto del monitoraggio del sito in seguito a un clic in un messaggio.

Tuttavia, puoi configurare la piattaforma in modo che raccolga tutte le visite alle pagine con un tag di web tracking da parte di un utente noto alla piattaforma.

Un utente noto alla piattaforma è un destinatario che è già stato eseguito il targeting di una consegna e che ha fatto clic su un messaggio ricevuto almeno una volta. Per identificare questo destinatario viene utilizzato un cookie permanente.

>[!IMPORTANT]
>
>La piattaforma Adobe Campaign non è destinata all’utilizzo come strumento di tracciamento del sito web oltre al contesto della visita del sito in seguito a un clic in un messaggio. Quando questa opzione è abilitata, può causare un uso molto elevato delle risorse sui computer che ospitano i server (reindirizzamento, applicazione e database). È consigliabile assicurarsi che l’architettura hardware in uso supporti questo carico ed evitare di inserire tag di web tracking nelle pagine visitate più frequentemente, ad esempio nella home page.

## Configurazione del server {#server-configuration}

I server sono configurati sovraccaricando alcuni elementi del **serverConf.xml** file. Questi file vengono salvati nel **conf** sottodirectory della directory di installazione di Adobe Campaign.

### Server di reindirizzamento {#redirection-server}

Per il server di reindirizzamento, imposta il **trackWebVisitors** dell&#39;attributo **reindirizzamento** elemento a **true**.

```
<redirection P3PCompactPolicy="CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV"
databaseId="" defLogCount="30" expirationURL="" maxJobsInCache="100"
startRedirection="true" startRedirectionInModule="true" trackWebVisitors="true"
trackingPassword=""
```

## Configurazione di una campagna corrispondente predefinita {#configuring-a-default-matching-campaign}

Per visualizzare le informazioni di tracciamento tramite la console client, devi:

* Crea un **consegna fittizia** (la mappatura della consegna deve essere identica alla mappatura dello schema di destinazione),
* Inserisci il **nome interno** di tale consegna **NmsTracking_WebTrackingDelivery** opzione .

Tutte le informazioni di tracciamento del sito non direttamente successive a un clic in un’e-mail possono essere visualizzate nella consegna fittizia creata.
