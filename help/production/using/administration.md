---
product: campaign
title: Amministrazione
description: Amministrazione
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 12a255fe-66f9-40ce-b19e-c24322c2e009
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 1%

---

# Amministrazione{#administration}

Avvio automatico dei moduli Adobe Campaign (**web**, **mta**, **wfserver**, ecc.) è fornito dal server **nlserver** .

L&#39;installazione di Adobe Campaign configura automaticamente il computer in modo che il servizio **nlserver** si avvii durante la sequenza di avvio.

I seguenti comandi vengono utilizzati per avviare e arrestare manualmente il servizio Adobe Campaign:

* In Windows:

   * **net start nlserver6**
   * **net stop nlserver6**

* In Linux (come root):

   * **/etc/init.d/nlserver6 start**
   * **/etc/init.d/nlserver6 stop**

>[!NOTE]
>
>A partire da 20.1, si consiglia di utilizzare invece il seguente comando (per Linux): **systemctl start nlserver** / **systemctl stop nlserver**

Ecco un elenco dei consueti comandi di amministrazione accessibili in Linux (come **Adobe Campaign**):

* Visualizza tutti i moduli Adobe Campaign avviati: **/etc/init.d/nlserver6 pdump** o **/etc/init.d/nlserver6 status**

   >[!NOTE]
   >
   >L&#39;aggiunta del parametro **-who** al comando **pdump** consente di raccogliere informazioni sulle connessioni correnti (utenti e processi).\
   >Il comando **/etc/init.d/nlserver6 status** (senza il parametro &quot;-who&quot;) restituirà:
   >
   >    * 0 se tutti i processi vengono eseguiti.
   >    * 1 se manca un processo.
   >    * 2 se non viene eseguito alcun processo.
   >    * un altro valore in caso di errore.


* Avviare/interrompere un modulo di istanza multipla o mono-istanza (**web**, **trackinglogd**, **syslogd**, **mta**, **wfserver**, **inmail**):

   **avvio nlserver`<module>[@<instance>]`**

   **arresto del server`<module>[@<instance>][-immediate][-noconsole]`**

   È inoltre possibile utilizzare il comando **nlserver riavvio`<module>[@<instance>]`** per riavviare un modulo.

   Esempio:

   **web di avvio nlserver**

   **avvio server mta@my_instance**

   **slogan di arresto del server nlserver**

   **arresto del server wfserver@my_instance**

   **nlserver stop web -immediate**

   **nlserver riavvio Web**

   >[!NOTE]
   >
   >* Se l’istanza non è specificata, verrà utilizzata l’istanza &quot;predefinita&quot;.
   >* In caso di emergenza, utilizza l&#39;opzione **-immediate** per forzare un arresto immediato del processo (equivalente al comando Unix **kill -9**).
   >* Utilizza l&#39;opzione **-noconsole** per assicurarti che il modulo avviato non visualizzi nulla sulla console. I registri verranno scritti sul disco tramite il modulo **syslogd**.
   >* Utilizza l&#39;opzione **-verbose** per visualizzare informazioni aggiuntive sulle azioni del processo.

      >
      >   
      Esempio:
      >
      >   
      **nlserver riavvio web -verbose**
      >
      >   
      **avvio nlserver mta@myinstance -verbose**
      >
      >   
      Questa opzione aggiunge altri registri. È consigliabile riavviare i processi senza l&#39;opzione **-verbose** una volta trovate le informazioni desiderate, per evitare di sovraccaricare i registri.


* Avvia tutti i processi Adobe Campaign (equivalente all&#39;avvio del servizio **nlserver6** ):

   **nlserver watchdog -noconsole**

* Spegni tutti i processi Adobe Campaign (equivalente all&#39;arresto del servizio **nlserver6** ):

   **chiusura nlserver**

* Ricarica la configurazione del modulo **nlserver web** (e il modulo di estensione del server web, se applicabile) quando i file **serverConf.xml** e **config-`<instance>  .xml </instance>`** sono stati modificati.

   **nlserver config -reload**

   >[!NOTE]
   >
   >Alcune modifiche di configurazione non vengono prese in considerazione in modo dinamico; Adobe Campaign deve essere arrestato e riavviato.
