---
product: campaign
title: Introduzione alle applicazioni web
description: Crea e condividi applicazioni web, pagine di destinazione e sondaggi dinamici
audience: web
content-type: reference
topic-tags: web-applications
exl-id: df58221f-f71b-49d5-a6a1-c81ddff27fdb
source-git-commit: f000cb8bae164c22d1ede15db4e763cf50530674
workflow-type: tm+mt
source-wordcount: '689'
ht-degree: 21%

---

# Introduzione alle applicazioni web{#about-web-applications}

![](../../assets/common.svg)

Adobe Campaign consente di creare e pubblicare applicazioni Web dinamiche e interattive con dati del database e contenuti adattati ai diritti dell’utente connesso.

È possibile creare pagine, ad esempio un modulo di modifica in una rete Intranet o moduli di notifica, compresi i dati del database con tabelle, grafici, moduli di input, ecc. Questa funzionalità consente di progettare e pubblicare pagine Web in cui gli utenti possono cercare o immettere informazioni.

Può trattarsi di un modulo di sottoscrizione contenente dati precaricati con informazioni contenute nel database Adobe Campaign, come illustrato di seguito:

![](assets/webapp_form_sample.png)

Questo capitolo fornisce una panoramica sulla gestione delle applicazioni Web.

>[!NOTE]
>
>Fai riferimento a [Lista di controllo protezione e privacy](https://helpx.adobe.com/it/campaign/kb/acc-security.html) per scoprire come ottimizzare la sicurezza per le applicazioni web.

>[!CAUTION]
>
>Per motivi di privacy, si consiglia di utilizzare HTTPS per tutte le risorse esterne.

## Ambito applicazione Web {#web-application-scope}

Le applicazioni web in Adobe Campaign consentono di accedere alle seguenti funzionalità:

* Creazione di moduli a più pagine. Per ulteriori informazioni, consulta questa [pagina](about-web-forms.md).
* Gestione delle indagini multilingue con uno strumento di traduzione integrato. Per ulteriori informazioni, consulta questa [pagina](translating-a-web-application.md).
* Interfaccia grafica per la gestione delle pagine, layout a più colonne. Per ulteriori informazioni, consulta questa [pagina](designing-a-web-application.md).
* Personalizzazione del rendering e posizione del campo. Per ulteriori informazioni, consulta questa [pagina](editing-content.md#adding-personalization-content).
* Visualizzazione condizionale dei campi del sondaggio in base alle risposte. Per ulteriori informazioni, consulta questa [pagina](form-rendering.md#defining-fields-conditional-display).
* Visualizzazione casuale delle domande. Per ulteriori informazioni, consulta questa [pagina](../../surveys/using/building-a-survey.md#adding-questions).
* Visualizzazione della pagina condizionale. Per ulteriori informazioni, consulta questa [pagina](defining-web-forms-page-sequencing.md#conditional-page-display).
* Verifica delle informazioni prima della convalida in base al tipo di dati previsto (numero, indirizzo e-mail, data, ecc.) e i campi obbligatori. Per ulteriori informazioni, consulta questa [pagina](form-rendering.md#defining-control-settings).
* Invia inviti o notifiche via e-mail. Per ulteriori informazioni, consulta questa [pagina](publishing-a-web-form.md#delivering-a-form-via-email).
* Personalizzazione dei messaggi di errore e di fine. Per ulteriori informazioni, consulta questa [pagina](defining-web-forms-properties.md#setting-up-an-error-page).
* Uso di immagini, video, collegamenti ipertestuali, captcha, ecc. Per ulteriori informazioni, consulta questa [pagina](editing-content.md).
* Monitoraggio delle risposte in tempo reale. Per ulteriori informazioni, consulta questa [pagina](../../surveys/using/publish--track-and-use-collected-data.md#response-tracking).

L&#39;opzione **Sondaggio** il modulo di creazione offre le seguenti funzionalità aggiuntive:

* Estensione dinamica del database: creazione di risposte non incluse nel modello dati iniziale. Per ulteriori informazioni, consulta questa [pagina](../../surveys/using/managing-answers.md#storing-collected-answers).
* Generazione di report dedicati. Per ulteriori informazioni, consulta questa [pagina](../../surveys/using/publish--track-and-use-collected-data.md#reports-on-surveys).

Rispetto alle applicazioni Web, i sondaggi hanno un&#39;interfaccia grafica semplificata con un numero ridotto di controlli di modifica.

>[!NOTE]
>
>Le indagini sono dettagliate in [questa sezione](../../surveys/using/about-surveys.md).
>
>Le funzionalità generali dei moduli web in Adobe Campaign sono descritte in [questa sezione](about-web-forms.md).

## Implementazione di applicazioni web {#web-application-implementation}

Per creare e pubblicare un&#39;applicazione Web, è necessario:

1. Crea il contenuto (campi, elenchi, tabelle, grafici, ecc.).

   È inoltre possibile visualizzare la sezione che descrive i campi disponibili per i moduli: tutti questi campi sono disponibili anche per le applicazioni Web. Queste informazioni sono disponibili in [questa pagina](adding-fields-to-a-web-form.md).

1. Se necessario, è possibile aggiungere passaggi di precaricamento, test e salvataggio e configurare il sistema di controllo accessi (principalmente nell&#39;ambito di una pubblicazione extranet).
1. Pubblicazione dell’applicazione Web per renderla disponibile su una rete extranet o in Adobe Campaign.

## Configurazione iniziale dell&#39;applicazione Web {#web-application-initial-configuration}

L&#39;applicazione web viene creata tramite **[!UICONTROL Web Applications]** nel collegamento **[!UICONTROL Campaigns]** e **[!UICONTROL Profiles and targets]** schede.

Le applicazioni web sono memorizzate in **[!UICONTROL Resources > Online > Web Applications]** nodo della struttura Adobe Campaign. Le configurazioni sono suddivise nelle cartelle seguenti:

* **[!UICONTROL Administration > Configuration > Form renderings]**: contiene i modelli di rendering per la presentazione del modulo Web (applicazioni e sondaggi). Il modello consente di generare il modulo. Utilizza anche un foglio di stile CSS. Questo foglio di stile può essere sovraccaricato a livello di modello. Per ulteriori informazioni, consulta [questa pagina](form-rendering.md#selecting-the-form-rendering-template).
* **[!UICONTROL Resources > Templates > Web application templates]**: contiene modelli di modulo. Per creare un modulo o un&#39;applicazione Web, è necessario iniziare da un modello.

## Modelli di applicazione web {#web-application-templates}

Per impostazione predefinita, Adobe Campaign fornisce un modello per applicazione Web disponibile.

>[!NOTE]
>
>È possibile convertire un&#39;applicazione Web esistente in un modello. A questo scopo, seleziona il modulo e fai clic con il pulsante destro del mouse sul modulo. Seleziona **[!UICONTROL Actions > Save as template...]**.

Puoi creare nuovi modelli tramite la **[!UICONTROL Resources > Templates > Web Application templates]** nodo della struttura Adobe Campaign.

La procedura guidata di creazione consente di selezionare le opzioni che si desidera abilitare, come illustrato di seguito.

![](assets/webapp_create_template.png)

>[!CAUTION]
>
>Le applicazioni disponibili dipendono dalle opzioni e dai moduli. Controlla il contratto di licenza.
