---
title: Sincronizzazione dei profili
seo-title: Sincronizzazione dei profili
description: Sincronizzazione dei profili
seo-description: null
page-status-flag: never-activated
uuid: 3d5f0fd4-dfe7-4b34-a75f-8cf36fb7c91d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: acs-connector
discoiquuid: 91115d4f-0cb6-4bce-b28d-17f15e9f9a0a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 56212b320d5077f9b66952e7c11eb8bdcea9e3b4
workflow-type: tm+mt
source-wordcount: '1203'
ht-degree: 0%

---


# Sincronizzazione dei profili{#synchronizing-profiles}

Il connettore ACS replica i dati da Campaign v7 ad Campaign Standard. I dati ricevuti da Campaign v7 possono essere utilizzati in Campaign Standard per creare consegne. Potete vedere come i profili vengono sincronizzati eseguendo le operazioni elencate di seguito.

* **Aggiungi nuovi destinatari**: Crea un nuovo destinatario in Campaign v7 e conferma che il profilo corrispondente è stato replicato in Campaign Standard. Consultate [Creazione di un nuovo destinatario](#creating-a-new-recipient).
* **Aggiorna destinatari**: Modificate un nuovo destinatario in Campaign v7 e visualizzate il profilo corrispondente in Campaign Standard per confermare che l&#39;aggiornamento è stato replicato. Consulta [Modifica di un destinatario](#editing-a-recipient).
* **Creare un flusso di lavoro in Campaign Standard**: Create un flusso di lavoro in Campaign Standard che includa una query con un&#39;audience o con profili replicati da Campaign v7. Consultate [Creazione di un flusso di lavoro](#creating-a-workflow).
* **Crea una consegna in Campaign Standard**: Segui il flusso di lavoro per completare l’invio. Consultate [Creazione di una consegna](#creating-a-delivery).
* **Verificare il collegamento** di annullamento della sottoscrizione: Utilizzate un&#39;applicazione Web Campaign v7 per essere certi che la scelta del destinatario di annullare l&#39;iscrizione a un servizio venga inviata al database Campaign v7. L&#39;opzione per interrompere la ricezione del servizio viene replicata in Campaign Standard. Consultate [Modifica del collegamento](#changing-the-unsubscription-link)di annullamento dell’iscrizione.

## Prerequisiti {#prerequisites}

Nelle sezioni seguenti viene descritto come ACS Connector consente di aggiungere e modificare i destinatari in Campaign v7 e di utilizzarli in una distribuzione Campaign Standard. Il connettore ACS richiede quanto segue:

* I destinatari in Campaign v7 sono stati replicati in Campaign Standard.
* Diritti degli utenti per l&#39;esecuzione di flussi di lavoro sia in Campaign v7 che in Campaign Standard.
* Diritti degli utenti per creare ed eseguire una consegna in Campaign Standard.

## Modifica del collegamento per l’annullamento della sottoscrizione {#changing-the-unsubscription-link}

Quando un destinatario fa clic sul collegamento di annullamento dell’iscrizione in un messaggio e-mail inviato da Campaign Standard, il profilo corrispondente in Campaign Standard viene aggiornato. Per essere certi che un profilo replicato includa la scelta dell&#39;utente di annullare l&#39;iscrizione a un servizio, le informazioni devono essere inviate a Campaign v7 anziché ad Campaign Standard. Per eseguire la modifica, il servizio di annullamento dell&#39;iscrizione è collegato a un&#39;applicazione Web Campaign v7 anziché ad Campaign Standard.

>[!NOTE]
>
>Chiedete al vostro consulente di configurare l&#39;applicazione Web per il servizio di annullamento dell&#39;iscrizione prima di seguire i passaggi indicati di seguito.

## Creating a new recipient {#creating-a-new-recipient}

1. Crea un nuovo destinatario in Campaign v7 per la replica in Campaign Standard. Inserite il maggior numero possibile di informazioni, inclusi cognome, nome, indirizzo e-mail e indirizzo postale del destinatario. Tuttavia, non scegliete un **[!UICONTROL Salutation]** dato che verrà aggiunto nella sezione successiva, [Modifica di un destinatario](#editing-a-recipient). Per ulteriori informazioni, vedere [Aggiunta di destinatari](../../platform/using/adding-profiles.md).

   ![](assets/acs_connect_profile_sync_01.png)

1. Conferma che il nuovo destinatario sia stato aggiunto ad Campaign Standard. Quando rivedete il profilo, accertatevi che i dati immessi in Campaign v7 siano disponibili anche in Campaign Standard. Per scoprire dove trovare i profili in Campaign Standard, consulta Nozioni di base sulla [navigazione](https://docs.adobe.com/content/help/en/campaign-standard/using/getting-started/discovering-the-interface/interface-description.html).

   ![](assets/acs_connect_profile_sync_02.png)

   Per impostazione predefinita, la replica periodica per il connettore ACS è una volta ogni 15 minuti. Per ulteriori informazioni, vedi Replica [](../../integrations/using/acs-connector-principles-and-data-cycle.md#data-replication)dati.

## Modifica di un destinatario {#editing-a-recipient}

La procedura seguente per modificare un singolo punto di dati offre un semplice esempio di come Campaign v7 diventa il database principale per Campaign Standard quando si utilizza la replica dei dati. La modifica o l&#39;eliminazione dei dati replicati in Campaign v7 ha lo stesso effetto sui dati corrispondenti in Campaign Standard.

1. Scegli il destinatario appena creato da [Creazione di un nuovo destinatario](#creating-a-new-recipient) e modifica il nome del destinatario. Ad esempio, scegliete una **[!UICONTROL Salutation]** per il destinatario (ad esempio, Sig. o Sig. Per ulteriori informazioni, consultate [Modifica di un profilo](../../platform/using/editing-a-profile.md).

   ![](assets/acs_connect_profile_sync_03.png)

1. Conferma che il nome del destinatario sia stato aggiornato in Campaign Standard. Per scoprire dove trovare i profili in Campaign Standard, consulta Nozioni di base sulla [navigazione](https://docs.adobe.com/content/help/en/campaign-standard/using/getting-started/discovering-the-interface/interface-description.html).

   ![](assets/acs_connect_profile_sync_04.png)

   Per impostazione predefinita, la replica periodica per il connettore ACS è una volta ogni 15 minuti. Per ulteriori informazioni, vedi Replica [](../../integrations/using/acs-connector-principles-and-data-cycle.md#data-replication)dati.

## Creazione di un flusso di lavoro {#creating-a-workflow}

I profili e i servizi replicati da Campaign v7 sono disponibili agli esperti di marketing digitale per sfruttare i dati avanzati in Campaign Standard. Le istruzioni riportate di seguito illustrano come aggiungere una query a un flusso di lavoro Campaign Standard e utilizzarla con il database replicato.

Per ulteriori informazioni e istruzioni complete sui flussi di lavoro Campaign Standard, consulta [Flussi di lavoro](../../workflow/using/about-workflows.md).

1. Andate su Campaign Standard e fate clic **[!UICONTROL Marketing Activities]**.
1. Fate clic **[!UICONTROL Create]** in alto a destra.
1. Clic **[!UICONTROL Workflow]**.
1. Fate clic **[!UICONTROL New workflow]** su e **[!UICONTROL Next]**.
1. Immettete un nome per il flusso di lavoro nel **[!UICONTROL Label]** campo e, se necessario, ulteriori informazioni. Clic **[!UICONTROL Next]**.
1. Da **[!UICONTROL Targeting]** sinistra, trascinate una **[!UICONTROL Query]** destinazione nell’area di lavoro.

   ![](assets/acs_connect_profile_sync_05.png)

1. Fate doppio clic sull&#39; **[!UICONTROL Query]** attività e scegliete un parametro che possa essere utilizzato con il database replicato. Ad esempio, potete:

   * Trascinare **[!UICONTROL Profiles]** nell’area di lavoro. Utilizzate il menu a discesa del campo per scegliere **[!UICONTROL Is external resource]** di trovare i profili replicati da Campaign v7.
   * Trascinate altri parametri di query per eseguire un ulteriore targeting dei profili replicati.

## Creating a delivery {#creating-a-delivery}

>[!NOTE]
>
>Le istruzioni per la creazione della consegna proseguono il flusso di lavoro iniziato con [Creazione di un flusso di lavoro](#creating-a-workflow).

Gli esperti di marketing digitale possono utilizzare un&#39;applicazione Web Campaign v7 per assicurarsi che la scelta del destinatario di annullare la sottoscrizione a un servizio venga inviata al database Campaign v7. Dopo che il destinatario fa clic sul collegamento di annullamento dell&#39;iscrizione, l&#39;opzione per interrompere la ricezione del servizio viene replicata da Campaign v7 ad Campaign Standard. Per ulteriori dettagli, consultate [Modifica del collegamento](#changing-the-unsubscription-link)di annullamento dell’iscrizione.

Seguite i passaggi riportati di seguito per aggiungere una consegna e-mail a un flusso di lavoro esistente con il servizio di annullamento dell&#39;iscrizione creato in Campaign v7. Per ulteriori informazioni e istruzioni complete sui flussi di lavoro Campaign Standard, consulta questo [documento](../../workflow/using/about-workflows.md).

>[!NOTE]
>
>Chiedete al vostro consulente di configurare l&#39;applicazione Web per il servizio di annullamento dell&#39;iscrizione prima di seguire i passaggi indicati di seguito.

1. Fate clic **[!UICONTROL Channels]** a sinistra.
1. Trascinare **[!UICONTROL Email delivery]** nel flusso di lavoro esistente nell’area di lavoro.

   ![](assets/acs_connect_profile_sync_07.png)

1. Fate doppio clic sull&#39; **[!UICONTROL Email delivery]** attività e scegliete **[!UICONTROL Single send email]** o **[!UICONTROL Recurring email]**. Selezionate le opzioni e fate clic **[!UICONTROL Next]**.
1. Fate clic **[!UICONTROL Send via email]** e fate clic **[!UICONTROL Next]**.

   ![](assets/acs_connect_profile_sync_08.png)

1. Immettete un nome per la consegna nel **[!UICONTROL Label]** campo e, se necessario, ulteriori informazioni. Clic **[!UICONTROL Next]**.

   ![](assets/acs_connect_profile_sync_09.png)

1. Nel **[!UICONTROL Subject]** campo, immettete l’oggetto che verrà visualizzato nella inbox di posta elettronica del destinatario.
1. Fate clic **[!UICONTROL Change content]** per aggiungere un modello HTML.

   ![](assets/acs_connect_profile_sync_10.png)

1. Scegliete il contenuto che include il collegamento per annullare l’iscrizione al servizio. Clic **[!UICONTROL Confirm]**.

   ![](assets/acs_connect_profile_sync_11.png)

1. Il collegamento di annullamento dell&#39;iscrizione corrente deve essere sostituito da un nuovo collegamento che utilizza l&#39;applicazione Web creata dal consulente. Individuate il collegamento di annullamento dell’iscrizione nella parte inferiore del contenuto dell’e-mail e fate clic su di esso una volta. Fai clic sull’icona del cestino per eliminare il collegamento.

   ![](assets/acs_connect_profile_sync_12.png)

1. Fare clic all&#39;interno della stessa area di contenuto e digitare **Annulla sottoscrizione**.

   ![](assets/acs_connect_profile_sync_13.png)

1. Evidenzia il testo con il cursore e fai clic sull’icona della catena.
1. Clic **[!UICONTROL Link to a landing page]**.

   ![](assets/acs_connect_profile_sync_14.png)

1. Fate clic sull’icona della cartella per scegliere la pagina di destinazione.

   ![](assets/acs_connect_profile_sync_15.png)

1. Scegliete l&#39;applicazione Web creata dal consulente e fate clic su **[!UICONTROL Confirm]**.

   ![](assets/acs_connect_profile_sync_16.png)

1. Clic **[!UICONTROL Create]**.
1. Tornate al flusso di lavoro facendo clic sul nome della consegna.

   ![](assets/acs_connect_profile_sync_17.png)

1. Fare clic **[!UICONTROL Start]** per inviare la consegna. L&#39;icona di consegna dell&#39;e-mail lampeggia per indicare che è in corso la preparazione per la consegna.

   ![](assets/acs_connect_profile_sync_18.png)

1. Fate doppio clic sul **[!UICONTROL Email delivery]** canale e scegliete **[!UICONTROL Confirm]** di inviare il messaggio e-mail. Fare clic **[!UICONTROL OK]** per inviare i messaggi.

   ![](assets/acs_connect_profile_sync_19.png)

## Verifica del servizio di annullamento della sottoscrizione {#verifying-the-unsubscription-service}

Seguite le istruzioni riportate in [Creazione di un flusso di lavoro](#creating-a-workflow) e [Creazione di una consegna](#creating-a-delivery) prima di passare ai passaggi descritti di seguito.

1. Il destinatario fa clic sul collegamento di annullamento dell’iscrizione nella consegna del messaggio e-mail.

   ![](assets/acs_connect_profile_sync_20.png)

1. Il destinatario conferma l’annullamento della sottoscrizione.

   ![](assets/acs_connect_profile_sync_21.png)

1. I dati del destinatario in Campaign v7 vengono aggiornati per indicare che l&#39;utente ha annullato la sottoscrizione. Verificare che la casella **[!UICONTROL No longer contact (by any channel)]** sia selezionata per il destinatario. Per informazioni su come visualizzare un destinatario in Campaign v7, consulta [Modifica di un profilo](../../platform/using/editing-a-profile.md).

   ![](assets/acs_connect_profile_sync_22.png)

1. Vai ad Campaign Standard e apri i dettagli del profilo del destinatario. Verificate che accanto a **[!UICONTROL No longer contact (by any channel)]**. Per scoprire dove trovare i profili in Campaign Standard, consulta Nozioni di base sulla [navigazione](https://docs.adobe.com/content/help/en/campaign-standard/using/getting-started/discovering-the-interface/interface-description.html).

   ![](assets/acs_connect_profile_sync_23.png)

