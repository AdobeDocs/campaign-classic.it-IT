---
product: campaign
title: Caso di utilizzo del test AB
description: Scopri come eseguire il test A/B tramite un caso d’uso dedicato
badge-v7: label="v7" type="Informative" tooltip="Applicabile a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: A/B Testing
role: User
exl-id: 4eb139a0-5342-4084-9f6d-d736e05bf1c6
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 4%

---

# Test AB: test A/B per questo caso d’uso {#ab-testing-use-case}

In questo caso d’uso, confronteremo due contenuti di consegna e-mail tramite un flusso di lavoro di targeting. Il messaggio e il testo sono identici in entrambe le consegne: cambia solo il layout.

La popolazione interessata è suddivisa in tre gruppi: due gruppi sperimentali e la popolazione rimanente. A ogni gruppo di test viene inviata una versione diversa della consegna.

Dopo la consegna, viene configurato un periodo di attesa di 5 giorni prima di raccogliere i risultati dei tassi di apertura migliori. Il contenuto della consegna con il punteggio più alto viene quindi recuperato da uno script e inviato alla popolazione che non è stata utilizzata come gruppo di test.

I criteri che determineranno quale consegna è la migliore possono essere modificati per soddisfare le tue esigenze. Può essere il tasso di apertura, il tasso di click-through, il tasso di abbonamento, la reattività, ecc.

Inoltre, il test descritto in questo caso d’uso si riferiva solo a due consegne, ma puoi testare tutte le versioni necessarie. È sufficiente aggiungere attività al flusso di lavoro.

I passaggi principali per eseguire questo caso d’uso sono:

* [Passaggio 1: creare un flusso di lavoro di targeting](a-b-testing-uc-targeting-workflow.md)
* [Passaggio 2: configurare i campioni di popolazione](a-b-testing-uc-population-samples.md)
* [Passaggio 3: creare due modelli di consegna](a-b-testing-uc-delivery-templates.md)
* [Passaggio 4: configurare le consegne nel flusso di lavoro](a-b-testing-uc-configuring-deliveries.md)
* [Passaggio 5: creare lo script](a-b-testing-uc-script.md)
* [Passaggio 6: definire la consegna finale](a-b-testing-uc-final-delivery.md)
* [Passaggio 7: avviare il flusso di lavoro](a-b-testing-uc-start-workflow.md)
* [Passaggio 8: analizzare il risultato](a-b-testing-uc-analyzing.md)

**Argomenti correlati:**

* [Introduzione ai test A/B](get-started-a-b-testing.md)
* [Configurare il test A/B](configuring-a-b-testing.md)
