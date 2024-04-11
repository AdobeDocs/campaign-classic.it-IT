---
product: campaign
title: Stati di consegna
description: Ulteriori informazioni sugli stati disponibili nel dashboard di consegna
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Monitoring, Deliverability
role: User
exl-id: 0663257a-3a70-4e0c-bbeb-8242aaa0876d
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '637'
ht-degree: 3%

---

# Stati di consegna {#delivery-statuses}



<!--ajouter intro 

ajouter screenshot -->

Una volta inviata la consegna, il dashboard di consegna visualizza uno stato che consente di monitorare se l’invio è stato eseguito correttamente. I possibili stati sono descritti nella sezione seguente.

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
   <td> La consegna è stata inviata correttamente al provider di messaggi (ma il destinatario non l’ha necessariamente ricevuta).<br /> </td> 
  </tr> 
  <tr> 
   <td> Ignorato<br /> </td> 
   <td> La consegna non è stata inviata al destinatario a causa di un errore con il suo indirizzo. È stato o messo in quarantena al elenco Bloccati, non fornito o duplicato. <br /> </td> 
  </tr> 
  <tr> 
   <td> Non riuscito<br /> </td> 
   <td> La consegna non è riuscita a raggiungere il destinatario a causa, ad esempio, di un indirizzo non valido o di una casella in entrata completa. Può anche essere collegato a un problema con i blocchi di personalizzazione, in quanto possono generare errori quando gli schemi non corrispondono alla mappatura della consegna. Consulta <a href="understanding-delivery-failures.md" target="_blank">Informazioni sugli errori di consegna</a><br /> </td> 
  </tr>
  <tr> 
   <td> In sospeso<br /> </td> 
   <td> La consegna è pronta per essere inviata e verrà elaborata dal server di consegna (MTA). Consulta <a href="#pending-status" target="_blank">Stato in sospeso</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> Non applicabile<br /> </td> 
   <td> La consegna è stata considerata dal server (MTA) ma non elaborata.<br /> </td> 
  </tr>  
  <tr> 
   <td> Consegna annullata<br /> </td> 
   <td> La consegna è stata annullata da un operatore.<br /> </td> 
  </tr> 
  <tr> 
   <td> Preso in considerazione dal fornitore di servizi<br /> </td> 
   <td> Il provider del servizio SMS ha ricevuto la consegna.<br /> Per le installazioni in hosting o ibride, se hai effettuato l’aggiornamento al <a href="sending-with-enhanced-mta.md" target="_blank">MTA avanzato</a>, il messaggio è stato inoltrato correttamente da Campaign all’MTA avanzato.</td> 
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
   <td> Stato intermedio utilizzato solo per i connettori esterni, ad esempio il canale mobile. Segue lo stato "In sospeso" ed è il connettore esterno che determinerà il seguente stato.<br /> </td> 
  </tr> 
 </tbody> 
</table>

Per informazioni su come ottimizzare il recapito dei messaggi e-mail in Adobe Campaign, consulta [questa sezione](about-deliverability.md). Per informazioni più approfondite sulla consegna dei messaggi, consulta [Guida alle procedure consigliate per la consegna dei messaggi di Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=it).

## Stato in sospeso {#pending-status}

Dopo aver confermato la consegna, puoi vedere che lo stato della consegna è **[!UICONTROL Pending]**. Questo stato indica che il processo di esecuzione è in attesa della disponibilità di alcune risorse.

Il **[!UICONTROL Pending]** Lo stato può significare innanzitutto che la consegna è stata pianificata ed è in sospeso fino alla data specificata. Per ulteriori informazioni, consulta [Pianificazione della consegna](steps-sending-the-delivery.md#scheduling-the-delivery-sending) sezione.

Se la consegna non viene inviata e il suo stato rimane **[!UICONTROL Pending]**, può essere il risultato di:

* L’MTA (Message Transfer Agent), che esegue moduli e processi sul server di consegna e gestisce l’invio di e-mail, potrebbe non essere stato avviato o potrebbe essere necessario riavviarlo.

  Per verificare e avviare il modulo, se necessario, attieniti alla seguente procedura:

  >[!NOTE]
  >
  >Questa operazione può essere eseguita con un **on-premise** o **ibrido** modello di hosting con accesso al server Campaign (consulta [modelli di hosting](../../installation/using/hosting-models.md)).

   1. Verifica che `mta@<instance>` I moduli vengono avviati sui server MTA.

      ```
      nlserver pdump
      HH:MM:SS > Application server for Adobe Campaign Classic (X.Y.Z YY.R build nnnn@SHA1) of DD/MM/YYYY
      [...]
      mta@<instance-name> (9268) - 23.0 Mb
      [...]
      ```

   1. Se l’MTA non è elencato, avvialo con il seguente comando:

      ```
      nlserver start mta@<instance-name>
      ```

      >[!NOTE]
      >
      >Sostituisci `<instance-name>` con il nome dell’istanza (produzione, sviluppo, ecc.). Il nome dell’istanza viene identificato tramite i file di configurazione: `[path of application]nl6/conf/config-<instance-name>.xml`

* È possibile che la consegna utilizzi un’affinità non configurata sul server di invio.

  In questo caso, controlla la configurazione della gestione del traffico (affinità IP) e utilizza **[!UICONTROL Managing affinities with IP addresses]** campo per collegare le consegne all’MTA che gestisce l’affinità. Per ulteriori informazioni sulle affinità, consulta [questa sezione](../../installation/using/configure-delivery-settings.md).

* Quando sono in esecuzione troppe campagne, lo stato di consegna rimane &quot;In sospeso&quot;.

  Il limite delle campagne simultanee è definito nel **[!UICONTROL NmsOperation_LimitConcurrency]** opzione. Il valore predefinito è 10.

  Ulteriori informazioni sulle opzioni disponibili in [questa pagina](../../installation/using/configuring-campaign-options.md).


**Argomenti correlati:**

* [Registri e cronologia delle consegne](#delivery-logs-and-history)
* [Informazioni sugli errori di consegna](understanding-delivery-failures.md)
* [Tipi e motivi di errori di consegna](understanding-delivery-failures.md#delivery-failure-types-and-reasons)
