---
product: campaign
title: Risorse e principi di gestione dei contenuti
description: Risorse e principio di gestione dei contenuti
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Templates
role: User, Developer
exl-id: ade3f1d1-2235-4148-9b6f-721d3f521a15
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 4%

---

# Risorse e principi di gestione dei contenuti{#content-manager-resources-and-principles}


È necessario definire un modello di pubblicazione contenente modelli di trasformazione per ogni contenuto.

Un blocco di contenuto è strutturato in un documento XML per l&#39;archiviazione dei dati. Un’interfaccia di modifica viene utilizzata per inserire il contenuto dalla console client di Adobe Campaign o tramite un browser web. Il contenuto può anche essere immesso automaticamente tramite l&#39;acquisizione di flussi XML o dati aggregati in un database.

La combinazione del documento XML e dei fogli di stile Modello XSL o Modello JavaScript genera automaticamente la proiezione del modello di pubblicazione nei vari formati (HTML, testo).

![](assets/d_ncs_content_process.png)

Per la configurazione del contenuto sono necessarie le seguenti risorse:

* Schemi di dati: descrizione della struttura del contenuto XML. Per ulteriori informazioni, consulta [Schemi di dati](data-schemas.md).
* Moduli per l’inserimento dei dati: costruzione di schermate per l’inserimento dei dati. Per ulteriori informazioni, consulta [Moduli di input](input-forms.md).
* Immagini: immagini utilizzate nei moduli di immissione dati. Per ulteriori informazioni, consulta [Gestione immagini](formatting.md#image-management).
* Fogli di stile: formattazione dei documenti di output utilizzando il linguaggio XSLT. Per ulteriori informazioni, consulta [Formattazione](formatting.md).
* Modelli JavaScript: formattazione di documenti di output in lingua JavaScript. Per ulteriori informazioni, consulta [Modelli di pubblicazione](publication-templates.md).
* Codici JavaScript: codici JavaScript per l’aggregazione dei dati. Per ulteriori informazioni, consulta [Aggregator](publication-templates.md#aggregator).
* Modelli di pubblicazione: definizione di modelli di pubblicazione. Per ulteriori informazioni, consulta [Modelli di pubblicazione](publication-templates.md).
* Contenuto: istanze di contenuto da creare e pubblicare. Per ulteriori informazioni, consulta [Utilizzo di un modello di contenuto](using-a-content-template.md).
