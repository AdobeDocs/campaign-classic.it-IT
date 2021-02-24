---
solution: Campaign Classic
product: campaign
title: Rilevamento degli URL di tracciamento
description: Ulteriori informazioni sul pattern consigliato per il tracciamento degli URL.
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: 151667637a12667f5eda1590e64e01de493be9ce
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 0%

---


# Rilevamento degli URL di tracciamento

## Esempio di non rilevamento

`<%= getURL("http://mynewsletter.com") %>` funziona e invia il contenuto effettivo della pagina Web tramite e-mail ai destinatari. Ma nessuno dei collegamenti è monitorato. Questo è dovuto al fatto che l&#39;MTA esegue `"<%=getURL(..."` per ogni e-mail prima dell&#39;invio. Può essere diverso per ciascun destinatario, pertanto  Adobe Campaign non è in grado di conoscere gli URL per il tracciamento e di assegnare loro un ID di tag.

Quando la pagina da scaricare è la stessa per tutti i destinatari, è consigliabile effettuare le seguenti operazioni:

`<%@ include url="http://mynewsletter.com" %>`

In tal caso, la pagina viene scaricata durante l&#39;analisi, prima del rilevamento del tracciamento. Consente  Adobe Campaign di individuare i collegamenti, assegnare un ID tag e tenerne traccia.

## Pattern consigliato

Dopo l&#39;elaborazione delle istruzioni `<%@`, l&#39;URL da monitorare ha la sintassi seguente: `<a href="http://myurl.com/a.php?param1=aaa&param2=<%=escapeUrl(recipient.xxx)%>&param3=<%=escapeUrl(recipient.xxx)%>">`

>[!IMPORTANT]
>
>Tutti gli altri modelli non sono supportati dal Adobe  e dovrebbero essere evitati per evitare potenziali carenze in materia di sicurezza.

## Avvisi per il pattern http://&lt;%=myURL%>

La sintassi `<a href="http://<%=myURL%>">` non è sicura e non è consigliata perché:

* Tidy può correggere erroneamente alcuni dei collegamenti, che possono accadere casualmente. Il sintomo tipico è un elemento HTML visibile nelle prove e-mail ma non nell’anteprima.
* La fuga dell’URL è problematica, alcuni caratteri nell’URL possono causare problemi.
* Non è possibile avere un parametro denominato ID in conflitto con il parametro nell’URL di reindirizzamento.
* L’interesse per il tracciamento è quindi limitato alle statistiche sulla distribuzione, in quanto  Adobe Campaign tiene traccia di tutti i possibili valori di &quot;myURL&quot;.

Fare riferimento a [questa pagina](https://helpx.adobe.com/campaign/kb/acc-security.html#privacy) per ulteriori informazioni.

