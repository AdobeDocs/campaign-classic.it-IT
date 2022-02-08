---
product: campaign
title: Selezionare una mappatura di destinazione
description: Scopri come eseguire la mappatura del target
exl-id: b5514fa3-1e65-45dc-8e40-d1ba3b673e7a
source-git-commit: 1e11b7419388698f5de366cbeddf2be88ef12873
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 10%

---

# Selezionare una mappatura di destinazione{#selecting-a-target-mapping}

![](../../assets/common.svg)

Per impostazione predefinita, target dei modelli di consegna **[!UICONTROL Recipients]**. La mappatura del target utilizza quindi i campi del **nms:recipient** tabella. Adobe Campaign offre altre mappature target per le consegne, da utilizzare in base alle tue esigenze.

![](assets/delivery_select_mapping.png)

Queste mappature sono le seguenti:

| Nome | Utilizzo | Schema standard |
|---|---|---|
| Destinatari | Consegna a destinatari del database Adobe Campaign | nms:recipient |
| Visitatori | Effettua la consegna ai visitatori i cui profili sono stati raccolti tramite riferimento (marketing virale) o tramite social network (Facebook, Twitter), ad esempio. | mns:visitatore |
| Abbonamenti | Consegnare a destinatari abbonati a un servizio di informazione, ad esempio una newsletter | nms:abbonamento |
| Abbonamenti ai visitatori | Consegna ai visitatori abbonati a un servizio di informazione | nms:visitorSub |
| Servizio | Pubblicare su un account Twitter o su una pagina Facebook | nms:servizio |
| Operatori | Consegna agli operatori Adobe Campaign | nms:operatore |
| File esterno | Consegna tramite un file contenente tutte le informazioni necessarie per la consegna | Nessun schema collegato, nessuna destinazione immessa |

>[!NOTE]
>
>Puoi anche creare nuove mappature target. Questa operazione è riservata agli utenti esperti. Per ulteriori informazioni, consulta [questa sezione](../../configuration/using/target-mapping.md).
