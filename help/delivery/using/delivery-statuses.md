---
product: campaign
title: Stati di consegna
description: Ulteriori informazioni sugli stati disponibili nel dashboard di consegna
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Monitoring, Deliverability
exl-id: 0663257a-3a70-4e0c-bbeb-8242aaa0876d
source-git-commit: 4b13e310fcee9ba24e83b697fca57bc494505642
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 8%

---

# Stati di consegna {#delivery-statuses}



<!--ajouter intro 

ajouter screenshot -->

Una volta inviata la consegna, il dashboard di consegna visualizza uno stato che ti consente di monitorare se l’invio ha avuto esito positivo. Gli stati possibili sono descritti in dettaglio nella sezione seguente.

![](assets/delivery-status.png)

Per ulteriori dettagli sui diversi errori di consegna riscontrabili e su come risolverli, consulta [questa pagina](understanding-delivery-failures.md).

**Argomenti correlati:**

* [Dashboard delle consegne](delivery-dashboard.md)
* [Risoluzione dei problemi nelle consegne](delivery-troubleshooting.md)
* [Introduzione al recapito messaggi](about-deliverability.md)

## Elenco degli stati di consegna {#list-delivery-statuses}

<table> 
 <thead> 
  <tr> 
   <th> Stato<br /> </th> 
   <th> Definizioni e soluzioni<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Inviato<br /> </td> 
   <td> La consegna è stata inviata correttamente al provider del messaggio (ma il destinatario non l’ha necessariamente ricevuta).<br /> </td> 
  </tr> 
  <tr> 
   <td> Ignorato<br /> </td> 
   <td> La consegna non è stata inviata al destinatario a causa di un errore con il relativo indirizzo. Era elenco Bloccati, messo in quarantena, non fornito o un duplicato. <br /> </td> 
  </tr> 
  <tr> 
   <td> Operazione non riuscita<br /> </td> 
   <td> Impossibile raggiungere il destinatario a causa di un indirizzo non valido o di una casella in entrata completa, ad esempio. Può anche essere collegato a un problema relativo ai blocchi di personalizzazione, in quanto possono generare errori quando gli schemi non corrispondono alla mappatura della consegna. Vedi <a href="understanding-delivery-failures.md" target="_blank">Informazioni sugli errori di consegna</a><br /> </td> 
  </tr>
  <tr> 
   <td> In sospeso<br /> </td> 
   <td> La consegna è pronta per essere inviata e verrà elaborata dal server di consegna (MTA). Vedi <a href="#pending-status" target="_blank">Stato in sospeso</a>.<br /> </td> 
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
   <td> Considerato dal fornitore di servizi<br /> </td> 
   <td> Il provider di servizi SMS ha ricevuto la consegna.<br /> Per le installazioni in hosting o ibride, se hai effettuato l’aggiornamento al <a href="sending-with-enhanced-mta.md" target="_blank">MTA avanzato</a>, il messaggio è stato inviato correttamente da Campaign all’MTA avanzato.</td> 
  </tr> 
  <tr> 
   <td> Ricevuto su dispositivo mobile<br /> </td> 
   <td> Il destinatario ha ricevuto l’SMS sul proprio dispositivo mobile.<br /> </td> 
  </tr>
  <tr> 
   <td> Inviato al fornitore di servizi<br /> </td> 
   <td> La consegna è stata inviata al provider di servizi SMS ma non è ancora stata ricevuta.<br />
   </td> 
  </tr> 
  <tr> 
   <td> Preparato<br /> </td> 
   <td> Stato intermedio utilizzato solo per connettori esterni, come il canale mobile. Segue lo stato "In sospeso" ed è il connettore esterno che determinerà lo stato seguente.<br /> </td> 
  </tr> 
 </tbody> 
</table>

Per scoprire come ottimizzare il recapito messaggi delle e-mail di Adobe Campaign, consulta [questa sezione](about-deliverability.md). Per informazioni più approfondite sul recapito messaggi, consulta [Guida alle best practice per il recapito messaggi di Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=it).

## Stato in sospeso {#pending-status}

Dopo aver confermato la consegna, puoi vedere che lo stato della consegna è **[!UICONTROL Pending]**. Questo stato significa che il processo di esecuzione è in attesa della disponibilità di alcune risorse.

La **[!UICONTROL Pending]** lo stato può prima significare che la consegna è stata pianificata ed è in sospeso fino alla data specificata. Per ulteriori informazioni, consulta la sezione [Pianificazione delle consegne](steps-sending-the-delivery.md#scheduling-the-delivery-sending) sezione .

Se la consegna non viene inviata e il suo stato rimane **[!UICONTROL Pending]**, può essere il risultato di:

* L’MTA (Agente di trasferimento messaggi), che esegue moduli e processi sul server di consegna e gestisce l’invio di e-mail, potrebbe non essere stato avviato o potrebbe essere necessario riavviare.

   Per verificare questo e per avviare il modulo, se necessario, esegui i seguenti passaggi:

   >[!NOTE]
   >
   >Questa operazione può essere eseguita con un **on-premise** o **ibrido** modello di hosting con accesso al server Campaign (vedi [modelli di hosting](../../installation/using/hosting-models.md)).

   1. Controlla che la tua `mta@<instance>` i moduli vengono lanciati sui server MTA.

      ```
      nlserver pdump
      HH:MM:SS > Application server for Adobe Campaign Classic (X.Y.Z YY.R build nnnn@SHA1) of DD/MM/YYYY
      [...]
      mta@<instance-name> (9268) - 23.0 Mb
      [...]
      ```

   1. Se l’MTA non è presente nell’elenco, avvialo con il seguente comando:

      ```
      nlserver start mta@<instance-name>
      ```

      >[!NOTE]
      >
      >Sostituisci `<instance-name>` con il nome della tua istanza (produzione, sviluppo, ecc.). Il nome dell’istanza viene identificato tramite i file di configurazione: `[path of application]nl6/conf/config-<instance-name>.xml`

* La consegna potrebbe utilizzare un’affinità non configurata sul server di invio.

   In questo caso, controlla la configurazione della gestione del traffico (affinità IP) e utilizza il **[!UICONTROL Managing affinities with IP addresses]** per collegare le consegne all’MTA che gestisce l’affinità. Per ulteriori informazioni sulle affinità, consulta [questa sezione](../../installation/using/configure-delivery-settings.md).

* Quando sono in esecuzione troppe campagne, lo stato di consegna rimane in sospeso.

   Il limite di campagne simultanee è definito nella **[!UICONTROL NmsOperation_LimitConcurrency]** opzione . Il valore predefinito è 10.

   Ulteriori informazioni sulle opzioni in [questa pagina](../../installation/using/configuring-campaign-options.md).


**Argomenti correlati:**

* [Log di consegna e cronologia](#delivery-logs-and-history)
* [Informazioni sugli errori di consegna](understanding-delivery-failures.md)
* [Tipi e motivi di errori di consegna](understanding-delivery-failures.md#delivery-failure-types-and-reasons)
