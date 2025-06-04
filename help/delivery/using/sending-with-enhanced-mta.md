---
product: campaign
title: Inviare con MTA avanzato in Adobe Campaign Classic
description: Scopri l’ambito e le specificità dell’invio di e-mail con MTA avanzato di Adobe Campaign
feature: Email
role: User, Admin, Developer
exl-id: 58cc23f4-9ab0-45c7-9aa2-b08487ec7e91
source-git-commit: b353b562bd2f0b0bd2dfde22c6477ab66d499483
workflow-type: tm+mt
source-wordcount: '1368'
ht-degree: 1%

---

# Invio con MTA avanzato {#sending-with-enhanced-mta}

L&#39;**MTA avanzato di Adobe Campaign** (Mail Transfer Agent) fornisce un&#39;infrastruttura di invio aggiornata che consente di migliorare il recapito messaggi, la reputazione, la velocità effettiva, il reporting, la gestione dei messaggi non recapitati, l&#39;incremento graduale dell&#39;IP e la gestione delle impostazioni di connessione.

È implementato per migliorare la scalabilità, aumentare la velocità effettiva di consegna e contribuire a inviare più e-mail più rapidamente. Ciò si ottiene con nuove tecniche di consegna adattiva che modificano le impostazioni di invio delle e-mail in tempo reale in base al feedback ricevuto dai provider di servizi Internet.

>[!IMPORTANT]
>
>L’MTA avanzato di Adobe Campaign è disponibile solo per i clienti Campaign Classic in hosting o ibridi. Le installazioni on-premise di Campaign Classic non possono essere aggiornate per utilizzare l’MTA avanzato.

