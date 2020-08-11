---
title: Monitoraggio di una consegna
seo-title: Monitoraggio di una consegna
description: Monitoraggio di una consegna
seo-description: null
page-status-flag: never-activated
uuid: 7cb409eb-a01c-4b4d-bb62-760e0bafdc8a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
discoiquuid: 3aab3d47-76fd-4c68-add4-9c14240c936e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: bc54cef4c44be4c694e062f56685dbb09d2fcf8e
workflow-type: tm+mt
source-wordcount: '2567'
ht-degree: 2%

---


# Monitoraggio di una consegna{#monitoring-a-delivery}

Il dashboard **di** distribuzione è fondamentale per monitorare le consegne e gli eventuali problemi riscontrati durante l&#39;invio dei messaggi.

**Argomenti correlati:**

* [Informazioni sugli errori di consegna](../../delivery/using/understanding-delivery-failures.md)
* [Informazioni sulla gestione della quarantena](../../delivery/using/understanding-quarantine-management.md)
* [Best practice di distribuzione](../../delivery/using/delivery-best-practices.md)
* [Gestione delle consegne](../../delivery/using/about-deliverability.md)

## Pannello consegna {#delivery-dashboard}

Per visualizzare le informazioni su una consegna, modificatela, visualizzate il dashboard e fate clic sulle schede disponibili.

Il contenuto della scheda potrebbe non essere più modificato dopo l&#39;invio.

![](assets/s_ncs_user_del_details.png)

### Riepilogo consegne {#delivery-summary}

La **[!UICONTROL Summary]** scheda contiene le caratteristiche della consegna: stato di consegna, canale utilizzato, informazioni sul mittente, oggetto, informazioni sull&#39;esecuzione. Per ulteriori informazioni, vedere [Numero di messaggi inviati](#number-of-messages-sent).

Il **[!UICONTROL reports]** collegamento consente di esaminare una serie di rapporti relativi all’azione di consegna: rapporto sulla consegna generale, rapporto dettagliato, rapporto sulla consegna, distribuzione di messaggi non riusciti, tasso di apertura, clic e transazioni, ecc. Il contenuto di questa scheda può essere configurato in base alle tue esigenze. Per ulteriori informazioni, consulta [questa sezione](../../reporting/using/delivery-reports.md).

### Registri di consegna e cronologia {#delivery-logs-and-history}

La **[!UICONTROL Delivery]** scheda fornisce una cronologia delle occorrenze della consegna. Contiene i registri di consegna, ovvero l’elenco dei messaggi inviati e il relativo stato e i messaggi associati.

Per una consegna, è possibile visualizzare (ad esempio) solo i destinatari con una consegna non riuscita o un indirizzo in quarantena. A tale scopo, fare clic sul **[!UICONTROL Filters]** pulsante e selezionare **[!UICONTROL By state]**. Selezionate quindi lo stato nell’elenco a discesa.

![](assets/s_ncs_user_delivery_delivery_tab.png)

