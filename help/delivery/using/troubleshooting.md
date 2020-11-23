---
solution: Campaign Classic
product: campaign
title: Risoluzione dei problemi
description: Risoluzione dei problemi
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 3%

---


# Risoluzione dei problemi{#troubleshooting}

Se il dispositivo mobile è connesso al Wi-Fi e non si ricevono notifiche, verificare che le porte FCM/APN non siano bloccate dal firewall.

**Android**: Il dispositivo mobile si collega ai server FCM sulle porte da 5228 a 5230. È pertanto necessario configurare il firewall in modo che autorizzi la connessione con FCM. Le porte da aprire sono: 5228 (il più utilizzato), 5229 e 5230.

**iOS**:

Connettore binario: per inviare le notifiche, è necessario autorizzare il traffico TCP in entrata e in uscita sulla porta 2195. I dispositivi collegati al servizio push devono autorizzare il traffico TCP in entrata e in uscita sulla porta 5223.

Connettore HTTP/2: è necessario consentire la comunicazione con e dai server seguenti:

* api.push.apple.com: porta 443
* api.development.push.apple.com: porta 443

>[!NOTE]
>
>Per ulteriori informazioni sui due connettori, vedere [Configurazione dell’applicazione mobile in  Adobe Campaign](../../delivery/using/configuring-the-mobile-application.md).
