---
title: Configurazione dell'integrazione
seo-title: Configurazione dell'integrazione
description: Configurazione dell'integrazione
seo-description: null
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0112d5bd052ad66169225073276d1da4f3c245d8
workflow-type: tm+mt
source-wordcount: '642'
ht-degree: 0%

---


# Risoluzione dei problemi relativi alla tubazione {#pipeline-troubleshooting}

**Impossibile eseguire la tubazione con errore &quot;Nessuna attività corrisponde alla maschera tubata@&quot;**

La versione di  Adobe Campaign Classic non supporta la pipeline.

1. Verificate la presenza dell&#39; [!DNL pipelined] elemento nel file di configurazione. In caso contrario, significa che non è supportato.
1. Aggiornamento alla versione 6.11 build 8705 o successiva.

**La tubazione non riesce con &#39;&#39; aurait du commencer par &#39;[&#39; ou &#39;{&#39; (iRc=16384)&quot;**

L&#39;opzione **NmsPipeline_Config** non è impostata. In realtà è un errore di analisi JSON.
Impostate la configurazione JSON nell’opzione **NmsPipeline_Config**. Vedere &quot;opzione di routing&quot; in questa pagina.

**Pipelled non riesce con &quot;l&#39;oggetto deve essere un&#39;organizzazione o un client valido&quot;**

La configurazione IMSOrgid non è valida.

1. Verificate che IMSOrgId sia impostato in serverConf.xml.
1. Cercare un IMSOrgId vuoto nel file di configurazione dell&#39;istanza che può ignorare il valore predefinito. In tal caso, rimuoverlo.
1. Verificate che IMSOrgId corrisponda a quello del cliente nell&#39;Experience Cloud .

**Pipeline non riuscita con &quot;chiave non valida&quot;**

Il parametro @authPrivateKey del file di configurazione dell&#39;istanza non è corretto.

1. Verificare che authPrivateKey sia impostato.
1. Controlla che authPrivateKey: inizia con @, termina con =, ed è lungo circa 4000 caratteri.
1. Cercare la chiave originale e verificare che sia: in formato RSA, 4096 bit di lunghezza e inizia con —BEGIN RSA PRIVATE KEY—.
   <br> Se necessario, ricreate la chiave e registratela in Adobe  Analytics. Fare riferimento a questa [sezione](../../integrations/using/configuring-pipeline.md#oauth-client-creation).
1. Verificate che la chiave sia stata codificata all’interno della stessa istanza di [!DNL pipelined]. <br>Se necessario, ripetete la codifica utilizzando il codice JavaScript o il flusso di lavoro di esempio.

**Impossibile leggere il token durante l&#39;autenticazione**

Il formato della chiave privata non è valido.

1. Esegui i passaggi per la crittografia chiave in questa pagina.
1. Verificate che la chiave sia crittografata nella stessa istanza.
1. Verificare che authPrivateKey nel file di configurazione corrisponda alla chiave generata. <br>Assicuratevi di usare OpenSSL per generare la coppia di chiavi. PuttyGen, ad esempio, non genera il formato corretto.

**Non vengono recuperati trigger**

Quando il [!DNL pipelined] processo è in esecuzione e non vengono recuperati attivatori:

1. Assicurarsi che l&#39;attivatore sia attivo in  Analytics e stia generando eventi.
1. Verificare che il [!DNL pipelined] processo sia in esecuzione.
1. Cercare gli errori nel [!DNL pipelined] registro.
1. Cercare gli errori nella pagina di [!DNL pipelined] stato. trigger-scarted, trigger-failures dovrebbe essere zero.
1. Verificate che il nome dell&#39;attivatore sia configurato nell&#39; **[!UICONTROL NmsPipeline_Config]** opzione. In caso di dubbi, utilizzate l&#39;opzione carattere jolly.
1. Verificare che  Analytics disponga di un attivatore attivo e stia generando eventi. Potrebbe verificarsi un ritardo di alcune ore dopo che la configurazione è stata realizzata in  Analytics prima che sia attiva.

**Gli eventi non sono collegati a un cliente**

Quando alcuni eventi non sono collegati a un cliente:

1. Verificare che il flusso di lavoro di riconciliazione sia in esecuzione, se applicabile.
1. Verificate che l&#39;evento contenga un ID cliente.
1. Eseguire una query sulla tabella cliente utilizzando l&#39;ID cliente.
1. Controllare la frequenza dell&#39;importazione del cliente. I nuovi clienti vengono importati  Adobe Campaign con un flusso di lavoro.

**Latenza nell&#39;elaborazione degli eventi**

Quando la marca temporale  Analytics è molto più vecchia della data di creazione dell&#39;evento in Campaign.

Generalmente, un attivatore può richiedere 15-90 minuti per avviare una campagna di marketing. Questo varia a seconda dell&#39;implementazione della raccolta di dati, del carico sulla pipeline, della configurazione personalizzata del trigger definito e del flusso di lavoro nel Adobe Campaign .

1. Verificare se il [!DNL pipelined] processo è stato in esecuzione.
1. Cercare gli errori in pipelified.log che possono causare nuovi tentativi. Correggete gli errori, se applicabile.
1. Controllate la pagina di [!DNL pipelined] stato per conoscere la dimensione della coda. Se la dimensione della coda è grande, migliorare le prestazioni del JS.
1. Poiché un ritardo sembra aumentare con il volume, configura gli attivatori su  Analytics utilizzando meno messaggi.
Allegati

**Come utilizzare il codice JavaScript di crittografia Key**

Eseguire un JavaScript per crittografare la chiave privata. È necessaria per la configurazione della pipeline.

Di seguito è riportato un esempio di codice che è possibile utilizzare per eseguire la funzione cryptString:

```
/*
USAGE:
  nlserver javascript -instance:<instancename> -file -arg:"<private_key.pem file>" -file encryptKey.js
*/
 
function usage()
{
  return "USAGE:\n" +
    '  nlserver javascript -instance:<instancename> -file -arg:"<private_key.pem file>" -file encryptKey.js\n'
}
 
var fn = application.arg;
if( fn == "" )
  logError("Missing key file file\n" + usage());
 
//open the pem file
plaintext = loadFile(fn)
 
if( !plaintext.match(/^-----BEGIN RSA PRIVATE KEY-----/) )
  logError("File should be an rsa private key")
 
logInfo("Encrypted key:\n" + cryptString(plaintext, <xtkSecretKey>))
```

Sul server, eseguite il codice JavaScript:

```
nlserver javascript -instance:<instancename> -file -arg:"<private_key.pem file>" -file encryptKey.js
```

Copiate e incollate la chiave codificata dall’output alla console.