---
title: Informazioni su Gestione risposte
seo-title: Informazioni su Gestione risposte
description: Informazioni su Gestione risposte
seo-description: null
page-status-flag: never-activated
uuid: 3087a96d-50fb-488a-9b76-70eb5c67deed
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: response-manager
discoiquuid: a4669fee-4512-455f-b495-ebd5a0746b76
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Informazioni su Gestione risposte{#about-response-manager}

## Obiettivi {#objectives}

Adobe Campaign offre un&#39;applicazione di gestione delle risposte (Response Manager) che consente di misurare il successo e la redditività delle campagne di marketing o delle proposte di offerte per tutti i canali di comunicazione (e-mail, mobile, telefono, posta diretta, fax, agenzia, ecc.).

## Concetto di ipotesi {#hypothesis-concept}

Le ipotesi possono essere configurate in un determinato periodo a partire dalla data del contatto per determinare il comportamento di coloro che hanno come destinazione il destinatario dopo la ricezione della consegna. Queste ipotesi si basano su una tabella delle **transazioni** che consente di risparmiare gli acquisti e i dettagli di tali acquisti.

Le ipotesi sono limitate nel tempo e possono essere applicate a un gruppo di controllo da confrontare con la popolazione bersaglio. I risultati delle ipotesi sono forniti da **indicatori** che vengono aggiornati automaticamente una volta completato il calcolo. Il ROI collegato alle ipotesi sarà preso in considerazione nei rapporti della campagna.

Inoltre, i **rapporti** forniti con Response Manager consentono di riepilogare le informazioni collegate all&#39;aumento del fatturato, al calcolo dei margini, nonché al ROI della consegna o dell&#39;offerta.

Inoltre, grazie alle linee di dettaglio dell&#39;acquisto, potete specificare le ipotesi in modo da concentrarsi su un solo particolare prodotto, ad esempio.

Ad esempio, dopo una consegna che promuove un articolo, desideriamo valutare i ricavi generati. Si applica l&#39;ipotesi che qualsiasi destinatario che abbia acquistato almeno un articolo nel mese successivo all&#39;attivazione della consegna abbia reagito a questa azione. La gestione delle risposte determinerà, in base a questa ipotesi, quali linee di richiesta di acquisto devono essere assegnate. Quindi, in base a questo, sarà possibile determinare le entrate risultanti come somma di queste linee.

>[!CAUTION]
>
>Response Manager è un&#39; **[!UICONTROL Campaign]** opzione. Controllare il contratto di licenza.

Potete anche calcolare tutte le reazioni per l&#39;intera famiglia del destinatario che ha ricevuto la consegna o l&#39;offerta.

Ogni ipotesi è collegata a una singola tabella delle transazioni. Una consegna o offerta può essere collegata a più ipotesi.

## Metodo {#method}

Prima di iniziare a utilizzare Response Manager, fare riferimento a [Configuration](../../campaign/using/configuration.md) ed eseguire le configurazioni necessarie.

Per lanciare un&#39;ipotesi su una consegna o un&#39;offerta, è necessario definirne il contesto in un modello che verrà utilizzato per ogni ipotesi creata.

Per definire e creare ipotesi di misurazione, eseguire il seguente processo:

1. Definire un modello di ipotesi. Fare riferimento a [Creazione di un modello](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model)di ipotesi.
1. Create una o più ipotesi su una consegna esistente. Fare riferimento a [Riferimento a un&#39;ipotesi nella distribuzione](../../campaign/using/creating-hypotheses.md#referencing-a-hypothesis-in-a-campaign-delivery)di una campagna.

   o

   Create una o più ipotesi sulle offerte. Fare riferimento a [Creazione di un&#39;ipotesi su un&#39;offerta](../../campaign/using/creating-hypotheses.md#creating-a-hypothesis-on-an-offer).

1. Controllare i risultati delle ipotesi. Fare riferimento al tracciamento delle [ipotesi](../../campaign/using/hypothesis-tracking.md).
1. Se necessario, riavviate le ipotesi. Fare riferimento a [Creazione di un&#39;ipotesi al volo su una consegna](../../campaign/using/creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery).

