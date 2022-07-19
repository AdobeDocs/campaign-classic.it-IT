---
product: campaign
title: Attività Approval
description: Attività Approval
feature: Workflows, Approvals
exl-id: 7ff5da71-ef82-48a2-a608-06a4ca188bb9
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 0%

---

# Attività Approval{#approval}

![](../../assets/v7-only.svg)

Un **Approvazione** Il compito richiede la partecipazione di un operatore. All’operatore viene assegnata un’attività e può rispondere tramite e-mail, utilizzando la pagina web collegata nel messaggio e-mail o tramite la console.

## Assegnazione attività {#task-assignment}

Per impostazione predefinita, l’approvazione viene assegnata a un gruppo di operatori. Questo gruppo rappresenta un ruolo, ad esempio &quot;Gruppo di contenuti per newsletter&quot; o &quot;Gruppo di destinazione per newsletter&quot;. Ogni operatore del gruppo può rispondere, ma si tiene conto solo della prima risposta (salvo in caso di più approvazioni).

Se necessario, è possibile assegnare l&#39;attività di approvazione a un singolo operatore o a un set di operatori definiti da un filtro.

* Per selezionare un singolo operatore, seleziona la **[!UICONTROL Operator]** nel **[!UICONTROL Assignment type]** e seleziona l’operatore pertinente nell’elenco a discesa del **[!UICONTROL Assignee]** campo .

   ![](assets/s_advuser_validation_box_assign.png)

   >[!CAUTION]
   >
   >Solo l’operatore scelto sarà autorizzato ad approvare l’attività.

* Puoi definire una query per filtrare l’approvazione degli operatori. A questo scopo, seleziona la **[!UICONTROL Filter]** nel **[!UICONTROL Assignment type]** e fai clic sul campo **[!UICONTROL Advanced parameters...]** per definire le condizioni di filtro, come illustrato nell’esempio seguente:

   ![](assets/s_advuser_validation_box_filter.png)

In caso di singola approvazione, la transizione corrispondente alla scelta dell&#39;operatore viene attivata e l&#39;attività è terminata: gli altri operatori non possono rispondere.

In caso di più approvazioni, le transizioni corrispondenti alla scelta di ciascun operatore sono abilitate. L&#39;attività è terminata quando tutti gli operatori del gruppo hanno risposto o quando l&#39;attività è scaduta.

Questa attività non blocca l’elaborazione e il flusso di lavoro può eseguire altre attività in attesa di una risposta.

Un operatore può approvare le attività assegnate a tale operatore dalla console. Un operatore con diritti di amministratore può visualizzare ed eliminare le attività assegnate a qualsiasi operatore, ma non può rispondervi.

La modifica del corpo del titolo o del messaggio dell’attività non influisce sulle attività correnti, ma, d’altra parte, la modifica delle possibili scelte influisce direttamente sulle attività correnti, che ereditano automaticamente il nuovo elenco di scelte.

**Approvazione** le attività di tipo sono accessibili dal **[!UICONTROL Administration > Production > Objects created automatically > Approvals pending]** nodo: gli operatori possono accedere al modulo di approvazione direttamente da questa visualizzazione.

![](assets/s_advuser_validation_from_console.png)

## Properties {#properties}

Le variabili di personalizzazione possono essere utilizzate nel messaggio inviato ai revisori. Possono essere inseriti nel titolo o nel corpo del messaggio.

![](assets/edit_validation.png)

Questo **[!UICONTROL Title]** il campo contiene il titolo del messaggio: Questo è l’oggetto del messaggio e-mail inviato. Il titolo e il corpo del messaggio sono modelli JavaScript e possono quindi contenere valori calcolati in base al contesto del flusso di lavoro.

La sezione inferiore dell’editor ti consente di definire l’elenco delle possibili risposte. Esiste una transizione corrispondente a ogni risposta. Il nome è l’identificatore interno e l’etichetta è il testo che verrà visualizzato nell’elenco delle scelte.

Fai clic sul pulsante **[!UICONTROL Advanced parameters...]** collegamento per selezionare il modello di consegna da utilizzare per la notifica agli operatori. Il modello predefinito (nome interno &quot;notifyAssignee&quot;) prende il titolo e il messaggio e aggiunge un collegamento alla pagina web utilizzata per rispondere.

È possibile modificare questo modello per personalizzare il layout del messaggio, ma è preferibile creare una copia. Il meccanismo di targeting (file esterno, mappatura target) non deve essere modificato perché è necessario per il corretto funzionamento delle notifiche.

Un esempio di approvazione viene mostrato in [Definizione delle approvazioni](defining-approvals.md).

## Parametri di output {#output-parameters}

* **[!UICONTROL response]**

   Commento relativo alla risposta

* **[!UICONTROL responseOperator]**

   Identificatore dell’operatore che ha risposto. Questo campo è un valore numerico, ma è **[!UICONTROL String]** campo .
