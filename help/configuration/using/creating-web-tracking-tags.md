---
product: campaign
title: Creare tag di web tracking
description: Scopri come creare tag di web tracking
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 160df6e1-43e5-4eb9-ad2f-5db444e314ea
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# Creare tag di web tracking{#creating-web-tracking-tags}

Ogni pagina del sito che desideri monitorare deve essere referenziata nella tua piattaforma Adobe Campaign. Questo riferimento può essere eseguito in due modi:

1. Definizione manuale degli URL da tracciare,
1. Creazione rapida di URL da tracciare.

## Definizione degli URL da tracciare nell’applicazione {#defining-the-urls-to-be-tracked-in-the-application}

Questo metodo ti consente di definire manualmente le pagine da tracciare e quindi di generare un esempio del tag di web tracking associato. Questa operazione è definita nella **[!UICONTROL Campaign execution>Resources>Web tracking tags]** nodo della console client.

![](assets/d_ncs_integration_webtracking_screen.png)

Per generare il codice HTML da inserire nella pagina:

* Inserisci l’etichetta del tag: sarà mostrato nei registri di tracciamento,
* Indica l’URL di origine: questo campo è a scopo informativo e consente di indicare la pagina tracciata (facoltativo),
* Se necessario, inserire un periodo di validità,
* Fai clic su **[!UICONTROL Generate]** Codice HTML.

Quindi copia il codice generato e incollalo nella pagina da tracciare.

## Creazione rapida di URL da tracciare {#on-the-fly-creation-of-urls-to-be-tracked}

Puoi creare al volo gli URL di web tracking aggiungendo informazioni al valore della **tagid** parametro:

* Tipo di pagina tracciato: &quot;w&quot; per WEB o &quot;t&quot; per TRANSAZIONE,
* Nome interno della cartella in cui deve essere creato l’URL.

Queste due informazioni devono essere concatenate con l’identificatore della pagina tracciata aggiungendo il carattere &#39;|&#39;:

```
tagid=<identifier>|<type>|<foldername>
```

>[!IMPORTANT]
>
>Ricorda di codificare il valore del **tagid** quando viene utilizzato come parametro URL.

**Esempio**: creazione di un URL di web tracking di tipo transazione.

**http://myserver.adobe.com/r/a?tagid=home%7Ct%7CMyFolder**
