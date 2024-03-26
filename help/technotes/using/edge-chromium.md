---
product: campaign
title: 'Nota tecnica: abilitare Microsoft Edge Chromium nell’ambiente Campaign'
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
description: Campaign - Cromo Edge
feature: Technote, Upgrade
exl-id: 22f4cbaf-ca37-47b9-b7dd-1ee73d5b348d
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 10%

---

# Come abilitare Microsoft Edge Chromium nell’ambiente {#edge-conf}




## Cosa è cambiato?

Dopo la fine del ciclo di vita di Microsoft Internet Explorer 11, il motore di rendering HTML per le dashboard nella console client utilizza Edge Chromium, a partire da Campaign Classic v7.3.

Oltre all&#39;installazione di Microsoft Edge WebView2 Runtime, ora [richiesto per qualsiasi installazione della console client](../../installation/using/installing-the-client-console.md#webview), Microsoft Edge Chromium deve essere abilitato sulle istanze.

## Sei interessato?

L’aggiornamento dell’ambiente a Campaign Classic v7.3 (o versione successiva) influisce su di esso.

## Come si esegue l’aggiornamento?

* As a **in hosting** cliente, Adobe ha già abilitato Microsoft Edge Chromium nelle istanze. Non è richiesta alcuna azione aggiuntiva.

* Come un **on-premise/ibrido** cliente, devi abilitare Microsoft Edge Chromium nelle istanze.

  Durante l’aggiornamento a Campaign Classic v7.3 (e versioni successive), viene `webView2Mode` L’attributo è disponibile nel file di configurazione del server Campaign `serverConf.xml`. Questo attributo deve essere abilitato.

  Per farlo, applica i seguenti passaggi a tutti gli ambienti (MKT, MID, RT):

   1. Modificare il file di configurazione del server Campaign (`serverConf.xml`)
   1. In `<web>` modulo, set `webView2Mode = "1"`
   1. Esegui il comando seguente per ricaricare la configurazione del server:

      ```
      nlserver config -reload
      ```

   1. Esegui il comando seguente per riavviare il server Web:

      ```
      nlserver restart web
      ```

   1. Se l’ambiente utilizza Apache come server web, esegui il seguente comando per riavviare Apache:

      ```
      /etc/init.d/apache2 restart
      ```


>[!NOTE]
>
>Per qualsiasi domanda su queste modifiche, contatta [Adobe Customer Care](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).
>

## Argomenti correlati

* [Aggiornare l’ambiente](../../production/using/build-upgrade.md)
* [Domande frequenti sull’aggiornamento della build](../../platform/using/faq-build-upgrade.md)
* [Installare la console client di Campaign](../../installation/using/installing-the-client-console.md)
