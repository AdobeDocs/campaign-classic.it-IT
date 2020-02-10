---
title: Risorse e principi di Content Manager
seo-title: Risorse e principi di Content Manager
description: Risorse e principi di Content Manager
seo-description: null
page-status-flag: never-activated
uuid: 3560e392-129a-471d-a211-05481cdda224
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: content-management
discoiquuid: b22b3abb-6fe5-4f4d-93fc-0d00d426edb6
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# Risorse e principi di Content Manager{#content-manager-resources-and-principles}

È necessario definire un modello di pubblicazione che contenga modelli di trasformazione per ciascun contenuto.

Un blocco di contenuto è strutturato in un documento XML per l&#39;archiviazione dei dati. Un&#39;interfaccia di modifica viene utilizzata per inserire il contenuto dalla console client Adobe Campaign o tramite un browser Web. Il contenuto può essere immesso automaticamente anche tramite l&#39;acquisizione di flusso XML o dati aggregati in un database.

Combinando il documento XML con i fogli di stile XSL o JavaScript Template si genera automaticamente la proiezione del modello di pubblicazione nei vari formati (HTML, testo).

![](assets/d_ncs_content_process.png)

Per la configurazione del contenuto sono necessarie le seguenti risorse:

* Schemi dati: descrizione della struttura del contenuto XML. Per ulteriori informazioni, vedere [Schemi](../../delivery/using/data-schemas.md)dati.
* Moduli di immissione dati: costruzione di schermate di immissione dati. Per ulteriori informazioni, vedere [Moduli](../../delivery/using/input-forms.md)di input.
* Immagini: immagini utilizzate nei moduli di immissione dati. Per ulteriori informazioni, consulta Gestione [](../../delivery/using/formatting.md#image-management)immagini.
* Fogli di stile: formattazione di documenti di output utilizzando il linguaggio XSLT. Per ulteriori informazioni, vedere [Formattazione](../../delivery/using/formatting.md).
* Modelli JavaScript: formattazione di documenti di output utilizzando il linguaggio JavaScript. Per ulteriori informazioni, consulta Modelli [di](../../delivery/using/publication-templates.md)pubblicazione.
* Codici JavaScript: Codici JavaScript per l&#39;aggregazione dei dati. Per ulteriori informazioni, vedere [Aggregator](../../delivery/using/publication-templates.md#aggregator).
* Modelli di pubblicazione: definizione di modelli di pubblicazione. Per ulteriori informazioni, consulta Modelli [di](../../delivery/using/publication-templates.md)pubblicazione.
* Contenuto: le istanze di contenuto da creare e pubblicare. Per ulteriori informazioni, consultate [Utilizzo di un modello](../../delivery/using/using-a-content-template.md)di contenuto.
