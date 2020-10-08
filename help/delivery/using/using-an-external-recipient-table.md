---
title: Utilizzo di una tabella dei destinatari esterna
seo-title: Utilizzo di una tabella dei destinatari esterna
description: Utilizzo di una tabella dei destinatari esterna
seo-description: null
page-status-flag: never-activated
uuid: a6147425-14f0-41e8-a47f-3e7072deafa7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
discoiquuid: 92c32b2d-d8bf-41ab-9349-ef4a15f10521
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '88'
ht-degree: 22%

---


# Utilizzo di una tabella dei destinatari esterna{#using-an-external-recipient-table}

Se la tabella di consegna è una tabella esterna, sarà necessario effettuare configurazioni aggiuntive. Lo **[!UICONTROL nms:seedmember]** schema deve essere esteso. Agli indirizzi iniziali viene aggiunta una scheda per definire i campi adeguati, come illustrato di seguito:

![](assets/s_ncs_user_seedlist_new_tab.png)

In questo caso, per aggiungere gli indirizzi iniziali alla consegna, immettete i campi adeguati direttamente nella scheda corrispondente, oppure importate i modelli di indirizzo:

![](assets/s_ncs_user_seedlist_add_new_tab.png)

L&#39;estensione **dello schema nms:seedMember** è [questa sezione](../../configuration/using/seed-addresses.md).
