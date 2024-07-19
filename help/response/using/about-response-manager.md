---
product: campaign
title: Informazioni sulla gestione della risposta
description: Informazioni sulla gestione della risposta
feature: Campaigns
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
exl-id: b5c0e960-2afe-4a98-b82c-d47a74659703
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 4%

---

# Guida introduttiva a Campaign Response Manager{#about-response-manager}



Adobe Campaign offre il componente aggiuntivo Gestione della risposta che consente di misurare il successo e la redditività delle campagne di marketing o delle proposte di offerte tra canali di comunicazione: e-mail, dispositivi mobili, direct mailing, ecc.

## Ipotesi {#hypothesis-concept}

Le ipotesi possono essere configurate in un dato periodo dalla data di contatto per dedurre il comportamento di coloro che sono stati oggetto di targeting dopo aver ricevuto una consegna. Queste ipotesi si basano su una tabella **transaction** che salva gli acquisti e i relativi dettagli.

Le ipotesi sono limitate nel tempo e possono essere applicate a un gruppo di controllo da confrontare con la popolazione target. I risultati delle ipotesi vengono forniti da **indicatori** che vengono aggiornati automaticamente al termine del calcolo. Il ritorno sull’investimento collegato alle ipotesi sarà preso in considerazione nei rapporti della campagna.

Inoltre, i **report** forniti con Response Manager consentono di riepilogare le informazioni collegate all&#39;aumento del fatturato, al calcolo del margine e al ROI della consegna o dell&#39;offerta.

Inoltre, grazie alle righe di dettaglio dell’acquisto, puoi specificare le tue ipotesi per concentrarti, ad esempio, su un solo prodotto particolare.

Ad esempio, dopo una consegna che promuove un elemento, vogliamo valutare i ricavi generati. Applichiamo l’ipotesi che qualsiasi destinatario che abbia acquistato almeno un articolo nel mese successivo all’attivazione della consegna abbia reagito a questa azione. La gestione della risposta determinerà, in base a questa ipotesi, quali righe della richiesta di acquisto devono essere assegnate ad essa. Quindi, sulla base di questo, sarà possibile determinare i ricavi risultanti come la somma di queste righe.

>[!CAUTION]
>
>Gestione risposte è un&#39;opzione **[!UICONTROL Campaign]**. Controlla il contratto di licenza.

Puoi anche calcolare tutte le reazioni per l’intera famiglia del destinatario che ha ricevuto la consegna o l’offerta.

Ogni ipotesi è collegata a una singola tabella di transazioni. Una consegna o un’offerta può essere collegata a più ipotesi.

## Passaggi di implementazione {#method}

Prima di iniziare a utilizzare Gestione risposte, fare riferimento a [Configurazione](configuration.md) ed eseguire le configurazioni necessarie.

Per avviare un’ipotesi su una consegna o un’offerta, è necessario definirne il contesto in un modello che verrà utilizzato per ogni ipotesi creata.

Per definire e creare ipotesi di misurazione, attenersi al seguente processo:

1. Definisci un modello di ipotesi. [Ulteriori informazioni](hypothesis-templates.md#creating-a-hypothesis-model)
1. Crea una o più ipotesi su una consegna esistente. [Ulteriori informazioni](creating-hypotheses.md#referencing-a-hypothesis-in-a-campaign-delivery)

   o

   Crea una o più ipotesi sulle offerte. [Ulteriori informazioni](creating-hypotheses.md#creating-a-hypothesis-on-an-offer)

1. Verifica i risultati dell’ipotesi. [Ulteriori informazioni](hypothesis-tracking.md)
1. Se necessario, riavvia le ipotesi. [Ulteriori informazioni](creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery)
