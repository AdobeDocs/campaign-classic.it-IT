---
product: campaign
title: Tracciare le visite in un’applicazione web
description: Tracciare le visite in un’applicazione web
feature: Web Apps
exl-id: 07bd36ce-c701-4998-974f-81fd4fac22a0
source-git-commit: b6f1556cf49492cefaf61c29a058584b0ccee16a
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 4%

---

# Tracciare le visite in un’applicazione web{#tracking-a-web-application}

![](../../assets/common.svg)

Adobe Campaign consente di monitorare e misurare le visite sulle pagine delle applicazioni Web inserendo tag di tracciamento. Questa funzionalità può essere utilizzata per tutti i tipi di applicazioni Web (moduli, pagine web, ecc.).

È quindi possibile definire diversi percorsi di navigazione e valutarne il successo. I dati recuperati sono quindi disponibili nei rapporti di ogni applicazione.

I principali miglioramenti descritti in questa versione sono i seguenti:

* Possibilità di inserire diversi tag di tracciamento sulla stessa pagina per facilitare la definizione dei percorsi di navigazione (ad esempio acquisto, abbonamento, ritorno, ecc.).
* Visualizzazione dei percorsi di navigazione e dei tag di tracciamento delle diverse pagine nel dashboard dell&#39;applicazione Web.

   ![](assets/trackers_1.png)

* Generazione di un rapporto di tracciamento completo.

   ![](assets/trackers_5.png)

   I principali indicatori sono i seguenti:

   * **Tasso di conversione**: numero di persone che hanno visualizzato tutti i passaggi di un percorso di navigazione.
   * **Frequenza di rimbalzo**: numero di persone che hanno visualizzato solo il primo passaggio
   * **Funnel di conversione**: tasso di perdita tra ciascun passo.

   Inoltre, un **Settore** grafico a tipi mostra la popolazione in base all’origine.

## Identificazione dell’origine del traffico {#identifying-the-traffic-source}

È possibile utilizzare due modalità diverse per identificare la provenienza del visitatore all’accesso a un’applicazione Web:

1. Invio di una consegna specifica per concedere l’accesso alle pagine dell’applicazione Web: in questo caso, l’origine del traffico è questa consegna,
1. Associazione dell&#39;applicazione Web a un&#39;origine traffico dedicata: in questo caso, deve essere una consegna esterna di tipo &quot;origine traffico&quot;. Può essere selezionato dalle proprietà dell&#39;applicazione Web o dalla mappatura di destinazione.

   ![](assets/trackers_6.png)

Per identificare l&#39;origine del traffico in un&#39;applicazione Web, Adobe Campaign cerca in modo successivo le seguenti informazioni:

1. l’identificatore di consegna di origine, se esiste (cookie nlId),
1. l&#39;identificatore della consegna esterna definito nelle proprietà dell&#39;applicazione Web, se esiste,
1. l’identificatore della consegna esterna definita nel mapping di destinazione, se presente.

>[!NOTE]
>
>Il tracciamento anonimo è disponibile solo se l’opzione è stata attivata nella procedura guidata di distribuzione durante l’installazione di Campaign.

## Applicazioni web progettate con Digital Content Editor (DCE) {#web-applications-designed-with-digital-content-editor--dce-}

Quando viene creata un’applicazione Web utilizzando l’editor di contenuti di HTML - **Editor di contenuti digitali (DCE)** - i tag di tracciamento vengono inseriti dal **[!UICONTROL Properties]** scheda dell’editor. Per ulteriori informazioni sull’editor di contenuti digitali (DCE), consulta [questa sezione](about-campaign-html-editor.md).

![](assets/trackers_2.png)

Quando si utilizza l’interfaccia Web, i tag di tracciamento devono essere inseriti dalle proprietà della pagina.

![](assets/trackers_3.png)

La **[!UICONTROL Display blocks]** consente di visualizzare il numero di tag di tracciamento definiti per la pagina.

![](assets/trackers_4.png)
