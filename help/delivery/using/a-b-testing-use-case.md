---
solution: Campaign Classic
product: campaign
title: Informazioni su questo caso di utilizzo
description: Scopri come eseguire test A/B tramite un caso d’uso dedicato.
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 346b72d522c947b2a2552176b910ded8d622f3ab
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---


# Informazioni sul caso di utilizzo {#about-use-case}

In questo caso di utilizzo, confronteremo due contenuti di distribuzione delle e-mail tramite un flusso di lavoro di targeting. Il messaggio e il testo sono identici in entrambe le consegne: cambia solo il layout.

La popolazione interessata è divisa in tre parti: due gruppi di test e la popolazione rimanente. A ogni gruppo di test viene inviata una versione diversa della consegna.

Dopo la consegna, viene configurato un periodo di attesa di 5 giorni prima di raccogliere i risultati delle migliori tariffe aperte. Il contenuto della distribuzione con il punteggio più alto viene quindi recuperato da uno script e inviato alla popolazione non utilizzata come gruppo di test.

Si prega di notare che i criteri che decideranno quale consegna è migliore possono essere modificati per soddisfare le vostre esigenze. Può trattarsi del tasso di apertura, del tasso di click-through, del tasso di sottoscrizione, della reattività, ecc.

Inoltre, il test dettagliato in questo caso d&#39;uso riguardava solo due consegne, ma potete testare tutte le versioni necessarie. È sufficiente aggiungere attività al flusso di lavoro.

I passaggi principali per eseguire questo caso di utilizzo sono:

* [Passaggio 1: Creare un flusso di lavoro di targeting](#step-1--creating-a-targeting-workflow)
* [Passaggio 2: Configurare i campioni popolazione](#step-2--configuring-population-samples)
* [Passaggio 3: Creare due modelli di consegna](#step-3--creating-two-delivery-templates)
* [Passaggio 4: Configurare le consegne nel flusso di lavoro](#step-4--configuring-the-deliveries-in-the-workflow)
* [Passaggio 5: Creare lo script](#step-5--creating-the-script)
* [Passaggio 7: Avviare il flusso di lavoro](#step-7--starting-the-workflow)
* [Passaggio 8: Analizzare il risultato](#step-8--analyzing-the-result).

**Argomenti correlati:**

* [Introduzione ai test A/B](../../delivery/using/get-started-a-b-testing.md)
* [Configurazione del test A/B](../../delivery/using/configuring-a-b-testing.md)
