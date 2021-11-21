---
product: campaign
title: E-mail in entrata
description: Ulteriori informazioni sull’attività del flusso di lavoro Inbound Emails
audience: workflow
content-type: reference
topic-tags: event-activities
exl-id: b2a05e07-a7d7-436b-b2c6-90ab55d031cd
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 1%

---

# E-mail in entrata{#inbound-emails}

![](../../assets/common.svg)

La **E-mail in entrata** activity ti consente di scaricare ed elaborare i messaggi e-mail da un server di posta POP3.

![](assets/email_rec_edit_1.png)

La prima scheda della **E-mail in entrata** activity ti consente di immettere i parametri del server POP3 e lo script da eseguire al ricevimento di ogni messaggio. La seconda scheda ti consente di assegnare una pianificazione all’attività e la terza definisce le condizioni di scadenza dell’attività.

1. **[!UICONTROL Inbound Emails]**

   * **[!UICONTROL Use an external account]**

      Quando questa opzione è attivata, è possibile selezionare un account POP3 esterno invece di immettere i parametri di connessione. La **[!UICONTROL External account]** campo specifica l’account POP3 esterno da utilizzare per connettersi al servizio e-mail. Questo campo è visibile solo se è abilitata l’opzione &quot;Utilizza un account esterno&quot;.

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

   Il contenuto del messaggio è accessibile dal **[!UICONTROL mailMessage]** variabile.

1. **[!UICONTROL Schedule]**

   Per definire una pianificazione per l’attività, fai clic sul pulsante **[!UICONTROL Scheduling]** scheda e controllo **[!UICONTROL Plan execution]**. Fai clic sul pulsante **[!UICONTROL Change]** per configurare la pianificazione.

   La configurazione della pianificazione è la stessa dell’attività di pianificazione. Fai riferimento a [Scheduler](scheduler.md).

1. **[!UICONTROL Expiration]**

   Puoi definire i ritardi di scadenza tramite la **[!UICONTROL Expiration]** scheda .

   ![](assets/email_rec_edit_3.png)

   La configurazione è la stessa dell’attività di pianificazione. Fai riferimento a [Scadenza](defining-approvals.md).
