---
solution: Campaign Classic
product: campaign
title: Configurazione del server Campaign
description: Configurazione del server Campaign
audience: installation
content-type: reference
topic-tags: initial-configuration
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 2%

---


# Configurazione del server Campaign{#campaign-server-configuration}

Nelle sezioni seguenti sono descritte le configurazioni server obbligatorie che garantiscono il funzionamento efficiente di  Adobe Campaign per la maggior parte delle configurazioni.

Configurazioni aggiuntive sono disponibili in [Configurazione del server](../../installation/using/configuring-campaign-server.md)Campaign.

>[!NOTE]
>
>Le configurazioni lato server possono essere eseguite solo da  Adobe per le distribuzioni ospitate da  Adobe. Per ulteriori informazioni sulle diverse distribuzioni, fare riferimento alla sezione Modelli [di](../../installation/using/hosting-models.md) hosting o alla matrice [](../../installation/using/capability-matrix.md)delle funzionalità.

## Identificatore interno {#internal-identifier}

L’identificatore **interno** è un login tecnico da utilizzare per l’installazione, l’amministrazione e la manutenzione. Questo login non è associato a un&#39;istanza.

Gli operatori connessi con questo login avranno tutti i diritti su tutte le istanze. Questo login non avrà una password nel caso di una nuova installazione. È necessario definire manualmente questa password.

Usa il comando seguente:

```
nlserver config -internalpassword
```

Vengono quindi visualizzate le informazioni seguenti. Immettete e confermate la password:

```
17:33:57 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
Enter the current password.
Password:
Enter the new password.
Password: XXXX
Confirmation: XXXX
17:34:02 >   Password successfully changed for account 'internal' (authentication mode 'nl')
```

## File di configurazione {#configuration-files}

I file di configurazione sono memorizzati nella cartella **conf** della cartella di installazione  Adobe Campaign. La configurazione è suddivisa in due file:

* **`config-<instance>.xml`** (dove **instance** è il nome dell’istanza): specifica configurazione dell&#39;istanza. Se condividete il server tra più istanze, inserite i parametri specifici per ciascuna istanza nel relativo file.
* **serverConf.xml**: configurazione generale per tutte le istanze. Questo file combina i parametri tecnici del server Adobe Campaign : vengono condivisi da tutte le istanze. La descrizione di alcuni di questi parametri è dettagliata di seguito. Fare riferimento al file stesso per visualizzare tutti i parametri disponibili. I diversi nodi e parametri ed elencati in questa [sezione](../../installation/using/the-server-configuration-file.md).

È possibile configurare la directory di memorizzazione (**var** directory) di  dati Adobe Campaign (registri, download, reindirizzamenti, ecc.). A questo scopo, utilizzate la variabile di sistema **XTK_VAR_DIR** :

* In Windows, indicare il seguente valore nella variabile di sistema **XTK_VAR_DIR** :

   ```
   D:\log\AdobeCampaign
   ```

* In Linux, andate al file **customer.sh** e indicate: **esporta XTK_VAR_DIR=/app/log/AdobeCampaign**.

   For more on this, refer to [Personalizing parameters](../../installation/using/installing-packages-with-linux.md#personalizing-parameters).

## Abilitazione dei processi {#enabling-processes}

 processi Adobe Campaign sul server sono attivati (e disabilitati) tramite **config-default.xml** e **`config-<instance>.xml`** file.

Per applicare le modifiche a questi file, se il servizio Adobe Campaign  è avviato, è necessario eseguire il comando **nlserver config -reload** .

Esistono due tipi di processi: istanza multipla e istanza singola.

* **istanza** multipla: viene avviato un singolo processo per tutte le istanze. Questo è il caso dei processi **Web**, **syslogd** e **tracking** .

   L&#39;abilitazione può essere configurata dal file **config-default.xml** .

   Dichiarazione di un server Adobe Campaign  per accedere alle console client e per il reindirizzamento (tracciamento):

   ```
   vi nl6/conf/config-default.xml
   <web args="-tomcat" autoStart="true"/>  
   <!-- to start if the machine is also a redirection server -->  
   <trackinglogd autoStart="true"/>
   ```

   In questo esempio, il file viene modificato utilizzando un comando **vi** in Linux. Può essere modificato utilizzando qualsiasi editor **.txt** o **.xml** .

* **mono-instance**: viene avviato un processo per ogni istanza (moduli: **mta**, **wfserver**, **inMail**, **sms** e **stat**).

   L&#39;abilitazione può essere configurata utilizzando il file di configurazione dell&#39;istanza:

   ```
   config-<instance>.xml
   ```

   Dichiarazione di un server per la distribuzione, esecuzione di istanze del flusso di lavoro e recupero di messaggi di rimbalzo:

   ```
   <mta autoStart="true" statServerAddress="localhost"/>
   <wfserver autoStart="true"/>  
   <inMail autoStart="true"/>
   <stat autoStart="true"/>
   ```

## Impostazioni di consegna {#delivery-settings}

I parametri di consegna devono essere configurati nella cartella **serverConf.xml** .

* **Configurazione** DNS: specificare il dominio di consegna e gli indirizzi IP (o host) dei server DNS utilizzati per rispondere alle query DNS di tipo MX effettuate dal modulo MTA a **`<dnsconfig>`** partire da.

   >[!NOTE]
   >
   >Il parametro **nameServers** è essenziale per un&#39;installazione in Windows. Per un&#39;installazione in Linux, deve essere lasciata vuota.

   ```
   <dnsConfig localDomain="domain.com" nameServers="192.0.0.1,192.0.0.2"/>
   ```

Gli altri parametri di consegna disponibili in questo file sono presentati in [Personalizzazione dei parametri](../../installation/using/configuring-campaign-server.md#personalizing-delivery-parameters)di consegna.

Fate anche riferimento alla recapito [e-mail](../../installation/using/email-deliverability.md).
