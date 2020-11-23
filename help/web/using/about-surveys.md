---
solution: Campaign Classic
product: campaign
title: Informazioni sui sondaggi
description: Informazioni sui sondaggi
audience: web
content-type: reference
topic-tags: online-surveys
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '584'
ht-degree: 1%

---


# Informazioni sui sondaggi{#about-surveys}

 Adobe Campaign include un modulo grafico per definire e pubblicare applicazioni Web. Viene utilizzato per creare pagine, ad esempio un modulo di modifica su una rete extranet, o moduli di notifica, inclusi i dati del database con tabelle, grafici, moduli di input e così via. Questa funzionalità consente di progettare e pubblicare pagine Web in cui gli utenti possono cercare o immettere informazioni.

Il modulo **Survey** opzionale consente di creare un nuovo tipo di applicazione Web per creare e gestire questionari online, ad esempio moduli per aggiungere o modificare informazioni sul profilo, per iscriversi o annullare l’iscrizione a un servizio di informazioni o a un modulo di partecipazione al concorso. Una volta raccolte, le risposte vengono memorizzate nel database o nelle variabili locali. Il modello di dati può essere esteso dinamicamente attraverso le risposte fornite ai questionari. Potete visualizzare i risultati in tempo reale, filtrare le risposte e analizzarle utilizzando grafici dedicati.

Questo capitolo descrive il metodo per la creazione e la gestione di **sondaggi**, gestione di campi e pagine, modalità di memorizzazione e record.

La procedura per la creazione di un modulo Web standard è descritta in [questa sezione](../../web/using/about-web-forms.md).

La gestione delle applicazioni Web è dettagliata in [questa sezione](../../web/using/about-web-applications.md). Per ulteriori informazioni, consultare questo capitolo.

>[!CAUTION]
>
>Per motivi di privacy, si consiglia di utilizzare HTTPS per tutte le risorse esterne.

## Ambito sondaggi campagna {#campaign-surveys-scope}

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

* Estensione dinamica del database: creazione di risposte che non fanno parte del modello dati iniziale. Per ulteriori informazioni, vedere [Memorizzazione delle risposte](../../web/using/managing-answers.md#storing-collected-answers)raccolte.
* Gestione del punteggio. For more on this, refer to [Score management](../../web/using/managing-answers.md#score-management).
* Visualizzazione casuale delle domande. For more on this, refer to [Adding questions](../../web/using/building-a-survey.md#adding-questions).
* Tracciamento delle risposte in tempo reale. For more on this, refer to [Response tracking](../../web/using/publish--track-and-use-collected-data.md#response-tracking).
* Generazione di rapporti dedicati. Per ulteriori informazioni, consulta [Rapporti sulle indagini](../../web/using/publish--track-and-use-collected-data.md#reports-on-surveys).

Rispetto alle applicazioni Web, i sondaggi hanno un&#39;interfaccia grafica semplificata con un numero ridotto di controlli di modifica.

## Procedure di implementazione delle indagini {#surveys-implementation-steps}

Per creare e distribuire un sondaggio ed elaborarne i risultati, effettuate le seguenti operazioni:

1. Create le pagine del sondaggio e il relativo contenuto (campi di input, elenchi a discesa, domande e così via).
1. Definire le modalità di salvataggio delle risposte.

   Per precaricare il modulo con i dati già presenti nel database, è possibile inserire una fase di pre-caricamento dei dati. Potete anche aggiungere una casella di prova.

1. Pubblicate, quindi distribuite il sondaggio ai destinatari (ad esempio, includete il collegamento in una consegna o in un sito Web).
1. Monitorare le risposte e visualizzare i rapporti.

Per ulteriori informazioni sulla configurazione e la sequenza di questi passaggi, consultare [questa sezione](../../web/using/about-web-forms.md). In questo capitolo sono descritte solo le configurazioni specifiche per i sondaggi.

## Configurazione sondaggi {#surveys-configuration}

I sondaggi sono memorizzati nel **[!UICONTROL Resources > Online > Web Applications]** nodo della struttura di Adobe Campaign . Le configurazioni si trovano nelle cartelle seguenti:

* **[!UICONTROL Administration > Configuration > Form rendering]**: contiene i modelli di rendering per la presentazione di moduli Web (applicazioni e sondaggi).
* **[!UICONTROL Resources > Templates > Web application templates]**: contiene i modelli di modulo. Per creare un modulo, è necessario iniziare con un modello.

>[!NOTE]
>
>Le informazioni sulla configurazione sono disponibili in [questa sezione](../../web/using/about-web-forms.md).

