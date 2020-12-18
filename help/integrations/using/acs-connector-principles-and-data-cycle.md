---
solution: Campaign Classic
product: campaign
title: Principi del connettore ACS e ciclo dati
description: Principi del connettore ACS e ciclo dati
audience: integrations
content-type: reference
topic-tags: acs-connector
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1990'
ht-degree: 0%

---


# Principi del connettore ACS e ciclo di dati{#acs-connector-principles-and-data-cycle}

## Introduzione {#introduction}

Ponti del connettore ACS  Adobe Campaign v7 e  Adobe Campaign Standard. Si tratta di una funzione integrata in Campaign v7 che replica automaticamente i dati ai Campaign Standard, unendo il meglio di entrambe le applicazioni. Campaign v7 dispone di strumenti avanzati per gestire il database di marketing principale. La replica dei dati di Campaign v7 consente ai Campaign Standard di sfruttare i dati avanzati in un ambiente semplice da utilizzare.

![](assets/acs_connect_puzzle_link_01.png)

Con il connettore ACS, i Campaign Standard continuano a essere utilizzati dai professionisti del marketing digitale per progettare, eseguire e indirizzare campagne mentre Campaign v7 è progettato appositamente per gli utenti orientati ai dati come gli addetti al marketing dei database.

>[!IMPORTANT]
>
>Il connettore ACS è disponibile solo come parte dell&#39;offerta  Adobe Campaign Prime. Per ulteriori informazioni su come concedere la licenza  Adobe Campaign Prime, contattate il vostro account manager.
>
>ACS Connector è disponibile solo per architetture ospitate e ibride. Non è disponibile per installazioni locali complete.
>
>Per utilizzare questa funzione, è necessario connettersi a Campaign con un Adobe ID  (IMS). Vedere [Collegamento tramite un Adobe ID ](../../integrations/using/about-adobe-id.md) .

Questo documento presenta le funzionalità del connettore ACS. Le sezioni seguenti forniscono informazioni su come la funzione replica i dati e istruzioni su come utilizzare i profili replicati.

