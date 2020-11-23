---
solution: Campaign Classic
product: campaign
title: Selezione di una mappatura target
description: Selezione di una mappatura target
audience: delivery
content-type: reference
topic-tags: using-delivery-templates
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 8%

---


# Selezione di una mappatura target{#selecting-a-target-mapping}

Per impostazione predefinita, target dei modelli di consegna **[!UICONTROL Recipients]**. La mappatura di destinazione utilizza pertanto i campi della tabella **nms:Recipient** .  Adobe Campaign offre altre mappature di destinazione per le consegne, da utilizzare in base alle esigenze.

![](assets/delivery_select_mapping.png)

Le mappature sono le seguenti:

| Nome | Use | Schema standard |
|---|---|---|
| Destinatari | Consegna ai destinatari del database Adobe Campaign  | nms:destinatario |
| Visitatori | Fornire ai visitatori i cui profili sono stati raccolti tramite riferimento (marketing virale) o tramite social network (Facebook, Twitter), ad esempio. | mns:visitatore |
| Iscrizioni | Consegna ai destinatari che dispongono di un’iscrizione a un servizio di informazione, ad esempio una newsletter | nms:iscrizione |
| Iscrizioni dei visitatori | Consegna ai visitatori che hanno sottoscritto un servizio di informazione | nms:visitorSub |
| Servizio | Pubblicare su un account Twitter o una pagina Facebook | nms:servizio |
| Operatori | Consegna agli operatori Adobe Campaign  | nms:operatore |
| File esterno | Consegna tramite un file contenente tutte le informazioni necessarie per la consegna | Nessuno schema collegato, nessuna destinazione inserita |

>[!NOTE]
>
>Potete anche creare nuove mappature di destinazione. Questa operazione è riservata agli utenti esperti. For more information, refer to the [Configuration guide](../../configuration/using/target-mapping.md).
