---
title: Risoluzione dei problemi
seo-title: Risoluzione dei problemi
description: Risoluzione dei problemi
seo-description: null
page-status-flag: never-activated
uuid: 02bd48cf-3928-4817-97b0-1e64cc8ad8ef
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
discoiquuid: b64c9729-cfe2-4d02-8c59-9e53efd34a96
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# Risoluzione dei problemi{#troubleshooting}

Se il dispositivo mobile è connesso al Wi-Fi e non si ricevono notifiche, verificare che le porte FCM/APNS non siano bloccate dal firewall.

**Android**: Il dispositivo mobile si collega ai server FCM sulle porte da 5228 a 5230. È pertanto necessario configurare il firewall in modo che autorizzi la connessione con FCM. Le porte da aprire sono: 5228 (il più utilizzato), 5229 e 5230.

**iOS**:

Connettore binario: per inviare le notifiche, è necessario autorizzare il traffico TCP in entrata e in uscita sulla porta 2195. I dispositivi collegati al servizio push devono autorizzare il traffico TCP in entrata e in uscita sulla porta 5223.

Connettore HTTP/2: è necessario consentire la comunicazione con e dai server seguenti:

* api.push.apple.com: porta 443
* api.development.push.apple.com: porta 443

>[!NOTE]
>
>Per ulteriori informazioni sui due connettori, vedere [Connettori](../../delivery/using/setting-up-mobile-app-channel.md#connectors).
