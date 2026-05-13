---
product: campaign
title: Utilizzare una tabella dei destinatari esterna
description: Utilizzare una tabella dei destinatari esterna
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Audiences
exl-id: b6aabc68-707d-4c6c-b008-277609166c6c
TQID: https://experienceleague.adobe.com/Uq5yqNYkyDrFVtueUlkIOEC9XEUaYtBArNy8-t1rKAw
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 91
ht-degree: 16%

---

# Utilizzare una tabella dei destinatari esterna{#using-an-external-recipient-table}



Se la tabella di consegna è esterna, dovrai effettuare configurazioni aggiuntive. Lo schema **[!UICONTROL nms:seedmember]** deve essere esteso. Agli indirizzi seed viene aggiunta una scheda per definire i campi appropriati, come illustrato di seguito:

![](assets/s_ncs_user_seedlist_new_tab.png)

In questo caso, per aggiungere indirizzi di seed alla consegna, inserisci i campi appropriati direttamente nella scheda corrispondente o importa i modelli di indirizzo:

![](assets/s_ncs_user_seedlist_add_new_tab.png)

L&#39;estensione dello schema **nms:seedMember** è [questa sezione](../../configuration/using/seed-addresses.md).
