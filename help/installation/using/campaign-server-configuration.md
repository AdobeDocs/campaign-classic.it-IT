---
solution: Campaign Classic
product: campaign
title: Configurazione del server Campaign
description: Configurazione del server Campaign
audience: installation
content-type: reference
topic-tags: initial-configuration
translation-type: tm+mt
source-git-commit: 95d0686c4ddeb4e25eb918ca92cbd6a0b1aa1f3c
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 2%

---


# Configurazione del server Campaign{#campaign-server-configuration}

Le sezioni seguenti descrivono le configurazioni server obbligatorie che garantiranno il funzionamento efficiente di Adobe Campaign per la maggior parte delle configurazioni.

Configurazioni aggiuntive sono disponibili in [Configurazione del server Campaign](../../installation/using/configuring-campaign-server.md).

>[!NOTE]
>
>Le configurazioni lato server possono essere eseguite solo per Adobe per le distribuzioni ospitate da Adobe. Per ulteriori informazioni sulle diverse implementazioni, consulta la sezione [Modelli di hosting](../../installation/using/hosting-models.md) o [la matrice delle funzionalità](../../installation/using/capability-matrix.md).

## Identificatore interno {#internal-identifier}

L&#39;identificatore **internal** è un login tecnico da utilizzare a scopo di installazione, amministrazione e manutenzione. Questo accesso non è associato a un&#39;istanza.

Gli operatori connessi che utilizzano questo accesso disporranno di tutti i diritti su tutte le istanze. Questo accesso non avrà una password nel caso di una nuova installazione. È necessario definire manualmente questa password.

Usa il comando seguente:

```
nlserver config -internalpassword
```

Vengono quindi visualizzate le seguenti informazioni. Immetti e conferma la password:

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

I file di configurazione vengono memorizzati nella cartella **conf** della cartella di installazione di Adobe Campaign. La configurazione viene suddivisa in due file:

* **`config-<instance>.xml`** (dove  **** istanza è il nome dell’istanza): configurazione specifica dell’istanza. Se condividi il server tra più istanze, inserisci i parametri specifici di ciascuna istanza nel relativo file.
* **serverConf.xml**: configurazione generale per tutte le istanze. Questo file combina i parametri tecnici del server Adobe Campaign: sono condivisi da tutte le istanze. La descrizione di alcuni di questi parametri è illustrata di seguito. Fai riferimento al file stesso per visualizzare tutti i parametri disponibili. I diversi nodi e parametri ed elencati in questa [sezione](../../installation/using/the-server-configuration-file.md).

È possibile configurare la directory di archiviazione (**var** directory) dei dati di Adobe Campaign (registri, download, reindirizzamenti, ecc.). A questo scopo, utilizza la variabile di sistema **XTK_VAR_DIR**:

* In Windows, indicare il seguente valore nella variabile di sistema **XTK_VAR_DIR**

   ```
   D:\log\AdobeCampaign
   ```

* In Linux, vai al file **customer.sh** e indica: **esporta XTK_VAR_DIR=/app/log/AdobeCampaign**.

   Per ulteriori informazioni, consulta [Personalizzare i parametri](../../installation/using/installing-packages-with-linux.md#personalizing-parameters).

## Abilita processi {#enabling-processes}

I processi Adobe Campaign sul server sono abilitati (e disabilitati) tramite i file **config-default.xml** e **`config-<instance>.xml`** .

Per applicare le modifiche a questi file, se si avvia il servizio Adobe Campaign, è necessario eseguire il comando **nlserver config -reload** .

Esistono due tipi di processi: istanza multipla e singola.

* **istanza** multipla: viene avviato un singolo processo per tutte le istanze. Questo è il caso dei processi **web**, **syslogd** e **trackinglogd**.

   L&#39;abilitazione può essere configurata dal file **config-default.xml** .

   Dichiarazione di un server Adobe Campaign per accedere alle console client e per il reindirizzamento (tracciamento):

   ```
   vi nl6/conf/config-default.xml
   <web args="-tomcat" autoStart="true"/>  
   <!-- to start if the machine is also a redirection server -->  
   <trackinglogd autoStart="true"/>
   ```

   In questo esempio, il file viene modificato utilizzando un comando **vi** in Linux. Può essere modificato utilizzando qualsiasi editor **.txt** o **.xml**.

* **mono-istanza**: viene avviato un processo per ogni istanza (moduli:  **mta**,  **wfserver**,  **inMail**,  **** smsabbia  **stat**).

   L’abilitazione può essere configurata utilizzando il file di configurazione dell’istanza:

   ```
   config-<instance>.xml
   ```

   Dichiarazione di un server per la consegna, esecuzione delle istanze del flusso di lavoro e recupero della posta non recapitata:

   ```
   <mta autoStart="true" statServerAddress="localhost"/>
   <wfserver autoStart="true"/>  
   <inMail autoStart="true"/>
   <stat autoStart="true"/>
   ```

## Impostazioni di consegna {#delivery-settings}

I parametri di consegna devono essere configurati nella cartella **serverConf.xml** .

* **Configurazione** DNS: specifica il dominio di consegna e gli indirizzi IP (o host) dei server DNS utilizzati per rispondere alle query DNS di tipo MX effettuate dal modulo MTA a  **`<dnsconfig>`** partire da .

   >[!NOTE]
   >
   >Il parametro **nameServers** è essenziale per un&#39;installazione in Windows. Per un&#39;installazione in Linux, deve essere lasciata vuota.

   ```
   <dnsConfig localDomain="domain.com" nameServers="192.0.0.1,192.0.0.2"/>
   ```

Gli altri parametri di consegna disponibili in questo file sono descritti in [Personalizzare i parametri di consegna](../../installation/using/configuring-campaign-server.md#personalizing-delivery-parameters).

Consulta anche [Consegna e-mail](../../installation/using/email-deliverability.md).
