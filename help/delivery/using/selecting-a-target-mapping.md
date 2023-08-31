---
product: campaign
title: Selezionare una mappatura di destinazione
description: Scopri come eseguire il targeting della mappatura
badge-v7: label="v7" type="Informative" tooltip="Applicabile a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Delivery Templates
role: User
exl-id: b5514fa3-1e65-45dc-8e40-d1ba3b673e7a
source-git-commit: d2f5f2a662c022e258fb3cc56c8502c4f4cb2849
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 14%

---

# Selezionare una mappatura di destinazione{#selecting-a-target-mapping}

Per impostazione predefinita, i modelli di consegna sono target **[!UICONTROL Recipients]**. La loro mappatura target utilizza quindi i campi del **nms:destinatario** tabella. Adobe Campaign offre altre mappature di destinazione per le consegne, da utilizzare in base alle tue esigenze.

![](assets/delivery_select_mapping.png)

Queste mappature sono le seguenti:

| Nome | Utilizzare | Schema standard |
|---|---|---|
| Destinatari | Consegna ai destinatari del database di Adobe Campaign | nms:destinatario |
| Visitatori | Distribuisci ai visitatori i cui profili sono stati raccolti tramite riferimento (marketing virale) o tramite social network (Facebook, Twitter), ad esempio. | mns:visitatore |
| Abbonamenti | Consegna ai destinatari abbonati a un servizio di informazioni, ad esempio una newsletter | nms:sottoscrizione |
| Abbonamenti visitatore | Consegna ai visitatori abbonati a un servizio di informazioni | nms:visitorSub |
| Servizio | Pubblicare su un account di Twitter o su una pagina Facebook | nms:service |
| Operatori | Consegna agli operatori Adobe Campaign | nms:operatore |
| File esterno | Consegna tramite un file contenente tutte le informazioni necessarie per la consegna | Nessuno schema collegato, nessuna destinazione immessa |

>[!NOTE]
>
>Puoi anche creare nuove mappature di destinazione. Questa operazione è riservata agli utenti esperti. Per ulteriori informazioni, consulta [questa sezione](../../configuration/using/target-mapping.md).
