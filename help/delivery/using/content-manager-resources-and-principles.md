---
solution: Campaign Classic
product: campaign
title: Risorse e principi di gestione dei contenuti
description: Risorse e principi di gestione dei contenuti
audience: delivery
content-type: reference
topic-tags: content-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 6%

---


# Risorse e principi di gestione dei contenuti{#content-manager-resources-and-principles}

È necessario definire un modello di pubblicazione, che contenga modelli di trasformazione per ciascun contenuto.

Un blocco di contenuto è strutturato in un documento XML per l&#39;archiviazione dei dati. Un&#39;interfaccia di modifica viene utilizzata per inserire il contenuto dalla console client Adobe Campaign  o tramite un browser Web. Il contenuto può essere immesso automaticamente anche tramite l&#39;acquisizione di flusso XML o dati aggregati in un database.

Combinando il documento XML con i fogli di stile XSL o JavaScript Template si genera automaticamente la proiezione del modello di pubblicazione nei vari formati (HTML, testo).

![](assets/d_ncs_content_process.png)

Per la configurazione del contenuto sono necessarie le seguenti risorse:

* Schemi di dati: descrizione della struttura del contenuto XML. Per ulteriori informazioni, vedere [Schemi di dati](../../delivery/using/data-schemas.md).
* Moduli di immissione dati: costruzione di schermate di immissione dati. Per ulteriori informazioni, fare riferimento a [Moduli di input](../../delivery/using/input-forms.md).
* Immagini: immagini utilizzate nei moduli di immissione dati. Per ulteriori informazioni, vedere [Gestione delle immagini](../../delivery/using/formatting.md#image-management).
* Fogli di stile: formattazione di documenti di output utilizzando il linguaggio XSLT. Per ulteriori informazioni, vedere [Formattazione](../../delivery/using/formatting.md).
* Modelli JavaScript: formattazione di documenti di output utilizzando il linguaggio JavaScript. Per ulteriori informazioni, consultare [Modelli di pubblicazione](../../delivery/using/publication-templates.md).
* Codici JavaScript: Codici JavaScript per l&#39;aggregazione dei dati. Per ulteriori informazioni, vedere [Aggregator](../../delivery/using/publication-templates.md#aggregator).
* Modelli di pubblicazione: definizione di modelli di pubblicazione. Per ulteriori informazioni, consultare [Modelli di pubblicazione](../../delivery/using/publication-templates.md).
* Contenuto: le istanze di contenuto da creare e pubblicare. Per ulteriori informazioni, vedere [Utilizzo di un modello di contenuto](../../delivery/using/using-a-content-template.md).
