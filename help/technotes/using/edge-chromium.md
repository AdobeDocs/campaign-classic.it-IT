---
product: campaign
title: Nota tecnica - Abilitazione di Microsoft Edge Chromium nell’ambiente Campaign
description: Campaign - Edge Chromium
feature: Technote, Upgrade
exl-id: 22f4cbaf-ca37-47b9-b7dd-1ee73d5b348d
TQID: 'https://experienceleague.adobe.com/6CrzuBxAxGlXi08NxwdnigO2bNu700luLxnz-3KzZ18'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: ab81f6c3-9317-564f-af92-6670a8784294
    internal-label: Technote
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
    internal-label: Integrations
subfeature_v2:
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
    internal-label: Analytics integration
  - id: eff19c99-440a-4318-b319-444edc4d8d8f
    internal-label: Upgrade
topic_v2:
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
    internal-label: Privacy
source-git-commit: 3e213ecc670d5a3cb8299c092ccbb5303858327d
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 10%
---
# Come abilitare Microsoft Edge Chromium nel tuo ambiente {#edge-conf}

## Cosa è cambiato?

Dopo la fine del ciclo di vita di Microsoft Internet Explorer 11, il motore di rendering HTML per le dashboard nella console client utilizza Edge Chromium, a partire da Campaign Classic v7.3.

Oltre all&#39;installazione di Microsoft Edge Webview 2 Runtime, attualmente [necessaria per qualsiasi installazione della console client](../../installation/using/installing-the-client-console.md#webview), Microsoft Edge Chromium deve essere abilitato nelle istanze.

>[!NOTE]
>
>Dopo aver abilitato Microsoft Edge Chromium, il collegamento `Ctrl+F` (Windows) o `Command+F` (Mac) per aprire la finestra di dialogo di ricerca del browser non funzionerà più.

## Sei interessato?

L’aggiornamento dell’ambiente a Campaign Classic v7.3 (o versione successiva) è stato modificato.

## Come si esegue l’aggiornamento?

* In qualità di cliente **in hosting**, Adobe ha già abilitato Microsoft Edge Chromium nelle tue istanze. Non è richiesta alcuna azione aggiuntiva.

* In qualità di cliente **on-premise/hybrid**, devi abilitare Microsoft Edge Chromium nelle tue istanze.

  Durante l’aggiornamento a Campaign Classic v7.3 (e versioni successive), è disponibile un nuovo attributo `webView2Mode` nel file di configurazione del server Campaign `serverConf.xml`. Questo attributo deve essere abilitato.

  Per farlo, applica i seguenti passaggi a tutti gli ambienti (MKT, MID, RT):

  1. Modifica il file di configurazione del server Campaign (`serverConf.xml`)
  1. Nel modulo `<web>`, imposta `webView2Mode = "1"`
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
