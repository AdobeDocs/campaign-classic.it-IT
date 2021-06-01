---
solution: Campaign Classic
product: campaign
title: Invio con l’MTA avanzato in Adobe Campaign Classic
description: Scopri l’ambito e le specificità dell’invio di e-mail con l’MTA avanzato di Adobe Campaign.
audience: delivery
content-type: reference
topic-tags: sending-emails
exl-id: 58cc23f4-9ab0-45c7-9aa2-b08487ec7e91
source-git-commit: 54d503e97a4374927c4ebe3ba4e0ec05e51d47db
workflow-type: tm+mt
source-wordcount: '1921'
ht-degree: 3%

---

# Invio con MTA avanzato {#sending-with-enhanced-mta}

L&#39; **MTA avanzato Adobe Campaign** (Agente di trasferimento posta) fornisce un&#39;infrastruttura di invio aggiornata che consente di migliorare la consegna, la reputazione, il throughput, la generazione di rapporti, la gestione dei messaggi non recapitati, la rampa IP e la gestione delle impostazioni di connessione.

È implementato per migliorare la scalabilità, aumentare il throughput di consegna e contribuire a inviare più e-mail più rapidamente. Questo si ottiene con nuove tecniche di consegna adattiva che modificano le impostazioni di invio delle e-mail in tempo reale in base al feedback ricevuto dai provider di servizi Internet.

>[!IMPORTANT]
>
>L’MTA avanzato di Adobe Campaign è disponibile solo per i clienti ospitati o ibridi di Campaign Classic. Impossibile aggiornare le installazioni on-premise di Campaign Classic per utilizzare l’MTA avanzato.

