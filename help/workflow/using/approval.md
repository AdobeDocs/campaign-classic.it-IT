---
product: campaign
title: Approvazione
description: Approvazione
feature: Workflows, Approvals
hide: true
hidefromtoc: true
exl-id: 7ff5da71-ef82-48a2-a608-06a4ca188bb9
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 0%

---

# Approvazione{#approval}



Un&#39;attività **Approval** richiede la partecipazione di un operatore. All’operatore viene assegnata un’attività e può rispondere tramite e-mail, utilizzando la pagina web collegata nel messaggio e-mail o tramite la console.

## Assegnazione attività {#task-assignment}

Per impostazione predefinita, l’approvazione viene assegnata a un gruppo di operatori. Questo gruppo rappresenta un ruolo, ad esempio &quot;Gruppo di contenuti newsletter&quot; o &quot;Gruppo di targeting newsletter&quot;. Ogni operatore del gruppo può rispondere, ma viene presa in considerazione solo la prima risposta (tranne in caso di più approvazioni).

Se necessario, è possibile assegnare l&#39;attività di approvazione a un singolo operatore o a un insieme di operatori definiti da un filtro.

* Per selezionare un singolo operatore, selezionare il valore **[!UICONTROL Operator]** nel campo **[!UICONTROL Assignment type]** e selezionare l&#39;operatore corrispondente nell&#39;elenco a discesa del campo **[!UICONTROL Assignee]**.

  ![](assets/s_advuser_validation_box_assign.png)

  >[!CAUTION]
  >
  >Solo l&#39;operatore scelto sarà autorizzato ad approvare l&#39;attività.

* Puoi definire una query per filtrare gli operatori di approvazione. A tale scopo, selezionare il valore **[!UICONTROL Filter]** nel campo **[!UICONTROL Assignment type]** e fare clic sul collegamento **[!UICONTROL Advanced parameters...]** per definire le condizioni di filtro, come illustrato nell&#39;esempio seguente:

  ![](assets/s_advuser_validation_box_filter.png)

In caso di approvazione singola, viene attivata la transizione corrispondente alla scelta dell’operatore e l’operazione è terminata: gli altri operatori non possono rispondere.

In caso di più approvazioni, sono abilitate le transizioni corrispondenti alla scelta di ciascun operatore. L&#39;attività viene completata quando tutti gli operatori del gruppo hanno risposto o quando l&#39;attività è scaduta.

Questa attività non blocca l’elaborazione e il flusso di lavoro può eseguire altre attività in attesa di risposta.

Un operatore può approvare i compiti assegnati a tale operatore dalla console. Un operatore con diritti di amministratore può visualizzare ed eliminare le attività assegnate a qualsiasi operatore, ma non può rispondervi.

La modifica del titolo o del corpo del messaggio dell’attività non influisce sulle attività correnti, ma, d’altra parte, la modifica delle scelte possibili influisce direttamente sulle attività correnti, che ereditano automaticamente il nuovo elenco di scelte.

Le attività di tipo **Approvazione** sono accessibili dal nodo **[!UICONTROL Administration > Production > Objects created automatically > Approvals pending]**: gli operatori possono accedere al modulo di approvazione direttamente tramite questa visualizzazione.

![](assets/s_advuser_validation_from_console.png)

## Proprietà {#properties}

Le variabili di personalizzazione possono essere utilizzate nel messaggio inviato ai revisori. Possono essere inseriti nel titolo o nel corpo del messaggio.

![](assets/edit_validation.png)

Questo campo **[!UICONTROL Title]** contiene il titolo del messaggio: Questo è l&#39;oggetto del messaggio e-mail inviato. Il titolo e il corpo del messaggio sono modelli di JavaScript e possono quindi contenere valori calcolati in base al contesto del flusso di lavoro.

La sezione inferiore dell’editor ti consente di definire l’elenco delle risposte possibili. Esiste una transizione corrispondente a ogni risposta. Il nome è l&#39;identificatore interno e l&#39;etichetta è il testo che verrà visualizzato nell&#39;elenco di scelte.

Fai clic sul collegamento **[!UICONTROL Advanced parameters...]** per selezionare il modello di consegna da utilizzare per la notifica agli operatori. Il modello predefinito (nome interno &quot;notificationAssignee&quot;) prende il titolo e il messaggio e aggiunge un collegamento alla pagina web utilizzata per rispondere.

Questo modello può essere modificato per personalizzare il layout del messaggio, ma è preferibile crearne una copia. Il meccanismo di targeting (file esterno, mappatura destinazione) non deve essere modificato perché è necessario per il corretto funzionamento delle notifiche.

Un esempio di approvazione viene visualizzato in [Definizione delle approvazioni](defining-approvals.md).

## Parametri di output {#output-parameters}

* **[!UICONTROL response]**

  Commento relativo alla risposta

* **[!UICONTROL responseOperator]**

  Identificatore dell’operatore che ha risposto. Questo campo è un valore numerico, ma un campo **[!UICONTROL String]**.