Diversi stati sono elencati in [questa pagina](#delivery-statuses).

>[!NOTE]
>
>Il **[!UICONTROL Display the mirror page for this message...]** collegamento consente di visualizzare in una nuova finestra la pagina mirror relativa al contenuto della consegna selezionata dall&#39;elenco. La pagina mirror è disponibile solo per le consegne per le quali è stato definito il contenuto HTML. Per ulteriori informazioni, vedere [Generazione della pagina](../../delivery/using/sending-messages.md#generating-the-mirror-page)mirror.

### Tracking logs {#tracking-logs}

La **[!UICONTROL Tracking]** scheda elenca la cronologia di tracciamento per la consegna. In questa scheda vengono visualizzati i dati di tracciamento dei messaggi inviati, ovvero tutti gli URL soggetti al tracciamento da parte  Adobe Campaign. I dati di tracciamento vengono aggiornati ogni ora.

>[!NOTE]
>
>Se il tracciamento non è abilitato per una consegna, questa scheda non viene visualizzata.

La configurazione del tracciamento viene eseguita nella fase appropriata della procedura guidata di consegna. Vedere [Come configurare i collegamenti](../../delivery/using/how-to-configure-tracked-links.md)tracciati.

**[!UICONTROL Tracking]** i dati vengono interpretati nei rapporti di consegna. Vedi [questa sezione](../../reporting/using/delivery-reports.md).

![](assets/s_ncs_user_delivery_tracking_tab.png)

### Controllo della consegna {#delivery-audit-}

La **[!UICONTROL Audit]** scheda contiene il registro di consegna e tutti i messaggi relativi alle prove. Il **[!UICONTROL Refresh]** pulsante consente di aggiornare i dati. Utilizzare il **[!UICONTROL Filters]** pulsante per definire un filtro per i dati.

Le icone speciali consentono di identificare errori o avvisi. Consultate [Analisi della consegna](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery).

La **[!UICONTROL Proofs]** sottoscheda consente di visualizzare l&#39;elenco delle prove che sono state inviate.

![](assets/s_ncs_user_delivery_log_tab.png)

È possibile modificare le informazioni visualizzate in questa finestra (e in quella delle **[!UICONTROL Delivery]** e **[!UICONTROL Tracking]** schede) selezionando le colonne da visualizzare. A tale scopo, fate clic sull’ **[!UICONTROL Configure list]** icona situata nell’angolo inferiore destro. Per ulteriori informazioni sulla configurazione della visualizzazione degli elenchi, consultare [questa sezione](../../platform/using/adobe-campaign-workspace.md#configuring-lists).

### Sincronizzazione dashboard di distribuzione {#delivery-dashboard-synchronization}

Dal dashboard di distribuzione, è necessario controllare i messaggi elaborati e i registri di consegna per verificare che la consegna sia stata inviata correttamente.

Alcuni indicatori o lo stato possono essere errati o non aggiornati. Questo problema può essere risolto con le seguenti soluzioni:

* Se lo stato di consegna non è corretto, verifica che siano state effettuate tutte le approvazioni necessarie per la consegna oppure che i flussi di lavoro **[!UICONTROL operationMgt]** e **[!UICONTROL deliveryMgt]** di lavoro siano in esecuzione senza errori. Ciò può anche essere dovuto al recapito tramite un&#39;affinità non configurata nell&#39;istanza di invio.
* Se gli indicatori di consegna sono ancora pari a zero e se siete in una configurazione mid-sourcing, controllate il flusso di lavoro **[!UICONTROL Mid-sourcing (delivery counters)]** tecnico. Avviatelo se il suo stato non è **[!UICONTROL Started]**. Potete quindi provare a calcolare gli indicatori facendo clic con il pulsante destro del mouse sulla distribuzione desiderata in  Adobe Campaign Explorer e selezionando **[!UICONTROL Actions]** > **[!UICONTROL Recompute delivery and tracking indicators]**. For more information on tracking indicators, refer to this [section](../../reporting/using/delivery-reports.md#tracking-indicators).
* Se il contatore di distribuzione non corrisponde alla consegna, provare a calcolare gli indicatori facendo clic con il pulsante destro del mouse sulla consegna desiderata in  Adobe Campaign Explorer e selezionando **[!UICONTROL Actions]** > **[!UICONTROL Recompute delivery and tracking indicators]** per eseguire nuovamente la sincronizzazione. For more information on tracking indicators, refer to this [section](../../reporting/using/delivery-reports.md#tracking-indicators).
* Se il contatore di distribuzione non è aggiornato per le distribuzioni di mid-sourcing, verificare che il flusso di lavoro **[!UICONTROL Mid-Sourcing (Delivery counters)]** tecnico sia in esecuzione. Per ulteriori informazioni, consulta questa [pagina](../../installation/using/mid-sourcing-deployment.md).

Puoi anche tenere traccia delle consegne con diversi rapporti tramite la dashboard di distribuzione. Per ulteriori informazioni, consulta questa [sezione](../../reporting/using/delivery-reports.md).

## Problemi di prestazioni {#performance-issues}

### Elenco di controllo {#checklist-}

Se le prestazioni di consegna sono sbagliate, è possibile controllare:

* **Dimensioni della consegna**: Il completamento delle consegne di grandi dimensioni può richiedere più tempo. Gli elementi figlio MTA sono configurati per gestire una dimensione batch predefinita, che funziona per la maggior parte delle istanze, ma devono essere controllati quando le consegne sono costantemente lente.
* **Destinazione della consegna**: Il divieto di prestazioni di consegna è influenzato da errori di rimbalzo soft, che vengono gestiti in base alla configurazione del nuovo tentativo. Maggiore è il numero di errori, maggiori saranno i tentativi necessari.
* **Il carico** complessivo della piattaforma: Quando vengono inviate diverse consegne di grandi dimensioni, la piattaforma globale può risentirne. È inoltre possibile controllare la reputazione dell&#39;IP e i problemi di recapito. Per ulteriori informazioni, consultare  Guida alle procedure ottimali per la [distribuzione di Adobe Campaign](../../delivery/using/deliverability-key-points.md) e consultare [questa pagina](../../delivery/using/about-deliverability.md).

La manutenzione di piattaforme e database può anche influire sulle prestazioni di invio delle consegne. For more on this, refer to [this page](../../production/using/database-performances.md).

### Consegne lente {#slow-deliveries}

Dopo aver fatto clic sul **[!UICONTROL Send]** pulsante, la consegna sembra richiedere più tempo del solito. Ciò può essere causato da diversi elementi:

* Alcuni provider di posta elettronica potrebbero aver aggiunto gli indirizzi IP a un elenco Bloccati . In questo caso, controlla i tuoi registri di trasmissione e consulta [questa sezione](../../delivery/using/about-deliverability.md).
* La consegna potrebbe essere troppo grande per essere elaborata rapidamente, questo potrebbe verificarsi con una personalizzazione JavaScript elevata o se il volume di consegna supera i 60 Kbyte. Per informazioni sulle linee guida relative ai contenuti, fare riferimento  best practice [per la](../../delivery/using/delivery-best-practices.md) distribuzione Adobe Campaign.
* Potrebbe essersi verificata una limitazione all&#39;interno della  MTA Adobe Campaign. Ciò è causato da:

   * Messaggi aperti (**[!UICONTROL quotas met]** messaggio): sono state rispettate le quote dichiarate dalle regole dichiarative MX definite in Campaign. Per ulteriori informazioni su questo messaggio, fare riferimento a [questa pagina](../../delivery/using/deliverability-faq.md) . Per ulteriori informazioni sulle regole MX, consultare [questa pagina](../../delivery/using/technical-recommendations.md#mx-rules).
   * Messaggi aperti (**[!UICONTROL dynamic flow control]** messaggio): Campaign MTA ha rilevato degli errori quando si tenta di inviare messaggi per un dato ISP che causano un rallentamento per evitare una densità di errore troppo grande e quindi affrontare il potenziale elenco Bloccati .

* Un problema del sistema può impedire ai server di interagire tra loro: questo può rallentare l&#39;intero processo di invio. Controlla i server per assicurarti che non ci siano problemi di memoria o di risorse che possano avere un impatto su Campaign, ad esempio nel processo di ottenimento dei dati di personalizzazione.

### Best practice per le prestazioni {#best-practices-performance}

* Non mantenere le consegne in stato di errore nell&#39;istanza, in quanto questo mantiene le tabelle temporanee e influisce sulle prestazioni.

* Rimuovere le consegne che non sono più necessarie.

* Destinatari inattivi negli ultimi 12 mesi da rimuovere dal database per mantenere la qualità degli indirizzi.

* Non provare a pianificare insieme consegne di grandi dimensioni. C&#39;è uno spazio di 5-10 minuti per distribuire uniformemente il carico sul sistema. Coordinate la pianificazione delle consegne con gli altri membri del team per garantire le migliori prestazioni. Quando il server di marketing gestisce contemporaneamente diverse attività, può rallentare le prestazioni.

* Mantenete le dimensioni dei vostri messaggi e-mail il più possibile ridotte. La dimensione massima consigliata per un messaggio e-mail è di circa 35 KB. La dimensione di una distribuzione di e-mail genera una certa quantità di volume nei server di invio.

* Le consegne di grandi dimensioni, come le consegne a più di un milione di destinatari, richiedono spazio nelle code di invio. Questo non è un problema per il server, ma se combinato con dozzine di altre consegne di grandi dimensioni che vanno tutte fuori allo stesso tempo, può introdurre un ritardo di invio.

* La personalizzazione nelle e-mail estrae i dati dal database per ciascun destinatario. Se sono presenti molti elementi di personalizzazione, questo aumenta la quantità di dati necessari per preparare la consegna.

* Indirizzi indice. Per ottimizzare le prestazioni delle query SQL utilizzate nell&#39;applicazione, è possibile dichiarare un indice dall&#39;elemento principale dello schema di dati.

>[!NOTE]
>
>Gli ISP disattiverebbero gli indirizzi dopo un periodo di inattività. I messaggi di rifiuto vengono inviati ai mittenti per informarli di questo nuovo stato.

## Stati di consegna {#delivery-statuses}

Durante l&#39;invio di una consegna, sul dashboard di consegna potresti avere il seguente stato:

<table> 
 <thead> 
  <tr> 
   <th> Stato<br /> </th> 
   <th> Definizioni e soluzioni<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Non applicabile<br /> </td> 
   <td> La consegna è stata presa in considerazione dal server (MTA) ma non elaborata.<br /> </td> 
  </tr> 
  <tr> 
   <td> Ignorato<br /> </td> 
   <td> La consegna non è stata inviata al destinatario a causa di un errore con il suo indirizzo. È stato aggiunto a un elenco Bloccati , messo in quarantena, non fornito o duplicato. <br /> </td> 
  </tr> 
  <tr> 
   <td> Inviato<br /> </td> 
   <td> La consegna è stata inviata correttamente al provider del messaggio (ma il destinatario non l'ha necessariamente ricevuta).<br /> </td> 
  </tr> 
  <tr> 
   <td> Operazione non riuscita<br /> </td> 
   <td> Impossibile contattare il destinatario a causa di un indirizzo non valido o di una inbox completa, ad esempio. Può anche essere collegato a un problema con i blocchi di personalizzazione, in quanto possono generare errori quando gli schemi non corrispondono alla mappatura della distribuzione. Vedere Stato <a href="#failed-status" target="_blank">non riuscito</a><br /> </td> 
  </tr> 
  <tr> 
   <td> Presa in considerazione dal fornitore di servizi<br /> </td> 
   <td> Il provider del servizio SMS ha ricevuto la consegna.<br /> </td> 
  </tr> 
  <tr> 
   <td> Ricevuto su dispositivo mobile<br /> </td> 
   <td> Il destinatario ha ricevuto l'SMS sul proprio dispositivo mobile.<br /> </td> 
  </tr> 
  <tr> 
   <td> In sospeso<br /> </td> 
   <td> La consegna è pronta per essere inviata e verrà elaborata dal server di consegna (MTA). Vedere Stato <a href="#pending-status" target="_blank"></a>in sospeso.<br /> </td> 
  </tr> 
  <tr> 
   <td> Consegna annullata<br /> </td> 
   <td> La consegna è stata annullata da un operatore.<br /> </td> 
  </tr> 
  <tr> 
   <td> Preparato<br /> </td> 
   <td> Stato intermedio utilizzato solo per connettori esterni come il canale mobile. Segue lo stato "In sospeso" ed è il connettore esterno che determinerà lo stato seguente.<br /> </td> 
  </tr> 
  <tr> 
   <td> Inviato al provider di servizi<br /> </td> 
   <td> La consegna è stata inviata al provider del servizio SMS ma non ancora ricevuta.<br /> </td> 
  </tr> 
 </tbody> 
</table>

Per informazioni su come ottimizzare la recapito dei messaggi e-mail di  Adobe Campaign, consultare  guida [alle procedure ottimali per la](../../delivery/using/deliverability-key-points.md) distribuzione di Adobe Campaign e consultare [questa pagina](../../delivery/using/about-deliverability.md).

### Stato in sospeso {#pending-status}

Dopo aver confermato la consegna, potete vedere che lo stato della consegna è **[!UICONTROL Pending]**. Questo stato significa che il processo di esecuzione è in attesa della disponibilità di alcune risorse.

Lo **[!UICONTROL Pending]** stato può innanzitutto indicare che la consegna è stata pianificata ed è in sospeso fino alla data specificata. For more on this, refer to the [Delivery scheduling](../../delivery/using/steps-sending-the-delivery.md#scheduling-the-delivery-sending) section.

Se la consegna non viene inviata e il suo stato rimane **[!UICONTROL Pending]**, può essere il risultato di:

* L&#39;agente MTA (Message Transfert Agent), che esegue moduli e processi sul server di consegna e che gestisce l&#39;invio di e-mail, potrebbe non essere stato avviato o deve essere riavviato. Per controllare questo e avviare il modulo, se necessario, eseguire i seguenti passaggi:

   * Verificate che `mta@<instance>` i moduli siano avviati sui server MTA.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Classic (X.Y.Z YY.R build nnnn@SHA1) of DD/MM/YYYY
   [...]
   mta@<INSTANCENAME> (9268) - 23.0 Mb
   [...]
   ```

   * Se l&#39;MTA non è elencato, avviarlo con il seguente comando:

   ```
   nlserver start mta@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >Sostituire `<INSTANCENAME>` con il nome dell’istanza (produzione, sviluppo, ecc.). Il nome dell’istanza viene identificato tramite i file di configurazione: `[path of application]nl6/conf/config-<INSTANCENAME>.xml`

* La consegna potrebbe utilizzare un&#39;affinità non configurata sul server di invio. In questo caso, controllate la configurazione della gestione del traffico (affinità IP) e utilizzate il **[!UICONTROL Managing affinities with IP addresses]** campo per collegare le consegne all&#39;MTA che gestisce l&#39;affinità. For more information on affinities, refer to [this section](../../installation/using/configuring-campaign-server.md#personalizing-delivery-parameters).
* Quando la preparazione della consegna è in sospeso, possono essere in esecuzione troppe campagne che hanno bloccato l&#39;aggiornamento dello stato della consegna. Per risolvere questo problema, passate a **[!UICONTROL Options]** e aumentate il valore di **[!UICONTROL NmsOperation_LimitConcurrency]** (il valore predefinito è 10). Non eseguire più campagne del valore assegnato a questa opzione specifica.

### Stato non riuscito {#failed-status}

Se lo stato di invio dell’e-mail è **[!UICONTROL Failed]**, può essere collegato a un problema relativo ai blocchi di personalizzazione. I blocchi di personalizzazione in una consegna possono generare errori se, ad esempio, gli schemi non corrispondono alla mappatura della consegna.

I registri di consegna sono la chiave per capire perché una consegna non è riuscita. Di seguito sono riportati possibili errori che è possibile rilevare dai registri di consegna:

* Se i messaggi del destinatario non riescono con un errore &quot;Non raggiungibile&quot; che indica: **Errore durante la compilazione della riga X dello script &#39;content htmlContent&#39;:`[table]`non è definito. JavaScript: durante la valutazione dello script &#39;content htmlContent**, la causa di questo problema è quasi sempre una personalizzazione all&#39;interno dell&#39;HTML che tenta di richiamare una tabella o un campo che non è stato definito o mappato nel targeting upstream o nella mappatura di destinazione della consegna.

   Per correggere questo problema, è necessario rivedere il flusso di lavoro e il contenuto di distribuzione per determinare in modo specifico quale personalizzazione sta tentando di chiamare la tabella in questione e se è possibile mappare la tabella. Da qui, la rimozione della chiamata a questa tabella nell’HTML o la correzione della mappatura alla consegna costituirebbe il percorso della risoluzione.

* Nel modello di distribuzione mid-sourcing, il messaggio seguente può essere visualizzato nei registri di distribuzione: **Errore durante la chiamata del metodo &#39;AppendDeliveryPart&#39; sul server di origine mid: &#39;Errore di comunicazione con il server: verificare che questo sia configurato correttamente. Codice HTTP 408 &#39;Servizio temporaneamente non disponibile&#39;**.

   La causa è collegata a problemi di prestazioni. Significa che l&#39;istanza di marketing impiega troppo tempo a generare dati prima di inviarli al server di mid-sourcing.

   Per risolvere questo problema, si consiglia di eseguire un vuoto e reindicizzare il database. For more information on database maintenance, refer to [this section](../../production/using/recommendations.md).

   È inoltre necessario riavviare tutti i flussi di lavoro con un&#39;attività pianificata e tutti i flussi di lavoro con stato di errore. Fai riferimento a [questa sezione](../../workflow/using/scheduler.md).

* Quando una consegna non riesce, nei registri di consegna può comparire il seguente errore: **DLV-XXXX Il numero di messaggi preparati (123) è maggiore del numero di messaggi da inviare (111). Contattare il supporto tecnico.**

   Solitamente, questo errore indica che all&#39;interno dell&#39;e-mail è presente un campo o un blocco di personalizzazione con più valori per il destinatario. Viene utilizzato un blocco di personalizzazione che raccoglie più record per un particolare destinatario.

   Per risolvere questo problema, controllate i dati di personalizzazione utilizzati, quindi verificate se nel target sono presenti più voci per i destinatari con più di una voce per ciascuno di questi campi. Potete inoltre utilizzare un&#39; **[!UICONTROL Deduplication]** attività nel flusso di lavoro di targeting prima dell&#39;attività di consegna per verificare che sia presente un solo campo di personalizzazione alla volta. For more information on deduplication, refer to [this page](../../workflow/using/deduplication.md).

* Alcune consegne potrebbero non riuscire con un errore &quot;Impossibile da raggiungere&quot; che indica: &quot;Rimbalzo e-mail in entrata (la regola &#39;Auto_answer&#39; ha trovato la stessa corrispondenza). Ciò significa che la consegna è riuscita, ma  Adobe Campaign ha ricevuto una risposta automatica dal destinatario (ad es. una risposta &quot;Fuori sede&quot;) che corrispondeva alle regole e-mail in entrata &#39;Auto_answer&#39;. L&#39;e-mail di risposta automatica viene ignorata da  Adobe Campaign e l&#39;indirizzo del destinatario non verrà inviato alle quarantena.

**Argomenti correlati:**

* [Registri di consegna e cronologia](#delivery-logs-and-history)
* [Informazioni sugli errori di consegna](../../delivery/using/understanding-delivery-failures.md)
* [Tipi e motivi di errori di consegna](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)

## Number of messages sent {#number-of-messages-sent}

È possibile accedere alle consegne dall&#39;elenco di consegna tramite il **[!UICONTROL Campaign Management > Deliveries]** nodo della struttura.

Per impostazione predefinita, l&#39;elenco delle consegne contiene i nomi e gli stati delle consegne create nel nodo selezionato. Mostra anche il numero di messaggi da inviare, elaborare e inviare con esito positivo.

* Il numero di **[!UICONTROL Messages to send]** destinatari corrisponde al numero di destinatari interessati dopo l’analisi e prima della consegna.
* Il numero di messaggi nella **[!UICONTROL Success]** colonna corrisponde al numero di messaggi inviati dal server e ricevuti dai destinatari.
* Il numero di **[!UICONTROL Processed]** messaggi corrisponde al numero di messaggi ricevuti più il numero di messaggi con errori.

Il dashboard di distribuzione consente di tenere traccia del numero di messaggi inviati.

>[!NOTE]
>
>Per le consegne di grandi dimensioni, potete aggiornare questi valori. A questo scopo, selezionate la consegna in questione e fate clic con il pulsante destro del mouse. Selezionate **[!UICONTROL Action > Recompute delivery and tracking indicators...]** e utilizzate la procedura guidata per aggiornare tali informazioni.

## Spedizioni programmate {#scheduled-deliveries-}

Se le consegne non vengono eseguite alla data pianificata esatta, è possibile che si tratti di una differenza tra il fuso orario dei server. L&#39;istanza mid-sourcing e l&#39;istanza di produzione possono essere in fusi orari diversi.

Ad esempio, se l’istanza mid-sourcing si trova nel fuso orario di Brisbane e l’istanza di produzione si trova nel fuso orario di Darwin, entrambi i fusi orari sono distanti mezz’ora, quindi nel registro di controllo si può vedere chiaramente che se la consegna è pianificata per la produzione alle 11:56, la stessa consegna prevista per metà sarà alle 12:26, con una differenza di mezz’ora.
