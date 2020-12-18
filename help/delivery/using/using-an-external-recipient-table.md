---
solution: Campaign Classic
product: campaign
title: Utilizzo di una tabella dei destinatari esterna
description: Utilizzo di una tabella dei destinatari esterna
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '83'
ht-degree: 18%

---


# Utilizzo di una tabella dei destinatari esterna{#using-an-external-recipient-table}

Se la tabella di consegna è una tabella esterna, sarà necessario effettuare configurazioni aggiuntive. Lo schema **[!UICONTROL nms:seedmember]** deve essere esteso. Agli indirizzi iniziali viene aggiunta una scheda per definire i campi adeguati, come illustrato di seguito:

![](assets/s_ncs_user_seedlist_new_tab.png)

In questo caso, per aggiungere gli indirizzi iniziali alla consegna, immettete i campi adeguati direttamente nella scheda corrispondente, oppure importate i modelli di indirizzo:

![](assets/s_ncs_user_seedlist_add_new_tab.png)

L&#39;estensione dello schema **nms:seedMember** è [questa sezione](../../configuration/using/seed-addresses.md).
