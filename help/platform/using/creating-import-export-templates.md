---
solution: Campaign Classic
product: campaign
title: Creazione di modelli di importazione ed esportazione
description: Scoprite come creare modelli di importazione ed esportazione in Campaign Classic.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: 37cc6cd8b71ec82cd4e6a910d6664a51ed5c091e
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%

---


# Creazione di modelli di importazione ed esportazione {#creating-import-export-templates}

I modelli di importazione ed esportazione sono memorizzati nella directory **[!UICONTROL Resources > Templates > Job templates]** della struttura di Adobe Campaign .

Per impostazione predefinita, in questa directory sono presenti tre modelli di importazione e uno di esportazione. Non devono essere modificati.

* Il modello nativo **[!UICONTROL Import denylist]** è già configurato per importare un elenco di indirizzi e-mail che sono stati aggiunti al elenco Bloccati.

* I modelli **[!UICONTROL New text import]** e **[!UICONTROL New text export]** consentono di configurare un&#39;importazione o un&#39;esportazione da zero.

![](assets/s_ncs_user_export_wizard_template_create.png)

Potete duplicare i modelli esistenti per creare modelli personalizzati, oppure creare un nuovo modello tramite il menu **[!UICONTROL New > Import template]** / **[!UICONTROL Export template]**.

La procedura per la configurazione di un modello è quindi la stessa descritta in queste sezioni:

* [Configurazione di un processo di importazione](../../platform/using/executing-import-jobs.md)
* [Configurazione di un processo di esportazione](../../platform/using/executing-export-jobs.md)
