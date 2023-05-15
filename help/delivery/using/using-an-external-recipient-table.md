---
product: campaign
title: Utilizzare una tabella dei destinatari esterna
description: Utilizzare una tabella dei destinatari esterna
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Audiences
exl-id: b6aabc68-707d-4c6c-b008-277609166c6c
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '83'
ht-degree: 18%

---

# Utilizzare una tabella dei destinatari esterna{#using-an-external-recipient-table}



Se la tabella di consegna è una tabella esterna, dovrai effettuare configurazioni aggiuntive. La **[!UICONTROL nms:seedmember]** lo schema deve essere esteso. Agli indirizzi di seed viene aggiunta una scheda per definire i campi appropriati, come illustrato di seguito:

![](assets/s_ncs_user_seedlist_new_tab.png)

In questo caso, per aggiungere gli indirizzi di seed alla consegna, immetti i campi appropriati direttamente nella scheda corrispondente o importa i modelli di indirizzo:

![](assets/s_ncs_user_seedlist_add_new_tab.png)

La **nms:seedMember** estensione dello schema [questa sezione](../../configuration/using/seed-addresses.md).
