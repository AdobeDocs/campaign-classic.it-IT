---
solution: Campaign Classic
product: campaign
title: Password persa
description: Password persa
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 3%

---


# Password persa{#lost-password}

È possibile cambiare o recuperare una password persa.

Esistono due possibili scenari:

* Password persa da un operatore Adobe Campaign .

   In questo caso, è possibile modificare la password dell&#39;operatore interessato. A tal fine, collegatevi tramite un operatore con diritti di amministratore, fate clic con il pulsante destro del mouse su un operatore, selezionate **[!UICONTROL Actions]** > **[!UICONTROL Reset password]** e impostate la nuova password dell&#39;operatore. È consigliabile che gli operatori cambino la password al primo riconnessione.

   ![](assets/operator-passwd.png)

* **Perdita** di password interna (solo per i clienti interni).

   Se la password **interna** viene persa, è necessario reinizializzarla. A tal fine, attenersi alla procedura seguente:

   1. Modificate il file **/usr/local/neolane/nl6/conf/serverConf.xml**.
   1. Vai alla riga **internalPassword**.

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

   1. È ora possibile utilizzare la nuova password per connettersi in modalità **Internal**.

