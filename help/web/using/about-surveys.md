---
solution: Campaign Classic
product: campaign
title: Introduzione ai sondaggi
description: Introduzione ai sondaggi di Campaign
audience: web
content-type: reference
topic-tags: online-surveys
translation-type: tm+mt
source-git-commit: e76eb171aac1f7088ff8647f99c928ec349b24fc
workflow-type: tm+mt
source-wordcount: '590'
ht-degree: 1%

---


# Introduzione ai sondaggi{#about-surveys}

 Adobe Campaign include un modulo grafico per definire e pubblicare applicazioni Web. Viene utilizzato per creare pagine, ad esempio un modulo di modifica su una rete extranet, o moduli di notifica, inclusi i dati del database con tabelle, grafici, moduli di input e così via. Questa funzionalità consente di progettare e pubblicare pagine Web in cui gli utenti possono cercare o immettere informazioni.

Il modulo opzionale **Survey** consente di creare un nuovo tipo di applicazione Web per creare e gestire questionari online, ad esempio moduli per aggiungere o modificare le informazioni sul profilo, per iscriversi o annullarne la sottoscrizione a un servizio di informazione o a un modulo di partecipazione al concorso. Una volta raccolte, le risposte vengono memorizzate nel database o nelle variabili locali. Il modello di dati può essere esteso dinamicamente attraverso le risposte fornite ai questionari. Potete visualizzare i risultati in tempo reale, filtrare le risposte e analizzarle utilizzando grafici dedicati.

Questo capitolo descrive il metodo per la creazione e la gestione di **Survey**, la gestione di campi e pagine, le modalità di memorizzazione e i record.

I passaggi per la creazione di un modulo Web standard sono descritti in [questa sezione](../../web/using/about-web-forms.md).

La gestione delle applicazioni Web è dettagliata in [questa sezione](../../web/using/about-web-applications.md). Per ulteriori informazioni, consultare questo capitolo.

>[!CAUTION]
>
>Per motivi di privacy, si consiglia di utilizzare HTTPS per tutte le risorse esterne.

## Ambito delle funzioni {#campaign-surveys-scope}

In  Adobe Campaign, le applicazioni Web in generale consentono di accedere alle seguenti funzionalità:

* Creazione di moduli con più pagine,
* Gestione delle indagini multilingue con uno strumento di traduzione integrato,
* Interfaccia grafica per la gestione delle pagine, layout a più colonne,
* Personalizzazione del rendering e posizione sul campo,
* Visualizzazione condizionale dei campi del sondaggio in base alle risposte,
* Visualizzazione della pagina condizionale,
* Verifica delle informazioni prima dell&#39;approvazione, in base al tipo di dati previsti (numero, indirizzo e-mail, date, ecc.) e campi obbligatori,
* Inviti/notifiche e-mail,
* Personalizzazione di messaggi di errore e messaggi finali,
* Utilizzo di immagini, video, collegamenti ipertestuali, captcha, ecc.

>[!NOTE]
>
>Tutte le configurazioni collegate ai moduli Web sono descritte in [questa sezione](../../web/using/about-web-forms.md). Fare riferimento a questo documento per informazioni dettagliate sui concetti e sulle funzionalità dei moduli Web utilizzando  Adobe Campaign.

Il modulo opzionale per la creazione di sondaggi (**Survey**) offre le seguenti funzionalità aggiuntive:

* Estensione dinamica del database: creazione di risposte che non fanno parte del modello dati iniziale. Per ulteriori informazioni, consultare [Memorizzazione delle risposte raccolte](../../web/using/managing-answers.md#storing-collected-answers).
* Gestione del punteggio. Per ulteriori informazioni, consultare [Gestione punteggio](../../web/using/managing-answers.md#score-management).
* Visualizzazione casuale delle domande. Per ulteriori informazioni, consultare [Aggiunta di domande](../../web/using/building-a-survey.md#adding-questions).
* Tracciamento delle risposte in tempo reale. Per ulteriori informazioni, vedere [Tracciamento delle risposte](../../web/using/publish--track-and-use-collected-data.md#response-tracking).
* Generazione di rapporti dedicati. Per ulteriori informazioni, fare riferimento a [Rapporti sulle indagini](../../web/using/publish--track-and-use-collected-data.md#reports-on-surveys).

Rispetto alle applicazioni Web, i sondaggi hanno un&#39;interfaccia grafica semplificata con un numero ridotto di controlli di modifica.

## Controlla i passaggi di implementazione {#surveys-implementation-steps}

Per creare e distribuire un sondaggio ed elaborarne i risultati, effettuate le seguenti operazioni:

1. Create le pagine del sondaggio e il relativo contenuto (campi di input, elenchi a discesa, domande e così via).
1. Definire le modalità di salvataggio delle risposte.

   Per precaricare il modulo con i dati già presenti nel database, è possibile inserire una fase di pre-caricamento dei dati. Potete anche aggiungere una casella di prova.

1. Pubblicate, quindi distribuite il sondaggio ai destinatari (ad esempio, includete il collegamento in una consegna o in un sito Web).
1. Monitorare le risposte e visualizzare i rapporti.

Per ulteriori informazioni sulla configurazione e la sequenza di questi passaggi, consultare [questa sezione](../../web/using/about-web-forms.md). In questo capitolo sono descritte solo le configurazioni specifiche per i sondaggi.

## Configurazione sondaggi {#surveys-configuration}

I sondaggi sono memorizzati nel nodo **[!UICONTROL Resources > Online > Web Applications]** della struttura di Adobe Campaign . Le configurazioni si trovano nelle cartelle seguenti:

* **[!UICONTROL Administration > Configuration > Form rendering]**: contiene i modelli di rendering per la presentazione di moduli Web (applicazioni e sondaggi).
* **[!UICONTROL Resources > Templates > Web application templates]**: contiene i modelli di modulo. Per creare un modulo, è necessario iniziare con un modello.

>[!NOTE]
>
>Le informazioni di configurazione sono disponibili in [questa sezione](../../web/using/about-web-forms.md).

