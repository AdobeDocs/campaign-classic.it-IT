---
product: campaign
title: Introduzione ai sondaggi
description: Guida introduttiva ai sondaggi su Campaign
audience: web
content-type: reference
topic-tags: online-surveys
exl-id: 7061a4f1-006f-4f19-8761-918d8930d885
source-git-commit: 91dec9adb177aedc4a82879011371b54886166be
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 4%

---

# Introduzione ai sondaggi{#about-surveys}

![](../../assets/v7-only.svg)

Adobe Campaign include un modulo grafico per definire e pubblicare applicazioni Web. Viene utilizzato per creare pagine, ad esempio un modulo di modifica su una extranet, o moduli di notifica, inclusi dati dal database con tabelle, grafici, moduli di input, ecc. Utilizza questa funzionalità per progettare e pubblicare pagine web in cui gli utenti possono cercare o immettere informazioni.

L&#39;opzione **Sondaggio** add-on consente di creare un nuovo tipo di applicazione Web per creare e gestire questionari online, ad esempio moduli per aggiungere o modificare informazioni di profilo, per effettuare o annullare l’iscrizione a un servizio informazioni o a un modulo di partecipazione a un concorso. Una volta raccolte le risposte, queste vengono memorizzate nel database o nelle variabili locali. Il modello di dati può essere esteso dinamicamente tramite le risposte fornite ai questionari. Puoi visualizzare i risultati in tempo reale, filtrare le risposte e analizzarle utilizzando grafici dedicati.

Questo capitolo descrive come creare e gestire **Indagini**, gestione dei campi e delle pagine, modalità di archiviazione e record.

Scopri come creare il tuo primo sondaggio in [questa pagina](getting-started-with-surveys.md).

>[!NOTE]
>
>* I passaggi dettagliati per la creazione di un modulo web standard sono disponibili in [presente documento](../../web/using/about-web-forms.md).
>
>* La gestione delle applicazioni web è descritta in [presente documento](../../web/using/about-web-applications.md). Fare riferimento a questo capitolo per ulteriori informazioni.


## Ambito delle funzioni {#campaign-surveys-scope}

In Adobe Campaign, utilizza [Applicazioni web](../../web/using/about-web-forms.md) a:

* Creare moduli a più pagine,
* Gestire i moduli multilingue con uno strumento di traduzione integrato,
* Gestire l’interfaccia grafica, layout di pagina a più colonne,
* Aggiungi la personalizzazione e definisci la posizione del campo,
* Visualizzazione delle condizioni dei campi del sondaggio in base alle risposte,
* Visualizzazione della pagina della condizione,
* Controllare le informazioni prima dell’approvazione, a seconda del tipo di dati previsti (numero, indirizzo e-mail, date, ecc.) e campi obbligatori,
* Inviare inviti/notifiche e-mail,
* Personalizzare le pagine di errore e le pagine finali,
* Aggiungere immagini, video, collegamenti ipertestuali, captcha, ecc. nei moduli

Il modulo di creazione di un sondaggio opzionale offre un’interfaccia utente intuitiva e le seguenti funzionalità aggiuntive:

* Estensione dinamica del database: creazione di risposte che non fanno parte del modello dati iniziale. [Ulteriori informazioni](../../surveys/using/managing-answers.md#storing-collected-answers).
* Gestione del punteggio. [Ulteriori informazioni](../../surveys/using/managing-answers.md#score-management).
* Visualizzazione casuale delle domande. [Ulteriori informazioni](../../surveys/using/building-a-survey.md#adding-questions).
* Tracciamento delle risposte in tempo reale. [Ulteriori informazioni](../../surveys/using/publish--track-and-use-collected-data.md#response-tracking).
* Generazione di report dedicati. [Ulteriori informazioni](../../surveys/using/publish--track-and-use-collected-data.md#reports-on-surveys).


## Passaggi di implementazione {#surveys-implementation-steps}

Per creare e distribuire un sondaggio ed elaborarne i risultati, effettua i seguenti passaggi:

1. Crea le pagine del sondaggio e il relativo contenuto (campi di input, elenchi a discesa, domande, ecc.).
1. Definisci come salvare le risposte. È possibile inserire un passaggio di precaricamento dei dati per precaricare il modulo con i dati già presenti nel database. È inoltre possibile aggiungere una casella di test.
1. Pubblica, quindi distribuisci il sondaggio ai destinatari (ad esempio, includi un collegamento in una consegna o in un sito web).
1. Monitora le risposte e visualizza i rapporti.

Per ulteriori informazioni sulla configurazione e la sequenza di questi passaggi, consulta [presente documento](../../web/using/about-web-forms.md). In questo capitolo sono descritte solo le configurazioni specifiche dei sondaggi.

>[!CAUTION]
>
>Per motivi di privacy, si consiglia di utilizzare HTTPS per tutte le risorse esterne.

## Impostazioni {#settings}

Per impostazione predefinita, i sondaggi sono disponibili nella **[!UICONTROL Resources > Online > Web Applications]** nodo della struttura Adobe Campaign.

Le impostazioni sono memorizzate nelle seguenti cartelle:

* **[!UICONTROL Administration > Configuration > Form rendering]**: contiene i modelli di rendering per la presentazione di moduli web (applicazioni e sondaggi).
* **[!UICONTROL Resources > Templates > Web application templates]**: contiene i modelli di modulo. Per creare un modulo, è necessario iniziare con un modello.

>[!NOTE]
>
>I dettagli delle impostazioni sono disponibili in [presente documento](../../web/using/about-web-forms.md).
