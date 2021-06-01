---
product: campaign
title: Introduzione ai sondaggi
description: Guida introduttiva ai sondaggi su Campaign
audience: web
content-type: reference
topic-tags: online-surveys
exl-id: 7061a4f1-006f-4f19-8761-918d8930d885
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '590'
ht-degree: 1%

---

# Introduzione ai sondaggi{#about-surveys}

Adobe Campaign include un modulo grafico per definire e pubblicare applicazioni Web. Viene utilizzato per creare pagine, ad esempio un modulo di modifica su una extranet, o moduli di notifica, inclusi dati dal database con tabelle, grafici, moduli di input, ecc. Questa funzionalità consente di progettare e pubblicare pagine web in cui gli utenti possono cercare o immettere informazioni.

Il modulo opzionale **Survey** consente di creare un nuovo tipo di applicazione Web per creare e gestire questionari online, ad esempio moduli per aggiungere o modificare informazioni sul profilo, per effettuare o annullare l’iscrizione a un servizio informazioni o a un modulo di partecipazione al concorso. Una volta raccolte le risposte, queste vengono memorizzate nel database o nelle variabili locali. Il modello di dati può essere esteso dinamicamente tramite le risposte fornite ai questionari. Puoi visualizzare i risultati in tempo reale, filtrare le risposte e analizzarle utilizzando grafici dedicati.

Questo capitolo descrive il metodo per creare e gestire **Sondaggi**, la gestione dei campi e delle pagine, le modalità di archiviazione e i record.

I passaggi per la creazione di un modulo web standard sono descritti in [questa sezione](../../web/using/about-web-forms.md).

La gestione delle applicazioni web è descritta in [questa sezione](../../web/using/about-web-applications.md). Fare riferimento a questo capitolo per ulteriori informazioni.

>[!CAUTION]
>
>Per motivi di privacy, si consiglia di utilizzare HTTPS per tutte le risorse esterne.

## Ambito della funzione {#campaign-surveys-scope}

In Adobe Campaign, le applicazioni web in generale consentono di accedere alle seguenti funzionalità:

* Creazione di moduli a più pagine,
* Gestione delle indagini multilingue con uno strumento di traduzione integrato,
* Interfaccia grafica per la gestione delle pagine, layout a più colonne,
* Personalizzazione del rendering e posizione del campo,
* Visualizzazione condizionale dei campi del sondaggio in base alle risposte,
* visualizzazione della pagina condizionale,
* Verifica delle informazioni prima dell’approvazione, a seconda del tipo di dati previsti (numero, indirizzo e-mail, date, ecc.) e campi obbligatori,
* Inviti/notifiche via e-mail,
* Personalizzazione dei messaggi di errore e dei messaggi finali,
* Uso di immagini, video, collegamenti ipertestuali, captcha, ecc.

>[!NOTE]
>
>Tutte le configurazioni collegate ai moduli web sono descritte in [questa sezione](../../web/using/about-web-forms.md). Fare riferimento a questo documento per ulteriori informazioni sui concetti e sulle funzionalità dei moduli web che utilizzano Adobe Campaign.

Il modulo di creazione di un sondaggio opzionale (**Survey**) offre le seguenti funzionalità aggiuntive:

* Estensione dinamica del database: creazione di risposte che non fanno parte del modello dati iniziale. Per ulteriori informazioni, consulta [Memorizzazione delle risposte raccolte](../../web/using/managing-answers.md#storing-collected-answers).
* Gestione del punteggio. Per ulteriori informazioni, consulta [Gestione punteggio](../../web/using/managing-answers.md#score-management).
* Visualizzazione casuale delle domande. Per ulteriori informazioni, consulta [Aggiunta di domande](../../web/using/building-a-survey.md#adding-questions).
* Tracciamento delle risposte in tempo reale. Per ulteriori informazioni, consulta [Tracciamento delle risposte](../../web/using/publish--track-and-use-collected-data.md#response-tracking).
* Generazione di report dedicati. Per ulteriori informazioni, consulta [Report sui sondaggi](../../web/using/publish--track-and-use-collected-data.md#reports-on-surveys).

Rispetto alle applicazioni Web, i sondaggi hanno un&#39;interfaccia grafica semplificata con un numero ridotto di controlli di modifica.

## Passi di implementazione dei sondaggi {#surveys-implementation-steps}

Per creare e distribuire un sondaggio ed elaborarne i risultati, effettua i seguenti passaggi:

1. Crea le pagine del sondaggio e il relativo contenuto (campi di input, elenchi a discesa, domande, ecc.).
1. Definisci come salvare le risposte.

   È possibile inserire un passaggio di precaricamento dei dati per precaricare il modulo con i dati già presenti nel database. È inoltre possibile aggiungere una casella di test.

1. Pubblica, quindi distribuisci il sondaggio ai destinatari (ad esempio, includi un collegamento in una consegna o in un sito web).
1. Monitora le risposte e visualizza i rapporti.

Per ulteriori informazioni sulla configurazione e la sequenza di questi passaggi, consulta [questa sezione](../../web/using/about-web-forms.md). In questo capitolo sono descritte solo le configurazioni specifiche dei sondaggi.

## Configurazione dei sondaggi {#surveys-configuration}

I sondaggi sono memorizzati nel nodo **[!UICONTROL Resources > Online > Web Applications]** della struttura di Adobe Campaign. Le configurazioni si trovano nelle seguenti cartelle:

* **[!UICONTROL Administration > Configuration > Form rendering]**: contiene i modelli di rendering per la presentazione di moduli web (applicazioni e sondaggi).
* **[!UICONTROL Resources > Templates > Web application templates]**: contiene i modelli di modulo. Per creare un modulo, è necessario iniziare con un modello.

>[!NOTE]
>
>Le informazioni di configurazione sono disponibili in [questa sezione](../../web/using/about-web-forms.md).