Se dopo settembre 2018 hai effettuato il provisioning di un’istanza di Campaign Classic, stai utilizzando l’MTA avanzato. Per tutti gli altri clienti Campaign Classic, vedi le [Domande frequenti](#enhanced-mta-faq) di seguito.

L’implementazione dell’MTA avanzato potrebbe influire su alcune delle funzionalità di Campaign esistenti. Per ulteriori informazioni, consulta le [Specificità MTA avanzate](#enhanced-mta-impacts).

>[!NOTE]
>
>Se sei un utente finale di Adobe Campaign e desideri sapere se l’istanza è stata aggiornata all’MTA avanzato, contatta il tuo amministratore interno di Campaign.

## Domande frequenti {#enhanced-mta-faq}

### Utilizzo e vantaggi

**Cos&#39;è l&#39;MTA avanzato?**

È ora possibile aggiornare Adobe Campaign per utilizzare un nuovo MTA (Mail Transfer Agent) che esegue l&#39;MTA dell&#39;e-mail commerciale di SparkPost denominato **Momentum**.

Momentum rappresenta una tecnologia MTA innovativa e ad alte prestazioni che include una gestione dei messaggi non recapitati più intelligente e una funzionalità di ottimizzazione automatizzata della consegna dei messaggi che consente ai mittenti di raggiungere e mantenere tassi di consegna della casella in entrata ottimali. <!--More than 37% of the world's business email is sent using SparkPost's MTA technology.-->

**Quali sono i vantaggi?**

* I clienti di Adobe Campaign che utilizzano l’MTA avanzato hanno registrato un <!--300%-->aumento massiccio della velocità effettiva complessiva e una <!--90%+-->riduzione significativa dei mancati recapiti non permanenti.
* L’MTA avanzato utilizza la tecnologia MTA più recente per fornire la velocità effettiva ottimale per la consegna delle e-mail.
* Adattandosi istantaneamente e automaticamente al feedback ricevuto, garantisce inoltre una consegna delle e-mail più precisa e intelligente con dati in tempo reale.

**Posso usare l&#39;MTA nativo di Adobe Campaign e l&#39;MTA avanzato contemporaneamente?**

No. È possibile utilizzare solo l’MTA avanzato per le consegne e-mail dopo l’aggiornamento dell’istanza.

<!--
**Is there a fee associated with upgrading my instance to and subsequent use of the Enhanced MTA?**
No, there is no extra fee associated with the upgrade process to enable the use of the Enhanced MTA.

**When will the Enhanced MTA be available to me?**

* If you are new to Adobe Campaign Classic, you are already using the Enhanced MTA.

* For Adobe Campaign Classic existing customers, we've implemented a phased rollout that covers all hosted or partially hosted (hybrid) instances. If you're not already using it, we'll be contacting you in the near future with the dates and details for upgrading your Adobe Campaign Classic instances to the Enhanced MTA.
-->

### Aggiornamento a MTA avanzato

**Cosa è necessario per eseguire l&#39;aggiornamento all&#39;MTA avanzato?**

Se dopo settembre 2018 hai effettuato il provisioning di un’istanza di Campaign Classic, non è necessaria alcuna azione in quanto stai già utilizzando l’MTA avanzato.

Per tutti gli altri clienti in hosting o parzialmente in hosting (ibridi), il team di Adobe Campaign cercherà di coordinare una data per la migrazione e fornirà dettagli sui passaggi appropriati necessari per la migrazione.

>[!IMPORTANT]
>
>L’MTA avanzato non è disponibile per le installazioni locali.

**Qual è il processo per aggiornare la mia istanza all&#39;MTA avanzato?**

L’intero processo per le istanze in hosting richiede alcuni minuti di inattività. Adobe monitorerà il throughput e la consegna delle e-mail fino a 24 ore dopo l’aggiornamento per valutare l’impatto sulle consegne delle e-mail.

Nel caso in cui vengano rilevati problemi, Adobe può ripristinare rapidamente e temporaneamente l’istanza all’MTA nativo di Adobe Campaign.

Attualmente, l’MTA avanzato influisce solo sul canale e-mail. Le notifiche push e le consegne di SMS continueranno a utilizzare l’MTA nativo di Campaign e non saranno influenzate in alcun modo dall’aggiornamento.

**Devo ripetere la preparazione dell&#39;IP dopo l&#39;aggiornamento all&#39;MTA avanzato?**

No. L’aggiornamento non richiede il passaggio a nuovi IP, quindi puoi continuare a utilizzare gli IP e-mail esistenti riscaldati.

**L&#39;aggiornamento all&#39;MTA avanzato influirà su eventuali campagne o consegne attualmente in corso?**

Per i clienti che utilizzano la funzionalità di messaggistica transazionale di Adobe Campaign, tutte le chiamate API per attivare un’e-mail verranno messe in coda durante il brevissimo tempo di inattività dell’aggiornamento e verranno tentate al termine dello stesso.

## Specificità MTA migliorate {#enhanced-mta-impacts}

### Nuove regole MX

Le regole di velocità effettiva di consegna della gestione MX non vengono più utilizzate. L’MTA avanzato dispone di proprie regole MX che gli consentono di personalizzare la velocità effettiva per dominio in base alla reputazione cronologica dell’e-mail e al feedback in tempo reale proveniente dai domini in cui stai inviando le e-mail.

Per ulteriori informazioni sulla configurazione MX, consulta [questa sezione](../../installation/using/email-deliverability.md#mx-configuration).

### Qualificazione di mancato recapito

Le qualifiche di mancato recapito nella tabella **[!UICONTROL Delivery log qualification]** della campagna non vengono più utilizzate per i messaggi di errore di consegna **sincroni**. L’MTA avanzato determina il tipo e la qualifica di mancato recapito e invia nuovamente tali informazioni a Campaign.

>[!NOTE]
>
>L’MTA avanzato qualifica il mancato recapito SMTP e invia nuovamente tale qualifica a Campaign sotto forma di un codice di mancato recapito mappato su un motivo e una qualifica di mancato recapito della campagna.

Per ulteriori informazioni sulla qualifica di mancato recapito, consulta [questa sezione](understanding-delivery-failures.md#bounce-mail-qualification).

### Consegna

Una consegna non può essere interrotta una volta trasferita all’MTA avanzato, anche se viene visualizzata con lo stato **[!UICONTROL Stopped]** in Campaign.

### Velocità di consegna

Il grafico della velocità effettiva di consegna della campagna non mostrerà più la velocità effettiva per i destinatari delle e-mail. Il grafico ora mostra la velocità effettiva per l’inoltro dei messaggi da Campaign all’MTA avanzato.

Per ulteriori informazioni sulla velocità effettiva di consegna, consulta [questa sezione](../../reporting/using/global-reports.md#delivery-throughput).

### Nuovi tentativi

Le impostazioni per i nuovi tentativi nella consegna non vengono più utilizzate da Campaign. I nuovi tentativi di mancato recapito non permanenti e il periodo di tempo che intercorre tra di essi sono determinati dall’MTA avanzato in base al tipo e alla gravità delle risposte di mancato recapito provenienti dal dominio e-mail del messaggio.

Per ulteriori informazioni sui nuovi tentativi, vedere [questa sezione](steps-sending-the-delivery.md#configuring-retries).

### Periodo di validità

L&#39;impostazione del periodo di validità nelle consegne di Campaign verrà utilizzata dall&#39;MTA avanzato solo se è impostato su **3,5 giorni o meno**. Se definisci un valore superiore a 3,5 giorni in Campaign, questo non verrà preso in considerazione.

Ad esempio, se il periodo di validità è impostato sul valore predefinito di 5 giorni in Campaign, i messaggi in soft bouncing verranno inseriti nella coda dei nuovi tentativi dell’MTA avanzato e verranno ritentati solo per un massimo di 3,5 giorni da quando il messaggio ha raggiunto l’MTA avanzato. In tal caso, il valore impostato in Campaign non verrà utilizzato.

Una volta che un messaggio è rimasto nella coda dell’MTA avanzato per 3,5 giorni e la consegna non è riuscita, si verificherà un timeout e il suo stato verrà aggiornato da **[!UICONTROL Sent]** a **[!UICONTROL Failed]** nei registri di consegna.

Per ulteriori informazioni sul periodo di validità, consulta [questa sezione](steps-sending-the-delivery.md#defining-validity-period).

### Firma DKIM

La firma di autenticazione dell’e-mail DKIM (DomainKeys Identified Mail) viene eseguita dall’MTA avanzato. La firma DKIM da parte dell’MTA nativo di Campaign verrà disattivata all’interno della tabella di gestione dei domini come parte dell’aggiornamento dell’MTA avanzato.
Per ulteriori informazioni su DKIM, consulta la [Guida alle best practice per il recapito messaggi di Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html?lang=it#authentication).

### Reporting sul successo della consegna

Nella visualizzazione **[!UICONTROL Summary]** di una consegna e-mail [dashboard](delivery-dashboard.md), la percentuale di **[!UICONTROL Success]** inizia al 100% e poi si abbassa progressivamente durante il [periodo di validità](steps-sending-the-delivery.md#defining-validity-period) della consegna, man mano che i mancati recapiti permanenti e permanenti vengono segnalati dall’MTA avanzato a Campaign.

In effetti, tutti i messaggi vengono visualizzati come **[!UICONTROL Sent]** nei [registri di invio](delivery-dashboard.md#delivery-logs-and-history) non appena vengono inoltrati correttamente da Campaign all’MTA avanzato. Rimangono in tale stato a meno che o fino a quando un [mancato recapito](understanding-delivery-failures.md#delivery-failure-types-and-reasons) per quel messaggio non viene comunicato dall&#39;MTA avanzato a Campaign.

Quando i messaggi non recapitabili vengono segnalati dall&#39;MTA avanzato, il loro stato cambia da **[!UICONTROL Sent]** a **[!UICONTROL Failed]** e la percentuale di **[!UICONTROL Success]** viene diminuita di conseguenza.

Quando i messaggi con mancati recapiti non permanenti vengono segnalati dall’MTA avanzato, vengono comunque visualizzati come **[!UICONTROL Sent]** e la percentuale **[!UICONTROL Success]** non è ancora aggiornata. I messaggi con mancati recapiti non permanenti vengono quindi [ritentati](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) per tutto il periodo di validità della consegna:

* Se un nuovo tentativo ha esito positivo prima della fine del periodo di validità, lo stato del messaggio rimane **[!UICONTROL Sent]** e la percentuale di **[!UICONTROL Success]** rimane invariata.

* In caso contrario, lo stato diventa **[!UICONTROL Failed]** e la percentuale di **[!UICONTROL Success]** viene diminuita di conseguenza.

Di conseguenza, è necessario attendere fino alla fine del periodo di validità per visualizzare la percentuale finale di **[!UICONTROL Success]** e il numero finale di messaggi effettivamente **[!UICONTROL Sent]** e **[!UICONTROL Failed]**.

La tabella seguente mostra i diversi passaggi del processo di invio con i KPI corrispondenti e gli stati dei registri di invio.

| Passaggio nel processo di invio | Riepilogo KPI | Stato dei registri di invio |
|--- |--- |--- |
| Il messaggio è stato inoltrato correttamente da Campaign all’MTA avanzato | **[!UICONTROL Success]** percentuale inizia al 100% | Inviato |
| I messaggi non recapitabili vengono segnalati dall’MTA avanzato | **[!UICONTROL Success]** percentuale diminuita di conseguenza | Non riuscito |
| I messaggi in soft-bouncing vengono segnalati dall’MTA avanzato | Nessuna modifica nella percentuale **[!UICONTROL Success]** | Inviato |
| Nuovi tentativi di messaggi con mancati recapiti non permanenti riusciti | Nessuna modifica nella percentuale **[!UICONTROL Success]** | Inviato | La percentuale di **[!UICONTROL Success]** viene aumentata di conseguenza | Inviato |
| Nuovi tentativi di messaggi con mancati recapiti non riusciti | **[!UICONTROL Success]** percentuale diminuita di conseguenza | Non riuscito |

