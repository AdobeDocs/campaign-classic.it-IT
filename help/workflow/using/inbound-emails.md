---
product: campaign
title: E-mail in entrata
description: Ulteriori informazioni sull’attività del flusso di lavoro Inbound Email
feature: Workflows, Channels Activity
exl-id: b2a05e07-a7d7-436b-b2c6-90ab55d031cd
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 1%

---

# E-mail in entrata{#inbound-emails}



L&#39;attività **Inbound emails** ti consente di scaricare ed elaborare messaggi di posta elettronica da un server di posta POP3.

![](assets/email_rec_edit_1.png)

La prima scheda dell&#39;attività **Posta in arrivo** consente di immettere i parametri del server POP3 e di immettere lo script da eseguire al ricevimento di ogni messaggio. La seconda scheda ti consente di assegnare una pianificazione all’attività e la terza scheda definisce le condizioni di scadenza dell’attività.

1. **[!UICONTROL Inbound Emails]**

   * **[!UICONTROL Use an external account]**

     Quando questa opzione è attivata, è possibile selezionare un account POP3 esterno invece di immettere i parametri di connessione. Il campo **[!UICONTROL External account]** specifica l&#39;account POP3 esterno da utilizzare per la connessione al servizio e-mail. Questo campo è visibile solo se è abilitata l’opzione &quot;Usa un account esterno&quot;.

     Se questa opzione non è selezionata, è necessario specificare i seguenti parametri:

     ![](assets/email_rec_edit_1b.png)

      * **[!UICONTROL POP3 server]**

        Nome del server POP3.

      * **[!UICONTROL POP3 account]**

        Nome dell’utente.

      * **[!UICONTROL Password]**

        Password dell’account utente.

      * **[!UICONTROL Port]**

        Numero porta di connessione POP3. La porta predefinita è 110.

   * **[!UICONTROL Stop as soon as email is processed]**

     Questa opzione consente di elaborare le e-mail singolarmente. L’attività attiva la relativa transizione una sola volta e quindi termina l’elaborazione, lasciando sul server i messaggi non elaborati.

1. **[!UICONTROL Script]**

   Lo script consente di elaborare il messaggio ed eseguire varie operazioni che dipendono dal contenuto del messaggio. Lo script viene eseguito per ogni messaggio e può determinare l’operazione da eseguire sui messaggi (lasciare o eliminare il messaggio) e l’attivazione della transizione in uscita.

   Il codice restituito deve essere uno dei seguenti valori:

   * 1 - Elimina il messaggio dal server e attiva la transizione in uscita.
   * 2 - Lascia il messaggio sul server e attiva la transizione in uscita.
   * 3 - Elimina il messaggio dal server.
   * 4 - Lascia il messaggio sul server.

   Il contenuto del messaggio è accessibile dalla variabile globale **[!UICONTROL mailMessage]**.

1. **[!UICONTROL Schedule]**

   Per definire una pianificazione per l&#39;attività, fare clic sulla scheda **[!UICONTROL Scheduling]** e selezionare **[!UICONTROL Plan execution]**. Fare clic sul pulsante **[!UICONTROL Change]** per configurare la pianificazione.

   La configurazione della pianificazione è la stessa dell’attività di pianificazione. Consulta [Scheduler](scheduler.md).

1. **[!UICONTROL Expiration]**

   È possibile definire i ritardi di scadenza tramite la scheda **[!UICONTROL Expiration]**.

   ![](assets/email_rec_edit_3.png)

   La configurazione è la stessa dell’attività di pianificazione. Consulta [Scadenze](defining-approvals.md).
