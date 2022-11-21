---
product: campaign
title: S con MTA avanzato in Adobe Campaign Classic
description: Scopri l’ambito e le specificità dell’invio di e-mail con l’MTA avanzato di Adobe Campaign
feature: Email
exl-id: 58cc23f4-9ab0-45c7-9aa2-b08487ec7e91
source-git-commit: 2d5166c355ee090639dcc52866252bae6beb81f6
workflow-type: tm+mt
source-wordcount: '1999'
ht-degree: 4%

---

# Invio con MTA avanzato {#sending-with-enhanced-mta}

![](../../assets/common.svg)

La **MTA avanzato di Adobe Campaign** (Mail Transfer Agent) fornisce un&#39;infrastruttura di invio aggiornata che consente di migliorare la consegna, la reputazione, il throughput, la generazione di rapporti, la gestione dei messaggi non recapitati, l&#39;espansione dell&#39;IP e la gestione delle impostazioni di connessione.

È implementato per migliorare la scalabilità, aumentare il throughput di consegna e contribuire a inviare più e-mail più rapidamente. Questo si ottiene con nuove tecniche di consegna adattiva che modificano le impostazioni di invio delle e-mail in tempo reale in base al feedback ricevuto dai provider di servizi Internet.

>[!IMPORTANT]
>
>L’MTA avanzato di Adobe Campaign è disponibile solo per i clienti ospitati o ibridi di Campaign Classic. Impossibile aggiornare le installazioni on-premise di Campaign Classic per utilizzare l’MTA avanzato.

