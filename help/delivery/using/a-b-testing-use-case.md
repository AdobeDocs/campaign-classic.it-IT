---
product: campaign
title: Caso d'uso del test AB
description: Scopri come eseguire test A/B tramite un caso d’uso dedicato
feature: A/B Testing
exl-id: 4eb139a0-5342-4084-9f6d-d736e05bf1c6
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 4%

---

# Test A/B di questo caso d’uso {#ab-testing-use-case}

![](../../assets/common.svg)

In questo caso d’uso, confronteremo due contenuti di consegna e-mail tramite un flusso di lavoro di targeting. Il messaggio e il testo sono identici in entrambe le consegne: cambia solo il layout.

La popolazione mirata è divisa in tre parti: due gruppi di test e la popolazione rimanente. A ogni gruppo di test viene inviata una versione diversa della consegna.

Dopo la consegna, viene configurato un periodo di attesa di 5 giorni prima di raccogliere i risultati dei migliori tassi di apertura. Il contenuto della consegna con il punteggio più alto viene quindi recuperato da uno script e inviato alla popolazione non utilizzata come gruppo di test.

Tieni presente che i criteri che decideranno quale consegna è la migliore possono essere modificati per soddisfare le tue esigenze. Può essere il tasso di apertura, il tasso di click-through, il tasso di abbonamento, la reattività, ecc.

Inoltre, il test descritto in questo caso d’uso riguardava solo due consegne, ma puoi testare tutte le versioni necessarie. È sufficiente aggiungere attività al flusso di lavoro.

I passaggi principali per eseguire questo caso d’uso sono i seguenti:

* [Passaggio 1: Creare un flusso di lavoro di targeting](a-b-testing-uc-targeting-workflow.md)
* [Passaggio 2: Configurare i campioni di popolazione](a-b-testing-uc-population-samples.md)
* [Passaggio 3: Creare due modelli di consegna](a-b-testing-uc-delivery-templates.md)
* [Passaggio 4: Configurare le consegne nel flusso di lavoro](a-b-testing-uc-configuring-deliveries.md)
* [Passaggio 5: Creare lo script](a-b-testing-uc-script.md)
* [Passaggio 6: Definire la consegna finale](a-b-testing-uc-final-delivery.md)
* [Passaggio 7: Avvia il flusso di lavoro](a-b-testing-uc-start-workflow.md)
* [Passaggio 8: Analizzare il risultato](a-b-testing-uc-analyzing.md)

**Argomenti correlati:**

* [Introduzione ai test A/B](get-started-a-b-testing.md)
* [Configurare il test A/B](configuring-a-b-testing.md)
