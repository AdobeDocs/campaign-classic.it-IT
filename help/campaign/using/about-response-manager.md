---
solution: Campaign Classic
product: campaign
title: Informazioni sulla gestione della risposta
description: Informazioni sulla gestione della risposta
audience: campaign
content-type: reference
topic-tags: response-manager
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 3%

---


# Informazioni sulla gestione della risposta{#about-response-manager}

## Obiettivi {#objectives}

 Adobe Campaign offre un&#39;applicazione di gestione delle risposte (Response Manager) che consente di misurare il successo e la redditività delle campagne di marketing o delle proposte di offerte per tutti i canali di comunicazione (e-mail, mobile, telefono, posta diretta, fax, agenzia, ecc.).

## Concetto di ipotesi {#hypothesis-concept}

Le ipotesi possono essere configurate in un determinato periodo a partire dalla data del contatto per determinare il comportamento di coloro che hanno come destinazione il destinatario dopo la ricezione della consegna. Queste ipotesi si basano su una tabella **transaction** che consente di risparmiare acquisti e dettagli relativi a tali acquisti.

Le ipotesi sono limitate nel tempo e possono essere applicate a un gruppo di controllo da confrontare con la popolazione bersaglio. I risultati dell&#39;ipotesi sono forniti da **indicatori** che vengono aggiornati automaticamente al termine del calcolo. Il ROI collegato alle ipotesi sarà preso in considerazione nei rapporti della campagna.

Inoltre, i **report** forniti con Response Manager consentono di riepilogare le informazioni collegate all&#39;aumento del fatturato, al calcolo dei margini, nonché al ROI della consegna o dell&#39;offerta.

Inoltre, grazie alle linee dei dettagli di acquisto, è possibile specificare le ipotesi per concentrarsi su un solo prodotto particolare, ad esempio.

Ad esempio, dopo una consegna che promuove un articolo, desideriamo valutare i ricavi generati. Si applica l&#39;ipotesi che qualsiasi destinatario che abbia acquistato almeno un articolo nel mese successivo all&#39;attivazione della consegna abbia reagito a questa azione. La gestione delle risposte determinerà, in base a questa ipotesi, quali linee di richiesta di acquisto devono essere assegnate. Quindi, in base a questo, sarà possibile determinare le entrate risultanti come somma di queste linee.

>[!CAUTION]
>
>Response Manager è un&#39;opzione **[!UICONTROL Campaign]**. Controlla il contratto di licenza.

Potete anche calcolare tutte le reazioni per l&#39;intera famiglia del destinatario che ha ricevuto la consegna o l&#39;offerta.

Ogni ipotesi è collegata a una singola tabella delle transazioni. Una consegna o un&#39;offerta può essere collegata a più ipotesi.

## Metodo {#method}

Prima di iniziare a utilizzare Response Manager, fare riferimento a [Configuration](../../campaign/using/configuration.md) ed eseguire le configurazioni necessarie.

Per lanciare un&#39;ipotesi su una consegna o un&#39;offerta, è necessario definirne il contesto in un modello che verrà utilizzato per ogni ipotesi creata.

Per definire e creare ipotesi di misurazione, eseguire il seguente processo:

1. Definire un modello di ipotesi. Fare riferimento a [Creazione di un modello di ipotesi](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model).
1. Create una o più ipotesi su una consegna esistente. Fare riferimento a [Riferimento a un&#39;ipotesi in una distribuzione di campagne](../../campaign/using/creating-hypotheses.md#referencing-a-hypothesis-in-a-campaign-delivery).

   o

   Create una o più ipotesi sulle offerte. Fare riferimento a [Creazione di un&#39;ipotesi su un&#39;offerta](../../campaign/using/creating-hypotheses.md#creating-a-hypothesis-on-an-offer).

1. Controllare i risultati delle ipotesi. Fare riferimento a [Tracciamento ipotesi](../../campaign/using/hypothesis-tracking.md).
1. Se necessario, riavviate le ipotesi. Fare riferimento a [Creazione di un&#39;ipotesi al volo su una consegna](../../campaign/using/creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery).

