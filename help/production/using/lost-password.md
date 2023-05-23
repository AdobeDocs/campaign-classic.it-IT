---
product: campaign
title: Password persa
description: Password persa
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 064eb41f-6685-4ac1-adc5-40f9d5a2f96d
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 8%

---

# Password persa{#lost-password}



È possibile modificare o recuperare una password persa.
Esistono due possibili scenari:

* [Password persa da un operatore Adobe Campaign](#password-lost-by-campaign-operator)
* [Password interna persa](#internal-password-lost) (solo clienti on-premise)

## Password persa da un operatore Campaign {#password-lost-by-campaign-operator}

Se un operatore Adobe Campaign perde la propria password, puoi modificarla.
A tale scopo, segui la procedura indicata di seguito:

1. Connetti tramite un operatore con diritti di amministratore.
1. Fare clic con il pulsante destro del mouse su un operatore.
1. Seleziona **[!UICONTROL Actions]** > **[!UICONTROL Reset password]**.

   ![](assets/operator-passwd.png)

1. Imposta la nuova password dell&#39;operatore. È consigliabile che l&#39;operatore modifichi la password alla prima riconnessione.

## Password interna persa {#internal-password-lost}

>[!NOTE]
>
>Questa sezione si applica solo ai clienti on-premise.

Se la password interna viene persa, è necessario reinizializzarla.
A tale scopo, attenersi alla procedura descritta di seguito.

1. Modifica il **/usr/local/neolane/nl6/conf/serverConf.xml** file.

1. Vai a **internalPassword** linea.

   ```
   <!-- XTK authentication mode internalPassword : Password of internal account -->
   <xtk internalPassword="myPassword"/>
   ```

1. Elimina la stringa tra virgolette, in questo caso: **password**

   Si ottiene così la seguente riga:

   ```
   !-- XTK authentication mode internalPassword : Password of internal account -->
   <xtk internalPassword=""/
   ```

1. Salva le modifiche e chiudi il file.

1. Configura la nuova password. A tale scopo, immetti i seguenti comandi:

   ```
   nlserver config -internalpassword
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   Enter current password.
   Password: (empty)
   Enter the new password.
   Password: 
   Confirmation 
   ```

1. Ora puoi usare la nuova password per connetterti a **Interno** modalità.
