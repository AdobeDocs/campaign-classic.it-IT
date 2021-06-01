---
product: campaign
title: Risoluzione dei problemi
description: Risoluzione dei problemi
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
exl-id: 313eae5f-40db-4b1a-b013-f4adf8781763
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 4%

---

# Risoluzione dei problemi{#troubleshooting}

Se il tuo dispositivo mobile è connesso al Wi-Fi e non ricevi notifiche, controlla che le porte FCM/APNs non siano bloccate dal firewall.

**Android**: Il dispositivo mobile si connette ai server FCM sulle porte da 5228 a 5230. È quindi necessario configurare il firewall in modo che autorizzi la connessione con FCM. Le porte da aprire sono: 5228 (il più utilizzato), 5229 e 5230.

**iOS**:

Connettore HTTP/2: è necessario consentire la comunicazione da e verso i server seguenti:

* api.push.apple.com: porta 443
* api.development.push.apple.com: porta 443

>[!NOTE]
>
>Per ulteriori informazioni sui due connettori, consulta [Configurazione dell’app mobile in Adobe Campaign](../../delivery/using/configuring-the-mobile-application.md).
