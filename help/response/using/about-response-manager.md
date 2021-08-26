---
product: campaign
title: Informazioni sulla gestione della risposta
description: Informazioni sulla gestione della risposta
audience: campaign
content-type: reference
topic-tags: response-manager
exl-id: b5c0e960-2afe-4a98-b82c-d47a74659703
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 5%

---

# Guida introduttiva a Campaign Response Manager{#about-response-manager}

![](../../assets/v7-only.svg)

Adobe Campaign offre un componente aggiuntivo Gestione della risposta che consente di misurare il successo e la redditività delle campagne di marketing o delle proposte di offerte tra canali di comunicazione: e-mail, dispositivi mobili, direct mailing, ecc.

## Ipotesi {#hypothesis-concept}

Le ipotesi possono essere configurate in un determinato periodo a partire dalla data di contatto per determinare il comportamento dei target dopo la ricezione di una consegna. Queste ipotesi si basano su una tabella **transaction** che salva gli acquisti e i dettagli di tali acquisti.

Le ipotesi sono limitate nel tempo e possono essere applicate a un gruppo di controllo da confrontare con la popolazione target. I risultati delle ipotesi sono forniti da **indicatori** che vengono aggiornati automaticamente una volta completato il calcolo. Nei rapporti sulle campagne si terrà conto del ROI connesso alle ipotesi.

Inoltre, i **report** forniti con Response Manager consentono di riepilogare le informazioni collegate all&#39;aumento del fatturato, al calcolo del margine, nonché al ROI della consegna o dell&#39;offerta.

Inoltre, grazie alle linee di dettaglio per l&#39;acquisto, è possibile specificare le ipotesi per concentrarsi su un solo prodotto particolare, ad esempio.

Ad esempio, dopo una consegna che promuove un articolo, desideriamo valutare i ricavi generati. Si applica l’ipotesi che qualsiasi destinatario che abbia acquistato almeno un articolo nel mese successivo all’attivazione della consegna abbia reagito a questa azione. La gestione della risposta determinerà, in base a questa ipotesi, quali linee di richiesta di acquisto devono essere assegnate ad essa. Quindi, sulla base di questo, sarà possibile determinare i ricavi risultanti come la somma di queste linee.

>[!CAUTION]
>
>Response Manager è un&#39;opzione **[!UICONTROL Campaign]**. Controlla il contratto di licenza.

Puoi anche calcolare tutte le reazioni per l’intera famiglia del destinatario che ha ricevuto la consegna o l’offerta.

Ciascuna ipotesi è collegata a una singola tabella delle transazioni. Una consegna o un’offerta può essere collegata a più ipotesi.

## Passaggi di implementazione {#method}

Prima di iniziare a utilizzare Gestione risposte, fai riferimento a [Configurazione](configuration.md) ed esegui le configurazioni necessarie.

Per lanciare un&#39;ipotesi su una consegna o un&#39;offerta, è necessario definirne il contesto in un modello che verrà utilizzato per ogni ipotesi creata.

Per definire e creare ipotesi di misurazione, eseguire il seguente processo:

1. Definire un modello di ipotesi. [Ulteriori informazioni](hypothesis-templates.md#creating-a-hypothesis-model)
1. Crea una o più ipotesi su una consegna esistente. [Ulteriori informazioni](creating-hypotheses.md#referencing-a-hypothesis-in-a-campaign-delivery)

   o

   Crea una o più ipotesi sulle offerte. [Ulteriori informazioni](creating-hypotheses.md#creating-a-hypothesis-on-an-offer)

1. Controlla i risultati delle ipotesi. [Ulteriori informazioni](hypothesis-tracking.md)
1. Se necessario, riavvia le ipotesi. [Ulteriori informazioni](creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery)
