---
product: campaign
title: Rilevamento degli URL di tracciamento
description: Ulteriori informazioni sul pattern consigliato per il tracciamento degli URL
feature: Monitoring
role: User, Developer, Data Engineer
exl-id: 7611d6a1-6c55-4ba3-b905-58426c944991
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 2%

---

# Rilevare gli URL di tracciamento

## Esempio di non rilevamento

`<%= getURL("http://mynewsletter.com") %>` funziona e invia il contenuto effettivo della pagina web tramite e-mail ai destinatari. Ma nessuno dei collegamenti viene tracciato. Questo perché l’MTA viene eseguito `"<%=getURL(..."` per ogni e-mail prima dell’invio. Può essere diverso per ogni destinatario, pertanto Adobe Campaign non può conoscere gli URL per il tracciamento e assegnare loro un ID tag.

Quando la pagina da scaricare è la stessa per tutti i destinatari, la best practice prevede di effettuare le seguenti operazioni:

`<%@ include url="http://mynewsletter.com" %>`

In tal caso, la pagina viene scaricata durante l’analisi, prima del rilevamento del tracciamento. Consente ad Adobe Campaign di scoprire i collegamenti, assegnare un ID tag e tracciarli.

## Pattern consigliato

Dopo l’elaborazione `<%@` istruzioni, l’URL da tracciare ha la seguente sintassi: `<a href="http://myurl.com/a.php?param1=aaa&param2=<%=escapeUrl(recipient.xxx)%>&param3=<%=escapeUrl(recipient.xxx)%>">`

>[!IMPORTANT]
>
>Tutti gli altri modelli non sono supportati da Adobe e devono essere evitati per evitare potenziali lacune di sicurezza.

## Pattern non protetto

Quando aggiungi collegamenti personalizzati al contenuto, evita sempre di includere alcuna personalizzazione nella parte nome host dell’URL per evitare potenziali lacune di sicurezza. Per ulteriori informazioni, consulta [questa pagina](../../installation/using/privacy.md#url-personalization).

Ad esempio, il `<a href="http://<%=myURL%>">` la sintassi è **non protetto** e devono essere evitati.

* L’utilizzo di questa sintassi può causare problemi di sicurezza se il collegamento generato da Adobe Campaign contiene uno o più parametri.
* Tidy può correggere in modo errato alcuni collegamenti, che possono verificarsi in modo casuale. Il sintomo tipico è un pezzo di HTML visibile nelle bozze e-mail ma non nell’anteprima.
* L’escape dall’URL è problematico; alcuni caratteri nell’URL possono causare problemi.
* Nell&#39;URL di reindirizzamento non può essere presente un parametro denominato ID in conflitto con il parametro.
* L’interesse del tracciamento è quindi limitato alle statistiche sulla consegna, in quanto Adobe Campaign tiene traccia in modo indifferente di tutti i possibili valori di &quot;myURL&quot;.
