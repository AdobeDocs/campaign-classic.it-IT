---
product: campaign
title: Risoluzione dei problemi relativi alla pipeline
description: Risoluzione dei problemi relativi alla pipeline
feature: Triggers
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
audience: integrations
content-type: reference
exl-id: 76645a6f-9536-49d6-b12a-fdd6113d31fa
TQID: https://experienceleague.adobe.com/CRFuACW6lPivyn8-BuA2Phb1Mzqdqf-9D3pezBfjPCU
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2:
  - id: c3bf7e1e-1db5-4c72-9293-e2f0b1ab73d0
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: d3cdead0-685a-4489-9250-4bb709942f66
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 722
ht-degree: 1%

---

# Risoluzione dei problemi relativi alla pipeline {#pipeline-troubleshooting}



**L&#39;operazione pipeline non riesce e viene visualizzato l&#39;errore &quot;Nessuna attività corrisponde alla maschera pipeline@&lt; istanza >&quot;**

La versione di Adobe Campaign Classic in uso non supporta la pipeline.

1. Verificare se l&#39;elemento [!DNL pipelined] è presente nel file di configurazione. In caso contrario, significa che non è supportato.
1. Eseguire l’aggiornamento a Campaign 20.3 / [!DNL Gold Standard] 11 o versione successiva.

**Errore del pipeline con &#39;&#39; aurait dow commencer par `[` ou `{` (iRc=16384)&quot;**

Opzione **NmsPipeline_Config** non impostata. In realtà si tratta di un errore di analisi JSON.
Imposta la configurazione JSON nell&#39;opzione **NmsPipeline_Config**. Consulta &quot;opzione di indirizzamento&quot; in questa pagina.

**Il pipeline non riesce e &quot;l&#39;oggetto deve essere un&#39;organizzazione o un client valido&quot;**

La configurazione dell&#39;ID organizzazione non è valida.

1. Verifica che l’ID organizzazione (ImsOrgId) sia impostato in serverConf.xml.
1. Seleziona questa opzione se un ID organizzazione vuoto nel file di configurazione dell’istanza potrebbe sostituire quello predefinito. In tal caso, rimuoverlo.
1. Verifica che l’ID organizzazione sia corretto. Per trovare il tuo ID organizzazione, fai riferimento a [questa pagina](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=it){_blank}

**Errore del pipeline con &quot;chiave non valida&quot;**

Il parametro @authPrivateKey del file di configurazione dell’istanza non è corretto.

1. Verifica che authPrivateKey sia impostato.
1. Verifica che authPrivateKey: inizi con @, termini con = e sia lungo circa 4000 caratteri.
1. Cercare la chiave originale e verificare che sia: in formato RSA, lunga 4096 bit e inizia con `-----BEGIN RSA PRIVATE KEY-----`.
   <br> Se necessario, ricreare la chiave e registrarla in Adobe Analytics.
1. Verificare che la chiave sia stata codificata nella stessa istanza di [!DNL pipelined]. <br>Se necessario, ripeti la codifica utilizzando il JavaScript o il flusso di lavoro di esempio.

**Errore del pipeline con &quot;impossibile leggere il token durante l&#39;autenticazione&quot;**

Formato della chiave privata non valido.

1. Eseguire i passaggi per la crittografia delle chiavi in questa pagina.
1. Verifica che la chiave sia crittografata nella stessa istanza.
1. Verifica che authPrivateKey nel file di configurazione corrisponda alla chiave generata. <br>Assicurarsi di utilizzare OpenSSL per generare la coppia di chiavi. PuttyGen, ad esempio, non genera il formato corretto.

**Errore del pipeline con &quot;non è più consentito ottenere il token di accesso&quot;**

I registri devono essere i seguenti:

