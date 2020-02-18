---
title: Amministrazione
seo-title: Amministrazione
description: Amministrazione
seo-description: null
page-status-flag: never-activated
uuid: 376efec1-1647-43b4-b72f-2603214c7cc6
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: 860be8be-f28c-4836-b4fb-e91c6a4616c6
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 3801665574d0cdc9c0caf46fb2f0eede38f1b2cc

---


# Amministrazione{#administration}

Avvio automatico dei moduli di Adobe Campaign (**Web**, **mta**, **wfserver**, ecc.) è fornito dal server **nlserver** .

L&#39;installazione di Adobe Campaign configura automaticamente il computer in modo che il servizio **nlserver** venga avviato durante la sequenza di avvio.

I seguenti comandi vengono utilizzati per avviare e arrestare manualmente il servizio Adobe Campaign:

* In Windows:

   * **net start nlserver6**
   * **net stop nlserver6**

* In Linux (come root):

   * **/etc/init.d di avvio/nlserver6**
   * **/etc/init.d/nlserver6 stop**

>[!NOTE]
>
>A partire da 20.1, si consiglia di utilizzare il seguente comando (per Linux): avvio **di sistema nlserver** / arresto di **sistema nlserver**

Di seguito è riportato un elenco dei comandi di amministrazione consueti accessibili in Linux (come **Adobe Campaign**):

* Visualizza tutti i moduli Adobe Campaign avviati: **/etc/init.d/nlserver6 pdump** o stato **/etc/init.d/nlserver6**

   >[!NOTE]
   >
   >L&#39;aggiunta del parametro **-who** al comando **pdump** consente di raccogliere informazioni sulle connessioni correnti (utenti e processi).\
   >Il comando di stato **** /etc/init.d/nlserver6 (senza il parametro &quot;-who&quot;) restituisce:
   >
   >    * 0 se tutti i processi vengono eseguiti.
   >    * 1 se manca un processo.
   >    * 2 se non viene eseguito alcun processo.
   >    * un altro valore in caso di errore.


* Avviate/interrompete un modulo con istanza multipla o mono (**Web**, **trackinglogd**, **syslogd**, **mta**, **wfserver******, inmail):

   **nlserver start`<module>[@<instance>]`**

   **nlserver stop`<module>[@<instance>][-immediate][-noconsole]`**

   È inoltre possibile utilizzare il **comando di riavvio`<module>[@<instance>]`**del server per riavviare un modulo.

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
   >    * In caso di emergenza, utilizzare l&#39;opzione **-immediate** per forzare l&#39;arresto immediato del processo (equivalente al comando Unix **kill -9**).
   >    * Utilizzate l&#39;opzione **-noconsole** per fare in modo che il modulo avviato non visualizzi nulla sulla console. I registri verranno scritti sul disco tramite il modulo **syslogd** .
   >    * Utilizzate l&#39;opzione **dettagliata** per visualizzare informazioni aggiuntive sulle azioni del processo.
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
      Questa opzione aggiunge altri registri. Si consiglia di riavviare i processi senza l&#39;opzione **dettagliata** una volta trovate le informazioni desiderate, per evitare di sovraccaricare i registri.


* Avvia tutti i processi di Adobe Campaign (equivalente all&#39;avvio del servizio **nlserver6** ):

   **nlserver watchdog -noconsole**

* Chiudi tutti i processi di Adobe Campaign (equivalente alla chiusura del servizio **nlserver6** ):

   **arresto di nlserver**

* Ricaricare la configurazione del modulo Web **del** server nlserver (e il modulo di estensione del server Web, se applicabile) quando i file **serverConf.xml** e **config-`<instance>  .xml </instance>`**sono stati modificati.

   **nlserver config -reload**

   >[!NOTE]
   >
   >Alcune modifiche alla configurazione non vengono prese in considerazione in modo dinamico; Adobe Campaign deve essere arrestato e riavviato.

