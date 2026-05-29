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
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
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
