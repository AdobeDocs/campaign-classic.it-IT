---
title: E-mail in entrata
description: Ulteriori informazioni sull'attività del flusso di lavoro Posta elettronica in ingresso
page-status-flag: never-activated
uuid: 6bcc7952-f051-4e50-8833-95d49c7ed781
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: event-activities
discoiquuid: 4c0530b1-0292-45bc-8730-668bc5b8550b
translation-type: tm+mt
source-git-commit: 6be6c353c3464839a74ba857d8d93d0f68bc8865
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 1%

---


# E-mail in entrata{#inbound-emails}

L&#39;attività **Inbound email** consente di scaricare ed elaborare i messaggi e-mail da un server di posta POP3.

![](assets/email_rec_edit_1.png)

La prima scheda dell&#39;attività **Inbound Emails** consente di inserire i parametri del server POP3 e di inserire lo script da eseguire dopo la ricezione di ogni messaggio. La seconda scheda consente di assegnare una pianificazione all&#39;attività, mentre la terza scheda definisce le condizioni di scadenza dell&#39;attività.

1. **[!UICONTROL Inbound Emails]**

   * **[!UICONTROL Use an external account]**

      Quando questa opzione è attivata, è possibile selezionare un account POP3 esterno invece di immettere i parametri di connessione. Il **[!UICONTROL External account]** campo specifica l&#39;account POP3 esterno da utilizzare per connettersi al servizio e-mail. Questo campo è visibile solo se è abilitata l&#39;opzione &quot;Usa un account esterno&quot;.

      Se questa opzione non è selezionata, è necessario specificare i seguenti parametri:

      ![](assets/email_rec_edit_1b.png)

      * **[!UICONTROL POP3 server]**

         Nome del server POP3.

      * **[!UICONTROL POP3 account]**

         Nome dell’utente.

      * **[!UICONTROL Password]**

         Password dell&#39;account utente.

      * **[!UICONTROL Port]**

         Numero porta di connessione POP3. La porta predefinita è 110.
   * **[!UICONTROL Stop as soon as email is processed]**

      Questa opzione consente di elaborare i messaggi e-mail uno per uno. L&#39;attività attiva la transizione una sola volta e termina l&#39;elaborazione, lasciando sul server i messaggi non elaborati.


1. **[!UICONTROL Script]**

   Lo script consente di elaborare il messaggio ed eseguire varie operazioni che dipendono dal contenuto del messaggio. Lo script viene eseguito per ciascun messaggio e può determinare l&#39;operazione da eseguire sui messaggi (lasciare o eliminare il messaggio) e l&#39;attivazione della transizione in uscita.

   Il codice restituito deve essere uno dei seguenti valori:

   * 1 - Elimina il messaggio dal server e attiva la transizione in uscita.
   * 2 - Lascia il messaggio sul server e attiva la transizione in uscita.
   * 3 - Elimina il messaggio dal server.
   * 4 - Lascia il messaggio sul server.

   Il contenuto del messaggio è accessibile dalla **[!UICONTROL mailMessage]** variabile globale.

1. **[!UICONTROL Schedule]**

   Per definire una pianificazione per l&#39;attività, fate clic sulla **[!UICONTROL Scheduling]** scheda e selezionate **[!UICONTROL Plan execution]**. Fate clic sul **[!UICONTROL Change]** pulsante per configurare la pianificazione.

   La configurazione della pianificazione è la stessa dell&#39;attività di pianificazione. Fare riferimento a [Scheduler](../../workflow/using/scheduler.md).

1. **[!UICONTROL Expiration]**

   È possibile definire i ritardi di scadenza tramite la **[!UICONTROL Expiration]** scheda.

   ![](assets/email_rec_edit_3.png)

   La configurazione è la stessa dell&#39;attività di pianificazione. Fare riferimento a [Scadenze](../../workflow/using/defining-approvals.md).

