---
product: campaign
title: Raccolta di tutte le visite
description: Raccolta di tutte le visite
feature: Configuration, Instance Settings
role: Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
exl-id: cc554d0d-bbab-4f72-b870-5fef5a2fda9d
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 5%

---

# Raccolta di tutte le visite{#collecting-all-visits}

Il modulo di web tracking fornito da Adobe Campaign ti consente di raccogliere le visite ad alcune pagine del sito eseguite da un destinatario nel contesto del site tracking a seguito di un clic in un messaggio.

Tuttavia, puoi configurare la piattaforma in modo che raccolga tutte le visite alle pagine con un tag di tracciamento web da parte di un utente noto alla piattaforma.

Un utente noto alla piattaforma è un destinatario che è già stato oggetto di targeting da una consegna e che ha fatto clic almeno una volta su un messaggio ricevuto. Per identificare questo destinatario viene utilizzato un cookie permanente.

>[!IMPORTANT]
>
>La piattaforma Adobe Campaign non è destinata all’utilizzo come strumento di tracciamento del sito web, se non nel contesto di una visita del sito a seguito di un clic in un messaggio. Se questa opzione è abilitata, può causare un utilizzo molto elevato delle risorse sui computer che ospitano i server (reindirizzamento, applicazione e database). È consigliabile assicurarsi che l’architettura hardware in uso supporti questo carico e evitare di inserire tag di tracciamento web nelle pagine visitate più di frequente, ad esempio nella home page.

## Configurazione del server {#server-configuration}

I server vengono configurati sovraccaricando alcuni elementi della **serverConf.xml** file. Questi file vengono salvati in **conf** sottodirectory della directory di installazione di Adobe Campaign.

### Server di reindirizzamento {#redirection-server}

Per il server di reindirizzamento, impostare **trackWebVisitors** attributo del **reindirizzamento** elemento a **true**.

```
<redirection P3PCompactPolicy="CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV"
databaseId="" defLogCount="30" expirationURL="" maxJobsInCache="100"
startRedirection="true" startRedirectionInModule="true" trackWebVisitors="true"
trackingPassword=""
```

## Configurazione di una campagna di corrispondenza predefinita {#configuring-a-default-matching-campaign}

Per visualizzare le informazioni di tracciamento tramite la console client, è necessario:

* Creare un **consegna fittizia** (la mappatura della consegna deve essere identica a quella dello schema di destinazione),
* Inserisci il **nome interno** di questa consegna in **NmsTracking_WebTrackingDelivery** opzione.

Tutte le informazioni di tracciamento del sito non direttamente successive a un clic in un’e-mail possono essere visualizzate nella consegna fittizia creata.
