---
solution: Campaign Classic
product: campaign
title: Invio con MTA avanzato in Adobe Campaign Classic
description: Scopri l’ambito e le specificità dell’invio di e-mail con l’MTA avanzata di Adobe Campaign .
audience: delivery
content-type: reference
topic-tags: sending-emails
translation-type: tm+mt
source-git-commit: 07ed17a093cb6fb2d7aae376325a127c61b1dcc2
workflow-type: tm+mt
source-wordcount: '1398'
ht-degree: 2%

---


# Invio con MTA avanzata {#sending-with-enhanced-mta}

L&#39;**Adobe Campaign Enhanced MTA** (Mail Transfer Agent) fornisce un&#39;infrastruttura di invio aggiornata che consente una migliore recapito, reputazione, throughput, reporting, gestione delle rimbalzi, configurazione della rampa IP e gestione delle impostazioni di connessione.

È implementato per migliorare la scalabilità, aumentare il throughput di distribuzione e aiutare a inviare più e-mail più rapidamente. Ciò si ottiene con nuove tecniche di consegna adattiva che modificano le impostazioni di invio delle e-mail in tempo reale in base al feedback ricevuto dai provider di servizi Internet.

>[!IMPORTANT]
>
>Il  Adobe Campaign Enhanced MTA è disponibile solo per i clienti Campaign Classic ospitati o ibridi. Impossibile aggiornare le installazioni Campaign Classic locali per utilizzare l&#39;MTA avanzato.

Se dopo settembre 2018 vi è stata fornita un&#39;istanza Campaign Classic, utilizzate l&#39;MTA avanzata. Per tutti gli altri clienti Campaign Classic, consultare la sezione [Domande frequenti](#enhanced-mta-faq) riportata di seguito.

L&#39;implementazione MTA avanzata potrebbe avere un impatto su alcune delle funzionalità di Campaign esistenti. Per ulteriori informazioni, vedere [Miglioramento delle specificità MTA](#enhanced-mta-impacts).

## Domande frequenti {#enhanced-mta-faq}

### Utilizzo e vantaggi

**Cos&#39;è l&#39;MTA avanzato?**

 Adobe Campaign può ora essere aggiornato per utilizzare un nuovo MTA (Mail Transfer Agent) che esegue l&#39;MTA commerciale di SparkPost denominato **Momentum**.

Momentum rappresenta una tecnologia MTA innovativa e ad alte prestazioni, che include una gestione dei rimbalzi più intelligente e una funzionalità di ottimizzazione della recapito automatizzata che consente ai mittenti di raggiungere e mantenere i tassi di consegna ottimali della posta in arrivo. <!--More than 37% of the world’s business email is sent using SparkPost’s MTA technology.-->

**Quali sono i benefici?**

*  client Adobe Campaign che utilizzano l&#39;MTA Enhanced hanno visto un <!--300%-->aumento massiccio della velocità effettiva complessiva e una <!--90%+-->riduzione significativa dei rimbalzi morbidi.
* L&#39;MTA avanzata utilizza la più recente tecnologia MTA per fornire la velocità di trasmissione ottimale per la distribuzione delle e-mail.
* Grazie all&#39;adattamento immediato e automatico ai commenti ricevuti, l&#39;e-mail viene inviata in modo più preciso e intelligente, con dati di consegna in tempo reale.

**È possibile utilizzare  MTA nativo Adobe Campaign e MTA avanzata allo stesso tempo?**

No. Solo l&#39;MTA avanzata può essere utilizzato per le comunicazioni e-mail dopo l&#39;aggiornamento dell&#39;istanza.

<!--
**Is there a fee associated with upgrading my instance to and subsequent use of the Enhanced MTA?**
No, there is no extra fee associated with the upgrade process to enable the use of the Enhanced MTA.

**When will the Enhanced MTA be available to me?**

* If you are new to Adobe Campaign Classic, you are already using the Enhanced MTA.

* For Adobe Campaign Classic existing customers, we’ve implemented a phased rollout that covers all hosted or partially hosted (hybrid) instances. If you’re not already using it, we’ll be contacting you in the near future with the dates and details for upgrading your Adobe Campaign Classic instances to the Enhanced MTA.
-->

### Aggiornamento all&#39;MTA avanzato

**Cosa è necessario per effettuare l&#39;aggiornamento all&#39;MTA avanzato?**

Se dopo settembre 2018 è stato eseguito il provisioning di un&#39;istanza Campaign Classic, non è richiesta alcuna azione, in quanto si sta già utilizzando l&#39;MTA avanzata.