Se dopo settembre 2018 ti è stato fornito un’istanza di Campaign Classic, utilizza l’MTA avanzato. Per tutti gli altri clienti Campaign Classic, consulta le [Domande frequenti](#enhanced-mta-faq) riportate di seguito.

L’implementazione dell’MTA avanzato potrebbe influire su alcune delle funzionalità esistenti di Campaign. Per ulteriori informazioni, consulta [Specifiche MTA avanzate](#enhanced-mta-impacts).

>[!NOTE]
>
>Se sei un utente finale di Adobe Campaign e desideri sapere se l’istanza è stata aggiornata all’MTA avanzato, contatta il tuo amministratore interno di Campaign.

## Domande frequenti {#enhanced-mta-faq}

### Utilizzo e vantaggi

**Cos’è l’MTA avanzato?**

È ora possibile aggiornare Adobe Campaign per utilizzare un nuovo MTA (Mail Transfer Agent) che esegue l’MTA commerciale di SparkPost denominato **Momentum**.

Momentum rappresenta una tecnologia MTA innovativa e ad alte prestazioni che include una gestione più intelligente dei messaggi non recapitati e una funzionalità di ottimizzazione automatizzata dei messaggi che aiuta i mittenti a raggiungere e mantenere tassi di consegna ottimali nella casella in entrata. <!--More than 37% of the world’s business email is sent using SparkPost’s MTA technology.-->

**Quali sono i vantaggi?**

* I client Adobe Campaign che utilizzano l’MTA avanzato hanno visto un <!--300%-->aumento massiccio della velocità effettiva complessiva e una <!--90%+-->significativa riduzione dei mancati recapiti software.
* L’MTA avanzato utilizza la tecnologia MTA più recente per fornire le velocità di throughput ottimali per la consegna delle e-mail.
* Adattandosi in modo istantaneo e automatico al feedback ricevuto, assicura anche una consegna e-mail più accurata e intelligente con dati di consegna in tempo reale.

**Posso utilizzare contemporaneamente l’MTA nativo di Adobe Campaign e l’MTA avanzato?**

No. Solo l’MTA avanzato può essere utilizzato per le consegne e-mail dopo l’aggiornamento dell’istanza.

<!--
**Is there a fee associated with upgrading my instance to and subsequent use of the Enhanced MTA?**
No, there is no extra fee associated with the upgrade process to enable the use of the Enhanced MTA.

**When will the Enhanced MTA be available to me?**

* If you are new to Adobe Campaign Classic, you are already using the Enhanced MTA.

* For Adobe Campaign Classic existing customers, we’ve implemented a phased rollout that covers all hosted or partially hosted (hybrid) instances. If you’re not already using it, we’ll be contacting you in the near future with the dates and details for upgrading your Adobe Campaign Classic instances to the Enhanced MTA.
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

Le ultime istanze di Campaign Classic includono codice che aggiunge le intestazioni MTA avanzate richieste a ogni messaggio. Se utilizzi Adobe Campaign 19.1 (build 9032) o versione successiva e in caso contrario, devi richiedere [Adobe Customer Care](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) di aggiungere il parametro &quot;useMomentum=true&quot; alla configurazione dell&#39;istanza di esecuzione (nel file [serverConf.xml](../../installation/using/the-server-configuration-file.md#mta) ), che può essere la tua istanza di marketing, [istanza di mid-sourcing](../../installation/using/mid-sourcing-server.md) o [istanza di esecuzione dei messaggi transazionali](../../message-center/using/configuring-instances.md#execution-instance), a seconda della configurazione.

Tuttavia, se utilizzi un’istanza precedente che non include questo codice, devi aggiungere una nuova regola di tipologia denominata **[!UICONTROL Typology Rule for Enhanced MTAs]** a tutte le tipologie esistenti nell’istanza Campaign.
Questa regola viene aggiunta da un pacchetto **[!UICONTROL Typology]** installato come parte dell’aggiornamento all’MTA avanzato.

>[!IMPORTANT]
>
>Se trovi questa regola di tipologia nelle tipologie, non eliminarla o modificarla in alcun modo. In caso contrario, le consegne delle e-mail potrebbero essere influenzate negativamente.

Questo pacchetto **[!UICONTROL Typology]** deve essere installato nell&#39;istanza di marketing di Adobe Campaign.

Se sei un client ibrido, il team Adobe Campaign ti fornirà istruzioni su come installare il pacchetto **[!UICONTROL Typology]** nella tua istanza di marketing come parte dell’aggiornamento all’MTA avanzato. Contatta il tuo account executive per ottenere le istruzioni complete.

>[!IMPORTANT]
>
>Le istruzioni fornite dal team Adobe Campaign su come installare il pacchetto **[!UICONTROL Typology]** devono essere seguite con attenzione. In caso contrario, potresti riscontrare problemi gravi con gli IP utilizzati per inviare e-mail.

Per ulteriori informazioni sulle tipologie, consulta [questa sezione](../../campaign/using/about-campaign-typologies.md).

### Nuove regole MX

Le regole della velocità effettiva di consegna della gestione MX non vengono più utilizzate. L’MTA avanzato dispone di proprie regole MX che le consentono di personalizzare il throughput in base al dominio in base alla reputazione storica dell’e-mail e al feedback in tempo reale proveniente dai domini in cui invii e-mail.

Per ulteriori informazioni sulla configurazione MX, consulta [questa sezione](../../installation/using/email-deliverability.md#mx-configuration).

### Qualificazione non recapitata

Le qualifiche di mancato recapito nella tabella Campaign **[!UICONTROL Delivery log qualification]** non vengono più utilizzate per i messaggi di errore di consegna **sincrono**. L’MTA avanzato determina il tipo di messaggio non recapitato e la relativa qualifica e invia nuovamente tali informazioni a Campaign.

>[!NOTE]
>
>L’MTA avanzato qualifica il messaggio non recapitato SMTP e lo invia nuovamente a Campaign sotto forma di codice non recapitato mappato a un motivo e a una qualifica di mancato recapito della campagna.

Per ulteriori informazioni sulla qualifica dei messaggi non recapitati, consulta [questa sezione](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification).

### Velocità effettiva di consegna

Il grafico della velocità effettiva di consegna di Campaign non visualizzerà più la velocità effettiva ai destinatari delle e-mail. Questo grafico ora mostra la velocità effettiva per il relay dei messaggi da Campaign all’MTA avanzato.

Per ulteriori informazioni sulla velocità effettiva di consegna, consulta [questa sezione](../../reporting/using/global-reports.md#delivery-throughput).

### Periodo di validità

L’impostazione del periodo di validità nelle consegne di Campaign viene utilizzata dall’MTA avanzato solo se è impostata su **3,5 giorni o meno**. Se definisci un valore superiore a 3,5 giorni in Campaign, non verrà preso in considerazione.

Ad esempio, se il periodo di validità è impostato sul valore predefinito di 5 giorni in Campaign, i messaggi di rimbalzo soft entreranno nella coda dei nuovi tentativi dell’MTA avanzato e verranno ritentati per un massimo di 3,5 giorni a partire dal momento in cui il messaggio ha raggiunto l’MTA avanzato. In tal caso, il valore impostato in Campaign non verrà utilizzato.

Una volta che un messaggio è rimasto nella coda dell’MTA avanzato per 3,5 giorni e la consegna non è riuscita, si verificherà un timeout e il suo stato verrà aggiornato da **[!UICONTROL Sent]** a **[!UICONTROL Failed]** nei log di consegna.

Per ulteriori informazioni sul periodo di validità, consulta [questa sezione](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period).

### Firma DKIM

La firma dell’autenticazione dell’e-mail DKIM (DomainKeys Identified Mail) viene eseguita dall’MTA avanzato. La firma DKIM da parte dell’MTA di Campaign nativo verrà disattivata all’interno della tabella di gestione del dominio come parte dell’aggiornamento dell’MTA avanzato.
Per ulteriori informazioni su DKIM, consulta la [Guida alle best practice per il recapito messaggi di Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication).

### Generazione rapporti di successo

Nella visualizzazione **[!UICONTROL Summary]** di una consegna e-mail [dashboard](../../delivery/using/delivery-dashboard.md), la percentuale **[!UICONTROL Success]** inizia al 100% e poi scende progressivamente per tutto il periodo di validità della consegna [](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period), in quanto i rimbalzi morbidi e rigidi vengono riportati dall’MTA avanzato a Campaign.

Infatti, tutti i messaggi vengono visualizzati come **[!UICONTROL Sent]** nel [log di invio](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history) non appena vengono correttamente inviati da Campaign all’MTA avanzato. Rimangono in tale stato a meno che o fino a quando un [rimbalzo](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons) per quel messaggio non viene comunicato nuovamente dall’MTA avanzato a Campaign.

Quando i messaggi di rimbalzo rigido vengono riportati dall’MTA avanzato, il loro stato cambia da **[!UICONTROL Sent]** a **[!UICONTROL Failed]** e la percentuale **[!UICONTROL Success]** viene ridotta di conseguenza.

Quando i messaggi di rimbalzo soft vengono segnalati dall’MTA avanzato, vengono comunque visualizzati come **[!UICONTROL Sent]** e la percentuale **[!UICONTROL Success]** non è ancora aggiornata. I messaggi di rimbalzo temporaneo vengono quindi [ritentati](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) per tutto il periodo di validità della consegna:

* Se un nuovo tentativo ha esito positivo prima della fine del periodo di validità, lo stato del messaggio rimane **[!UICONTROL Sent]** e la percentuale **[!UICONTROL Success]** rimane invariata.

* In caso contrario, lo stato cambia in **[!UICONTROL Failed]** e la percentuale **[!UICONTROL Success]** viene ridotta di conseguenza.

Di conseguenza, è necessario attendere fino alla fine del periodo di validità per visualizzare la percentuale finale **[!UICONTROL Success]** e il numero finale dei messaggi effettivamente **[!UICONTROL Sent]** e **[!UICONTROL Failed]**.

<!--The fact that the Success percentage will go to 100% very quickly indicates that your instance has been upgraded to the Enhanced MTA.-->

### Servizio feedback e-mail (beta) {#email-feedback-service}

Grazie alla funzionalità EFS (Email Feedback Service), lo stato di ogni e-mail viene riportato con precisione, in quanto il feedback viene acquisito direttamente dall’MTA avanzato (Message Transfer Agent).

>[!IMPORTANT]
>
>Il servizio e-mail e-mail e’ attualmente disponibile come funzionalità beta.
>
>Se sei interessato a partecipare a questo programma beta, compila [questo modulo](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4Rol2vQGupxItW9_BerXV6VUQTJPN1Q5WUI4OFNTWkYzQjg3WllUSDAxWi4u) e ti ritorneremo.

Una volta avviata la consegna, la percentuale **[!UICONTROL Success]** non subirà alcuna modifica quando il messaggio viene inoltrato correttamente da Campaign all’MTA avanzato.

<!--![](assets/efs-sending.png)-->

I registri di consegna mostrano lo stato **[!UICONTROL Taken into account by the service provider]** per ogni indirizzo di destinazione.

<!--![](assets/efs-pending.png)-->

Quando il messaggio viene effettivamente recapitato ai profili di destinazione e una volta che tali informazioni sono state segnalate nuovamente in tempo reale dall’MTA avanzato, i registri di consegna mostrano lo stato **[!UICONTROL Sent]** per ogni indirizzo che ha ricevuto correttamente il messaggio. La percentuale **[!UICONTROL Success]** viene aumentata di conseguenza con ogni consegna riuscita.

Quando i messaggi di rimbalzo rigido vengono riportati dall’MTA avanzato, lo stato del registro cambia da **[!UICONTROL Taken into account by the service provider]** a **[!UICONTROL Failed]**<!-- and the **[!UICONTROL Bounces + errors]** percentage is increased accordingly-->.

Quando i messaggi di rimbalzo non recapitati vengono segnalati dall’MTA avanzato, lo stato del registro rimane invariato (**[!UICONTROL Taken into account by the service provider]**): viene aggiornato solo il [motivo errore](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)<!-- and the **[!UICONTROL Bounces + errors]** percentage is increased accordingly-->. La percentuale **[!UICONTROL Success]** rimane invariata. I messaggi di rimbalzo morbido vengono quindi ritentati durante il periodo di validità della consegna [](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period):

* Se un nuovo tentativo ha esito positivo prima della fine del periodo di validità, lo stato del messaggio cambia in **[!UICONTROL Sent]** e la percentuale **[!UICONTROL Success]** viene aumentata di conseguenza.

* In caso contrario, lo stato cambia in **[!UICONTROL Failed]**. La percentuale **[!UICONTROL Success]** <!--and **[!UICONTROL Bounces + errors]** -->rimane invariata.

>[!NOTE]
>
>Per ulteriori informazioni sui rimbalzi rigidi e morbidi, consulta [questa sezione](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons).
>
>Per ulteriori informazioni sui nuovi tentativi dopo un errore temporaneo di consegna, consulta [questa sezione](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure).


Le tabelle riportate di seguito mostrano le modifiche apportate ai KPI e agli stati dei registri di invio introdotte dalla funzionalità EFS.

**Con il servizio di feedback via e-mail**

| Passaggio nel processo di invio | Riepilogo KPI | Stato dei registri di invio |
|--- |--- |--- |
| Il messaggio viene inviato correttamente da Campaign all’MTA avanzato | **[!UICONTROL Success]** percentuale non visualizzata (inizia a 0%) | Presa in considerazione dal fornitore di servizi |
| I messaggi di rimbalzo rigido vengono segnalati nuovamente dall’MTA avanzato | Nessuna modifica nella percentuale **[!UICONTROL Success]** | Non riuscito |
| I messaggi di rimbalzo morbido vengono segnalati nuovamente dall’MTA avanzato | Nessuna modifica nella percentuale **[!UICONTROL Success]** | Presa in considerazione dal fornitore di servizi |
| I nuovi tentativi dei messaggi di rimbalzo non sono riusciti | **[!UICONTROL Success]** la percentuale viene aumentata di conseguenza | Inviato |
| Messaggi di rimbalzo morbido non riusciti | Nessuna modifica nella percentuale **[!UICONTROL Success]** | Non riuscito |

**Servizio senza feedback e-mail**

| Passaggio nel processo di invio | Riepilogo KPI | Stato dei registri di invio |
|--- |--- |--- |
| Il messaggio viene inviato correttamente da Campaign all’MTA avanzato | **[!UICONTROL Success]** percentuale inizia al 100% | Inviato |
| I messaggi di rimbalzo rigido vengono segnalati nuovamente dall’MTA avanzato | **[!UICONTROL Success]** la percentuale diminuisce di conseguenza | Non riuscito |
| I messaggi di rimbalzo morbido vengono segnalati nuovamente dall’MTA avanzato | Nessuna modifica nella percentuale **[!UICONTROL Success]** | Inviato |
| I nuovi tentativi dei messaggi di rimbalzo non sono riusciti | Nessuna modifica nella percentuale **[!UICONTROL Success]** | Inviato | **[!UICONTROL Success]** la percentuale viene aumentata di conseguenza | Inviato |
| Messaggi di rimbalzo morbido non riusciti | **[!UICONTROL Success]** la percentuale diminuisce di conseguenza | Non riuscito |
