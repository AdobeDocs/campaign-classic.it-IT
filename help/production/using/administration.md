---
solution: Campaign Classic
product: campaign
title: Administration
description: Amministrazione
audience: production
content-type: reference
topic-tags: production-procedures
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 1%

---


# Administration{#administration}

Avvio automatico dei moduli Adobe Campaign  (**web**, **mta**, **wfserver** ecc.) è fornito dal server **nlserver**.

L&#39;installazione  Adobe Campaign configura automaticamente il computer in modo che il servizio **nlserver** venga avviato durante la sequenza di avvio.

I seguenti comandi vengono utilizzati per avviare e arrestare manualmente il servizio Adobe Campaign :

* In Windows:

   * **net start nlserver6**
   * **net stop nlserver6**

* In Linux (come root):

   * **/etc/init.d di avvio/nlserver6**
   * **/etc/init.d/nlserver6 stop**

>[!NOTE]
>
>A partire da 20.1, si consiglia di utilizzare il seguente comando (per Linux): **sistema avviare il server** / **sistema arrestare il server**

Di seguito è riportato un elenco dei comandi di amministrazione standard accessibili in Linux (come **Adobe Campaign**):

* Visualizza tutti  moduli Adobe Campaign avviati: **/etc/init.d/nlserver6 pdump** o **/etc/init.d/nlserver6 status**

   >[!NOTE]
   >
   >L&#39;aggiunta del parametro **-who** al comando **pdump** consente di raccogliere informazioni sulle connessioni correnti (utenti e processi).\
   >Il comando **/etc/init.d/nlserver6 status** (senza il parametro &quot;-who&quot;) restituirà:
   >
   >    * 0 se tutti i processi sono in esecuzione.
   >    * 1 se manca un processo.
   >    * 2 se non viene eseguito alcun processo.
   >    * un altro valore in caso di errore.


* Avviare/arrestare un modulo di istanza multipla o mono (**web**, **trackinglogd**, **syslogd**, **mta**, **wfserver**, **inmail&lt;a1/>):**

   **nlserver start`<module>[@<instance>]`**

   **nlserver stop`<module>[@<instance>][-immediate][-noconsole]`**

   Per riavviare un modulo è inoltre possibile utilizzare il comando **riavvio del server`<module>[@<instance>]`**.

   Esempio:

   **web di avvio del server**

   **avvio nlserver mta@my_instance**

   **slogan di arresto del server nlserver**

   **arresto del server nlserver wfserver@my_instance**

   **nlserver stop web - immediate**

   **riavvio Web**

   >[!NOTE]
   > 
   >    * Se l&#39;istanza non è specificata, verrà utilizzata l&#39;istanza &quot;predefinita&quot;.
   >    * In caso di emergenza, utilizzare l&#39;opzione **-immediate** per interrompere immediatamente il processo (equivalente al comando Unix **kill -9**).
   >    * Utilizzate l&#39;opzione **-noconsole** per fare in modo che il modulo avviato non visualizzi nulla sulla console. I registri verranno scritti sul disco tramite il modulo **syslogd**.
   >    * Utilizzate l&#39;opzione **-verbose** per visualizzare informazioni aggiuntive sulle azioni del processo.

      >    
      >      
      Esempio:
      >    
      >      
      **nlserver riavvio web -verbose**
      >    
      >      
      **nlserver start mta@myinstance -verbose**
      >    
      >      
      Questa opzione aggiunge altri registri. È consigliabile riavviare i processi senza l&#39;opzione **-verbose** una volta trovate le informazioni desiderate, per evitare di sovraccaricare i registri.


* Avviare tutti  processi Adobe Campaign (equivalente all&#39;avvio del servizio **nlserver6**):

   **nlserver watchdog -noconsole**

* Arrestare tutti  processi Adobe Campaign (equivalente alla chiusura del servizio **nlserver6**):

   **arresto di nlserver**

* Ricaricare la configurazione del modulo **server Web** (e il modulo di estensione del server Web, se applicabile) quando i file **serverConf.xml** e **config-`<instance>  .xml </instance>`** sono stati modificati.

   **nlserver config -reload**

   >[!NOTE]
   >
   >Alcune modifiche alla configurazione non vengono prese in considerazione in modo dinamico;  Adobe Campaign deve essere chiuso e riavviato.

