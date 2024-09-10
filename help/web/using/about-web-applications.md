---
product: campaign
title: Introduzione alle applicazioni web
description: Creazione e condivisione di applicazioni Web, pagine di destinazione e sondaggi dinamici
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Landing Pages, Web Apps
exl-id: df58221f-f71b-49d5-a6a1-c81ddff27fdb
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '694'
ht-degree: 20%

---

# Introduzione alle applicazioni web{#about-web-applications}



Adobe Campaign consente di creare e pubblicare applicazioni web dinamiche e interattive con dati provenienti dal database e contenuti adattati ai diritti dell’utente connesso.

È possibile creare pagine, ad esempio un modulo di modifica su una extranet, o moduli di notifica che includono dati provenienti dal database con tabelle, grafici, moduli di input e così via. Questa funzionalità consente di progettare e pubblicare pagine Web in cui gli utenti possono cercare o immettere informazioni.

Può trattarsi di un modulo di abbonamento contenente dati precaricati con le informazioni contenute nel database di Adobe Campaign, come illustrato di seguito:

![](assets/webapp_form_sample.png)

In questo capitolo viene fornita una panoramica sulla gestione delle applicazioni Web.

>[!NOTE]
>
>Per informazioni su come ottimizzare la protezione per le applicazioni Web, consultare l&#39;[elenco di controllo protezione e privacy](https://helpx.adobe.com/it/campaign/kb/acc-security.html).

>[!CAUTION]
>
>Per motivi di privacy, consigliamo di utilizzare HTTPS per tutte le risorse esterne.

## Ambito applicazione Web {#web-application-scope}

Le applicazioni web in Adobe Campaign consentono di accedere alle seguenti funzionalità:

* Creazione di moduli con più pagine. Per ulteriori informazioni, consulta questa [pagina](about-web-forms.md).
* Gestione di sondaggi multilingue con uno strumento di traduzione integrato. Per ulteriori informazioni, consulta questa [pagina](translating-a-web-application.md).
* Interfaccia di gestione delle pagine grafiche, layout di pagina a più colonne. Per ulteriori informazioni, consulta questa [pagina](designing-a-web-application.md).
* Personalizzazione del rendering e posizione del campo. Per ulteriori informazioni, consulta questa [pagina](editing-content.md#adding-personalization-content).
* Visualizzazione condizionale dei campi del sondaggio in base alle risposte fornite. Per ulteriori informazioni, consulta questa [pagina](form-rendering.md#defining-fields-conditional-display).
* Visualizzazione casuale delle domande. Per ulteriori informazioni, consulta questa [pagina](../../surveys/using/building-a-survey.md#adding-questions).
* Visualizzazione pagina condizionale. Per ulteriori informazioni, consulta questa [pagina](defining-web-forms-page-sequencing.md#conditional-page-display).
* Verifica delle informazioni prima della convalida in base al tipo di dati previsto (numero, indirizzo e-mail, data, ecc.) e i campi obbligatori. Per ulteriori informazioni, consulta questa [pagina](form-rendering.md#defining-control-settings).
* Inviti o notifiche e-mail. Per ulteriori informazioni, consulta questa [pagina](publishing-a-web-form.md#delivering-a-form-via-email).
* Personalization dei messaggi di errore e di fine. Per ulteriori informazioni, consulta questa [pagina](defining-web-forms-properties.md#setting-up-an-error-page).
* Utilizzo di immagini, video, collegamenti ipertestuali, captcha, ecc. Per ulteriori informazioni, consulta questa [pagina](editing-content.md).
* Monitoraggio delle risposte in tempo reale Per ulteriori informazioni, consulta questa [pagina](../../surveys/using/publish-track-and-use-collected-data.md#response-tracking).

Il modulo opzionale per la creazione di **Sondaggio** offre le seguenti funzionalità aggiuntive:

* Estensione dinamica del database: creazione di risposte non incluse nel modello di dati iniziale. Per ulteriori informazioni, consulta questa [pagina](../../surveys/using/managing-answers.md#storing-collected-answers).
* Generazione di rapporti dedicati. Per ulteriori informazioni, consulta questa [pagina](../../surveys/using/publish-track-and-use-collected-data.md#reports-on-surveys).

Rispetto alle applicazioni Web, i sondaggi hanno un&#39;interfaccia grafica semplificata con un numero ridotto di controlli di modifica.

>[!NOTE]
>
>I sondaggi sono descritti in [questa sezione](../../surveys/using/about-surveys.md).
>
>Le funzionalità generali dei moduli Web in Adobe Campaign sono descritte in dettaglio in [questa sezione](about-web-forms.md).

## Implementazione dell’applicazione web {#web-application-implementation}

Per creare e pubblicare un&#39;applicazione Web, è necessario:

1. Crea il contenuto (campi, elenchi, tabelle, grafici, ecc.).

   È inoltre possibile visualizzare la sezione che descrive i campi disponibili per i moduli: tutti questi campi sono disponibili anche per le applicazioni Web. Informazioni disponibili in [questa pagina](adding-fields-to-a-web-form.md).

1. Se necessario, puoi aggiungere passaggi di precaricamento, test e salvataggio e configurare il sistema di controllo degli accessi (principalmente nel framework di una pubblicazione Extranet).
1. Pubblicazione dell&#39;applicazione Web per renderla disponibile su una rete Extranet o in Adobe Campaign.

## Configurazione iniziale dell’applicazione web {#web-application-initial-configuration}

L&#39;applicazione Web viene creata tramite il collegamento **[!UICONTROL Web Applications]** nelle schede **[!UICONTROL Campaigns]** e **[!UICONTROL Profiles and targets]**.

Le applicazioni Web sono archiviate nel nodo **[!UICONTROL Resources > Online > Web Applications]** della struttura Adobe Campaign. Le configurazioni sono suddivise nelle seguenti cartelle:

* **[!UICONTROL Administration > Configuration > Form renderings]**: contiene i modelli di rendering per la presentazione del modulo Web (applicazioni e sondaggi). Il modello consente di generare il modulo. Viene inoltre utilizzato un foglio di stile CSS. Questo foglio di stile può essere sovraccaricato a livello di modello. Per ulteriori informazioni, consulta [questa pagina](form-rendering.md#selecting-the-form-rendering-template).
* **[!UICONTROL Resources > Templates > Web application templates]**: contiene modelli di modulo. Per creare un modulo o un&#39;applicazione Web, è necessario partire da un modello.

## Modelli di applicazioni web {#web-application-templates}

Per impostazione predefinita, Adobe Campaign fornisce un modello per ogni applicazione Web disponibile.

>[!NOTE]
>
>È possibile convertire un&#39;applicazione Web esistente in un modello. A tale scopo, selezionare il modulo e fare clic con il pulsante destro del mouse. Seleziona **[!UICONTROL Actions > Save as template...]**.

È possibile creare nuovi modelli tramite il nodo **[!UICONTROL Resources > Templates > Web Application templates]** della struttura Adobe Campaign.

L’assistente alla creazione ti consente di selezionare le opzioni che desideri abilitare, come mostrato di seguito.

![](assets/webapp_create_template.png)

>[!CAUTION]
>
>Le applicazioni disponibili dipendono dalle opzioni e dai moduli. Controlla il contratto di licenza.
