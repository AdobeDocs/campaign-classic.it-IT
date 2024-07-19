---
product: campaign
title: Creazione di modelli di importazione ed esportazione
description: Scopri come creare modelli di importazione ed esportazione in Campaign
feature: Templates
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 1180e664-5ead-4d5d-b1c3-6fe397c1f3a2
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 3%

---

# Creare modelli di importazione ed esportazione {#creating-import-export-templates}



I modelli di importazione ed esportazione sono archiviati nella directory **[!UICONTROL Resources > Templates > Job templates]** della struttura Adobe Campaign.

Per impostazione predefinita, in questa directory sono presenti tre modelli di importazione e un modello di esportazione. Non devono essere modificati.

* Il modello nativo **[!UICONTROL Import denylist]** è già configurato per importare un elenco di indirizzi di posta elettronica aggiunti al inserisco nell&#39;elenco Bloccati di.

* I modelli **[!UICONTROL New text import]** e **[!UICONTROL New text export]** consentono di configurare un&#39;importazione o un&#39;esportazione da zero.

![](assets/s_ncs_user_export_wizard_template_create.png)

È possibile duplicare i modelli esistenti per creare modelli personalizzati o creare un nuovo modello tramite il menu **[!UICONTROL New > Import template]** / **[!UICONTROL Export template]**.

Il processo di configurazione di un modello è quindi lo stesso di quello presentato in queste sezioni:

* [Configurare un processo di importazione](../../platform/using/executing-import-jobs.md)
* [Configurare un processo di esportazione](../../platform/using/executing-export-jobs.md)
