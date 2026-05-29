---
product: campaign
title: Risorse e principi di gestione dei contenuti
description: Risorse e principio di gestione dei contenuti
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Templates
role: User, Developer
exl-id: ade3f1d1-2235-4148-9b6f-721d3f521a15
TQID: https://experienceleague.adobe.com/xWBOrnm4v7N3XOVvOcPNqngz0cDvvT39tI3xJVKdFZg
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: ce44533e-8ec8-4e11-a9e9-78b0fe561832
feature_v2: id: b631758a-142d-425f-b9aa-f756d85cb979id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2: id: e95a583b-fcfa-4524-8666-46a29c828119id: c8da4fdd-eb94-4751-a43c-f82733fb2d6eid: d5bbe3da-ba85-4242-817e-54f7c4b943e0id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 247
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
