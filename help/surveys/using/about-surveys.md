---
product: campaign
title: Introduzione ai sondaggi
description: Introduzione ai sondaggi di Campaign
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Surveys
exl-id: 7061a4f1-006f-4f19-8761-918d8930d885
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 3%

---

# Introduzione ai sondaggi{#about-surveys}



Adobe Campaign include un modulo grafico per definire e pubblicare le applicazioni web. Viene utilizzato per creare pagine, ad esempio un modulo di modifica su una extranet, o moduli di notifica che includono dati provenienti dal database con tabelle, grafici, moduli di input e così via. Utilizzare questa funzionalità per progettare e pubblicare pagine Web in cui gli utenti possono cercare o immettere informazioni.

L&#39;opzione **Sondaggio** il componente aggiuntivo consente di creare un nuovo tipo di applicazione Web per creare e gestire questionari online, ad esempio moduli per aggiungere o modificare informazioni sul profilo, per sottoscrivere o annullare l&#39;abbonamento a un servizio di informazioni o un modulo per l&#39;iscrizione a un concorso. Una volta raccolte, le risposte vengono memorizzate nel database o in variabili locali. Il modello di dati può essere esteso dinamicamente tramite le risposte date ai questionari. Puoi visualizzare i risultati in tempo reale, filtrare le risposte e analizzarle utilizzando grafici dedicati.

Questo capitolo descrive come creare e gestire **Sondaggi**, gestione di campi e pagine, modalità di archiviazione e record.

Scopri come creare il tuo primo sondaggio in [questa pagina](getting-started-with-surveys.md).

>[!NOTE]
>
>* I passaggi dettagliati per la creazione di un modulo web standard sono disponibili in [questo documento](../../web/using/about-web-forms.md).
>
>* La gestione delle applicazioni web è descritta in [questo documento](../../web/using/about-web-applications.md). Fare riferimento a questo capitolo per ulteriori informazioni.

## Ambito della funzione {#campaign-surveys-scope}

In Adobe Campaign, utilizza [Applicazioni web](../../web/using/about-web-forms.md) a:

* Creare moduli a più pagine
* Gestire i moduli multilingue con uno strumento di traduzione integrato
* Gestione dell&#39;interfaccia grafica, layout di pagina a più colonne,
* Aggiungere personalizzazione e definire la posizione del campo
* Visualizzazione delle condizioni dei campi dell’indagine in base alle risposte,
* Visualizzazione pagina condizione,
* Controllare le informazioni prima dell’approvazione, a seconda del tipo di dati previsti (numero, indirizzo e-mail, date, ecc.) e campi obbligatori,
* Inviare inviti/notifiche via e-mail,
* Personalizzare le pagine di errore e finali
* Aggiungere immagini, video, collegamenti ipertestuali, captcha, ecc., nei moduli

Il modulo opzionale per la creazione di sondaggi offre un’interfaccia utente intuitiva e le seguenti funzionalità aggiuntive:

* Estensione dinamica del database: creazione di risposte che non fanno parte del modello dati iniziale. [Ulteriori informazioni](../../surveys/using/managing-answers.md#storing-collected-answers).
* Gestione dei punteggi. [Ulteriori informazioni](../../surveys/using/managing-answers.md#score-management).
* Visualizzazione casuale delle domande. [Ulteriori informazioni](../../surveys/using/building-a-survey.md#adding-questions).
* Tracciamento in tempo reale delle risposte. [Ulteriori informazioni](../../surveys/using/publish-track-and-use-collected-data.md#response-tracking).
* Generazione di rapporti dedicati. [Ulteriori informazioni](../../surveys/using/publish-track-and-use-collected-data.md#reports-on-surveys).


## Passaggi di implementazione {#surveys-implementation-steps}

Applica i seguenti passaggi per creare e consegnare un sondaggio ed elaborarne i risultati:

1. Crea le pagine del sondaggio e il relativo contenuto (campi di input, elenchi a discesa, domande, ecc.).
1. Definisci come salvare le risposte. È possibile inserire un passaggio di precaricamento dei dati per precaricare il modulo con i dati già presenti nel database. È inoltre possibile aggiungere una casella di test.
1. Pubblica, quindi distribuisci il sondaggio ai destinatari (ad esempio, includi il collegamento in una consegna o in un sito web).
1. Monitora le risposte e visualizza i rapporti.

Per ulteriori informazioni sulla configurazione e la sequenza di questi passaggi, consulta [questo documento](../../web/using/about-web-forms.md). In questo capitolo sono descritte solo le configurazioni specifiche dei sondaggi.

>[!CAUTION]
>
>Per motivi di privacy, consigliamo di utilizzare HTTPS per tutte le risorse esterne.

## Impostazioni {#settings}

Per impostazione predefinita, i sondaggi sono disponibili nel **[!UICONTROL Resources > Online > Web Applications]** della struttura Adobe Campaign.

Le impostazioni vengono memorizzate nelle seguenti cartelle:

* **[!UICONTROL Administration > Configuration > Form rendering]**: contiene i modelli di rendering per la presentazione dei moduli web (applicazioni e sondaggi).
* **[!UICONTROL Resources > Templates > Web application templates]**: contiene i modelli di modulo. Per creare un modulo, è necessario iniziare con un modello.

>[!NOTE]
>
>I dettagli delle impostazioni sono disponibili in [questo documento](../../web/using/about-web-forms.md).
