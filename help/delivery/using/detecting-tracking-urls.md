---
product: campaign
title: Rilevamento degli URL di tracciamento
description: Ulteriori informazioni sul pattern consigliato per il tracciamento degli URL
audience: delivery
content-type: reference
topic-tags: tracking-messages
exl-id: 7611d6a1-6c55-4ba3-b905-58426c944991
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 3%

---

# Rilevamento degli URL di tracciamento

## Esempio di mancata rilevazione

`<%= getURL("http://mynewsletter.com") %>` funziona e invia il contenuto effettivo della pagina web tramite e-mail ai destinatari. Ma nessuno dei collegamenti è tracciato. Il motivo è che l’MTA viene eseguito `"<%=getURL(..."` per ogni e-mail prima dell’invio. Può essere diverso per ogni destinatario, pertanto Adobe Campaign non può conoscere gli URL per il tracciamento e assegnargli un ID tag.

Quando la pagina da scaricare è la stessa per tutti i destinatari, si consiglia di effettuare le seguenti operazioni:

`<%@ include url="http://mynewsletter.com" %>`

In tal caso, la pagina viene scaricata durante l’analisi, prima del rilevamento del tracciamento. Consente ad Adobe Campaign di individuare i collegamenti, assegnare un ID tag e tenerli traccia.

## Pattern consigliato

Dopo l’elaborazione `<%@` , l’URL da tracciare presenta la seguente sintassi: `<a href="http://myurl.com/a.php?param1=aaa&param2=<%=escapeUrl(recipient.xxx)%>&param3=<%=escapeUrl(recipient.xxx)%>">`

>[!IMPORTANT]
>
>Tutti gli altri modelli non sono supportati dall&#39;Adobe e dovrebbero essere evitati per evitare potenziali lacune di sicurezza.

## Pattern non protetto

Quando aggiungi collegamenti personalizzati al contenuto, evita sempre di avere alcuna personalizzazione nella parte dell’URL relativa al nome host per evitare potenziali lacune nella sicurezza. Per ulteriori informazioni, consulta [questa pagina](../../installation/using/privacy.md#url-personalization).

Ad esempio, il `<a href="http://<%=myURL%>">` sintassi **non protetto** e deve essere evitato.

* L’utilizzo di questa sintassi può causare problemi di sicurezza se il collegamento generato da Adobe Campaign contiene uno o più parametri.
* Tidy può attaccare in modo errato alcuni dei collegamenti, che possono accadere in modo casuale. Il sintomo tipico è un elemento di HTML visibile nelle bozze e-mail ma non nell’anteprima.
* La fuga dall’URL è problematica, alcuni caratteri nell’URL possono causare problemi.
* Nell&#39;URL di reindirizzamento non può essere presente un parametro denominato ID in conflitto con il parametro .
* L’interesse del tracciamento è quindi limitato alle statistiche sulla consegna, in quanto Adobe Campaign tiene traccia indifferentemente di tutti i valori possibili di &quot;myURL&quot;.
