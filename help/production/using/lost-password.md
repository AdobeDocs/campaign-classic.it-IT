---
product: campaign
title: Password persa
description: Password persa
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 064eb41f-6685-4ac1-adc5-40f9d5a2f96d
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 8%

---

# Password persa{#lost-password}

![](../../assets/v7-only.svg)

È possibile modificare o recuperare una password persa.
Esistono due possibili scenari:

* [Password persa da un operatore Adobe Campaign](#password-lost-by-campaign-operator)
* [Password interna persa](#internal-password-lost) (solo per i clienti on-premise)

## Password persa da un operatore Campaign {#password-lost-by-campaign-operator}

Se un operatore Adobe Campaign perde la password, puoi modificarla.
A tale scopo, segui la procedura indicata di seguito:

1. Connessione tramite un operatore con diritti di amministratore.
1. Fai clic con il pulsante destro del mouse su un operatore.
1. Seleziona **[!UICONTROL Actions]** > **[!UICONTROL Reset password]**.

   ![](assets/operator-passwd.png)

1. Imposta la nuova password dell&#39;operatore. È consigliabile che l’operatore cambi la password al primo riconnettersi.

## Password interna persa {#internal-password-lost}

>[!NOTE]
>
>Questa sezione si applica solo ai clienti on-premise.

Se la password interna viene persa, è necessario reinizializzarla.
A questo scopo, applicare la seguente procedura:

1. Modifica le **/usr/local/neolane/nl6/conf/serverConf.xml** file.

1. Vai a **internalPassword** linea.

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

1. Salva le modifiche e chiudi il file.

1. Configura la nuova password. A questo scopo, immetti i seguenti comandi:

   ```
   nlserver config -internalpassword
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   Enter current password.
   Password: (empty)
   Enter the new password.
   Password: 
   Confirmation 
   ```

1. È ora possibile utilizzare la nuova password per connettersi a **Interno** modalità.
