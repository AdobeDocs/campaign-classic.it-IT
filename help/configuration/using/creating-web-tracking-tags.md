---
product: campaign
title: Creazione di tag di tracciamento web
description: Creazione di tag di tracciamento web
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
exl-id: 160df6e1-43e5-4eb9-ad2f-5db444e314ea
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 4%

---

# Creazione di tag di tracciamento web{#creating-web-tracking-tags}

![](../../assets/v7-only.svg)

Ogni pagina del sito che desideri monitorare deve essere referenziata nella tua piattaforma Adobe Campaign. Questo riferimento può essere eseguito in due modi:

1. Definizione manuale degli URL da tracciare,
1. Creazione rapida di URL da tracciare.

## Definizione degli URL da tracciare nell’applicazione {#defining-the-urls-to-be-tracked-in-the-application}

Questo metodo ti consente di definire manualmente le pagine da tracciare e quindi di generare un esempio del tag di web tracking associato. Questa operazione è definita nel nodo **[!UICONTROL Campaign execution>Resources>Web tracking tags]** della console client.

![](assets/d_ncs_integration_webtracking_screen.png)

Per generare il codice HTML da inserire nella pagina:

* Inserisci l’etichetta del tag: sarà mostrato nei registri di tracciamento,
* Indica l’URL di origine: questo campo è a scopo informativo e consente di indicare la pagina tracciata (facoltativo),
* Se necessario, inserire un periodo di validità,
* Fai clic su **[!UICONTROL Generate]** Codice HTML.

Quindi copia il codice generato e incollalo nella pagina da tracciare.

## Creazione rapida di URL da tracciare {#on-the-fly-creation-of-urls-to-be-tracked}

Puoi creare gli URL di web tracking immediatamente aggiungendo informazioni al valore del parametro **tagid** :

* Tipo di pagina tracciato: &quot;w&quot; per WEB o &quot;t&quot; per TRANSAZIONE,
* Nome interno della cartella in cui deve essere creato l’URL.

Queste due informazioni devono essere concatenate con l’identificatore della pagina tracciata aggiungendo il carattere &#39;|&#39;:

```
tagid=<identifier>|<type>|<foldername>
```

>[!IMPORTANT]
>
>Ricorda di codificare il valore del parametro **tagid** quando viene utilizzato come parametro URL.

**Esempio**: creazione di un URL di web tracking di tipo transazione.

**http://myserver.adobe.com/r/a?tagid=home%7Ct%7CMyFolder**
