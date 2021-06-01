---
product: campaign
title: Utilizzo di una tabella dei destinatari esterna
description: Utilizzo di una tabella dei destinatari esterna
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
exl-id: b6aabc68-707d-4c6c-b008-277609166c6c
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '83'
ht-degree: 18%

---

# Utilizzo di una tabella dei destinatari esterna{#using-an-external-recipient-table}

Se la tabella di consegna è una tabella esterna, dovrai effettuare configurazioni aggiuntive. Lo schema **[!UICONTROL nms:seedmember]** deve essere esteso. Agli indirizzi di seed viene aggiunta una scheda per definire i campi appropriati, come illustrato di seguito:

![](assets/s_ncs_user_seedlist_new_tab.png)

In questo caso, per aggiungere gli indirizzi di seed alla consegna, immetti i campi appropriati direttamente nella scheda corrispondente o importa i modelli di indirizzo:

![](assets/s_ncs_user_seedlist_add_new_tab.png)

L&#39;estensione dello schema **nms:seedMember** è [questa sezione](../../configuration/using/seed-addresses.md).
