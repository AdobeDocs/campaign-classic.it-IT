---
title: Informazioni sulle applicazioni Web
seo-title: Informazioni sulle applicazioni Web
description: Informazioni sulle applicazioni Web
seo-description: null
page-status-flag: never-activated
uuid: acfa6e5e-b503-4a1a-871e-e70007874f57
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-applications
discoiquuid: 3af763ad-6b0d-4f4c-aed1-c5e12efd4760
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c9c9d5f96856ce9e19571bad032d2bf04eaa60bd

---


# Informazioni sulle applicazioni Web{#about-web-applications}

Adobe Campaign consente di creare e pubblicare applicazioni Web dinamiche e interattive con dati provenienti dal database e contenuti adattati ai diritti dell&#39;utente connesso. È possibile creare pagine, ad esempio un modulo di modifica su una rete extranet, o moduli di notifica, inclusi i dati del database con tabelle, grafici, moduli di input e così via. Questa funzionalità consente di progettare e pubblicare pagine Web in cui gli utenti possono cercare o immettere informazioni.

Può trattarsi di un modulo di iscrizione contenente dati precaricati con informazioni contenute nel database Adobe Campaign, come illustrato di seguito:

![](assets/webapp_form_sample.png)

Questo capitolo fornisce una panoramica della gestione delle applicazioni Web.

>[!CAUTION]
>
>Per motivi di privacy, si consiglia di utilizzare HTTPS per tutte le risorse esterne.

## Ambito applicazione Web {#web-application-scope}

Le applicazioni Web in Adobe Campaign consentono di accedere alle seguenti funzionalità:

* Creazione di moduli con più pagine,
* Gestione delle indagini multilingue con uno strumento di traduzione integrato,
* Interfaccia grafica per la gestione delle pagine, layout a più colonne,
* Personalizzazione del rendering e posizione sul campo,
* Visualizzazione condizionale dei campi del sondaggio in base alle risposte,
* Visualizzazione casuale delle domande,
* Visualizzazione della pagina condizionale,
* Controllo delle informazioni prima della convalida in base al tipo di dati previsto (numero, indirizzo e-mail, data, ecc.) e i campi obbligatori,
* inviti e-mail o notifiche,
* Personalizzazione di messaggi di errore e messaggi finali,
* Utilizzo di immagini, video, collegamenti ipertestuali, captcha, ecc.
* Monitoraggio delle risposte in tempo reale.

Il modulo di creazione **sondaggio** opzionale offre le seguenti funzionalità aggiuntive:

* Estensione dinamica del database: creazione di risposte non incluse nel modello di dati iniziale,
* Generazione di rapporti dedicati.

Rispetto alle applicazioni Web, i sondaggi hanno un&#39;interfaccia grafica semplificata con un numero ridotto di controlli di modifica.

>[!NOTE]
>
>Le indagini sono dettagliate in [questa sezione](../../web/using/about-surveys.md).
>
>Le funzionalità generali dei moduli Web in Adobe Campaign sono descritte in [questa sezione](../../web/using/about-web-forms.md).

## Implementazione applicazione Web {#web-application-implementation}

Per creare e pubblicare un&#39;applicazione Web, è necessario:

1. Creare il contenuto (campi, elenchi, tabelle, grafici ecc.).

   È inoltre possibile visualizzare la sezione con i dettagli dei campi disponibili per i moduli: tutti questi campi sono disponibili anche per le applicazioni Web. Queste informazioni sono disponibili in [questa pagina](../../web/using/adding-fields-to-a-web-form.md).

1. Se necessario, potete aggiungere passaggi di precaricamento, test e salvataggio e configurare il sistema di controllo degli accessi (principalmente all&#39;interno del framework di una pubblicazione extranet).
1. Pubblicazione dell&#39;applicazione Web per renderla disponibile su una rete extranet o in Adobe Campaign.

## Configurazione iniziale applicazione Web {#web-application-initial-configuration}

L&#39;applicazione Web viene creata tramite il **[!UICONTROL Web Applications]** collegamento nelle **[!UICONTROL Campaigns]** schede e **[!UICONTROL Profiles and targets]** .

Le applicazioni Web sono memorizzate nel **[!UICONTROL Resources > Online > Web Applications]** nodo della struttura di Adobe Campaign. Le configurazioni sono suddivise nelle cartelle seguenti:

* **[!UICONTROL Administration > Configuration > Form renderings]**: contiene i modelli di rendering per la presentazione del modulo Web (applicazioni e sondaggi). Il modello consente di generare il modulo. Utilizza anche un foglio di stile CSS. Questo foglio di stile può essere sovraccaricato a livello di modello. For more on this, refer to [this page](../../web/using/form-rendering.md#selecting-the-form-rendering-template).
* **[!UICONTROL Resources > Templates > Web application templates]**: contiene modelli di modulo. Per creare un modulo o un&#39;applicazione Web, è necessario iniziare da un modello.

## Modelli di applicazioni Web {#web-application-templates}

Per impostazione predefinita, Adobe Campaign fornisce un modello per l&#39;applicazione Web disponibile.

>[!NOTE]
>
>È possibile convertire un&#39;applicazione Web esistente in un modello. A tale scopo, selezionare il modulo e fare clic con il pulsante destro del mouse. Selezionare **[!UICONTROL Actions > Save as template...]**.

Puoi creare nuovi modelli tramite il **[!UICONTROL Resources > Templates > Web Application templates]** nodo della struttura di Adobe Campaign.

La procedura guidata di creazione consente di selezionare le opzioni che si desidera abilitare, come illustrato di seguito.

![](assets/webapp_create_template.png)

>[!CAUTION]
>
>Le applicazioni disponibili dipendono dalle opzioni e dai moduli. Controllare il contratto di licenza.

