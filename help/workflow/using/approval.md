---
solution: Campaign Classic
product: campaign
title: Approvazione
description: Approvazione
audience: workflow
content-type: reference
topic-tags: flow-control-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 0%

---


# Approvazione{#approval}

Un&#39;attività di **approvazione** richiede la partecipazione di un operatore. All&#39;operatore viene assegnata un&#39;attività e può rispondere via e-mail, utilizzando la pagina Web collegata al messaggio e-mail o tramite la console.

## Assegnazione task {#task-assignment}

Per impostazione predefinita, l’approvazione è assegnata a un gruppo di operatori. Questo gruppo rappresenta un ruolo, ad esempio &#39;Gruppo di contenuto newsletter&#39; o &#39;Gruppo di destinazione newsletter&#39;. Ciascun operatore del gruppo può rispondere, ma si prende in considerazione solo la prima risposta (tranne nel caso di più approvazioni).

Se necessario, potete assegnare l&#39;attività di approvazione a un singolo operatore o a un insieme di operatori definiti da un filtro.

* Per selezionare un singolo operatore, selezionare il **[!UICONTROL Operator]** valore nel **[!UICONTROL Assignment type]** campo e selezionare l&#39;operatore appropriato nell&#39;elenco a discesa del **[!UICONTROL Assignee]** campo.

   ![](assets/s_advuser_validation_box_assign.png)

   >[!CAUTION]
   >
   >Solo l&#39;operatore scelto sarà autorizzato ad approvare l&#39;attività.

* È possibile definire una query per filtrare gli operatori autorizzati. A questo scopo, selezionate il **[!UICONTROL Filter]** valore nel **[!UICONTROL Assignment type]** campo e fate clic sul **[!UICONTROL Advanced parameters...]** collegamento per definire le condizioni di filtro, come illustrato nell&#39;esempio seguente:

   ![](assets/s_advuser_validation_box_filter.png)

In caso di singola approvazione, la transizione corrispondente alla scelta dell&#39;operatore viene attivata e l&#39;attività è terminata: gli altri operatori non possono rispondere.

In caso di approvazioni multiple, sono attivate le transizioni corrispondenti alla scelta di ciascun operatore. L&#39;attività è terminata quando tutti gli operatori del gruppo hanno risposto o quando l&#39;attività è scaduta.

Questa attività non blocca l&#39;elaborazione e il flusso di lavoro può eseguire altre attività in attesa di una risposta.

Un operatore può approvare le attività assegnate a tale operatore dalla console. Un operatore con diritti di amministratore può visualizzare ed eliminare le attività assegnate a qualsiasi operatore, ma non può rispondervi.

La modifica del titolo o del corpo del messaggio dell&#39;attività non influisce sulle attività correnti, ma, d&#39;altra parte, la modifica delle possibili scelte influisce direttamente sulle attività correnti, che ereditano automaticamente il nuovo elenco di scelte.

**Le attività relative al tipo di approvazione** sono accessibili dal **[!UICONTROL Administration > Production > Objects created automatically > Approvals pending]** nodo: gli operatori possono accedere al modulo di approvazione direttamente tramite questa visualizzazione.

![](assets/s_advuser_validation_from_console.png)

## Properties {#properties}

Le variabili di personalizzazione possono essere utilizzate nel messaggio inviato ai revisori. Possono essere inseriti nel titolo o nel corpo del messaggio.

![](assets/edit_validation.png)

Questo **[!UICONTROL Title]** campo contiene il titolo del messaggio: Oggetto del messaggio e-mail inviato. Il titolo e il corpo del messaggio sono modelli JavaScript e possono quindi contenere valori calcolati in base al contesto del flusso di lavoro.

La sezione inferiore dell’editor consente di definire l’elenco delle possibili risposte. Esiste una transizione corrispondente a ciascuna risposta. Il nome è l’identificatore interno e l’etichetta è il testo che verrà visualizzato nell’elenco delle scelte.

Fate clic sul **[!UICONTROL Advanced parameters...]** collegamento per selezionare il modello di consegna da utilizzare per inviare le notifiche agli operatori. Il modello predefinito (nome interno &#39;notificationAssignee&#39;) prende il titolo e il messaggio e aggiunge un collegamento alla pagina Web utilizzata per rispondere.

Questo modello può essere modificato per personalizzare il layout del messaggio, ma è preferibile eseguire una copia. Il meccanismo di targeting (file esterno, mappatura destinazione) non deve essere modificato perché è necessario per il corretto funzionamento delle notifiche.

Un esempio di approvazione viene visualizzato in [Definizione delle approvazioni](../../workflow/using/defining-approvals.md).

## Parametri di output {#output-parameters}

* **[!UICONTROL response]**

   Commento relativo alla risposta

* **[!UICONTROL responseOperator]**

   Identificatore dell&#39;operatore che ha risposto. Questo campo è un valore numerico, ma un **[!UICONTROL String]** campo.

