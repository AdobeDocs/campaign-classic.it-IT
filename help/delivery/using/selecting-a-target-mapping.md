---
title: Selezione di una mappatura target
seo-title: Selezione di una mappatura target
description: Selezione di una mappatura target
seo-description: null
page-status-flag: never-activated
uuid: 29a666a3-2ecc-4732-b068-c93935929771
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-delivery-templates
discoiquuid: e2c6e273-1640-4f46-a80e-0cecb06e2769
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 10%

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
