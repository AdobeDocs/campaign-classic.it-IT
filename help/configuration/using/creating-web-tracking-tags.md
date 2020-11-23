---
solution: Campaign Classic
product: campaign
title: Creazione di etichette di web tracking
description: Creazione di etichette di web tracking
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 4%

---


# Creazione di etichette di web tracking{#creating-web-tracking-tags}

Ogni pagina del sito da monitorare deve essere indicata nella piattaforma Adobe Campaign . Questo riferimento può essere eseguito in due modi:

1. definizione manuale degli URL da tracciare,
1. Creazione rapida di URL da tracciare.

## Definizione degli URL da tracciare nell’applicazione {#defining-the-urls-to-be-tracked-in-the-application}

Questo metodo consente di definire manualmente le pagine da tracciare e di generare un esempio del tag di tracciamento Web associato. Questa operazione è definita nel **[!UICONTROL Campaign execution>Resources>Web tracking tags]** nodo della console client.

![](assets/d_ncs_integration_webtracking_screen.png)

Per generare il codice HTML da inserire nella pagina:

* Immettete l’etichetta del tag: sarà visualizzato nei registri di monitoraggio,
* Indicate l’URL sorgente: questo campo è a scopo informativo e consente di indicare la pagina tracciata (facoltativo),
* Se necessario, inserire un periodo di validità,
* Fate clic su Codice **[!UICONTROL Generate]** HTML.

Quindi copiate il codice generato e incollatelo nella pagina da monitorare.

## Creazione rapida di URL da tracciare {#on-the-fly-creation-of-urls-to-be-tracked}

Potete creare al volo gli URL di tracciamento Web aggiungendo informazioni al valore del parametro **tagid** :

* Tipo di pagina tracciata: &#39;w&#39; per WEB o &#39;t&#39; per TRANSAZIONE,
* Nome interno della cartella in cui deve essere creato l’URL.

Queste due informazioni devono essere concatenate con l&#39;identificatore della pagina tracciata aggiungendo il carattere &quot;|&quot;:

```
tagid=<identifier>|<type>|<foldername>
```

>[!IMPORTANT]
>
>Ricorda di codificare il valore del parametro **tagid** quando viene utilizzato come parametro URL.

**Esempio**: creazione di un URL di tracciamento Web di tipo transazione.

**http://myserver.adobe.com/r/a?tagid=home%7Ct%7CMyFolder**