```
2021-05-31T08:42:18.124Z        66462   66501   1       error   log     Listener: JWT Token is empty. (iRc=16384)
2021-05-31T08:42:18.210Z        66462   66501   1       error   log     Unknown authentication mode: 'Bearer realm="Adobe Analytics"'. (iRc=-55)
2021-05-31T08:42:18.210Z        66462   66501   1       error   log     BAS-010007 Function not implemented (iRc=-55)
2021-05-31T08:42:48.582Z        66462   66501   1       warning log     Connection seems to have been lost. Attempting to reconnect.
2021-05-31T08:43:09.156Z        66462   66501   1       error   log     INT-150012 The HTTP query returned a 'Forbidden' type error (403) (iRc=-53)
2021-05-31T08:43:09.160Z        66462   66501   1       error   log     Error while authenticating: '{"error":"This client: df73c224e5-triggers-test is no longer allowed to get access token."}' (iRc=16384)
```

Questo messaggio di errore indica che l’autenticazione è configurata utilizzando la OAuth legacy di Omniture base. Consulta la documentazione [Configurazione di Adobe I/O per i trigger di Adobe Experience Cloud](../../integrations/using/about-triggers.md#implement) per aggiornare l&#39;autenticazione.

**Nessun trigger recuperato**

Quando il processo [!DNL pipelined] è in esecuzione e non vengono recuperati trigger:

1. Assicurati che il trigger sia attivo in Analytics e stia generando eventi.
1. Verificare che il processo [!DNL pipelined] sia in esecuzione.
1. Cercare gli errori nel registro [!DNL pipelined].
1. Cercare gli errori nella pagina di stato [!DNL pipelined]. trigger-rifiutato, trigger-failures deve essere zero.
1. Verificare che il nome del trigger sia configurato nell&#39;opzione **[!UICONTROL NmsPipeline_Config]**. In caso di dubbi, utilizzare l&#39;opzione relativa ai caratteri jolly.
1. Verifica che Analytics abbia un trigger attivo e stia generando eventi. Potrebbe verificarsi un ritardo di alcune ore dopo che la configurazione viene effettuata in Analytics prima che sia attiva.

**Gli eventi non sono collegati a un cliente**

Quando alcuni eventi non sono collegati a un cliente:

1. Se applicabile, verifica che il flusso di lavoro di riconciliazione sia in esecuzione.
1. Verifica che l’evento contenga un ID cliente.
1. Eseguire una query sulla tabella dei clienti utilizzando l&#39;ID cliente.
1. Controlla la frequenza dell’importazione del cliente. I nuovi clienti vengono importati in Adobe Campaign con un flusso di lavoro.

**Latenza nell&#39;elaborazione degli eventi**

Quando la marca temporale di Analytics è molto precedente alla data di creazione dell’evento in Campaign.

In genere, un trigger può richiedere dai 15 ai 90 minuti per avviare una campagna di marketing. Questo varia a seconda dell’implementazione della raccolta di dati, del caricamento sulla pipeline, della configurazione personalizzata del trigger definito e del flusso di lavoro in Adobe Campaign.

1. Verificare se il processo [!DNL pipelined] è in esecuzione.
1. Cerca gli errori in pipeline.log che possono causare nuovi tentativi. Correggi gli errori, se applicabile.
1. Controllare la pagina di stato [!DNL pipelined] per le dimensioni della coda. Se la coda è di grandi dimensioni, migliora le prestazioni di JS.
1. Poiché un ritardo sembra aumentare con il volume, configura i trigger su Analytics utilizzando meno messaggi.

**Aggiornamento delle istanze della fase dall&#39;autenticazione legacy all&#39;autenticazione IO Adobe**

La modifica dell’autenticazione dell’integrazione nell’istanza di stage non influisce sulla configurazione dell’istanza di produzione. Puoi scegliere di aggiornare l’istanza Stage, quindi aggiornare l’autenticazione a Adobe IO e testare i trigger sull’istanza Stage.

L’istanza di produzione continuerà a utilizzare l’autenticazione legacy e non sarà interessata da questa modifica.
