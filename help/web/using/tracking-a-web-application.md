---
product: campaign
title: Tracciare le visite in un’applicazione web
description: Tracciare le visite in un’applicazione web
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Web Apps, Reporting, Monitoring
exl-id: 07bd36ce-c701-4998-974f-81fd4fac22a0
source-git-commit: 0fba6a2ad4ffa864e2f726f241aa9d7cd39072a6
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 4%

---

# Tracciare le visite in un’applicazione web{#tracking-a-web-application}



Adobe Campaign consente di tenere traccia e misurare le visite sulle pagine delle applicazioni web inserendo tag di tracciamento. Questa funzionalità può essere utilizzata per tutti i tipi di applicazioni Web (moduli, pagine Web e così via).

In questo modo, puoi definire diversi percorsi di navigazione e valutarne il successo. I dati recuperati sono quindi disponibili nei rapporti di ciascuna applicazione.

I principali miglioramenti presenti in questa versione sono i seguenti:

* Possibilità di inserire diversi tag di tracciamento nella stessa pagina per semplificare la definizione dei percorsi di navigazione (ad esempio acquisto, abbonamento, restituzione, ecc.).
* Visualizzazione dei percorsi di navigazione e dei tag di tracciamento delle diverse pagine nel dashboard dell’applicazione Web.

  ![](assets/trackers_1.png)

* Generazione di un rapporto di tracciamento completo.

  ![](assets/trackers_5.png)

  I principali indicatori sono i seguenti:

   * **Tasso di conversione**: numero di persone che hanno visualizzato tutti i passaggi di un percorso di navigazione.
   * **Percentuale non recapitate**: numero di persone che hanno visualizzato solo il primo passaggio
   * **Funnel di conversione**: tasso di perdita tra ciascun passaggio.

  Inoltre, un grafico di tipo **Settore** mostra la popolazione in base alla sua origine.

## Identificazione dell’origine del traffico {#identifying-the-traffic-source}

Per identificare l’origine del visitatore durante l’accesso a un’applicazione web è possibile utilizzare due diverse modalità:

1. Invio di una consegna specifica per concedere l’accesso alle pagine dell’applicazione web: in questo caso, l’origine del traffico è la consegna,
1. Associazione dell’applicazione web a un’origine del traffico dedicata: in questo caso, deve essere una consegna esterna di tipo &quot;origine del traffico&quot;. Può essere selezionato dalle proprietà dell’applicazione web o dalla mappatura di destinazione.

   ![](assets/trackers_6.png)

Per identificare l’origine del traffico in un’applicazione web, Adobe Campaign cerca successivamente le seguenti informazioni:

1. l’identificatore della consegna sorgente, se esistente (cookie nlId),
1. l’identificatore della consegna esterna definito nelle proprietà dell’applicazione web, se presente,
1. l’identificatore della consegna esterna definito nella mappatura di destinazione, se presente.

>[!NOTE]
>
>Il tracciamento anonimo è disponibile solo se l’opzione è stata attivata nella procedura guidata di distribuzione durante l’installazione di Campaign.

## Applicazioni Web progettate con Digital Content Editor (DCE) {#web-applications-designed-with-digital-content-editor--dce-}

Quando un&#39;applicazione Web viene creata utilizzando l&#39;editor di contenuti HTML - **Digital Content Editor (DCE)** - i tag di tracciamento vengono inseriti dalla scheda **[!UICONTROL Properties]** dell&#39;editor. Per ulteriori informazioni su Digital Content Editor (DCE), consultare [questa sezione](about-campaign-html-editor.md).

![](assets/trackers_2.png)

Quando si utilizza l’interfaccia web, i tag di tracciamento devono essere inseriti dalle proprietà della pagina.

![](assets/trackers_3.png)

L&#39;icona **[!UICONTROL Display blocks]** ti consente di visualizzare il numero di tag di tracciamento definiti per la pagina.

![](assets/trackers_4.png)
