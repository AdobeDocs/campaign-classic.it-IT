---
product: campaign
title: Amministrazione
description: Amministrazione
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 12a255fe-66f9-40ce-b19e-c24322c2e009
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 1%

---

# Amministrazione{#administration}



Avvio automatico dei moduli Adobe Campaign (**web**, **mta**, **wfserver**, ecc.) è fornito da **nlserver** server.

L’installazione di Adobe Campaign configura automaticamente il computer in modo che il **nlserver** il servizio viene avviato durante la sequenza di avvio.

I seguenti comandi vengono utilizzati per avviare e arrestare manualmente il servizio Adobe Campaign:

* In Windows:

   * **net start nlserver6**
   * **net stop nlserver6**

* In Linux (come root):

   * **/etc/init.d/nlserver6 start**
   * **/etc/init.d/nlserver6 stop**

>[!NOTE]
>
>A partire da 20.1, si consiglia di utilizzare invece il seguente comando (per Linux): **system start nlserver** / **system stop nlserver**

Ecco un elenco dei consueti comandi di amministrazione accessibili in Linux (come **Adobe Campaign**):

* Visualizza tutti i moduli Adobe Campaign avviati: **/etc/init.d/nlserver6 pdump** o **/etc/init.d/nlserver6 status**

   >[!NOTE]
   >
   >Aggiunta di **-chi** al **scampo** consente di raccogliere informazioni sulle connessioni correnti (utenti e processi).\
   >La **/etc/init.d/nlserver6 status** (senza il parametro &quot;-who&quot;) restituirà:
   >
   >    * 0 se tutti i processi vengono eseguiti.
   >    * 1 se manca un processo.
   >    * 2 se non viene eseguito alcun processo.
   >    * un altro valore in caso di errore.


* Avviare/interrompere un modulo di istanza multipla o mono-istanza (**web**, **trackinglogd**, **syslogd**, **mta**, **wfserver**, **posta indesiderata**):

   **avvio nlserver`<module>[@<instance>]`**

   **arresto del server`<module>[@<instance>][-immediate][-noconsole]`**

   È inoltre possibile utilizzare **riavvio del server`<module>[@<instance>]`** per riavviare un modulo.

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
   >* In caso di emergenza, utilizza il **-immediate** opzione per interrompere immediatamente il processo (equivalente al comando Unix) **kill-9**).
   >* Utilizza la **-noconsole** per garantire che il modulo avviato non venga visualizzato nella console. I registri verranno scritti sul disco tramite il **syslogd** modulo .
   >* Utilizza la **-verboso** per visualizzare informazioni aggiuntive sulle azioni del processo.

      >
      >   Esempio:
      >
      >   **nlserver riavvio web -verbose**
      >
      >   **avvio nlserver mta@myinstance -verbose**
      >
      >   Questa opzione aggiunge altri registri. È consigliabile riavviare i processi senza **-verboso** una volta trovate le informazioni desiderate, per evitare di sovraccaricare i log.


* Avvia tutti i processi Adobe Campaign (equivalente all’avvio del **nlserver6** servizio):

   **nlserver watchdog -noconsole**

* Arresta tutti i processi Adobe Campaign (equivalente all’arresto del **nlserver6** servizio):

   **chiusura nlserver**

* Ricarica il **web nlserver** la configurazione del modulo (e il modulo di estensione del server web, se applicabile) quando **serverConf.xml** e **config-`<instance>  .xml </instance>`** i file sono stati modificati.

   **nlserver config -reload**

   >[!NOTE]
   >
   >Alcune modifiche di configurazione non vengono prese in considerazione in modo dinamico; Adobe Campaign deve essere arrestato e riavviato.