Per tutti gli altri clienti ospitati o parzialmente ospitati (ibridi), il team Adobe Campaign  cercherà di coordinare una data per la migrazione e fornirà dettagli sui passaggi necessari per effettuare la migrazione.

>[!IMPORTANT]
>
>L&#39;MTA avanzata non è disponibile per le installazioni locali.

**Qual è il processo per aggiornare la mia istanza all&#39;MTA avanzato?**

L&#39;intero processo per le istanze ospitate richiede alcuni minuti di inattività.  Adobe controllerà il throughput e la recapito delle e-mail fino a 24 ore dopo l&#39;aggiornamento per valutare l&#39;impatto sulle consegne delle e-mail.

In caso di problemi riscontrati,  Adobe può ripristinare rapidamente e temporaneamente l’istanza all’MTA  Adobe Campaign nativo.

Attualmente, l’MTA avanzata interessa solo il canale e-mail. Le notifiche push e le consegne di SMS continueranno a utilizzare il MTA nativo della campagna e non saranno influenzate in alcun modo dall&#39;aggiornamento.

**Devo affrontare nuovamente il riscaldamento IP dopo l&#39;aggiornamento all&#39;MTA avanzato?**

No. L&#39;aggiornamento non richiede il passaggio a nuovi IP, pertanto puoi continuare a utilizzare i tuoi IP e-mail esistenti e riscaldati.

**L&#39;aggiornamento all&#39;MTA avanzato avrà un impatto su eventuali campagne o consegne in corso?**

Tutte le consegne che erano state preparate prima dell&#39;aggiornamento dell&#39;istanza per l&#39;utilizzo dell&#39;MTA avanzato dovranno essere preparate nuovamente per poter utilizzare correttamente il nuovo MTA.

Per i clienti che utilizzano  funzionalità di messaggistica transazionale di Adobe Campaign, qualsiasi chiamata API per attivare un&#39;e-mail verrà messa in coda durante i tempi di inattività dell&#39;aggiornamento molto brevi e tentata al termine dell&#39;aggiornamento.

## Specifiche MTA migliorate {#enhanced-mta-impacts}

### Intestazioni MTA migliorate

Le ultime istanze di Campaign Classic includono il codice che aggiunge le intestazioni MTA avanzate richieste a ogni messaggio. Se utilizzi  Adobe Campaign 19.1 (build 9032) o versione successiva e in caso contrario, devi aggiungere il parametro &quot;useMomentum=true&quot; alla configurazione dell&#39;istanza di marketing (nel file [serverConf.xml](../../installation/using/the-server-configuration-file.md#mta)).

Tuttavia, se utilizzi un&#39;istanza precedente che non include questo codice, una nuova regola di tipologia denominata **[!UICONTROL Typology Rule for Enhanced MTAs]** deve essere aggiunta a tutti i tipi di tipologie esistenti nell&#39;istanza Campaign.
Questa regola viene aggiunta da un pacchetto **[!UICONTROL Typology]** installato come parte dell&#39;aggiornamento all&#39;MTA avanzato.

>[!IMPORTANT]
>
>Se visualizzi questa regola di tipologia nelle tue tipologie, non eliminarla o modificarla in alcun modo. In caso contrario, le comunicazioni e-mail potrebbero essere influenzate negativamente.

Questo pacchetto **[!UICONTROL Typology]** deve essere installato nell&#39;istanza di marketing di Adobe Campaign .

Se sei un client ibrido, il team Adobe Campaign  ti fornirà istruzioni su come installare il pacchetto **[!UICONTROL Typology]** nell&#39;istanza di marketing come parte dell&#39;aggiornamento all&#39;MTA avanzato. Contattate il vostro responsabile commerciale per ottenere le istruzioni complete.

>[!IMPORTANT]
>
>Le istruzioni fornite dal team Adobe Campaign  su come installare il pacchetto **[!UICONTROL Typology]** devono essere seguite con attenzione. In caso contrario, potrebbero verificarsi problemi rilevanti con gli IP utilizzati per inviare e-mail.

Per ulteriori informazioni sulle tipologie, vedere [questa sezione](../../campaign/using/about-campaign-typologies.md).

### Nuove regole MX

Le regole del throughput di gestione MX non vengono più utilizzate. L&#39;MTA avanzata dispone di regole MX specifiche che consentono di personalizzare il throughput in base al dominio in base alla reputazione storica dell&#39;e-mail e al feedback in tempo reale proveniente dai domini in cui invii le e-mail.

