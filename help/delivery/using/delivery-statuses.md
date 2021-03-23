---
solution: Campaign Classic
product: campaign
title: Stati di consegna
description: Ulteriori informazioni sugli stati disponibili nel dashboard di consegna.
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
translation-type: tm+mt
source-git-commit: 8bf1b5b1a6763cf933d86f2af61b2bb68e870222
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 3%

---


# Stati di consegna {#delivery-statuses}

<!--ajouter intro 

ajouter screenshot -->

Una volta inviata la consegna, il dashboard di consegna visualizza uno stato che ti consente di monitorare se l’invio è andato a buon fine. Gli stati possibili sono descritti in dettaglio nella sezione seguente.

![](assets/delivery-status.png)

Per ulteriori dettagli sui diversi errori di consegna riscontrabili e su come risolverli, consulta [questa pagina](../../delivery/using/understanding-delivery-failures.md).

**Argomenti correlati:**

* [Dashboard delle consegne](../../delivery/using/delivery-dashboard.md)
* [Risoluzione dei problemi relativi alle consegne](../../delivery/using/delivery-troubleshooting.md)
* [Informazioni sul recapito messaggi](../../delivery/using/about-deliverability.md)

## Elenco degli stati di consegna {#list-delivery-statuses}

<table> 
 <thead> 
  <tr> 
   <th> Status<br /> </th> 
   <th> Definizioni e soluzioni<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Inviato<br /> </td> 
   <td> La consegna è stata inviata correttamente al provider del messaggio (ma il destinatario non l'ha necessariamente ricevuta).<br /> </td> 
  </tr> 
  <tr> 
   <td> Ignorato<br /> </td> 
   <td> La consegna non è stata inviata al destinatario a causa di un errore con il suo indirizzo. Era elenco Bloccati, messo in quarantena, non fornito o un duplicato. <br /> </td> 
  </tr> 
  <tr> 
   <td> Non riuscito<br /> </td> 
   <td> Impossibile raggiungere il destinatario a causa di un indirizzo non valido o di una casella in entrata completa, ad esempio. Può anche essere collegato a un problema relativo ai blocchi di personalizzazione, in quanto possono generare errori quando gli schemi non corrispondono alla mappatura della consegna. Consulta <a href="../../delivery/using/understanding-delivery-failures.md" target="_blank">Informazioni sugli errori di consegna</a><br /> </td> 
  </tr>
  <tr> 
   <td> Pending<br /> </td> 
   <td> La consegna è pronta per essere inviata e verrà elaborata dal server di consegna (MTA). Vedere <a href="#pending-status" target="_blank">Stato in sospeso</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> Non applicabile<br /> </td> 
   <td> La consegna è stata presa in considerazione dal server (MTA) ma non è stata elaborata.<br /> </td> 
  </tr>  
  <tr> 
   <td> Consegna annullata<br /> </td> 
   <td> La consegna è stata annullata da un operatore.<br /> </td> 
  </tr> 
  <tr> 
   <td> Preso in considerazione dal fornitore di servizi<br /> </td> 
   <td> Il provider di servizi SMS ha ricevuto la consegna.<br /> Per le installazioni in hosting o ibride, se hai effettuato l’aggiornamento all’MTA  <a href="../../delivery/using/sending-with-enhanced-mta.md" target="_blank">avanzato</a>, il messaggio è stato inoltrato correttamente da Campaign all’MTA avanzato.</td> 
  </tr> 
  <tr> 
   <td> Ricevuto su mobile<br /> </td> 
   <td> Il destinatario ha ricevuto l'SMS sul proprio dispositivo mobile.<br /> </td> 
  </tr>
  <tr> 
   <td> Inviato al provider di servizi<br /> </td> 
   <td> La consegna è stata inviata al provider di servizi SMS ma non è ancora stata ricevuta.<br />
   </td> 
  </tr> 
  <tr> 
   <td> Preparato<br /> </td> 
   <td> Stato intermedio utilizzato solo per connettori esterni, come il canale mobile. Segue lo stato "In sospeso" ed è il connettore esterno che determinerà il seguente stato.<br /> </td> 
  </tr> 
 </tbody> 
</table>

Per scoprire come ottimizzare il recapito messaggi delle e-mail di Adobe Campaign, consulta [questa sezione](../../delivery/using/about-deliverability.md). Per informazioni più approfondite sul recapito messaggi, consulta la [Guida alle best practice per il recapito messaggi di Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html).

## Stato in sospeso {#pending-status}

Dopo aver confermato la consegna, puoi vedere che lo stato della consegna è **[!UICONTROL Pending]**. Questo stato significa che il processo di esecuzione è in attesa della disponibilità di alcune risorse.

Lo stato **[!UICONTROL Pending]** può prima indicare che la consegna è stata pianificata ed è in sospeso fino alla data specificata. Per ulteriori informazioni, consulta la sezione [Pianificazione delle consegne](../../delivery/using/steps-sending-the-delivery.md#scheduling-the-delivery-sending) .

Se la consegna non viene inviata e il suo stato rimane **[!UICONTROL Pending]**, può essere il risultato di:

* MTA (Message Transfer Agent), che esegue moduli e processi sul server di consegna e che gestisce l’invio di e-mail, potrebbe non essere stato avviato o deve essere riavviato.

   Per verificare questo e per avviare il modulo, se necessario, esegui i seguenti passaggi:

   >[!NOTE]
   >
   >Questa operazione può essere eseguita con un modello di hosting **on-premise** o **ibrido** con accesso al server Campaign (vedi [modelli di hosting](../../installation/using/hosting-models.md)).

   1. Verifica che i moduli `mta@<instance>` siano lanciati sui server MTA.

      ```
      nlserver pdump
      HH:MM:SS > Application server for Adobe Campaign Classic (X.Y.Z YY.R build nnnn@SHA1) of DD/MM/YYYY
      [...]
      mta@<INSTANCENAME> (9268) - 23.0 Mb
      [...]
      ```

   1. Se l’MTA non è presente nell’elenco, avvialo con il seguente comando:

      ```
      nlserver start mta@<INSTANCENAME>
      ```

      >[!NOTE]
      >
      >Sostituisci `<INSTANCENAME>` con il nome della tua istanza (produzione, sviluppo, ecc.). Il nome dell’istanza viene identificato tramite i file di configurazione: `[path of application]nl6/conf/config-<INSTANCENAME>.xml`

* La consegna potrebbe utilizzare un’affinità non configurata sul server di invio.

   In questo caso, controlla la configurazione della gestione del traffico (affinità IP) e utilizza il campo **[!UICONTROL Managing affinities with IP addresses]** per collegare le consegne all’MTA che gestisce l’affinità. Per ulteriori informazioni sulle affinità, consulta [questa sezione](../../installation/using/configuring-campaign-server.md#personalizing-delivery-parameters).

* Quando sono in esecuzione troppe campagne, lo stato di consegna rimane in sospeso.

   Il limite di campagne simultanee è definito nell’opzione **[!UICONTROL NmsOperation_LimitConcurrency]** . Il valore predefinito è 10.

   Ulteriori informazioni sulle opzioni in [questa pagina](../../installation/using/configuring-campaign-options.md).


**Argomenti correlati:**

* [Log di consegna e cronologia](#delivery-logs-and-history)
* [Informazioni sugli errori di consegna](../../delivery/using/understanding-delivery-failures.md)
* [Tipi e motivi di errori di consegna](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)
