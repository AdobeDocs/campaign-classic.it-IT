---
product: campaign
title: Marketing virale e social marketing
description: Marketing virale e social marketing
audience: delivery
content-type: reference
topic-tags: subscriptions-and-referrals
exl-id: 10fd561f-1b07-490e-9f66-d67e44a0def5
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 2%

---

# Marketing virale e social marketing{#viral-and-social-marketing}

![](../../assets/common.svg)

## Informazioni sul marketing virale {#about-viral-marketing}

Adobe Campaign ti consente di configurare strumenti per incoraggiare il marketing virale.

Questo consente ai destinatari della consegna o ai visitatori del sito web di condividere informazioni con la loro rete: dall’aggiunta di un collegamento al proprio profilo Facebook o Twitter all’invio di un messaggio a un amico.

![](assets/s_ncs_user_viral_icons.png)

>[!CAUTION]
>
>Affinché i collegamenti aggiunti funzionino correttamente, la pagina speculare corrispondente deve essere disponibile. A questo scopo, includi il collegamento alla pagina speculare nella consegna.

## Reti sociali: condivisione di un collegamento {#social-networks--sharing-a-link}

Per consentire ai destinatari della consegna di condividere il contenuto dei messaggi con i membri della loro rete, devi includere il blocco di personalizzazione corrispondente.

![](assets/s_ncs_user_viral_add_link.png)

>[!NOTE]
>
>Per impostazione predefinita, questo collegamento non è disponibile nell’elenco dei blocchi. Per accedervi, fai clic su **[!UICONTROL Other...]** e selezionando la **[!UICONTROL Social network sharing links]** blocco.

![](assets/s_ncs_user_viral_add_link_via_others.png)

Il rendering sarà il seguente:

![](assets/s_ncs_user_viral_add_link_rendering.png)

Quando il destinatario fa clic sull&#39;icona di uno dei social network visualizzati, viene automaticamente reindirizzato al proprio account e può condividere il contenuto del messaggio tramite un collegamento. Ciò consente ai membri della loro rete di accedere alla comunicazione.

>[!NOTE]
>
>Questo blocco di personalizzazione contiene tutti i collegamenti (per l’invio di messaggi e la condivisione con tutti i social network). Può essere modificato per soddisfare le tue esigenze. Tuttavia, la configurazione è riservata agli utenti avanzati. Per modificare il blocco di personalizzazione corrispondente, vai alla pagina **[!UICONTROL Resources > Campaign management > Personalization blocks]** nodo della struttura Adobe Campaign.

## Marketing virale: inoltrare a un amico {#viral-marketing--forward-to-a-friend}

Un servizio virale consente di eseguire azioni di tipo referral: queste azioni ti consentono di inoltrare un messaggio a un amico. Il profilo dell&#39;arbitro o degli arbitri viene temporaneamente memorizzato nel database (in una tabella dedicata). I messaggi inoltrati includono un collegamento per l’utente da sottoscrivere: in tal caso, verranno aggiunti al database di Adobe Campaign.

L&#39;inoltro dei messaggi si basa sugli stessi principi dei collegamenti dei social network.

Applicare le seguenti fasi:

1. Aggiungi il **[!UICONTROL Social network sharing links]** blocco di personalizzazione nel corpo del messaggio originale.
1. Il destinatario del messaggio può fare clic sul pulsante **[!UICONTROL Email]** per inviare il messaggio a uno o più amici.

   ![](assets/s_ncs_user_viral_email_link.png)

   Un modulo di riferimento consente di inserire gli indirizzi e-mail dei referee.

   ![](assets/s_ncs_user_viral_email_msg.png)

   Il messaggio viene inviato quando il destinatario principale fa clic sul pulsante **[!UICONTROL Next]** pulsante .

   >[!NOTE]
   >
   >Il contenuto di questo messaggio può essere personalizzato in base alle tue esigenze. Viene creato in base al **[!UICONTROL Transfer of original message]** che viene memorizzato nel **[!UICONTROL Administration > Campaign management > Technical delivery templates]** nodo.
   >
   >È anche possibile modificare il modulo di inoltro del messaggio reso disponibile al referente A questo scopo, è necessario modificare il **Forma virale** Applicazione Web memorizzata in **[!UICONTROL Resources > Online > Web applications]** nodo.

1. Nel messaggio inoltrato, un collegamento consente all’arbitro di salvare il suo profilo nel database. A tal fine viene fornito un modulo di iscrizione.

   ![](assets/s_ncs_user_viral_create_account_form.png)

   >[!NOTE]
   >
   >Questa configurazione può essere adattata. A questo scopo, devi modificare il **Iscrizione al destinatario** Applicazione Web memorizzata in **[!UICONTROL Resources > Online > Web applications]** nodo.
   >
   >Per ulteriori informazioni sulle applicazioni Web, fare riferimento a [questa sezione](../../web/using/about-web-applications.md).

   Dopo la convalida, viene loro inviato un messaggio di conferma: saranno registrati per sempre solo dopo aver attivato il collegamento nel messaggio di conferma. Questo messaggio viene creato in base al **[!UICONTROL Registration confirmation]** che viene memorizzato nel **[!UICONTROL Administration > Campaign management > Technical delivery templates]** nodo.

   L’arbitro viene aggiunto al **Destinatari** della cartella del database ed è sottoscritto (per impostazione predefinita) al **Newsletter** servizio informazioni.

## Tracciamento della condivisione social network {#tracking-social-network-sharing}

La condivisione e l&#39;accesso alle informazioni condivise vengono tracciati. Queste informazioni raccolte da Adobe Campaign sono accessibili in due posizioni:

* in **[!UICONTROL Tracking]** scheda della consegna (o singolarmente per ciascun destinatario):

   ![](assets/s_ncs_user_network_del_tracking_tab.png)

* in una **[!UICONTROL Sharing to social networks]** rapporto:

   ![](assets/s_ncs_user_viral_report.png)