* [Processo](#process): Panoramica del connettore ACS e modalità di gestione della replica dei dati.
* [Implementazione](#implementation): Panoramica su come iniziare a utilizzare il connettore ACS e istruzioni su come replicare i dati di base e avanzati.
* [Sincronizzazione dei profili](../../integrations/using/synchronizing-profiles.md): Istruzioni su come replicare i profili e come creare consegne con essi.
* [Sincronizzazione dei tipi di pubblico](../../integrations/using/synchronizing-audiences.md): Istruzioni su come eseguire il targeting di un elenco di destinatari in Campaign v7, quindi replicare l&#39;elenco in Campaign Standard come pubblico.
* [Sincronizzazione delle applicazioni](../../integrations/using/synchronizing-web-applications.md) Web: Istruzioni su come collegare le applicazioni Web Campaign v7 ai Campaign Standard.
* [Risoluzione dei problemi relativi al connettore](../../integrations/using/troubleshooting-the-acs-connector.md) ACS: Consultate le risposte ai problemi più comuni.

>[!NOTE]
>
>Il connettore ACS è incluso con Campaign v7 in base al contratto di licenza. Per utilizzare il connettore ACS, accertatevi di poter passare da Campaign v7 a Campaign Standard. Se non siete certi della versione e delle funzioni incluse, contattate l’amministratore.

## Processo {#process}

### Replica dati {#data-replication}

![](assets/acs_connect_flows_01.png)

Il connettore ACS replica periodicamente i seguenti elementi da Campaign v7 a Campaign Standard:

* **Destinatari**
* **Iscrizioni**
* **Servizi**
* **Pagine di destinazione**

Per impostazione predefinita, la replica periodica per il connettore ACS è una volta ogni 15 minuti. L&#39;estensione della replica periodica può essere regolata in base alle esigenze. Contatta il tuo consulente se sono necessarie modifiche.

La replica dei dati per destinatari, iscrizioni, servizi e pagine di destinazione è incrementale, il che significa che solo i nuovi destinatari e le modifiche apportate ai destinatari esistenti vengono replicati da Campaign v7 a Campaign Standard. Tuttavia, la replica per un&#39;audience si verifica in una singola istanza. Potete creare un&#39;audience in Campaign v7 e replicarla una volta per Campaign Standard. La replica è immediata e non può essere configurata per aggiornamenti regolari. Per istruzioni, vedere [Sincronizzazione dei tipi di pubblico](../../integrations/using/synchronizing-audiences.md).

>[!NOTE]
>
>La replica iniziale di un database di grandi dimensioni può richiedere diverse ore. Tuttavia, le successive repliche sono incrementali e molto più veloci.

Il connettore ACS replica periodicamente i seguenti elementi da Campaign Standard a Campaign v7:

* **[!UICONTROL Delivery IDs]**
* **[!UICONTROL Email broad logs]**
* **[!UICONTROL Email tracking logs]**

La replica degli ID di consegna e dei registri e-mail consente di accedere alla cronologia delle consegne e ai dati di tracciamento per i destinatari v7 da Campaign v7.

>[!IMPORTANT]
>
>Solo i log di trasmissione e tracciamento delle e-mail vengono replicati dai Campaign Standard a Campaign v7.

### Sincronizzazione dati {#data-synchronization}

![](assets/acs_connect_flows_02.png)

Il connettore ACS sincronizza le quarantena tra Campaign v7 e Campaign Standard.

Ad esempio, un profilo replicato da Campaign v7 a Campaign Standard include un indirizzo e-mail. Se l&#39;indirizzo e-mail è in quarantena per Campaign Standard, i dati vengono passati a Campaign v7 durante la sincronizzazione successiva. Per ulteriori informazioni sulle quarantena, vedere [Gestione delle quarantena](../../delivery/using/understanding-quarantine-management.md) e [Campaign Standard Quarantines](https://docs.adobe.com/content/help/en/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html).

### Utilizzo dei profili replicati {#using-replicated-profiles}

I profili replicati possono essere utilizzati da Campaign Standard e Campaign v7 per i flussi di lavoro di targeting nelle campagne di marketing.

Per istruzioni su come inviare una consegna in Campaign Standard utilizzando i profili replicati, vedere [Sincronizzazione dei profili](../../integrations/using/synchronizing-profiles.md). Ulteriori istruzioni sono fornite per condividere i dati di annullamento dell&#39;iscrizione tra Campaign v7 e Campaign Standard.

### Limitazioni {#limitations}

I profili replicati sono facilmente disponibili per le consegne, ma presentano alcune limitazioni in Campaign Standard. Leggi gli elementi riportati di seguito per scoprire come gestirli al meglio.

* **Profili di sola lettura per Campaign Standard**: I profili replicati sono di sola lettura in Campaign Standard. Tuttavia, puoi modificare i destinatari in Campaign v7 e le modifiche vengono aggiornate automaticamente in Campaign Standard tramite il connettore ACS.
* **Profili creati in Campaign Standard**: Il connettore ACS replica i dati del destinatario in una direzione, da Campaign v7 a Campaign Standard. Pertanto, i profili originati in Campaign Standard non vengono replicati in Campaign v7.
* **Dati del destinatario di base per Campaign Standard**: Il connettore ACS replica i dati del destinatario adatti per i Campaign Standard. Include i nomi, gli indirizzi, gli indirizzi e-mail, i numeri di telefono cellulare, i numeri di telefono di casa e altre informazioni di contatto pertinenti. Se altri campi di destinazione e tabelle di targeting personalizzate disponibili in Campaign v7 sono fondamentali per il flusso di lavoro, rivolgiti al tuo consulente.
* **Importazione di profili** in quarantena: Gli elenchi di profili che non desiderano essere contattati possono essere importati in Campaign v7 o Campaign Standard come profili in quarantena. Lo stato dei profili è incluso nella sincronizzazione di quarantena tra le applicazioni e non sarà utilizzato nelle consegne.
* **Annulla sottoscrizione a un servizio in Campaign Standard**: La scelta di annullare l’iscrizione a una consegna non viene sincronizzata da Campaign Standard a Campaign v7. Tuttavia, potete configurare la consegna di un Campaign Standard per indirizzare il relativo collegamento di annullamento dell&#39;iscrizione a Campaign v7. Il profilo del destinatario che fa clic sul collegamento di annullamento dell&#39;iscrizione viene aggiornato in Campaign v7 e i dati vengono replicati in Campaign Standard. Vedere [Modifica del collegamento di annullamento dell&#39;iscrizione](../../integrations/using/synchronizing-profiles.md#changing-the-unsubscription-link).
* Solo i log di trasmissione e tracciamento delle e-mail vengono replicati dai Campaign Standard a Campaign v7.

### Billing {#billing}

La fatturazione non viene influenzata dalla scelta dell&#39;applicazione per l&#39;invio di consegne, Campaign v7 o Campaign Standard. Le informazioni di fatturazione vengono riconciliate tra Campaign v7 e Campaign Standard. Pertanto, se invii le consegne allo stesso destinatario utilizzando entrambe le applicazioni, viene comunque conteggiato come un unico profilo attivo.

## Implementazione {#implementation}

Esistono due tipi di implementazione per il connettore ACS. Entrambi sono sempre eseguiti dal team  Adobe Campaign Consulting.

>[!IMPORTANT]
>
>Questa sezione è destinata solo agli utenti esperti, per fornire loro una visione globale del processo di implementazione e dei suoi passi principali.
>
>Non cercate, in alcun modo, di eseguire direttamente nessuna di queste implementazioni. È strettamente riservato ai consulenti Adobe Campaign .

L&#39; **implementazione di base** consente di replicare destinatari (campi out-of-the-box), servizi e iscrizioni, applicazioni Web e audience. Si tratta di una replica unidirezionale da Campaign v7 a Campaign Standard.

L&#39; **implementazione avanzata** consentirà di eseguire casi d&#39;uso più complessi, ad esempio se si dispone di campi di destinazione aggiuntivi o di tabelle di destinatari personalizzate (ad esempio, tabella delle transazioni). Vedere [Implementazione avanzata](#advanced-implementation).

### Installazione del pacchetto {#installing-the-package}

Per utilizzare la funzione, è necessario installare il pacchetto **[!UICONTROL ACS Connector]**. Questo viene sempre eseguito dall&#39;amministratore tecnico o consulente  Adobe.

Tutti gli elementi tecnici relativi al connettore ACS sono disponibili nel nodo **[!UICONTROL Administration > ACS Connector]** dell&#39;esploratore.

### Flussi di lavoro tecnici e di replica {#technical-and-replication-workflows}

Dopo l&#39;installazione del pacchetto, sono disponibili due flussi di lavoro tecnici in **[!UICONTROL Administration > ACS Connector > Process]**.

>[!IMPORTANT]
>
>Non provare mai a modificare questi flussi di lavoro. Non dovrebbero mai essere in errore o messi in pausa. In tal caso, contattate il vostro consulente Adobe Campaign .

![](assets/acs_connect_implementation_3.png)

* **[!UICONTROL `[ACS] Quarantine synchronization`]** (quarantenaSync): questo flusso di lavoro sincronizza tutte le informazioni sulla quarantena. Tutte le nuove quarantena in Campaign v7 vengono replicate in Campaign Standard. Tutte le nuove quarantena dai Campaign Standard vengono replicate in Campaign v7. In questo modo tutte le regole di esclusione vengono sincronizzate tra Campaign v7 e Campaign Standard.
* **[!UICONTROL `[ACS] Security group synchronization`]** (securityGroupSync): questo flusso di lavoro viene utilizzato per la conversione dei diritti. Vedere [Conversione diritti](#rights-conversion).

I seguenti flussi di lavoro di replica sono disponibili come modelli &quot;pronti per essere utilizzati&quot;. Devono essere implementati dal tuo consulente Adobe Campaign .

![](assets/acs_connect_implementation_2.png)

* **[!UICONTROL `[ACS] Profile replication`]** (newProfileReplication): questo flusso di lavoro incrementale replica i destinatari in Campaign Standard. Per impostazione predefinita, replica tutti i campi dei destinatari out-of-the-box. Vedere [Campi destinatari predefiniti](#default-recipient-fields).
* **[!UICONTROL `[ACS] Service replication`]** (newServiceReplication): questo flusso di lavoro incrementale replica i servizi selezionati in Campaign Standard. Vedere il caso d&#39;uso [Sincronizzazione di applicazioni Web](../../integrations/using/synchronizing-web-applications.md).
* **[!UICONTROL `[ACS] Landing pages replication`]** (newLandingPageReplication): questo flusso di lavoro incrementale replica le applicazioni Web selezionate in Campaign Standard. Le applicazioni Web Campaign v7 vengono visualizzate come pagine di destinazione in Campaign Standard. Vedere il caso d&#39;uso [Sincronizzazione di applicazioni Web](../../integrations/using/synchronizing-web-applications.md).
* **[!UICONTROL `[ACS] New replication`]** (nuovaReplica): questo flusso di lavoro incrementale è un esempio che può essere utilizzato per replicare una tabella personalizzata. Vedere [Implementazione avanzata](#advanced-implementation).
* **[!UICONTROL `[ACS] Delivery-mesage replication`]** (newDlvMsgQualified): questo flusso di lavoro incrementale replica i messaggi di consegna da Campaign Standard a Campaign v7.
* **[!UICONTROL `[ACS] Profile delivery log replication`]** (nuovaRcpDeliveryLogReplication): questo flusso di lavoro incrementale replica gli ID di consegna, i registri di indirizzi e-mail ampi e i registri di tracciamento delle e-mail dai Campaign Standard a Campaign v7. Prende in considerazione solo le consegne inviate dal Campaign Standard ai profili che fanno parte della tabella nms:Recipients di Campaign v7.
* **[!UICONTROL `[ACS] New delivery log replication`]** (nuovaRcpDeliveryLogReplication): questo flusso di lavoro incrementale replica gli ID di consegna, i registri di indirizzi e-mail ampi e i registri di tracciamento delle e-mail dai Campaign Standard a Campaign v7. Prende in considerazione solo le consegne inviate dal Campaign Standard ai profili che fanno parte di una tabella specifica (per definire, diversi da nms:destinatari) di Campaign v7.

### Campi destinatario predefiniti {#default-recipient-fields}

Se sono presenti campi aggiuntivi o tabelle personalizzate (ad esempio, tabella delle transazioni), non saranno replicate per impostazione predefinita. È necessario eseguire la configurazione avanzata. Vedere [Implementazione avanzata](#advanced-implementation).

Di seguito è riportato l&#39;elenco dei campi dei destinatari replicati con l&#39;implementazione di base. Questi sono i campi predefiniti:

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etichetta</strong><br /> </td> 
   <td> <strong>Nome interno</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> ID origine<br /> </td> 
   <td> @sourceId<br /> </td> 
  </tr> 
  <tr> 
   <td> Data creazione<br /> </td> 
   <td> @created<br /> </td> 
  </tr> 
  <tr> 
   <td> Data modifica<br /> </td> 
   <td> @lastModified<br /> </td> 
  </tr> 
  <tr> 
   <td> E-mail<br /> </td> 
   <td> @email<br /> </td> 
  </tr> 
  <tr> 
   <td> Cognome<br /> </td> 
   <td> @lastName<br /> </td> 
  </tr> 
  <tr> 
   <td> Nome<br /> </td> 
   <td> @firstName<br /> </td> 
  </tr> 
  <tr> 
   <td> Middle name<br /> </td> 
   <td> @MiddleName<br /> </td> 
  </tr> 
  <tr> 
   <td> Mobile<br /> </td> 
   <td> @mobilePhone<br /> </td> 
  </tr> 
  <tr> 
   <td> Data di nascita<br /> </td> 
   <td> @bornDate<br /> </td> 
  </tr> 
  <tr> 
   <td> Genere<br /> </td> 
   <td> @gender<br /> </td> 
  </tr> 
  <tr> 
   <td> Saluto<br /> </td> 
   <td> @formulaSalute<br /> </td> 
  </tr> 
  <tr> 
   <td> Nessun contatto (da un canale)<br /> </td> 
   <td> @blackList<br /> </td> 
  </tr> 
  <tr> 
   <td> Non contatta più tramite e-mail<br /> </td> 
   <td> @blackListEmail<br /> </td> 
  </tr> 
  <tr> 
   <td> Nessun contatto più tramite SMS<br /> </td> 
   <td> @blackListMobile<br /> </td> 
  </tr> 
  <tr> 
   <td> Phone<br /> </td> 
   <td> @phone<br /> </td> 
  </tr> 
  <tr> 
   <td> Fax<br /> </td> 
   <td> @fax<br /> </td> 
  </tr> 
  <tr> 
   <td> Indirizzo 1 (appartamento)<br /> </td> 
   <td> [percorso/@indirizzo1]<br /> </td> 
  </tr> 
  <tr> 
   <td> Indirizzo 2<br /> </td> 
   <td> [percorso/@indirizzo2]<br /> </td> 
  </tr> 
  <tr> 
   <td> Indirizzo 3 (numero e via)<br /> </td> 
   <td> [location/@address3]<br /> </td> 
  </tr> 
  <tr> 
   <td> Indirizzo 4 (contea)<br /> </td> 
   <td> [percorso/@indirizzo4]<br /> </td> 
  </tr> 
  <tr> 
   <td> CAP<br /> </td> 
   <td> [location/@zipCode]<br /> </td> 
  </tr> 
  <tr> 
   <td> Città<br /> </td> 
   <td> [location/@city]<br /> </td> 
  </tr> 
  <tr> 
   <td> Codice stato/provincia<br /> </td> 
   <td> [location/@stateCode]<br /> </td> 
  </tr> 
  <tr> 
   <td> Codice paese<br /> </td> 
   <td> [location/@countryCode]<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Conversione diritti {#rights-conversion}

I diritti vengono gestiti in modo diverso in Campaign v7 e Campaign Standard. In Campaign v7, la gestione dei diritti è basata su cartelle, mentre in Campaign Standard è basata sull&#39;accesso unitario (unità organizzative/geografiche). Un utente Campaign Standard appartiene al gruppo di sicurezza che contiene il contesto della restrizione. Pertanto, il sistema di diritti Campaign v7 deve essere convertito in modo che corrisponda a quello Campaign Standard. Esistono diversi modi per eseguire la conversione dei diritti. Di seguito è riportato un esempio di implementazione.

1. In **[!UICONTROL Administration > ACS Connector > Rights management > Security groups]**, utilizzare il pulsante **[!UICONTROL Synchronize]** per recuperare tutti i gruppi di sicurezza Campaign Standard. I gruppi di Campaign Standard forniti sono esclusi.

   ![](assets/acs_connect_implementation_4.png)

1. Se la gestione dei diritti è basata su cartelle, andate a **[!UICONTROL Administration > ACS Connector > Rights management > Folder mapping]** e mappate ogni cartella necessaria con un gruppo di sicurezza.

   ![](assets/acs_connect_implementation_5.png)

1. I flussi di lavoro di replica utilizzeranno queste informazioni e aggiungeranno le unità organizzative/geografiche corrispondenti a ciascun oggetto da replicare.

### Implementazione avanzata {#advanced-implementation}

Questa sezione descrive alcune delle possibilità in termini di implementazione avanzata.

>[!IMPORTANT]
>
>Queste informazioni possono essere utilizzate solo come linee guida generali. Rivolgiti al tuo consulente Adobe Campaign  per l&#39;implementazione.

L&#39;implementazione avanzata aggiunge flussi di lavoro di replica personalizzati, a seconda delle esigenze del cliente. Di seguito sono riportati alcuni esempi:

* Replica distribuzione
* Replica delle campagne
* Replica del programma
* Replica dei membri del seme
* Replica transazionale
* ecc.

**Replica dei campi estesi sui destinatari**

Con l&#39;implementazione di base, i campi dei destinatari out-of-the-box vengono replicati. Se si desidera replicare i campi personalizzati aggiunti allo schema del destinatario, è necessario identificarli.

1. In **[!UICONTROL Administration > ACS Connector > Data mapping]**, create una mappatura di targeting sulla tabella **[!UICONTROL nms:recipient]**.

   ![](assets/acs_connect_implementation_6.png)

1. Selezionate i campi aggiuntivi da replicare e altre informazioni necessarie (indice, collegamenti, chiavi di identificazione).

   ![](assets/acs_connect_implementation_7.png)

1. Aprite il flusso di lavoro dedicato per la replica del profilo (non il modello, ma l’istanza del flusso di lavoro). Modificare le attività **[!UICONTROL Query]** e **[!UICONTROL Update data]** per includere questi campi. Vedere [Flussi di lavoro tecnici e di replica](#technical-and-replication-workflows).

   ![](assets/acs_connect_implementation_8.png)

   ![](assets/acs_connect_implementation_9.png)

**Replica di tabelle di profilo personalizzate**

Con l&#39;implementazione di base, la tabella dei destinatari out-of-the-box viene replicata. Se hai aggiunto tabelle di destinatari personalizzate, ecco come le identifichi.

1. In **[!UICONTROL Administration > ACS Connector > Data mapping]**, create una mappatura di targeting sulla tabella del profilo personalizzato.

   ![](assets/acs_connect_implementation_10.png)

1. Definire i dati di identificazione, l&#39;indice, i collegamenti e i campi da replicare.

   ![](assets/acs_connect_implementation_10.png)

1. Se la gestione dei diritti è basata su cartelle, andate a **[!UICONTROL Administration > ACS Connector > Rights management > Folder mapping]** e definite un gruppo di sicurezza per le cartelle collegate alle tabelle personalizzate. Vedere [Conversione diritti](#rights-conversion).
1. Utilizzate il flusso di lavoro **[!UICONTROL New replication]** (non il modello, ma l&#39;istanza del flusso di lavoro) per includere la tabella personalizzata e i campi da replicare. Vedere [Flussi di lavoro tecnici e di replica](#technical-and-replication-workflows).

