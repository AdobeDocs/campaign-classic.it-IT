---
product: campaign
title: Configurazione dell’integrazione
description: Configurazione dell’integrazione
audience: integrations
content-type: reference
exl-id: 76645a6f-9536-49d6-b12a-fdd6113d31fa
source-git-commit: 45a84e1bf43678bbc31d8bac15a7e6520204fdc2
workflow-type: tm+mt
source-wordcount: '647'
ht-degree: 1%

---

# Risoluzione dei problemi relativi alla pipeline {#pipeline-troubleshooting}

**Impossibile eseguire la pipeline con errore &quot;Nessun task corrisponde alla maschera tubata@&lt;>&quot;**

La versione di Adobe Campaign Classic non supporta la pipeline.

1. Controlla se l&#39;elemento [!DNL pipelined] è presente nel file di configurazione. In caso contrario, significa che non è supportato.
1. Effettua l’aggiornamento a Campaign 20.3 o [!DNL Gold Standard] 11.

**Il tubo non riesce con &#39;&#39; aurait du comencer par  `[` ou  `{` (iRc=16384)&quot;**

L&#39;opzione **NmsPipeline_Config** non è impostata. In realtà è un errore di analisi JSON.
Imposta la configurazione JSON nell&#39;opzione **NmsPipeline_Config**. Vedi &quot;opzione di routing&quot; in questa pagina.

**Impossibile eseguire la pipeline con &quot;l&#39;oggetto deve essere un&#39;organizzazione o un client valido&quot;**

La configurazione dell&#39;identificatore dell&#39;organizzazione non è valida.

1. Verifica che IMSOrgId sia impostato nel serverConf.xml.
1. Cerca un IMSOrgId vuoto nel file di configurazione dell’istanza che può ignorare il valore predefinito. In tal caso, rimuovila.
1. Verifica che IMSOrgId corrisponda a quello del cliente nell’Experience Cloud .

**Errore della pipeline con &quot;chiave non valida&quot;**

Il parametro @authPrivateKey del file di configurazione dell&#39;istanza non è corretto.

1. Verifica che authPrivateKey sia impostato.
1. Controlla che authPrivateKey: inizia con @, termina con =, ed è lungo circa 4000 caratteri.
1. Cerca la chiave originale e controlla che sia: in formato RSA, lunghi 4096 bit e inizia con —BEGIN RSA PRIVATE KEY—.
   <br> Se necessario, ricreate la chiave e registratela su Adobe Analytics.
1. Verifica che la chiave sia stata codificata all’interno della stessa istanza di [!DNL pipelined]. <br>Se necessario, ripristina la codifica utilizzando il JavaScript o il flusso di lavoro di esempio.

**Impossibile leggere il token durante l&#39;autenticazione**

Formato della chiave privata non valido.

1. Esegui i passaggi per la crittografia chiave in questa pagina.
1. Verifica che la chiave sia crittografata nella stessa istanza.
1. Verifica che authPrivateKey nel file di configurazione corrisponda alla chiave generata. <br>Assicurati di utilizzare OpenSSL per generare la coppia di chiavi. PuttyGen, ad esempio, non genera il formato corretto.

**Nessun trigger recuperato**

Quando il processo [!DNL pipelined] è in esecuzione e non vengono recuperati trigger:

1. Assicurati che il trigger sia attivo in Analytics e stia generando eventi.
1. Assicurati che il processo [!DNL pipelined] sia in esecuzione.
1. Cerca gli errori nel registro [!DNL pipelined].
1. Cerca gli errori nella pagina di stato [!DNL pipelined]. trigger-scarted, trigger-failed dovrebbe essere zero.
1. Verifica che il nome del trigger sia configurato nell’opzione **[!UICONTROL NmsPipeline_Config]** . In caso di dubbi, utilizza l’opzione carattere jolly .
1. Controlla che Analytics abbia un trigger attivo e stia generando eventi. Potrebbe verificarsi un ritardo di alcune ore dopo che la configurazione viene effettuata in Analytics prima che sia attiva.

**Gli eventi non sono collegati a un cliente**

Quando alcuni eventi non sono collegati a un cliente:

1. Verifica che il flusso di lavoro di riconciliazione sia in esecuzione, se applicabile.
1. Verifica che l&#39;evento contenga un ID cliente.
1. Esegui una query sulla tabella cliente utilizzando l’ID cliente.
1. Controlla la frequenza dell’importazione del cliente. I nuovi clienti vengono importati in Adobe Campaign con un flusso di lavoro.

**Latenza nell’elaborazione degli eventi**

Quando la marca temporale di Analytics è molto più vecchia della data di creazione dell’evento in Campaign.

In genere, un trigger può richiedere 15-90 minuti per avviare una campagna di marketing. Questo varia a seconda dell’implementazione della raccolta di dati, del caricamento sulla pipeline, della configurazione personalizzata del trigger definito e del flusso di lavoro in Adobe Campaign.

1. Controlla se il processo [!DNL pipelined] è in esecuzione.
1. Cerca gli errori in pipelined.log che possono causare nuovi tentativi. Correggi gli errori, se applicabile.
1. Controlla la pagina di stato [!DNL pipelined] per le dimensioni della coda. Se le dimensioni della coda sono grandi, migliora le prestazioni del JS.
1. Poiché un ritardo sembra aumentare con il volume, configura gli attivatori su Analytics utilizzando meno messaggi.

**Aggiornamento delle istanze dell’area di visualizzazione dall’autenticazione legacy all’autenticazione I/O di Adobe**

La modifica dell’autenticazione dell’integrazione nell’istanza di stage non influisce sulla configurazione dell’istanza di produzione. È possibile scegliere di aggiornare l&#39;istanza di stage, quindi aggiornare l&#39;autenticazione per Adobe IO e testare i trigger sull&#39;istanza di stage.

L’istanza di produzione continuerà a utilizzare l’autenticazione legacy e non sarà interessata da questa modifica.
