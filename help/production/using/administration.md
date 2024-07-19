---
product: campaign
title: Amministrazione
description: Amministrazione
feature: Monitoring
badge-v7-prem: label="Solo on-premise/ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 12a255fe-66f9-40ce-b19e-c24322c2e009
source-git-commit: b7dedddc080d1ea8db700fabc9ee03238b3706cc
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 1%

---

# Amministrazione{#administration}

Avvio automatico dei moduli di Adobe Campaign (**web**, **mta**, **wfserver**, ecc.) è fornito dal server **nlserver**.

L&#39;installazione di Adobe Campaign configura automaticamente il computer in modo che il servizio **nlserver** venga avviato durante la sequenza di avvio.

I seguenti comandi vengono utilizzati per avviare e arrestare manualmente il servizio Adobe Campaign:

* In Windows:

   * **net start nlserver6**
   * **net stop nlserver6**

* In Linux (come radice):

   * **/etc/init.d/nlserver6 start**
   * **/etc/init.d/nlserver6 stop**

>[!NOTE]
>
>A partire dalla versione 20.1, è consigliabile utilizzare il comando seguente (per Linux): **systemctl start nlserver** / **systemctl stop nlserver**

Di seguito è riportato un elenco dei normali comandi di amministrazione accessibili in Linux (come **Adobe Campaign**):

* Visualizza tutti i moduli Adobe Campaign avviati: **/etc/init.d/nlserver6 pdump** o **/etc/init.d/nlserver6 stato**

  >[!NOTE]
  >
  >L&#39;aggiunta del parametro **-who** al comando **pdump** consente di raccogliere informazioni sulle connessioni correnti (utenti e processi).\
  >Il comando **/etc/init.d/nlserver6 status** (senza il parametro &quot;-who&quot;) restituirà:
  >
  >    * 0 se tutti i processi sono in esecuzione.
  >    * 1 se manca un processo.
  >    * 2 se non viene eseguito alcun processo.
  >    * un altro valore in caso di errore.
  >

* Avvia/arresta un modulo a più istanze o a istanza mono (**web**, **trackinglogd**, **syslogd**, **mta**, **wfserver**, **inmail**):

  **nlserver start`<module>[@<instance>]`**

  **nlserver stop`<module>[@<instance>][-immediate][-noconsole]`**

  È inoltre possibile utilizzare il comando **nlserver restart`<module>[@<instance>]`** per riavviare un modulo.

  Esempio:

  **nlserver avvia Web**

  **nlserver start mta@my_instance**

  **nlserver stop syslogd**

  **nlserver stop wfserver@my_instance**

  **nlserver stop web -immediate**

  **nlserver riavvia Web**

  >[!NOTE]
  >
  >* Se l’istanza non è specificata, verrà utilizzata l’istanza &quot;predefinita&quot;.
  >* In caso di emergenza, utilizzare l&#39;opzione **-immediate** per forzare l&#39;arresto immediato del processo, equivalente al comando Unix **kill -9**.
  >* Utilizza l&#39;opzione **-noconsole** per assicurarti che il modulo avviato non visualizzi nulla nella console. I registri verranno scritti sul disco tramite il modulo **syslogd**.
  >* Utilizzare l&#39;opzione **-verbose** per visualizzare ulteriori informazioni sulle azioni del processo.
  >
  >   Esempio:
  >
  >   **nlserver riavvia Web -verbose**
  >
  >   **nlserver start mta@myinstance -verbose**
  >
  >   Questa opzione consente di aggiungere altri registri. È consigliabile riavviare i processi senza l&#39;opzione **-verbose** dopo aver trovato le informazioni desiderate, per evitare di sovraccaricare i registri.

* Avvia tutti i processi di Adobe Campaign (equivalente all&#39;avvio del servizio **nlserver6**):

  **nlserver watchdog -noconsole**

* Arresta tutti i processi Adobe Campaign (equivalente alla chiusura del servizio **nlserver6**):

  **nlserver arrestato**

* Ricarica la configurazione del modulo **nlserver web** (e il modulo di estensione del server Web, se applicabile) quando i file **serverConf.xml** e **config-`<instance>  .xml </instance>`** sono stati modificati.

  **nlserver config -reload**

  >[!NOTE]
  >
  >Alcune modifiche alla configurazione non vengono prese in considerazione in modo dinamico; Adobe Campaign deve essere arrestato e quindi riavviato.
