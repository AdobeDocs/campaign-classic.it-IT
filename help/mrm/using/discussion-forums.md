---
product: campaign
title: Forum di discussione
description: Scopri come utilizzare i forum di discussione di Campaign
audience: campaign
content-type: reference
topic-tags: tasks--resources-and-budgets
exl-id: 222853c5-c754-4c0b-8ee4-a64b2f8677a4
source-git-commit: 98380c18b915cfebc980e68f9840f9d8919eaca4
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 0%

---

# Forum di discussione{#discussion-forums}

![](../../assets/v7-only.svg)

Gli operatori di Adobe Campaign possono utilizzare forum di discussione per condividere informazioni. I seguenti elementi hanno un proprio forum: piani, programmi, campagne, risorse, simulazioni, stock. Ogni operatore ha anche un forum personale. Tutte le discussioni sono pubbliche, anche su forum personali.

Gli operatori possono iscriversi a un forum per ricevere un’e-mail di notifica ogni volta che viene pubblicato un messaggio.

## Accedere a un forum {#accessing-a-forum}

Per visitare il forum di una campagna, un operatore, ecc., accedi al relativo dashboard e fai clic sul **[!UICONTROL Forum]** nell&#39;angolo in alto a destra. Questo collegamento fornisce anche il numero totale di messaggi presenti nel forum.

![](assets/mrm_forum_access_link.png)

## Utilizzare un forum {#using-a-forum}

I messaggi e le relative risposte sono visualizzati in ordine cronologico (dal più recente al più vecchio).

Per visualizzare il contenuto di un messaggio, fai clic sulla relativa intestazione.

![](assets/mrm_forum_expand_msg.png)

**Avvia una nuova discussione**

Per avviare una nuova discussione, fai clic sul pulsante **[!UICONTROL Add a discussion]** nell&#39;angolo in alto a destra. La **[!UICONTROL Discussion forum]** viene visualizzata (vedi sotto).

![](assets/mrm_forum_new_thread.png)

**Invia un messaggio a una discussione esistente**

Per pubblicare un messaggio in una discussione esistente, apri il messaggio a cui desideri rispondere, quindi fai clic sul pulsante **[!UICONTROL Reply]** nell&#39;angolo in alto a sinistra. La **[!UICONTROL Discussion forum]** viene visualizzata (vedi sotto).

![](assets/mrm_forum_answer_msg.png)

Quando rispondi a un messaggio, la persona che ha pubblicato il messaggio originale riceverà una notifica.

**Scrivere un messaggio**

In **[!UICONTROL Discussion forum]** casella:

1. Inserisci il testo nel **[!UICONTROL Message]** e un titolo di discussione nel **[!UICONTROL Subject]** campo .

   ![](assets/mrm_forum_edit_msg.png)

1. Se necessario:

   * Se desideri che qualcuno prenda parte alla discussione che non è iscritto al forum, utilizza il **[!UICONTROL Operator to notify]** campo . L’operatore riceverà un messaggio e-mail di notifica per questo messaggio specifico (non saranno abbonati al forum). Per avvisare diversi operatori, selezionare un gruppo di operatori.
   * Per aggiungere un allegato al messaggio, fai clic su **[!UICONTROL Browse]**. L’allegato verrà incluso anche nell’e-mail di notifica. Gli allegati possono essere inviati solo singolarmente: per inviare diversi file, è necessario comprimerli.

1. Fai clic su **[!UICONTROL Create the message]** per pubblicarlo sul forum.

>[!NOTE]
>
>Una volta pubblicato il messaggio nel forum, non è più possibile modificarlo o eliminarlo.

## Invia al forum personale di un operatore {#posting-to-the-personal-forum-of-an-operator}

Puoi inviare un messaggio al forum di un operatore se, ad esempio, il messaggio non riguarda una campagna specifica ma desideri comunque tenere traccia della conversazione in Adobe Campaign. I forum personali sono pubblici e tutti gli operatori vedranno il tuo messaggio. L’operatore riceve un messaggio ogni volta che qualcuno invia un messaggio al proprio forum personale.

Per accedere al forum di un operatore:

* Se disponi dei diritti necessari per accedere al **[!UICONTROL Administration > Access management > Operators]** nodo dell&#39;esploratore, apri il dashboard dell&#39;operatore desiderato e fai clic sul **[!UICONTROL Forum]** nell&#39;angolo in alto a destra.
* In caso contrario, trova il nome dell’operatore in Adobe Campaign (tramite un messaggio inviato al forum da questo operatore, un’attività che viene loro assegnata) e fai clic su di esso per accedere al loro dashboard. Puoi anche chiedere all’amministratore di creare una visualizzazione della cartella dell’operatore.

## Iscriviti a un forum {#subscribing-to-a-forum}

La sottoscrizione a un forum consente di seguire le discussioni. Riceverai una notifica e-mail ogni volta che un messaggio viene inviato al forum. Questo messaggio e-mail conterrà il corpo del messaggio ed eventuali allegati. Per rispondere a un messaggio, fai clic su nel corpo dell’e-mail, quindi accedi all’interfaccia web di Adobe Campaign. Con l’abbonamento a un forum, queste informazioni sono visibili a tutti.

* Per iscriverti a un forum, fai clic sul pulsante **[!UICONTROL Follow discussions]** nella sezione in alto a destra sopra l’elenco dei messaggi.

   ![](assets/mrm_forum_subscribe.png)

   La sezione diventa blu e mostra che sei iscritto al forum.

* Per annullare l’iscrizione a un forum, fai clic sul pulsante **[!UICONTROL Unsubscribe]** pulsante .

   ![](assets/mrm_forum_unsubscribe.png)

* Il dashboard personale elenca i forum a cui ti sei iscritto. Fai clic sul pulsante **[!UICONTROL Subscription to discussion forums]** per visualizzare l’elenco, quindi fare clic sull’elemento che interessa l’accesso al relativo forum.

   ![](assets/platform_dashboard_operator_subscr_forums.png)

   Per ulteriori informazioni sulle dashboard personali, consulta [questa sezione](../../platform/using/access-management-operators.md).

* Per vedere chi è iscritto a un forum, fai clic sul pulsante **[!UICONTROL List of subscribers to this discussion forum]** link sopra l&#39;elenco dei messaggi.

   ![](assets/mrm_forum_subscribers.png)

## Verifica consegna notifiche {#checking-notification-delivery}

Se gli operatori abbonati a un forum non ricevono le notifiche come previsto:

* Verifica che gli indirizzi e-mail siano inseriti nei profili dell’operatore.
* Vai a **[!UICONTROL Administration > Production > Technical workflows > Campaign processes]** e controlla che **[!UICONTROL Jobs in discussion forums]** il flusso di lavoro viene avviato senza errori.
* Visualizza i registri di consegna:

   * Nella home page di Adobe Campaign, vai a **[!UICONTROL Campaigns > Navigation > Deliveries]**, quindi apri la **[!UICONTROL Discussion forum notification]** consegna.
   * Nell&#39;esploratore, vai a **[!UICONTROL Administration > Production > Objects created automatically > Technical deliveries > Workflow notifications]**, quindi fai clic su **[!UICONTROL Discussion forum notifications]**.
   In **[!UICONTROL Discussion forum notifications]** i registri di consegna si trovano nella **[!UICONTROL Edit > Delivery]** scheda . È inoltre possibile visualizzare le **[!UICONTROL Tracking > Log]** e **[!UICONTROL Exclusion causes]** schede.
