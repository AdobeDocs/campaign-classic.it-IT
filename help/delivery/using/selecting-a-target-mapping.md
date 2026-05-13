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
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
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
