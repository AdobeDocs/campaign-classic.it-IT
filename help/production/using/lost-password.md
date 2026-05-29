---
product: campaign
title: Password persa
description: Password persa
feature: Monitoring, Access Management
badge-v7-prem: label="Solo on-premise/ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 064eb41f-6685-4ac1-adc5-40f9d5a2f96d
TQID: https://experienceleague.adobe.com/MaAtheK2WnozPDuEO-qPq2l9u-AOGj5aGu2TgKslgLc
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
feature_v2: []
subfeature_v2:
  - id: c03a11ff-bdf9-4e5b-b279-f468b4293464
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 247
ht-degree: 9%

---

# Password persa{#lost-password}

>[!NOTE]
>
>Questa pagina si applica solo agli operatori che si connettono a Campaign con autenticazione nativa.

È possibile modificare o recuperare una password persa.
Esistono due possibili scenari:

* [Password persa da un operatore Adobe Campaign](#password-lost-by-campaign-operator)
* [Password interna persa](#internal-password-lost) (solo clienti locali)

## Password persa da un operatore Campaign {#password-lost-by-campaign-operator}

Se un operatore Adobe Campaign perde la propria password, puoi modificarla.

>[!NOTE]
>
>Questa procedura si applica solo agli operatori che si connettono a Campaign con autenticazione nativa. Per l&#39;autenticazione Adobe IMS, consulta [questa documentazione](https://helpx.adobe.com/ie/manage-account/using/change-or-reset-password.html){target="_blank"}.

Per reimpostare la password di una campagna, effettua le seguenti operazioni:

1. Connetti tramite un operatore con diritti di amministratore.
1. Fare clic con il pulsante destro del mouse su un operatore.
1. Selezionare **[!UICONTROL Actions]** > **[!UICONTROL Reset password]**.

   ![](assets/operator-passwd.png)

1. Imposta la nuova password dell&#39;operatore. È consigliabile che l&#39;operatore modifichi la password alla prima riconnessione.

## Password interna persa {#internal-password-lost}

>[!NOTE]
>
>Questa sezione si applica solo ai clienti on-premise.

Se la password interna viene persa, è necessario reinizializzarla.

A tale scopo, attenersi alla procedura descritta di seguito.

1. Modifica il file **/usr/local/neolane/nl6/conf/serverConf.xml**.

1. Vai alla riga **internalPassword**.

   ```xml
   <!-- XTK authentication mode internalPassword : Password of internal account -->
   <xtk internalPassword="myPassword"/>
   ```

1. Eliminare la stringa tra virgolette, in questo caso: `myPassword`. Viene visualizzata la seguente riga:

   ```xml
   <!-- XTK authentication mode internalPassword : Password of internal account -->
   <xtk internalPassword=""/>
   ```

1. Salva le modifiche e chiudi il file.

1. Arresta il processo `nlserver`.

1. Configura la nuova password. A tale scopo, immetti i seguenti comandi:

   ```javascript
   nlserver config -internalpassword
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   Enter current password.
   Password: (empty)
   Enter the new password.
   Password: 
   Confirmation 
   ```

1. Avvia il processo `nlserver`.

1. È ora possibile utilizzare la nuova password per connettersi in modalità **Interna**.
