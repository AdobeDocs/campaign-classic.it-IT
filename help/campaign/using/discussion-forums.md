---
solution: Campaign Classic
product: campaign
title: Forum di discussione
description: Forum di discussione
audience: campaign
content-type: reference
topic-tags: tasks--resources-and-budgets
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '723'
ht-degree: 0%

---


# Forum di discussione{#discussion-forums}

 gli operatori Adobe Campaign possono utilizzare i forum di discussione per condividere le informazioni. I seguenti elementi hanno un proprio forum: piani, programmi, campagne, risorse, simulazioni, scorte. Ogni operatore ha anche un forum personale. Tutte le discussioni sono pubbliche, anche su forum personali.

Gli operatori possono iscriversi a un forum per ricevere un’e-mail di notifica ogni volta che viene pubblicato un messaggio.

## Accesso a un forum {#accessing-a-forum}

Per visitare il forum di una campagna, un operatore ecc., andate al relativo dashboard e fate clic sul collegamento **[!UICONTROL Forum]** nell&#39;angolo in alto a destra. Questo collegamento fornisce anche il numero totale di messaggi nel forum.

![](assets/mrm_forum_access_link.png)

## Utilizzo di un forum {#using-a-forum}

I messaggi e le relative risposte sono visualizzati in ordine cronologico (dal più recente al più vecchio).

Per visualizzare il contenuto di un messaggio, fai clic sulla relativa intestazione.

![](assets/mrm_forum_expand_msg.png)

**Avviare una nuova discussione**

Per iniziare una nuova discussione, fate clic sul pulsante **[!UICONTROL Add a discussion]** nell&#39;angolo in alto a destra. Viene visualizzata la casella **[!UICONTROL Discussion forum]** (vedere di seguito).

![](assets/mrm_forum_new_thread.png)

**Pubblicare un messaggio su una discussione esistente**

Per inviare un messaggio a una discussione esistente, aprite il messaggio a cui desiderate rispondere, quindi fate clic sul collegamento **[!UICONTROL Reply]** nell&#39;angolo in alto a sinistra. Viene visualizzata la casella **[!UICONTROL Discussion forum]** (vedere di seguito).

![](assets/mrm_forum_answer_msg.png)

Quando rispondi a un messaggio, la persona che ha pubblicato il messaggio originale riceverà una notifica.

**Scrittura di un messaggio**

Nella casella **[!UICONTROL Discussion forum]**:

1. Immettete il testo nel campo **[!UICONTROL Message]** e un titolo di discussione nel campo **[!UICONTROL Subject]**.

   ![](assets/mrm_forum_edit_msg.png)

1. Se necessario:

   * Se desiderate che qualcuno prenda parte alla discussione che non è iscritto al forum, utilizzate il campo **[!UICONTROL Operator to notify]**. L’operatore riceve un messaggio e-mail di notifica relativo a questo messaggio specifico (non verrà sottoscritto al forum). Per inviare una notifica a più operatori, selezionare un gruppo di operatori.
   * Per aggiungere un allegato al messaggio, fare clic su **[!UICONTROL Browse]**. L&#39;allegato verrà incluso anche nel messaggio e-mail di notifica. Gli allegati possono essere inviati solo singolarmente: per inviare diversi file, è necessario comprimerli.

1. Fate clic su **[!UICONTROL Create the message]** per inviarlo al forum.

>[!NOTE]
>
>Una volta pubblicato nel forum, il messaggio non può più essere modificato o eliminato.

## Inserimento nel forum personale di un operatore {#posting-to-the-personal-forum-of-an-operator}

È possibile inviare un messaggio al forum di un operatore se, ad esempio, il messaggio non riguarda una campagna specifica ma si desidera comunque tenere traccia della conversazione in  Adobe Campaign. I forum personali sono pubblici e tutti gli operatori visualizzeranno il messaggio. L&#39;operatore riceve un messaggio ogni volta che un utente inserisce nel proprio forum personale.

Per accedere al forum di un operatore:

* Se disponete dei diritti necessari per accedere al nodo **[!UICONTROL Administration > Access management > Operators]** dell&#39;esploratore, aprite il dashboard dell&#39;operatore desiderato e fate clic sul collegamento **[!UICONTROL Forum]** nell&#39;angolo superiore destro.
* In caso contrario, trovate il nome dell&#39;operatore in  Adobe Campaign (tramite un messaggio inviato al forum da questo operatore, un&#39;attività a lui assegnata) e fate clic su di esso per accedere al dashboard. Potete anche chiedere all’amministratore di creare una visualizzazione della cartella dell’operatore.

## Iscrizione a un forum {#subscribing-to-a-forum}

La sottoscrizione a un forum consente di seguire le discussioni. Riceverete una notifica e-mail ogni volta che un messaggio viene inviato al forum. Il messaggio e-mail conterrà il corpo del messaggio e gli eventuali allegati. Per rispondere a un messaggio, fai clic sul corpo del messaggio e-mail, quindi accedi all&#39;interfaccia Web  Adobe Campaign. Con l’iscrizione a un forum, queste informazioni sono visibili a tutti.

* Per iscriversi a un forum, fate clic sul pulsante **[!UICONTROL Follow discussions]** nella sezione in alto a destra sopra l&#39;elenco dei messaggi.

   ![](assets/mrm_forum_subscribe.png)

   La sezione diventa blu e indica che siete iscritti al forum.

* Per annullare l&#39;iscrizione a un forum, fate clic sul pulsante **[!UICONTROL Unsubscribe]**.

   ![](assets/mrm_forum_unsubscribe.png)

* Il dashboard personale elenca i forum a cui siete iscritti. Fate clic sul collegamento **[!UICONTROL Subscription to discussion forums]** per visualizzare l&#39;elenco, quindi fate clic sull&#39;elemento che vi interessa per accedere al relativo forum.

   ![](assets/platform_dashboard_operator_subscr_forums.png)

   Per ulteriori informazioni sulle dashboard personali, fare riferimento alla sezione [this](../../platform/using/access-management.md#operators).

* Per vedere chi è iscritto a un forum, fai clic sul collegamento **[!UICONTROL List of subscribers to this discussion forum]** sopra l&#39;elenco dei messaggi.

   ![](assets/mrm_forum_subscribers.png)

## Controllo della consegna delle notifiche {#checking-notification-delivery}

Se gli operatori sottoscritti a un forum non ricevono le notifiche come previsto:

* Verificate che gli indirizzi e-mail siano inseriti nei profili dell&#39;operatore.
* Andate al nodo **[!UICONTROL Administration > Production > Technical workflows > Campaign processes]** e verificate che il flusso di lavoro **[!UICONTROL Jobs in discussion forums]** sia avviato e privo di errori.
* Visualizza i registri di consegna:

   * Nella home page di  Adobe Campaign, passare a **[!UICONTROL Campaigns > Navigation > Deliveries]**, quindi aprire la **[!UICONTROL Discussion forum notification]** consegna.
   * Nell&#39;elenco di cartelle, passare a **[!UICONTROL Administration > Production > Objects created automatically > Technical deliveries > Workflow notifications]**, quindi fare clic su **[!UICONTROL Discussion forum notifications]**.

   Nella casella **[!UICONTROL Discussion forum notifications]**, i registri di consegna si trovano nella scheda **[!UICONTROL Edit > Delivery]**. È inoltre possibile visualizzare le schede **[!UICONTROL Tracking > Log]** e **[!UICONTROL Exclusion causes]**.

