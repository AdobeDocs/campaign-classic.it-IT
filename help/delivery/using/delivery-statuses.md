---
solution: Campaign Classic
product: campaign
title: Stati di consegna
description: Ulteriori informazioni sugli stati disponibili nel dashboard di distribuzione.
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
translation-type: tm+mt
source-git-commit: de0e4555d3e2c5dff8d86a22ff4db85953105db1
workflow-type: tm+mt
source-wordcount: '592'
ht-degree: 2%

---


# Stati di consegna {#delivery-statuses}

<!--ajouter intro 

ajouter screenshot -->

Una volta inviata la consegna, il dashboard di distribuzione visualizza uno stato che consente di controllare se l&#39;invio è andato a buon fine. Gli stati possibili sono descritti nella sezione seguente.

![](assets/delivery-status.png)

Per ulteriori dettagli sui diversi errori di consegna riscontrabili e su come risolverli, fare riferimento a [questa pagina](../../delivery/using/understanding-delivery-failures.md).

**Argomenti correlati:**

* [Pannello consegna](../../delivery/using/delivery-dashboard.md)
* [Risoluzione dei problemi di consegna](../../delivery/using/delivery-troubleshooting.md)
* [Informazioni sul recapito messaggi](../../delivery/using/about-deliverability.md)

## Elenco di stati di consegna {#list-delivery-statuses}

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
   <td> La consegna non è stata inviata al destinatario a causa di un errore con il suo indirizzo. Era elenco Bloccati, in quarantena, non fornito o un duplicato. <br /> </td> 
  </tr> 
  <tr> 
   <td> Operazione non riuscita<br /> </td> 
   <td> Impossibile contattare il destinatario a causa di un indirizzo non valido o di una inbox completa, ad esempio. Può anche essere collegato a un problema con i blocchi di personalizzazione, in quanto possono generare errori quando gli schemi non corrispondono alla mappatura della distribuzione. Vedere <a href="../../delivery/using/understanding-delivery-failures.md" target="_blank">Informazioni sugli errori di consegna</a><br /> </td> 
  </tr>
  <tr> 
   <td> In sospeso<br /> </td> 
   <td> La consegna è pronta per essere inviata e verrà elaborata dal server di consegna (MTA). Vedere <a href="#pending-status" target="_blank">Stato in sospeso</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> Non applicabile<br /> </td> 
   <td> La consegna è stata presa in considerazione dal server (MTA) ma non elaborata.<br /> </td> 
  </tr>  
  <tr> 
   <td> Consegna annullata<br /> </td> 
   <td> La consegna è stata annullata da un operatore.<br /> </td> 
  </tr> 
  <tr> 
   <td> Preso in considerazione dal fornitore di servizi<br /> </td> 
   <td> Il provider di servizi SMS ha ricevuto la consegna.<br /> </td> 
  </tr> 
  <tr> 
   <td> Ricevuto su dispositivo mobile<br /> </td> 
   <td> Il destinatario ha ricevuto l'SMS sul proprio dispositivo mobile.<br /> </td> 
  </tr>
  <tr> 
   <td> Inviato al provider di servizi<br /> </td> 
   <td> La consegna è stata inviata al provider di servizi SMS ma non ancora ricevuta.<br />
   </td> 
  </tr> 
  <tr> 
   <td> Preparato<br /> </td> 
   <td> Stato intermedio utilizzato solo per connettori esterni come il canale mobile. Segue lo stato "In sospeso" ed è il connettore esterno che determinerà lo stato seguente.<br /> </td> 
  </tr> 
 </tbody> 
</table>

Per informazioni su come ottimizzare la recapito dei messaggi e-mail di  Adobe Campaign, consultare  guida alle best practice di recapito di Adobe Campaign [e [questa pagina](../../delivery/using/about-deliverability.md).](../../delivery/using/deliverability-key-points.md)

## Stato in sospeso {#pending-status}

Dopo aver confermato la consegna, potete vedere che lo stato della consegna è **[!UICONTROL Pending]**. Questo stato significa che il processo di esecuzione è in attesa della disponibilità di alcune risorse.

Lo stato **[!UICONTROL Pending]** può innanzitutto indicare che la consegna è stata pianificata ed è in sospeso fino alla data specificata. Per ulteriori informazioni, consultare la sezione [Pianificazione consegna](../../delivery/using/steps-sending-the-delivery.md#scheduling-the-delivery-sending).

Se la consegna non viene inviata e il suo stato rimane **[!UICONTROL Pending]**, può essere il risultato di:

* L&#39;agente MTA (Message Transfert Agent), che esegue moduli e processi sul server di consegna e che gestisce l&#39;invio di e-mail, potrebbe non essere stato avviato o deve essere riavviato.

   Per controllare questo e avviare il modulo, se necessario, eseguire i seguenti passaggi:

   >[!NOTE]
   >
   >Questa operazione può essere eseguita con un modello di hosting **locale** o **ibrido** con accesso al server Campaign (vedere [modelli di hosting](../../installation/using/hosting-models.md)).

   1. Verificate che i moduli `mta@<instance>` siano avviati sui server MTA.

      ```
      nlserver pdump
      HH:MM:SS > Application server for Adobe Campaign Classic (X.Y.Z YY.R build nnnn@SHA1) of DD/MM/YYYY
      [...]
      mta@<INSTANCENAME> (9268) - 23.0 Mb
      [...]
      ```

   1. Se l&#39;MTA non è elencato, avviarlo con il seguente comando:

      ```
      nlserver start mta@<INSTANCENAME>
      ```

      >[!NOTE]
      >
      >Sostituire `<INSTANCENAME>` con il nome dell&#39;istanza (produzione, sviluppo, ecc.). Il nome dell’istanza viene identificato tramite i file di configurazione: `[path of application]nl6/conf/config-<INSTANCENAME>.xml`

* La consegna potrebbe utilizzare un&#39;affinità non configurata sul server di invio.

   In questo caso, controllate la configurazione della gestione del traffico (affinità IP) e utilizzate il campo **[!UICONTROL Managing affinities with IP addresses]** per collegare le consegne all&#39;MTA che gestisce l&#39;affinità. Per ulteriori informazioni sulle affinità, fare riferimento a [questa sezione](../../installation/using/configuring-campaign-server.md#personalizing-delivery-parameters).

* Se sono in esecuzione troppe campagne, lo stato di consegna rimane in sospeso.

   Il limite di campagne simultanee è definito nell&#39;opzione **[!UICONTROL NmsOperation_LimitConcurrency]**. Il valore predefinito è 10.

   Ulteriori informazioni sulle opzioni in [questa pagina](../../installation/using/configuring-campaign-options.md).


**Argomenti correlati:**

* [Registri di consegna e cronologia](#delivery-logs-and-history)
* [Informazioni sugli errori di consegna](../../delivery/using/understanding-delivery-failures.md)
* [Tipi e motivi di errori di consegna](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)
