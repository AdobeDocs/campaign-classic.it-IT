---
product: campaign
title: Risoluzione dei problemi push
description: Risoluzione dei problemi push
feature: Push, Troubleshooting
role: User
hide: true
exl-id: 313eae5f-40db-4b1a-b013-f4adf8781763
TQID: https://experienceleague.adobe.com/3T6eC52Edyai-8Bn-ioDxvB5C04iDqBNmlZzuxVturE
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 109
ht-degree: 0%

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
>Per ulteriori informazioni sui due connettori, fare riferimento a [Configurazione dell&#39;app mobile in Adobe Campaign](configuring-the-mobile-application.md).
