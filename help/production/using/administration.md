---
product: campaign
title: Amministrazione
description: Amministrazione
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
badge-v7-prem: label="on-premise e ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 12a255fe-66f9-40ce-b19e-c24322c2e009
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 3%

---

# Amministrazione{#administration}



Avvio automatico dei moduli di Adobe Campaign (**web**, **mta**, **wfserver**, ecc.) è fornito da **nlserver** server.

L’installazione di Adobe Campaign configura automaticamente il computer in modo che **nlserver** il servizio viene avviato durante la sequenza di avvio.

I seguenti comandi vengono utilizzati per avviare e arrestare manualmente il servizio Adobe Campaign:

* In Windows:

   * **net start nlserver6**
   * **net stop nlserver6**

* In Linux (come radice):

   * **/etc/init.d/nlserver6 start**
   * **/etc/init.d/nlserver6 stop**

>[!NOTE]
>
>A partire dalla versione 20.1, si consiglia invece di utilizzare il seguente comando (per Linux): **systemctl start nlserver** / **systemctl stop nlserver**

Di seguito è riportato un elenco dei normali comandi di amministrazione accessibili in Linux (come **Adobe Campaign**):

* Visualizza tutti i moduli Adobe Campaign avviati: **/etc/init.d/nlserver6** o **Stato /etc/init.d/nlserver6**

  >[!NOTE]
  >
  >Aggiunta di **-chi** parametro per **pdump** consente di raccogliere informazioni sulle connessioni correnti (utenti e processi).\
  >Il **Stato /etc/init.d/nlserver6** (senza il parametro &quot;-who&quot;) restituirà:
  >
  >    * 0 se tutti i processi sono in esecuzione.
  >    * 1 se manca un processo.
  >    * 2 se non viene eseguito alcun processo.
  >    * un altro valore in caso di errore.
  >

* Avviare/arrestare un modulo a più istanze o mono istanze (**web**, **trackinglogd**, **syslogd**, **mta**, **wfserver**, **posta in arrivo**):

  **nlserver start`<module>[@<instance>]`**

  **nlserver stop`<module>[@<instance>][-immediate][-noconsole]`**

  È inoltre possibile utilizzare **riavvio nlserver`<module>[@<instance>]`** comando per riavviare un modulo.

  Esempio:

  **nlserver start web**

  **avvio nlserver mta@my_instance**

  **nlserver stop syslogd**

  **nlserver stop wfserver@my_instance**

  **nlserver stop web -immediate**

  **nlserver riavvia Web**

  >[!NOTE]
  >
  >* Se l’istanza non è specificata, verrà utilizzata l’istanza &quot;predefinita&quot;.
  >* In caso di emergenza, utilizzare **-immediate** opzione per forzare un&#39;interruzione immediata del processo (equivalente al comando Unix **kill -9**).
  >* Utilizza il **-noconsole** per garantire che il modulo avviato non venga visualizzato nella console. I registri verranno scritti sul disco tramite **syslogd** modulo.
  >* Utilizza il **-verboso** per visualizzare informazioni aggiuntive sulle azioni del processo.
  >
  >   Esempio:
  >
  >   **nlserver restart web -verbose**
  >
  >   **nlserver start mta@myinstance -verbose**
  >
  >   Questa opzione consente di aggiungere altri registri. È consigliabile riavviare i processi senza **-verboso** dopo aver trovato le informazioni desiderate, per evitare di sovraccaricare i registri.

* Avvia tutti i processi di Adobe Campaign (equivalente all&#39;avvio del **nlserver6** service):

  **watchdog nlserver - noconsole**

* Arresta tutti i processi di Adobe Campaign (equivalente alla chiusura del **nlserver6** service):

  **Arresto nlserver**

* Ricarica **nlserver web** (e il modulo di estensione del server web, se applicabile) quando **serverConf.xml** e **config-`<instance>  .xml </instance>`** i file sono stati modificati.

  **nlserver config -ricarica**

  >[!NOTE]
  >
  >Alcune modifiche alla configurazione non vengono prese in considerazione in modo dinamico; Adobe Campaign deve essere arrestato e quindi riavviato.
