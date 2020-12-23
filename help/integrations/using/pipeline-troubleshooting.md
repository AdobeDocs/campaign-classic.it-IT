---
solution: Campaign Classic
product: campaign
title: Configurazione dell’integrazione
description: Configurazione dell’integrazione
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
translation-type: tm+mt
source-git-commit: 57093a687534ed1e7f77738ca233d4cc86cf40cf
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 1%

---


# Risoluzione dei problemi relativi alla pipeline {#pipeline-troubleshooting}

**Impossibile eseguire la tubazione con errore &quot;Nessuna attività corrisponde alla maschera tubata@&lt;>&quot;**

La versione di Adobe Campaign Classic non supporta la pipeline.

1. Verificate che l&#39;elemento [!DNL pipelined] sia presente nel file di configurazione. In caso contrario, significa che non è supportato.
1. Aggiornamento a Campaign 20.3 o Gold Standard 11.

**Il tubo non funziona con &#39;&#39; aurait du commencer par  `[` ou  `{` (iRc=16384)&quot;**

L&#39;opzione **NmsPipeline_Config** non è impostata. In realtà è un errore di analisi JSON.
Impostate la configurazione JSON nell&#39;opzione **NmsPipeline_Config**. Vedere &quot;opzione di routing&quot; in questa pagina.

**Pipelled non riesce con &quot;l&#39;oggetto deve essere un&#39;organizzazione o un client valido&quot;**

La configurazione dell&#39;identificatore dell&#39;organizzazione non è valida.

1. Verificate che IMSOrgId sia impostato in serverConf.xml.
1. Cercare un IMSOrgId vuoto nel file di configurazione dell&#39;istanza che può ignorare il valore predefinito. In tal caso, rimuoverlo.
1. Verificate che IMSOrgId corrisponda a quello del cliente nel Experience Cloud .

**Pipeline non riuscita con &quot;chiave non valida&quot;**

Il parametro @authPrivateKey del file di configurazione dell&#39;istanza non è corretto.

1. Verificare che authPrivateKey sia impostato.
1. Controlla che authPrivateKey: inizia con @, termina con =, ed è lungo circa 4000 caratteri.
1. Cercare la chiave originale e verificare che sia: in formato RSA, 4096 bit di lunghezza e inizia con —BEGIN RSA PRIVATE KEY—.
   <br> Se necessario, ricreate la chiave e registratela su  Adobe Analytics.
1. Verificate che la chiave sia stata codificata all&#39;interno della stessa istanza di [!DNL pipelined]. <br>Se necessario, ripetete la codifica utilizzando il codice JavaScript o il flusso di lavoro di esempio.

**Impossibile leggere il token durante l&#39;autenticazione**

Il formato della chiave privata non è valido.

1. Esegui i passaggi per la crittografia chiave in questa pagina.
1. Verificate che la chiave sia crittografata nella stessa istanza.
1. Verificare che authPrivateKey nel file di configurazione corrisponda alla chiave generata. <br>Assicuratevi di usare OpenSSL per generare la coppia di chiavi. PuttyGen, ad esempio, non genera il formato corretto.

**Non vengono recuperati trigger**

Quando il processo [!DNL pipelined] è in esecuzione e non vengono recuperati trigger:

1. Accertatevi che l&#39;attivatore sia attivo in Analytics e stia generando eventi.
1. Assicurarsi che il processo [!DNL pipelined] sia in esecuzione.
1. Cercare gli errori nel registro [!DNL pipelined].
1. Cercare gli errori nella pagina di stato [!DNL pipelined]. trigger-scarted, trigger-failures dovrebbe essere zero.
1. Verificate che il nome del trigger sia configurato nell&#39;opzione **[!UICONTROL NmsPipeline_Config]**. In caso di dubbi, utilizzate l&#39;opzione carattere jolly.
1. Verifica che Analytics disponga di un attivatore attivo e stia generando eventi. Potrebbe verificarsi un ritardo di alcune ore dopo che la configurazione è stata effettuata in Analytics prima che sia attiva.

**Gli eventi non sono collegati a un cliente**

Quando alcuni eventi non sono collegati a un cliente:

1. Verificare che il flusso di lavoro di riconciliazione sia in esecuzione, se applicabile.
1. Verificate che l&#39;evento contenga un ID cliente.
1. Eseguire una query sulla tabella cliente utilizzando l&#39;ID cliente.
1. Controllare la frequenza dell&#39;importazione del cliente. I nuovi clienti vengono importati in  Adobe Campaign con un flusso di lavoro.

**Latenza nell&#39;elaborazione degli eventi**

Quando la marca temporale di Analytics è molto più vecchia della data di creazione dell&#39;evento in Campaign.

Generalmente, un attivatore può richiedere 15-90 minuti per avviare una campagna di marketing. Questo varia a seconda dell&#39;implementazione della raccolta di dati, del caricamento sulla pipeline, della configurazione personalizzata del trigger definito e del flusso di lavoro in  Adobe Campaign.

1. Verificare che il processo [!DNL pipelined] sia in esecuzione.
1. Cercare gli errori in pipelified.log che possono causare nuovi tentativi. Correggete gli errori, se applicabile.
1. Verificare la dimensione della coda nella pagina di stato [!DNL pipelined]. Se la dimensione della coda è grande, migliorare le prestazioni del JS.
1. Poiché un ritardo sembra aumentare con il volume, configura gli attivatori in Analytics con un numero minore di messaggi.
