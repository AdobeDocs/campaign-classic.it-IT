---
product: campaign
title: Selezionare una mappatura di destinazione
description: Scopri come eseguire il targeting della mappatura
feature: Delivery Templates
hide: true
role: User
exl-id: b5514fa3-1e65-45dc-8e40-d1ba3b673e7a
TQID: https://experienceleague.adobe.com/VpmfQdFoJ2Lfzetqx-s5MAdFdTTEsHxz2ISL15wNXIo
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
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
source-wordcount: 177
ht-degree: 40%

---

# Selezionare una mappatura di destinazione{#selecting-a-target-mapping}

Per impostazione predefinita, i modelli di consegna sono destinati a **[!UICONTROL Recipients]**. La mappatura di destinazione utilizza pertanto i campi della tabella **nms:recipient**. Adobe Campaign offre altre mappature di destinazione per le consegne, da utilizzare in base alle tue esigenze.

![](assets/delivery_select_mapping.png)

Queste mappature sono le seguenti:

| Nome | Utilizzo | Schema standard |
|---|---|---|
| Destinatari | Consegna ai destinatari del database di Adobe Campaign | nms:recipient |
| Visitatori | Distribuisci ai visitatori i cui profili sono stati raccolti tramite riferimento (marketing virale) o tramite social network (Facebook, X, precedentemente noto come Twitter), ad esempio. | mns:visitor |
| Abbonamenti | Consegnare ai destinatari abbonati o iscritti a un servizio informativo, ad esempio una newsletter | nms:subscription |
| Abbonamenti visitatore | Consegnare ai visitatori abbonati o iscritti a un servizio informativo | nms:visitorSub |
| Servizio | Pubblicare su un account X o su una pagina Facebook | nms:service |
| Operatori | Consegnare agli operatori Adobe Campaign | nms:operator |
| File esterno | Consegnare tramite un file contenente tutte le informazioni necessarie per la consegna | Nessuno schema collegato, nessuna destinazione immessa |

>[!NOTE]
>
>Puoi anche creare nuove mappature di destinazione. Questa operazione è riservata agli utenti esperti. Per ulteriori informazioni, consulta [questa sezione](../../configuration/using/target-mapping.md).
