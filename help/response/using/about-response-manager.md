---
product: campaign
title: Informazioni sulla gestione della risposta
description: Informazioni sulla gestione della risposta
feature: Campaigns
badge-v7: label="v7" type="Informative" tooltip="Applicabile a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
exl-id: b5c0e960-2afe-4a98-b82c-d47a74659703
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 4%

---

# Guida introduttiva a Campaign Response Manager{#about-response-manager}



Adobe Campaign offre il componente aggiuntivo Gestione della risposta che consente di misurare il successo e la redditività delle campagne di marketing o delle proposte di offerte tra canali di comunicazione: e-mail, dispositivi mobili, direct mailing, ecc.

## Ipotesi {#hypothesis-concept}

Le ipotesi possono essere configurate in un dato periodo dalla data di contatto per dedurre il comportamento di coloro che sono stati oggetto di targeting dopo aver ricevuto una consegna. Queste ipotesi si basano su un **transazione** tabella che consente di salvare gli acquisti e i relativi dettagli.

Le ipotesi sono limitate nel tempo e possono essere applicate a un gruppo di controllo da confrontare con la popolazione target. I risultati delle ipotesi sono forniti da **indicatori** che vengono aggiornati automaticamente al termine del calcolo. Il ritorno sull’investimento collegato alle ipotesi sarà preso in considerazione nei rapporti della campagna.

Inoltre, il **rapporti** fornito con Response Manager consente di riepilogare le informazioni relative all’aumento del fatturato, al calcolo dei margini e al ROI della consegna o dell’offerta.

Inoltre, grazie alle righe di dettaglio dell’acquisto, puoi specificare le tue ipotesi per concentrarti, ad esempio, su un solo prodotto particolare.

Ad esempio, dopo una consegna che promuove un elemento, vogliamo valutare i ricavi generati. Applichiamo l’ipotesi che qualsiasi destinatario che abbia acquistato almeno un articolo nel mese successivo all’attivazione della consegna abbia reagito a questa azione. La gestione della risposta determinerà, in base a questa ipotesi, quali righe della richiesta di acquisto devono essere assegnate ad essa. Quindi, sulla base di questo, sarà possibile determinare i ricavi risultanti come la somma di queste righe.

>[!CAUTION]
>
>Gestione della risposta è un **[!UICONTROL Campaign]** opzione. Controlla il contratto di licenza.

Puoi anche calcolare tutte le reazioni per l’intera famiglia del destinatario che ha ricevuto la consegna o l’offerta.

Ogni ipotesi è collegata a una singola tabella di transazioni. Una consegna o un’offerta può essere collegata a più ipotesi.

## Passaggi di implementazione {#method}

Prima di iniziare a utilizzare Response Manager, consulta [Configurazione](configuration.md) ed effettuare le configurazioni necessarie.

Per avviare un’ipotesi su una consegna o un’offerta, è necessario definirne il contesto in un modello che verrà utilizzato per ogni ipotesi creata.

Per definire e creare ipotesi di misurazione, attenersi al seguente processo:

1. Definisci un modello di ipotesi. [Ulteriori informazioni](hypothesis-templates.md#creating-a-hypothesis-model)
1. Crea una o più ipotesi su una consegna esistente. [Ulteriori informazioni](creating-hypotheses.md#referencing-a-hypothesis-in-a-campaign-delivery)

   o

   Crea una o più ipotesi sulle offerte. [Ulteriori informazioni](creating-hypotheses.md#creating-a-hypothesis-on-an-offer)

1. Verifica i risultati dell’ipotesi. [Ulteriori informazioni](hypothesis-tracking.md)
1. Se necessario, riavvia le ipotesi. [Ulteriori informazioni](creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery)
