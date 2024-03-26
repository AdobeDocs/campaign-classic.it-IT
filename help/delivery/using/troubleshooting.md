---
product: campaign
title: Risoluzione dei problemi push
description: Risoluzione dei problemi push
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
feature: Push, Troubleshooting
role: User
exl-id: 313eae5f-40db-4b1a-b013-f4adf8781763
source-git-commit: d2f5f2a662c022e258fb3cc56c8502c4f4cb2849
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 6%

---

# Risoluzione dei problemi{#troubleshooting}

Se il dispositivo mobile è connesso a Wi-Fi e non si ricevono notifiche, verificare che le porte FCM/APN non siano bloccate dal firewall.

**Android**: il dispositivo mobile si connette ai server FCM sulle porte da 5228 a 5230. Devi quindi configurare il firewall in modo che autorizzi la connessione con FCM. Le porte da aprire sono: 5228 (le più utilizzate), 5229 e 5230.

**iOS**:

Connettore HTTP/2: è necessario consentire la comunicazione da e verso i seguenti server:

* api.push.apple.com: porta 443
* api.development.push.apple.com: porta 443

>[!NOTE]
>
>Per ulteriori informazioni sui due connettori, fare riferimento a [Configurazione dell’app mobile in Adobe Campaign](configuring-the-mobile-application.md).
