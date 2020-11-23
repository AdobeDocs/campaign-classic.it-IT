---
solution: Campaign Classic
product: campaign
title: '"Caso di utilizzo: creazione di un modulo per invitare un amico"'
description: '"Caso di utilizzo: creazione di un modulo per invitare un amico"'
audience: web
content-type: reference
topic-tags: online-surveys
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 3%

---


# Caso di utilizzo: creazione di un modulo per invitare un amico{#use-case-creating-a-refer-a-friend-form}

In questo esempio, vogliamo offrire un concorso ai destinatari del database. Il modulo Web avrà una sezione per l&#39;immissione delle risposte e un&#39;altra per il riferimento a un amico immettendo il proprio indirizzo e-mail.

![](assets/s_ncs_admin_survey_viral_sample_0.png)

I blocchi di identificazione e concorrenza vengono creati utilizzando i processi descritti in precedenza.

Per configurare e creare il blocco di riferimento, procedere come segue:

1. Crea un modulo Web per la concorrenza con domande e un campo per l&#39;immissione delle informazioni di contatto di un amico, come mostrato di seguito:

   ![](assets/s_ncs_admin_survey_viral_sample_2.png)

   Il campo **Messaggio** dell&#39;utente può immettere un messaggio per l&#39;oggetto. Il referente deve anche inserire il **Cognome**, il **Nome** e l’ **E-mail**.

   Le informazioni inserite nei campi sono memorizzate in una tabella specifica nota come tabella visitatore.

   >[!NOTE]
   >
   >Fintanto che il destinatario non ha dato il proprio consenso, non è possibile archiviarli con i destinatari nel database. Saranno memorizzati temporaneamente nella tabella **visitatore** (**nms:visitor**) progettata per le campagne di marketing virali. Questa tabella viene svuotata regolarmente grazie alle operazioni di **pulizia** .
   >
   >In questo esempio, desideriamo indirizzare i destinatari affinché suggeriscano loro di partecipare al concorso raccomandato dal loro referrer. Tuttavia, in questo messaggio vogliamo anche offrire loro un abbonamento a uno dei nostri servizi di informazione. Se dispongono di un’iscrizione, possono essere memorizzati nel database.

   ![](assets/s_ncs_admin_survey_viral_sample_5.png)

   Il contenuto dei campi che riguardano l&#39;arbitro verrà utilizzato nello script di creazione del profilo e nel messaggio a esso inviato.

1. Iniziate creando uno script per collegare il referente all&#39;oggetto.

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

   Il valore APP5 corrisponde al nome interno del modulo Web: queste informazioni consentono di individuare l&#39;origine dell&#39;arbitro, ovvero collegare il visitatore al modulo Web in base al quale è stato creato.

1. La casella di archiviazione consente di raccogliere informazioni e archiviarle nel database.

   ![](assets/s_ncs_admin_survey_viral_sample_4b.png)

1. Quindi create il modello di consegna collegato al servizio informazioni creato durante il passaggio 1. Sarà selezionato nel **[!UICONTROL Choose scenario]** campo del servizio informazioni.

   Il modello di consegna utilizzato per creare il messaggio di offerta di riferimento contiene le informazioni seguenti:

   ![](assets/s_ncs_admin_survey_viral_sample_7.png)

   Questo modello presenta le seguenti caratteristiche:

   * Selezionate la tabella visitatore come mappatura di destinazione.

      ![](assets/s_ncs_admin_survey_viral_sample_7b.png)

   * Le informazioni di contatto dell&#39;arbitro e quelle relative al referente vengono ricavate dalla tabella del visitatore. Viene inserito utilizzando il pulsante di personalizzazione.

      ![](assets/s_ncs_admin_survey_viral_sample_7a.png)

   * Questo modello contiene un collegamento al modulo per il concorso e il collegamento per l’iscrizione dell’utente a una newsletter.

      Il collegamento di iscrizione viene inserito tramite un blocco di personalizzazione. Per impostazione predefinita, consente di effettuare la sottoscrizione dei profili al servizio **newsletter** . Questo blocco di personalizzazione può essere modificato in base alle tue esigenze, ad esempio per abbonare il destinatario a un altro servizio.

   * Il nome interno (&#39;referrer&#39; qui) verrà utilizzato nello script di distribuzione dei messaggi come mostrato di seguito.
   >[!NOTE]
   >
   >Per ulteriori informazioni sui modelli di consegna, consultate [questa pagina](../../delivery/using/about-templates.md) .

1. Create il secondo script per la distribuzione dei messaggi di iscrizione.

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

1. Pubblicate il modulo del concorso e inviate un invito ai destinatari della destinazione iniziale. Quando uno di loro invita un amico, viene creata una consegna basata sul modello di offerta **di** riferimento.

   ![](assets/s_ncs_admin_survey_viral_sample_8.png)

   L’oggetto viene aggiunto alla cartella del visitatore nel **[!UICONTROL Administration > Visitors node]**:

   ![](assets/s_ncs_admin_survey_viral_sample_9.png)

   Il profilo contiene le informazioni inserite dal relativo referente. È memorizzato in base alle configurazioni immesse nello script del modulo. Se decidono di iscriversi alla newsletter, verranno salvati nella tabella dei destinatari.

