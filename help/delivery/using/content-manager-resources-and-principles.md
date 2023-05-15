---
product: campaign
title: Risorse e principi di gestione dei contenuti
description: Risorse e principi di gestione dei contenuti
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Templates
exl-id: ade3f1d1-2235-4148-9b6f-721d3f521a15
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 4%

---

# Risorse e principi di gestione dei contenuti{#content-manager-resources-and-principles}



È necessario definire un modello di pubblicazione, che contiene modelli di trasformazione per ciascun contenuto.

Un blocco di contenuto è strutturato in un documento XML per l’archiviazione dei dati. Un’interfaccia di modifica viene utilizzata per inserire il contenuto dalla console client di Adobe Campaign o tramite un browser web. Il contenuto può anche essere immesso automaticamente tramite l’acquisizione di flussi XML o dati aggregati in un database.

La combinazione del documento XML e dei fogli di stile XSL o JavaScript Template genera automaticamente la proiezione del modello di pubblicazione nei vari formati (HTML, testo).

![](assets/d_ncs_content_process.png)

Per la configurazione del contenuto sono necessarie le seguenti risorse:

* Schemi di dati: descrizione della struttura del contenuto XML. Per ulteriori informazioni, consulta [Schemi di dati](data-schemas.md).
* Moduli di immissione dati: costruzione di schermate di immissione dati. Per ulteriori informazioni, consulta [Moduli di input](input-forms.md).
* Immagini: immagini utilizzate nei moduli di immissione dati. Per ulteriori informazioni, consulta [Gestione delle immagini](formatting.md#image-management).
* Fogli di stile: formattazione di documenti di output utilizzando il linguaggio XSLT. Per ulteriori informazioni, consulta [Formattazione](formatting.md).
* Modelli JavaScript: formattazione di documenti di output utilizzando il linguaggio JavaScript. Per ulteriori informazioni, consulta [Modelli di pubblicazione](publication-templates.md).
* Codici JavaScript: Codici JavaScript per l’aggregazione dei dati. Per ulteriori informazioni, consulta [Aggregatore](publication-templates.md#aggregator).
* Modelli di pubblicazione: definizione dei modelli di pubblicazione. Per ulteriori informazioni, consulta [Modelli di pubblicazione](publication-templates.md).
* Contenuto: istanze di contenuto da creare e pubblicare. Per ulteriori informazioni, consulta [Utilizzo di un modello di contenuto](using-a-content-template.md).
