---
solution: Campaign Classic
product: campaign
title: Password persa
description: Password persa
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 1fdee02e98ce66ec184d8587d0838557f027cf75
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 8%

---


# Password persa{#lost-password}

È possibile cambiare o recuperare una password persa.
Esistono due possibili scenari:

* [Password persa da un operatore Adobe Campaign ](#password-lost-by-campaign-operator)
* [Password interna persa](#internal-password-lost)  (solo per i clienti interni)

## Password persa dall&#39;operatore di campagna {#password-lost-by-campaign-operator}

Se un operatore Adobe Campaign  perde la password, è possibile modificarla.
Per farlo, segui la procedura indicata di seguito:

1. Connessione tramite un operatore con diritti di amministratore.
1. Fare clic con il pulsante destro del mouse su un operatore.
1. Seleziona **[!UICONTROL Actions]** > **[!UICONTROL Reset password]**.

   ![](assets/operator-passwd.png)

1. Impostare la nuova password dell&#39;operatore. È consigliabile che l&#39;operatore cambi la password al primo riconnessione.

## Password interna persa {#internal-password-lost}

>[!NOTE]
>
>Questa sezione si applica solo ai clienti interni.

Se la password interna viene persa, è necessario reinizializzarla.
A tal fine, attenersi alla procedura seguente:

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