Per ulteriori informazioni sulla configurazione MX, vedere [questa sezione](../../installation/using/email-deliverability.md#mx-configuration).

### Qualifica di rifiuto

I titoli di rimbalzo nella tabella Campaign **[!UICONTROL Delivery log qualification]** non vengono più utilizzati per i messaggi di errore di consegna **sincroni**. L&#39;MTA avanzata determina il tipo di rimbalzo e la qualifica e invia nuovamente tali informazioni a Campaign.

>[!NOTE]
>
>L&#39;MTA avanzata qualifica il rimbalzo SMTP e invia tale qualifica a Campaign sotto forma di codice di rimbalzo mappato a un motivo e a una qualifica di rimbalzo della campagna.

Per ulteriori informazioni sulla qualifica del rimbalzo, vedere [questa sezione](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification).

### Stato inviato con MTA avanzata

Nella **[!UICONTROL Summary]** visualizzazione di un&#39;e-mail di consegna [dashboard](../../delivery/using/delivery-dashboard.md), la percentuale **[!UICONTROL Success]** inizia al 100% e poi scende progressivamente durante il periodo di validità [consegna](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period), poiché i rimbalzi morbidi e duri vengono riportati dall&#39;MTA avanzata alla campagna.

In effetti, tutti i messaggi vengono visualizzati come **[!UICONTROL Sent]** nel [log di invio](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history) non appena vengono correttamente inviati da Campaign all&#39;MTA avanzato. Rimangono nello stato a meno che o fino a quando un [bounce](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons) per quel messaggio non venga comunicato nuovamente dall&#39;MTA avanzato alla campagna.

Quando i messaggi di rimbalzo rigido vengono segnalati dall&#39;MTA avanzata, il loro stato cambia da **[!UICONTROL Sent]** a **[!UICONTROL Failed]** e la percentuale **[!UICONTROL Success]** viene ridotta di conseguenza.

Quando i messaggi di rimbalzo soft vengono segnalati dall&#39;MTA avanzata, vengono comunque visualizzati come **[!UICONTROL Sent]** e la percentuale **[!UICONTROL Success]** non è ancora aggiornata. I messaggi di rimbalzo temporaneo vengono quindi [riprovati](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) durante il periodo di validità della consegna:

* Se un tentativo ha esito positivo prima della fine del periodo di validità, lo stato del messaggio rimane **[!UICONTROL Sent]** e la percentuale **[!UICONTROL Success]** rimane invariata.

* In caso contrario, lo stato cambia in **[!UICONTROL Failed]** e la percentuale **[!UICONTROL Success]** viene diminuita di conseguenza.

Di conseguenza, è necessario attendere fino alla fine del periodo di validità per visualizzare la percentuale finale **[!UICONTROL Success]** e il numero finale di messaggi effettivi **[!UICONTROL Sent]** e **[!UICONTROL Failed]**.

<!--The fact that the Success percentage will go to 100% very quickly indicates that your instance has been upgraded to the Enhanced MTA.-->

### Velocità effettiva di consegna

Il grafico del throughput di distribuzione delle campagne non visualizzerà più il throughput ai destinatari delle e-mail. Questo grafico ora mostra la velocità effettiva per il inoltro dei messaggi da Campaign all&#39;MTA avanzato.

Per ulteriori informazioni sulla velocità di consegna, vedere [questa sezione](../../reporting/using/global-reports.md#delivery-throughput).

### Periodo di validità

L&#39;impostazione del periodo di validità nelle consegne della campagna verrà utilizzata dall&#39;MTA avanzata solo se impostata su **3,5 giorni o meno**. Se in Campaign definisci un valore superiore a 3,5 giorni, non verrà preso in considerazione.

Ad esempio, se il periodo di validità è impostato sul valore predefinito di 5 giorni in Campaign, i messaggi di rimbalzo temporaneo entreranno nella coda dei tentativi MTA avanzata e verranno ritentati per un massimo di 3,5 giorni a partire dal momento in cui il messaggio ha raggiunto l&#39;MTA avanzato. In tal caso, il valore impostato in Campaign non verrà utilizzato.

Una volta che un messaggio è rimasto nella coda dell’MTA avanzato per 3,5 giorni e la consegna non è riuscita, si verificherà un timeout e il suo stato verrà aggiornato da **[!UICONTROL Sent]** a **[!UICONTROL Failed]** nei log di consegna.

Per ulteriori informazioni sul periodo di validità, vedere [questa sezione](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period).

### Firma DKIM

La firma dell&#39;autenticazione tramite e-mail DKIM (DomainKeys Identified Mail) viene fatta dall&#39;MTA avanzata. La firma DKIM da parte dell&#39;MTA della campagna nativa verrà disattivata all&#39;interno della tabella di gestione del dominio come parte dell&#39;aggiornamento MTA avanzato.
Per ulteriori informazioni su DKIM, vedere [questa sezione](../../delivery/using/technical-recommendations.md#dkim).