Se dopo settembre 2018 ti è stato fornito un’istanza di Campaign Classic, utilizza l’MTA avanzato. Per tutti gli altri clienti Campaign Classic, consulta la sezione [Domande frequenti](#enhanced-mta-faq) sotto.

L’implementazione dell’MTA avanzato potrebbe influire su alcune delle funzionalità esistenti di Campaign. Per ulteriori informazioni, consulta la sezione [Specifiche MTA migliorate](#enhanced-mta-impacts).

>[!NOTE]
>
>Se sei un utente finale di Adobe Campaign e desideri sapere se l’istanza è stata aggiornata all’MTA avanzato, contatta il tuo amministratore interno di Campaign.

## Domande frequenti {#enhanced-mta-faq}

### Utilizzo e vantaggi

**Cos’è l’MTA avanzato?**

È ora possibile aggiornare Adobe Campaign per utilizzare un nuovo MTA (Mail Transfer Agent) che esegue l&#39;MTA commerciale di SparkPost chiamato **Momento**.

Momentum rappresenta una tecnologia MTA innovativa e ad alte prestazioni che include una gestione più intelligente dei messaggi non recapitati e una funzionalità di ottimizzazione automatizzata dei messaggi che aiuta i mittenti a raggiungere e mantenere tassi di consegna ottimali nella casella in entrata. <!--More than 37% of the world's business email is sent using SparkPost's MTA technology.-->

**Quali sono i vantaggi?**

* I client Adobe Campaign che utilizzano l’MTA avanzato hanno visualizzato un <!--300%-->aumento massiccio della velocità effettiva complessiva e <!--90%+-->riduzione significativa dei rimbalzi morbidi.
* L’MTA avanzato utilizza la tecnologia MTA più recente per fornire le velocità di throughput ottimali per la consegna delle e-mail.
* Adattandosi in modo istantaneo e automatico al feedback ricevuto, assicura anche una consegna e-mail più accurata e intelligente con dati di consegna in tempo reale.

**Posso utilizzare contemporaneamente l’MTA nativo di Adobe Campaign e l’MTA avanzato?**

No. Solo l’MTA avanzato può essere utilizzato per le consegne e-mail dopo l’aggiornamento dell’istanza.

<!--
**Is there a fee associated with upgrading my instance to and subsequent use of the Enhanced MTA?**
No, there is no extra fee associated with the upgrade process to enable the use of the Enhanced MTA.

**When will the Enhanced MTA be available to me?**

* If you are new to Adobe Campaign Classic, you are already using the Enhanced MTA.

* For Adobe Campaign Classic existing customers, we've implemented a phased rollout that covers all hosted or partially hosted (hybrid) instances. If you're not already using it, we'll be contacting you in the near future with the dates and details for upgrading your Adobe Campaign Classic instances to the Enhanced MTA.
-->

### Aggiornamento all’MTA avanzato

**Cosa è necessario per eseguire l’aggiornamento all’MTA avanzato?**

Se dopo settembre 2018 è stato eseguito il provisioning di un’istanza di Campaign Classic, non è necessaria alcuna azione, in quanto si utilizza già l’MTA avanzato.

Per tutti gli altri clienti in hosting o parzialmente ospitati (ibridi), il team Adobe Campaign si rivolgerà per coordinare una data di migrazione e fornirà dettagli sui passaggi appropriati necessari per effettuare la migrazione.

>[!IMPORTANT]
>
>L’MTA avanzato non è disponibile per le installazioni on-premise.

**Qual è il processo per aggiornare la mia istanza all’MTA avanzato?**

L&#39;intero processo per le istanze ospitate richiede alcuni minuti di inattività. Adobe controllerà il throughput delle e il recapito di messaggi e-mail per un massimo di 24 ore dopo l’aggiornamento per valutare l’impatto sulle consegne delle e-mail.

Se vengono rilevati problemi, Adobe può ripristinare rapidamente e temporaneamente l’istanza all’MTA nativo di Adobe Campaign.

Attualmente, l’MTA avanzato influisce solo sul canale e-mail. Le notifiche push e le consegne SMS continueranno a utilizzare l’MTA nativo di Campaign e non saranno influenzate in alcun modo dall’aggiornamento.

**È necessario rivedere il riscaldamento dell’IP dopo l’aggiornamento all’MTA avanzato?**

No. L’aggiornamento non richiede il passaggio a nuovi IP, pertanto puoi continuare a utilizzare gli IP e-mail esistenti e scaldati.

**L’aggiornamento all’MTA avanzato influisce su eventuali campagne o consegne attualmente in corso?**

Eventuali consegne preparate prima dell’aggiornamento dell’istanza per l’utilizzo dell’MTA avanzato dovranno essere preparate nuovamente per utilizzare correttamente il nuovo MTA.

Per i clienti che utilizzano la funzionalità di messaggistica transazionale di Adobe Campaign, tutte le chiamate API per attivare un’e-mail verranno messe in coda durante i tempi di inattività dell’aggiornamento molto brevi e verranno tentate al termine dell’aggiornamento.

## Specifiche MTA migliorate {#enhanced-mta-impacts}

### Intestazioni MTA migliorate

Le ultime istanze di Campaign Classic includono codice che aggiunge le intestazioni MTA avanzate richieste a ogni messaggio. Se utilizzi Adobe Campaign 19.1 (build 9032) o versione successiva e in caso contrario, devi richiedere [Adobe Customer Care](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) per aggiungere il parametro &quot;useMomentum=true&quot; alla configurazione dell’istanza di esecuzione (nel [serverConf.xml](../../installation/using/the-server-configuration-file.md#mta) file), che può essere la tua istanza di marketing, [istanza mid-sourcing](../../installation/using/mid-sourcing-server.md)oppure [istanza di esecuzione dei messaggi transazionali](../../message-center/using/configuring-instances.md#execution-instance), a seconda della configurazione.

Tuttavia, se utilizzi un’istanza precedente che non include questo codice, una nuova regola di tipologia denominata **[!UICONTROL Typology Rule for Enhanced MTAs]** deve essere aggiunto a tutte le tipologie esistenti nell’istanza Campaign.
Questa regola viene aggiunta da un **[!UICONTROL Typology]** pacchetto installato come parte dell’aggiornamento all’MTA avanzato.

>[!IMPORTANT]
>
>Se trovi questa regola di tipologia nelle tipologie, non eliminarla o modificarla in alcun modo. In caso contrario, le consegne delle e-mail potrebbero essere influenzate negativamente.

Questo **[!UICONTROL Typology]** Il pacchetto deve essere installato nell’istanza di marketing di Adobe Campaign.

Se sei un client ibrido, il team Adobe Campaign ti fornirà istruzioni su come installare il **[!UICONTROL Typology]** nell’istanza di marketing come parte dell’aggiornamento all’MTA avanzato. Contatta il tuo account executive per ottenere le istruzioni complete.

>[!IMPORTANT]
>
>Istruzioni fornite dal team Adobe Campaign su come installare il **[!UICONTROL Typology]** Il pacchetto deve essere seguito attentamente. In caso contrario, potresti riscontrare problemi gravi con gli IP utilizzati per inviare e-mail.

Per ulteriori informazioni sulle tipologie, consulta [questa sezione](../../campaign-opt/using/about-campaign-typologies.md).

### Nuove regole MX

Le regole della velocità effettiva di consegna della gestione MX non vengono più utilizzate. L’MTA avanzato dispone di proprie regole MX che le consentono di personalizzare il throughput in base al dominio in base alla reputazione storica dell’e-mail e al feedback in tempo reale proveniente dai domini in cui invii e-mail.

Per ulteriori informazioni sulla configurazione MX, consulta [questa sezione](../../installation/using/email-deliverability.md#mx-configuration).

### Qualificazione non recapitata

Qualifiche di mancato recapito nella campagna **[!UICONTROL Delivery log qualification]** tabella non più utilizzata per **sincrono** messaggi di errore di consegna. L’MTA avanzato determina il tipo di messaggio non recapitato e la relativa qualifica e invia nuovamente tali informazioni a Campaign.

>[!NOTE]
>
>L’MTA avanzato qualifica il messaggio di mancato recapito SMTP e lo invia nuovamente a Campaign sotto forma di codice non recapitato mappato a un motivo e a una qualifica di mancato recapito della campagna.

Per ulteriori informazioni sulla qualifica dei messaggi non recapitati, consulta [questa sezione](understanding-delivery-failures.md#bounce-mail-qualification).

### Velocità effettiva di consegna

Il grafico della velocità effettiva di consegna di Campaign non visualizzerà più la velocità effettiva ai destinatari delle e-mail. Questo grafico ora mostra la velocità effettiva per il relay dei messaggi da Campaign all’MTA avanzato.

Per ulteriori informazioni sulla velocità effettiva di consegna, consulta [questa sezione](../../reporting/using/global-reports.md#delivery-throughput).

>[!NOTE]
>
>Con la [Servizio di feedback e-mail](#email-feedback-service) (EFS) (attualmente disponibile come versione beta), il grafico della velocità effettiva di consegna delle campagne mostra ancora la velocità effettiva ai destinatari delle e-mail.

### Nuovi tentativi

Le impostazioni relative ai tentativi nella consegna non vengono più utilizzate da Campaign. I nuovi tentativi di mancato recapito e il periodo di tempo tra di essi sono determinati dall’MTA avanzato in base al tipo e alla gravità delle risposte non recapitate provenienti dal dominio e-mail del messaggio.

Per ulteriori informazioni sui nuovi tentativi, consulta [questa sezione](steps-sending-the-delivery.md#configuring-retries).

### Periodo di validità

L’impostazione del periodo di validità nelle consegne di Campaign viene utilizzata dall’MTA avanzato solo se è impostata su **3,5 giorni o meno**. Se definisci un valore superiore a 3,5 giorni in Campaign, non verrà preso in considerazione.

Ad esempio, se il periodo di validità è impostato sul valore predefinito di 5 giorni in Campaign, i messaggi di rimbalzo soft entreranno nella coda dei nuovi tentativi dell’MTA avanzato e verranno ritentati per un massimo di 3,5 giorni a partire dal momento in cui il messaggio ha raggiunto l’MTA avanzato. In tal caso, il valore impostato in Campaign non verrà utilizzato.

Una volta che un messaggio è rimasto nella coda dell’MTA avanzato per 3,5 giorni e la consegna non è riuscita, si verificherà un timeout e il suo stato verrà aggiornato da **[!UICONTROL Sent]** a **[!UICONTROL Failed]** nei log di consegna.

Per ulteriori informazioni sul periodo di validità, consulta [questa sezione](steps-sending-the-delivery.md#defining-validity-period).

### Firma DKIM

La firma dell’autenticazione dell’e-mail DKIM (DomainKeys Identified Mail) viene eseguita dall’MTA avanzato. La firma DKIM da parte dell’MTA di Campaign nativo verrà disattivata all’interno della tabella di gestione del dominio come parte dell’aggiornamento dell’MTA avanzato.
Per ulteriori informazioni su DKIM, consulta la sezione [Guida alle best practice per il recapito messaggi di Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication).

### Generazione rapporti di successo

In **[!UICONTROL Summary]** visualizzazione di una consegna e-mail [dashboard](delivery-dashboard.md), **[!UICONTROL Success]** percentuale inizia al 100% e poi scende progressivamente per tutta la consegna [periodo di validità](steps-sending-the-delivery.md#defining-validity-period), in quanto i messaggi non recapitati soft e hard vengono segnalati nuovamente dall’MTA avanzato a Campaign.

Infatti, tutti i messaggi appaiono come **[!UICONTROL Sent]** in [registri di invio](delivery-dashboard.md#delivery-logs-and-history) non appena vengono correttamente reindirizzati da Campaign all’MTA avanzato. Rimangono nello status a meno che [rimbalzo](understanding-delivery-failures.md#delivery-failure-types-and-reasons) il messaggio viene comunicato nuovamente dall’MTA avanzato a Campaign.

Quando i messaggi di rimbalzo rigido vengono segnalati dall’MTA avanzato, il loro stato cambia da **[!UICONTROL Sent]** a **[!UICONTROL Failed]** e **[!UICONTROL Success]** la percentuale è diminuita di conseguenza.

Quando i messaggi di rimbalzo soft vengono segnalati dall’MTA avanzato, vengono comunque visualizzati come **[!UICONTROL Sent]** e **[!UICONTROL Success]** percentuale non ancora aggiornata. I messaggi di rimbalzo morbido vengono quindi [nuovo](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) per tutto il periodo di validità della consegna:

* Se un nuovo tentativo ha esito positivo prima della fine del periodo di validità, lo stato del messaggio rimane uguale a **[!UICONTROL Sent]** e **[!UICONTROL Success]** La percentuale rimane invariata.

* In caso contrario, lo stato viene modificato in **[!UICONTROL Failed]** e **[!UICONTROL Success]** la percentuale è diminuita di conseguenza.

Di conseguenza, è necessario attendere fino alla fine del periodo di validità per vedere il **[!UICONTROL Success]** e il numero finale di **[!UICONTROL Sent]** e **[!UICONTROL Failed]** messaggi.

<!--The fact that the Success percentage will go to 100% very quickly indicates that your instance has been upgraded to the Enhanced MTA.-->

### Servizio di feedback e-mail (versione beta) {#email-feedback-service}

Grazie alla funzionalità EFS (Email Feedback Service), lo stato di ogni e-mail viene riportato con precisione, in quanto il feedback viene acquisito direttamente dall’MTA avanzato (Message Transfer Agent).

>[!IMPORTANT]
>
>Il servizio e-mail e-mail e’ attualmente disponibile come funzionalità beta.
>
>Se sei interessato a partecipare a questo programma beta, compila [questo modulo](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4Rol2vQGupxItW9_BerXV6VUQTJPN1Q5WUI4OFNTWkYzQjg3WllUSDAxWi4u) e torneremo da te.

Una volta avviata la consegna, non vi è alcuna modifica nella **[!UICONTROL Success]** percentuale quando il messaggio viene inviato correttamente da Campaign all’MTA avanzato.

<!--![](assets/efs-sending.png)-->

I registri di consegna mostrano le **[!UICONTROL Taken into account by the service provider]** stato per ogni indirizzo di destinazione.

<!--![](assets/efs-pending.png)-->

Quando il messaggio viene effettivamente recapitato ai profili target e una volta che tali informazioni vengono segnalate nuovamente in tempo reale dall’MTA avanzato, i registri di consegna mostrano i **[!UICONTROL Sent]** stato per ogni indirizzo che ha ricevuto correttamente il messaggio. La **[!UICONTROL Success]** viene aumentata di conseguenza con ogni consegna riuscita.

Quando i messaggi di rimbalzo rigido vengono segnalati dall’MTA avanzato, lo stato del registro cambia da **[!UICONTROL Taken into account by the service provider]** a **[!UICONTROL Failed]**<!-- and the **[!UICONTROL Bounces + errors]** percentage is increased accordingly-->.

Quando i messaggi di messaggio non recapitati vengono segnalati nuovamente dall’MTA avanzato, lo stato del registro rimane invariato (**[!UICONTROL Taken into account by the service provider]**): solo il [motivo errore](understanding-delivery-failures.md#delivery-failure-types-and-reasons) è aggiornato<!-- and the **[!UICONTROL Bounces + errors]** percentage is increased accordingly-->. La **[!UICONTROL Success]** La percentuale rimane invariata. I messaggi di rimbalzo temporaneo vengono quindi ritentati durante l’intera consegna [periodo di validità](steps-sending-the-delivery.md#defining-validity-period):

* Se un nuovo tentativo ha esito positivo prima della fine del periodo di validità, lo stato del messaggio cambia in **[!UICONTROL Sent]** e **[!UICONTROL Success]** la percentuale viene aumentata di conseguenza.

* In caso contrario, lo stato viene modificato in **[!UICONTROL Failed]**. La **[!UICONTROL Success]** <!--and **[!UICONTROL Bounces + errors]** -->La percentuale rimane invariata.

>[!NOTE]
>
>Per ulteriori informazioni sui rimbalzi rigidi e morbidi, vedi [questa sezione](understanding-delivery-failures.md#delivery-failure-types-and-reasons).
>
>Per ulteriori informazioni sui nuovi tentativi dopo un errore temporaneo di consegna, consulta [questa sezione](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure).


Le tabelle riportate di seguito mostrano le modifiche apportate ai KPI e agli stati dei registri di invio introdotte dalla funzionalità EFS.

**Con il servizio di feedback via e-mail**

| Passaggio nel processo di invio | Riepilogo KPI | Stato dei registri di invio |
|--- |--- |--- |
| Il messaggio viene inviato correttamente da Campaign all’MTA avanzato | **[!UICONTROL Success]** percentuale non visualizzata (inizia a 0%) | Considerato dal fornitore di servizi |
| I messaggi di rimbalzo rigido vengono segnalati nuovamente dall’MTA avanzato | Nessuna modifica in **[!UICONTROL Success]** percentuale | Non riuscito |
| I messaggi di rimbalzo morbido vengono segnalati nuovamente dall’MTA avanzato | Nessuna modifica in **[!UICONTROL Success]** percentuale | Considerato dal fornitore di servizi |
| I nuovi tentativi dei messaggi di rimbalzo non sono riusciti | **[!UICONTROL Success]** la percentuale viene aumentata di conseguenza | Inviato |
| Messaggi di rimbalzo morbido non riusciti | Nessuna modifica in **[!UICONTROL Success]** percentuale | Non riuscito |

**Servizio senza feedback e-mail**

| Passaggio nel processo di invio | Riepilogo KPI | Stato dei registri di invio |
|--- |--- |--- |
| Il messaggio viene inviato correttamente da Campaign all’MTA avanzato | **[!UICONTROL Success]** percentuale inizia al 100% | Inviato |
| I messaggi di rimbalzo rigido vengono segnalati nuovamente dall’MTA avanzato | **[!UICONTROL Success]** la percentuale diminuisce di conseguenza | Non riuscito |
| I messaggi di rimbalzo morbido vengono segnalati nuovamente dall’MTA avanzato | Nessuna modifica in **[!UICONTROL Success]** percentuale | Inviato |
| I nuovi tentativi dei messaggi di rimbalzo non sono riusciti | Nessuna modifica in **[!UICONTROL Success]** percentuale | Inviato | **[!UICONTROL Success]** la percentuale viene aumentata di conseguenza | Inviato |
| Messaggi di rimbalzo morbido non riusciti | **[!UICONTROL Success]** la percentuale diminuisce di conseguenza | Non riuscito |
