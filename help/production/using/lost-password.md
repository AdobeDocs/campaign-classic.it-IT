---
title: Password persa
seo-title: Password persa
description: Password persa
seo-description: null
page-status-flag: never-activated
uuid: caac68bf-abdc-45da-9697-b689ebd37002
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: d52eeadc-19c6-4d48-995a-1c1f2ca3b5ec
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 5%

---


# Password persa{#lost-password}

È possibile cambiare o recuperare una password persa.

Esistono due possibili scenari:

* Password persa da un operatore Adobe Campaign .

   In questo caso, è possibile modificare la password dell&#39;operatore interessato. A tal fine, collegatevi tramite un operatore con diritti di amministratore, fate clic con il pulsante destro del mouse su un operatore, selezionate **[!UICONTROL Actions]** > **[!UICONTROL Reset password]** e impostate la nuova password dell&#39;operatore. È consigliabile che gli operatori cambino la password al primo riconnessione.

   ![](assets/operator-passwd.png)

* **Perdita interna** della password (solo per i clienti interni).

   Se la password **interna** viene persa, è necessario reinizializzarla. A tal fine, attenersi alla procedura seguente:

   1. Modificate il file **/usr/local/neolane/nl6/conf/serverConf.xml** .
   1. Vai alla riga **internalPassword** .

      ```
      <!-- XTK authentication mode internalPassword : Password of internal account -->
       <xtk internalPassword="myPassword"/>
      ```

   1. Elimina la stringa tra virgolette, in questo caso: **myPassword**

      Si ottiene così la seguente riga:

      ```
      !-- XTK authentication mode internalPassword : Password of internal account -->
      <xtk internalPassword=""/
      ```

   1. Salvare le modifiche e chiudere il file.
   1. Configurare la nuova password. A tal fine, immettete i seguenti comandi:

      ```
      nlserver config -internalpassword
      HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
      Enter current password.
      Password: (empty)
      Enter the new password.
      Password: 
      Confirmation 
      ```

   1. È ora possibile utilizzare la nuova password per connettersi in modalità **interna** .

