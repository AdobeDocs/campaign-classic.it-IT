---
product: campaign
title: 'Nota tecnica: abilitare Microsoft Edge Chromium nell’ambiente Campaign'
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
description: Campaign - Cromo Edge
exl-id: 22f4cbaf-ca37-47b9-b7dd-1ee73d5b348d
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 13%

---

# Come abilitare Microsoft Edge Chromium nell’ambiente {#edge-conf}




## Cosa è cambiato?

Dopo la fine del ciclo di vita di Microsoft Internet Explorer 11, il motore di rendering HTML per le dashboard nella console client utilizza Edge Chromium, a partire da Campaign Classic v7.3.

Oltre all’installazione del runtime Microsoft Edge Webview 2, che è ora [necessaria per qualsiasi installazione della console client](../../installation/using/installing-the-client-console.md#webview), Microsoft Edge Chromium deve essere abilitato nelle istanze.

## Sei interessato da questo problema?

Se l’ambiente è stato aggiornato a Campaign Classic v7.3 (o versione successiva), l’utente è interessato.

## Come si esegue l’aggiornamento?

* Come **ospitato** cliente, Adobe ha già abilitato Microsoft Edge Chromium nelle istanze. Non è richiesta alcuna azione aggiuntiva.

* Come **on-premise/ibrido** cliente, devi abilitare Microsoft Edge Chromium nelle istanze.

   Durante l’aggiornamento ad Campaign Classic v7.3 (e versioni successive), viene visualizzata una nuova `webView2Mode` l’attributo è disponibile nel file di configurazione del server Campaign `serverConf.xml`. Questo attributo deve essere abilitato.

   Per eseguire questa operazione, applica i seguenti passaggi a tutti gli ambienti (MKT, MID, RT):

   1. Modifica il file di configurazione del server Campaign (`serverConf.xml`)
   1. In `<web>` modulo, set `webView2Mode = "1"`
   1. Esegui il comando seguente per ricaricare la configurazione del server:

      ```
      nlserver config -reload
      ```

   1. Esegui il seguente comando per riavviare il server Web:

      ```
      nlserver restart web
      ```

   1. Se il tuo ambiente utilizza Apache come server web, esegui il seguente comando per riavviare Apache:

      ```
      /etc/init.d/apache2 restart
      ```


>[!NOTE]
>
>Per qualsiasi domanda su queste modifiche, contatta [Adobe Customer Care](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Argomenti correlati

* [Aggiornare l’ambiente](../../production/using/build-upgrade.md)
* [Domande frequenti sull’aggiornamento della build](../../platform/using/faq-build-upgrade.md)
* [Installare la console client di Campaign](../../installation/using/installing-the-client-console.md)
