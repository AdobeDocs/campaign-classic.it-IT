---
product: campaign
title: Creare un sondaggio per invitare un amico
description: Scopri come creare un modulo per invitare un amico
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Surveys
exl-id: bd94c41a-813a-4ddb-a2bd-c3deab022482
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 0%

---

# Caso d’uso: creare un modulo di riferimento{#use-case-creating-a-refer-a-friend-form}



In questo esempio, vogliamo offrire un concorso ai destinatari nel database. Nel modulo Web sarà presente una sezione per l&#39;immissione delle risposte e un&#39;altra per l&#39;invio di un messaggio a un amico immettendo il proprio indirizzo di posta elettronica.

![](assets/s_ncs_admin_survey_viral_sample_0.png)

I blocchi di identificazione e di concorrenza vengono creati utilizzando i processi descritti in precedenza.

Per configurare e creare il blocco di riferimento, attieniti alla seguente procedura:

1. Creare un modulo Web per la concorrenza con domande e un campo per l&#39;immissione delle informazioni di contatto di un amico come illustrato di seguito:

   ![](assets/s_ncs_admin_survey_viral_sample_2.png)

   Il campo **Messaggio** consente di immettere un messaggio per l&#39;arbitro. Il referente deve inoltre immettere **Cognome**, **Nome** e **E-mail**.

   Le informazioni immesse nei campi vengono memorizzate in una tabella specifica nota come tabella dei visitatori.

   >[!NOTE]
   >
   >Se il destinatario non ha dato il proprio consenso, non è possibile memorizzarlo con i destinatari nel database. Verranno archiviati temporaneamente nella tabella **visitor** (**nms:visitor**) progettata per le campagne di marketing virale. Questa tabella viene eliminata regolarmente grazie alle **operazioni di pulizia**.
   >
   >In questo esempio, vogliamo indirizzare i destinatari affinché suggeriscano di partecipare al concorso raccomandato dal loro referrer. Tuttavia, in questo messaggio vogliamo offrire loro anche un abbonamento a uno dei nostri servizi informativi. Se si iscrivono, possono essere memorizzati nel database.

   ![](assets/s_ncs_admin_survey_viral_sample_5.png)

   Il contenuto dei campi che riguardano l’arbitro verrà utilizzato nello script di creazione del profilo e nel messaggio a loro inviato.

1. Inizia creando uno script per collegare il referente all’arbitro.

   Contiene le seguenti istruzioni:

   ![](assets/s_ncs_admin_survey_viral_sample_4.png)

   ```
   ctx.recipient.visitor.@id = xtk.session.GetNewIds(1)
   ctx.recipient.visitor.@forwardUrl = "APP5"
   ctx.recipient.visitor.@referrerEmail = ctx.recipient.@email
   ctx.recipient.visitor.@referrerFirstName = ctx.recipient.@firstName
   ctx.recipient.visitor.@referrerLastName = ctx.recipient.@lastName
   ```

   Il cognome, il nome e l’indirizzo e-mail immessi nel blocco di identificazione della pagina sono identificati come cognome, nome e indirizzo e-mail del referente. Questi campi verranno reinseriti nel corpo del messaggio inviato all&#39;arbitro.

   Il valore APP5 corrisponde al nome interno del modulo Web: queste informazioni consentono di individuare l&#39;origine dell&#39;arbitro, ovvero di collegare il visitatore al modulo Web in base al quale è stato creato.

1. La casella di memorizzazione consente di raccogliere le informazioni e di memorizzarle nel database.

   ![](assets/s_ncs_admin_survey_viral_sample_4b.png)

1. Quindi crea il modello di consegna collegato al servizio informazioni creato durante il passaggio 1. Verrà selezionato nel campo **[!UICONTROL Choose scenario]** del servizio informazioni.

   Il modello di consegna utilizzato per creare il messaggio di offerta di riferimento contiene le seguenti informazioni:

   ![](assets/s_ncs_admin_survey_viral_sample_7.png)

   Questo modello presenta le seguenti caratteristiche:

   * Seleziona la tabella dei visitatori come mappatura di destinazione.

     ![](assets/s_ncs_admin_survey_viral_sample_7b.png)

   * Le informazioni di contatto dell’arbitro e quelle sul referente vengono ricavate dalla tabella dei visitatori. Viene inserito utilizzando il pulsante di personalizzazione.

     ![](assets/s_ncs_admin_survey_viral_sample_7a.png)

   * Questo modello contiene un collegamento al modulo del concorso e il collegamento di abbonamento per l&#39;abbonamento alla newsletter da parte dell&#39;arbitro.

     Il collegamento di abbonamento viene inserito tramite un blocco di personalizzazione. Per impostazione predefinita, ti consente di abbonare i profili al servizio **newsletter**. Questo blocco di personalizzazione può essere modificato in base alle tue esigenze, ad esempio per abbonare il destinatario a un servizio diverso.

   * Il nome interno (&quot;referrer&quot; qui) verrà utilizzato nello script di consegna del messaggio come mostrato di seguito.

   >[!NOTE]
   >
   >Per ulteriori informazioni sui modelli di consegna, consulta la [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-templates.html){target="_blank"}.

1. Crea il secondo script per la consegna dei messaggi di abbonamento.

   ![](assets/s_ncs_admin_survey_viral_sample_7c.png)

   ```
   // Updtate visitor to have a link to the referrer recipient
   ctx.recipient.visitor.@referrerId = ctx.recipient.@id
   ctx.recipient.visitor.@xtkschema = "nms:visitor"
   ctx.recipient.visitor.@_operation = "update" 
   ctx.recipient.visitor.@_key = "@id" 
   xtk.session.Write(ctx.recipient.visitor)
   
   // Send email to friend
   nms.delivery.QueueNotification("referrer",
   <delivery>
   <targets>
     <deliveryTarget>
       <targetPart type='query' exclusion='false' ignoreDeleteStatus='false'>
         <where>
           <condition expr={'@id IN ('+ ctx.recipient.visitor.@id +')' }/>
         </where>
       </targetPart>
      </deliveryTarget>
     </targets>
    </delivery>)
   ```

1. Pubblica il modulo di concorso e invia un invito ai destinatari del target iniziale. Quando uno di loro invita un amico, viene creata una consegna basata sul modello **Offerta di riferimento**.

   ![](assets/s_ncs_admin_survey_viral_sample_8.png)

   L&#39;arbitro viene aggiunto alla cartella dei visitatori in **[!UICONTROL Administration > Visitors node]**:

   ![](assets/s_ncs_admin_survey_viral_sample_9.png)

   Il loro profilo contiene le informazioni inserite dal referente. Viene memorizzato in base alle configurazioni immesse nello script del modulo. Se decidono di abbonarsi alla newsletter, verranno salvati nella tabella dei destinatari.
