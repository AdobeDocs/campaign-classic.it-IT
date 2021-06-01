---
product: campaign
title: E-mail in entrata
description: Ulteriori informazioni sull’attività del flusso di lavoro Inbound Emails
audience: workflow
content-type: reference
topic-tags: event-activities
exl-id: b2a05e07-a7d7-436b-b2c6-90ab55d031cd
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 1%

---

# E-mail in entrata{#inbound-emails}

L’attività **Inbound emails** consente di scaricare ed elaborare messaggi e-mail da un server di posta POP3.

![](assets/email_rec_edit_1.png)

La prima scheda dell’attività **Inbound Emails** ti consente di immettere i parametri del server POP3 e inserire lo script da eseguire al ricevimento di ciascun messaggio. La seconda scheda ti consente di assegnare una pianificazione all’attività e la terza definisce le condizioni di scadenza dell’attività.

1. **[!UICONTROL Inbound Emails]**

   * **[!UICONTROL Use an external account]**

      Quando questa opzione è attivata, è possibile selezionare un account POP3 esterno invece di immettere i parametri di connessione. Il campo **[!UICONTROL External account]** specifica l’account POP3 esterno da utilizzare per connettersi al servizio e-mail. Questo campo è visibile solo se è abilitata l’opzione &quot;Utilizza un account esterno&quot;.

      Se questa opzione non è selezionata, è necessario specificare i seguenti parametri:

      ![](assets/email_rec_edit_1b.png)

      * **[!UICONTROL POP3 server]**

         Nome del server POP3.

      * **[!UICONTROL POP3 account]**

         Nome dell&#39;utente.

      * **[!UICONTROL Password]**

         Password dell&#39;account utente.

      * **[!UICONTROL Port]**

         Numero della porta di connessione POP3. La porta predefinita è 110.
   * **[!UICONTROL Stop as soon as email is processed]**

      Questa opzione ti consente di elaborare le e-mail una per una. L’attività attiva la relativa transizione una sola volta e quindi termina l’elaborazione, lasciando messaggi non elaborati sul server.


1. **[!UICONTROL Script]**

   Lo script consente di elaborare il messaggio ed eseguire varie operazioni in base al contenuto del messaggio. Lo script viene eseguito per ciascun messaggio e può determinare l’operazione da eseguire sui messaggi (lasciare o eliminare il messaggio) e l’attivazione della transizione in uscita.

   Il codice restituito deve essere uno dei seguenti valori:

   * 1 - Elimina il messaggio dal server e attiva la transizione in uscita.
   * 2 - Lascia il messaggio sul server e attiva la transizione in uscita.
   * 3 - Elimina il messaggio dal server.
   * 4 - Lascia il messaggio sul server.

   Il contenuto del messaggio è accessibile dalla variabile globale **[!UICONTROL mailMessage]** .

1. **[!UICONTROL Schedule]**

   Per definire una pianificazione per l’attività, fai clic sulla scheda **[!UICONTROL Scheduling]** e seleziona **[!UICONTROL Plan execution]**. Fai clic sul pulsante **[!UICONTROL Change]** per configurare la pianificazione.

   La configurazione della pianificazione è la stessa dell’attività di pianificazione. Fare riferimento a [Scheduler](../../workflow/using/scheduler.md).

1. **[!UICONTROL Expiration]**

   Puoi definire i ritardi di scadenza tramite la scheda **[!UICONTROL Expiration]** .

   ![](assets/email_rec_edit_3.png)

   La configurazione è la stessa dell’attività di pianificazione. Fare riferimento a [Scadenza](../../workflow/using/defining-approvals.md).
