---
product: campaign
title: Componenti web di Campaign e versione 100 nei browser Chrome e Firefox
description: Componenti web di Campaign e versione 100 nei browser Chrome e Firefox
hide: true
hidefromtoc: true
source-git-commit: d238f0aa28289c69c91dc6a028792260708ed9f3
workflow-type: tm+mt
source-wordcount: '619'
ht-degree: 0%

---

# Chrome e Firefox v100 hanno un impatto sui componenti web di Campaign {#version-100}

Google e Mozilla avvertono che Chrome e Firefox potrebbero interrompere alcuni siti web a causa delle loro prossime versioni a 3 cifre.

La modifica del numero di versione da 2 a 3 cifre può causare alcuni problemi quando si visitano siti web che non sono preparati per questa modifica. Alcune pagine web potrebbero non essere visualizzate correttamente in queste nuove versioni del browser.

Chrome v100 è impostato per il rilascio il **29 marzo 2022** e Firefox v100 on **3 maggio 2022**.

Mozilla e Google stanno testando la compatibilità dei principali siti web in anticipo. Se ci sono problemi con i siti che non possono risolvere prima del rilascio di queste versioni, entrambi dispongono di piani di backup pronti per garantire che i siti non siano interessati.

I potenziali problemi o la perdita di funzionalità sul sito web derivano dalla stringa dell&#39;agente utente che i browser inviano ai siti web che stai visitando: l’agente utente è una stringa inviata dal browser al sito web per comunicare al sito il browser e la versione utilizzati e la tecnologia associata. Quando il browser invia una richiesta a un sito web, si identifica con la stringa agente utente prima di recuperare il contenuto richiesto. I dati nella stringa dell&#39;agente utente aiutano il sito web a consegnare il contenuto in un formato adatto al tuo browser. La versione dell’agente utente viene incrementata in modo che corrisponda al numero di versione del browser. Il passaggio da 2 a 3 cifre può causare problemi.

## Sei interessato da questo problema?{#version-100-impact}

Adobe consiglia di testare le applicazioni web Campaign, compresi i moduli web e i sondaggi, per assicurarsi che funzionino comunque correttamente con queste nuove versioni del browser.

Questa raccomandazione si applica a tutte le applicazioni web e soprattutto se hai incluso il codice JavaScript.

È necessario controllare sia con Firefox e Chrome, mobile e desktop.

## Come fare il test?{#version-100-test}

In Chrome e Firefox, puoi configurare il browser per segnalare la versione 100 in questo momento, quindi segnalare e correggere eventuali problemi riscontrati.

### Test con Firefox 100{#test-firefox-100}

Per testare le tue pagine web con Mozilla Firefox 100, puoi simulare la prossima modifica dell&#39;agente utente sulle tue app web modificando manualmente la stringa dell&#39;agente utente.

1. Apri Firefox, immetti `about:config` nella barra degli indirizzi e premere invio.
1. Cerca `general.useragent.override`.
1. Selezionare &quot;Stringa&quot;, quindi fare clic sul segno più (+).

   ![](assets/force-user-agent-firefox.png)

1. Immetti il seguente testo nel campo :

   ```
   Mozilla/5.0 (Windows NT 10.0; rv:100.0) Gecko/20100101 Firefox/100.0
   ```

1. Fai clic sul pulsante blu del segno di spunta per salvare l&#39;impostazione.
1. Chiudi e riavvia il browser.

Con queste impostazioni, il browser invia la nuova stringa agente utente ai siti web, indicando che il browser è Firefox 100. Se si verificano problemi con i moduli web, è necessario creare un nuovo rapporto di bug per Mozilla. È consigliabile ricostruire questi moduli web prima che questa modifica sia ampiamente disponibile.

Per ripristinare l&#39;agente utente predefinito, è sufficiente tornare al `about:config` e cerca `general.useragent.override` di nuovo.  Quando appare, fai clic sull&#39;icona del cestino per eliminare l&#39;impostazione e riavvia il browser.

### Test con Chrome 100{#test-chrome-100}

Per testare l&#39;agente utente Google Chrome 100 sulle tue app web, puoi abilitare questo test seguendo i seguenti passaggi:

1. Apri Chrome, immetti `chrome://flags` nella barra degli indirizzi e premere invio.
1. Ricerca `Force major version to 100 in User-Agent` nel campo di ricerca e attivalo come mostrato di seguito.

   ![](assets/force-user-agent-chrome.png)

1. Chiudi e riavvia il browser.
1. Chiudi `chrome://flags` schermo.

Con queste impostazioni, il browser invia la nuova stringa agente utente ai siti web, indicando che il browser è Chrome 100. Se si verificano problemi con i siti web visitati, è necessario creare un nuovo rapporto di bug per Google. È consigliabile ricostruire questi moduli web prima che questa modifica sia ampiamente disponibile.

Per ripristinare l&#39;agente utente predefinito, segui questo processo e modifica l&#39;impostazione del flag in `Default` e riavvia il browser.
