---
title: Informazioni sull’editor HTML di Campaign
seo-title: Informazioni sull’editor HTML di Campaign
description: Informazioni sull’editor HTML di Campaign
seo-description: null
page-status-flag: never-activated
uuid: 1b1d392d-4f19-4092-b57d-02051a242675
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: editing-html-content
discoiquuid: 1ffe9f58-7258-4794-a314-524065f8a33b
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 4%

---


# Informazioni sull’editor HTML di Campaign{#about-campaign-html-editor}

DCE ( **Digital Content Editor)** è un editor di contenuti HTML che consente di creare o modificare facilmente modelli o contenuti in formato HTML all&#39;interno  Adobe Campaign.

Digital Content Editor consente di inserire e formattare elementi di pagina e di associare campi di database agli elementi di una pagina HTML. Per impostazione predefinita, questa opzione è disponibile quando si crea una pagina per un&#39;applicazione Web o quando si creano consegne basate su un modello in cui è attiva.

>[!NOTE]
>
>DCE consente solo di eseguire le operazioni descritte in questa sezione.
>
>Se desiderate aggiungere codice JavaScript lato server, è meglio aggiungerlo nei blocchi di personalizzazione. Per ulteriori informazioni sulla creazione e la modifica dei blocchi di personalizzazione, consulta [questa pagina](../../delivery/using/personalization-blocks.md).

>[!CAUTION]
>
>Per motivi di privacy, si consiglia di utilizzare HTTPS per tutte le risorse esterne.

## Funzionamento generale di Content Editor {#content-editor-general-operation}

Questa sezione illustra i passaggi principali per modificare e caricare il contenuto modificato con DCE nel contesto di un&#39;applicazione Web e nel contesto di una distribuzione.

L&#39;operazione generale è la seguente:

![](assets/dce_schema.png)

Per creare una semplice applicazione Web, procedere come segue:

* Creare un&#39;applicazione Web, per ulteriori informazioni, fare riferimento a [Creazione di una pagina](../../web/using/creating-a-landing-page.md)di destinazione,
* Selezionate il contenuto esistente o create il contenuto da un modello standard, per ulteriori informazioni, fate riferimento a Gestione [](../../web/using/template-management.md)modelli,
* Per ulteriori informazioni, consulta [Modifica dei contenuti](../../web/using/editing-content.md),
* Pubblicate l&#39;applicazione Web, per ulteriori informazioni, consultate [Pubblicazione del contenuto](../../web/using/creating-a-landing-page.md#step-3---publishing-content) e [questa pagina](../../web/using/publishing-a-web-form.md#managing-web-forms-delivery-and-tracking).

>[!NOTE]
>
>Per un esempio completo che descrive l&#39;implementazione di DCE nel framework di un&#39;applicazione Web, vedere [Creazione di una pagina](../../web/using/creating-a-landing-page.md)di destinazione.

Per creare una consegna tramite e-mail, effettuate le seguenti operazioni:

* Creare una consegna da un modello di tipo e-mail in cui il DCE è attivo,
* Selezionate il contenuto esistente o create il contenuto da un modello standard,
* Modifica e configurazione di contenuti online,
* Invia la consegna, per ulteriori informazioni, consulta [questa sezione](../../delivery/using/steps-about-delivery-creation-steps.md).

>[!NOTE]
>
>Per un esempio completo con dettagli sull&#39;implementazione del DCE nel quadro di una consegna tramite e-mail, fare riferimento a [questo caso](../../web/using/use-case--creating-an-email-delivery.md)d&#39;uso.

