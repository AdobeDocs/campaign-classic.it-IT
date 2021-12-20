---
product: campaign
title: Terminazione del supporto per TLS 1.0 e 1.1
description: Terminazione del supporto per TLS 1.0 e 1.1
audience: delivery
content-type: reference
topic-tags: tracking-messages
source-git-commit: 70240d5f62fd3d7b755389b5ad8c4b499c94657d
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 1%

---

# Terminazione del supporto per TLS 1.0 e 1.1{#eol-tls-support}

![](../../assets/v7-only.svg)

Adobe non supporta più i sistemi utente e client che non sono conformi al protocollo Transport Layer Security (TLS) 1.2. Se continui a utilizzare versioni precedenti di TLS, potresti perdere l’accesso a tutti i prodotti e i servizi di Adobe.

## Perché sto vedendo questa pagina?

Se viene visualizzato il seguente messaggio: **Impossibile visualizzare questa pagina**, ciò significa che le app, la pagina web o il servizio Adobe a cui stai tentando di accedere richiedono una connessione di rete più sicura con il browser web, il sistema operativo o l’app in uso. È obbligatorio utilizzare **TLS 1.2** per una comunicazione di rete e uno scambio di dati sicuri tra i sistemi degli utenti e le app di Adobe e i servizi web.

Adobe ha dichiarato obsoleto il supporto per le versioni precedenti di TLS (comprese TLS 1.0 e 1.1). Per informazioni tecniche sul protocollo TLS 1.2, consulta [Domande frequenti](#faq).

## Cosa posso fare per riprendere il servizio?

I browser web moderni supportano TLS 1.2. L’aggiornamento del browser può consentirti di accedere a queste app e a questi servizi.

Puoi scaricare e installare uno dei seguenti browser più diffusi:

* [Google Chrome](https://www.google.com/chrome/)
* [Apple Safari](https://www.apple.com/safari/)
* [Firefox](https://www.mozilla.org/en-US/firefox/new/)
* [Microsoft Edge](https://www.microsoft.com/en-us/edge)

Se utilizzi un altro browser, assicurati che supporti TLS 1.2.

Il tuo sistema operativo e i tuoi framework applicativi devono anche supportare TLS 1.2. Se l’aggiornamento del browser non risolve il problema, assicurati che il computer soddisfi i requisiti di sistema elencati in [Matrice di compatibilità di Campaign](../../rn/using/compatibility-matrix.md).

## Domande frequenti{#faq}

* **Cos’è TLS (Transport Layer Security)?**

   [Transport Layer Security](https://en.wikipedia.org/wiki/Transport_Layer_Security) (TLS) è un protocollo di sicurezza che fornisce privacy e integrità dei dati tra due applicazioni di comunicazione. È ampiamente distribuito per i browser web e altre applicazioni che richiedono lo scambio sicuro dei dati attraverso una rete.

   In base alle specifiche del protocollo, TLS include due livelli, il protocollo TLS Record e il protocollo TLS Handshake. Il protocollo Record fornisce la protezione della connessione. Il protocollo Handshake consente al server e al client di eseguire l’autenticazione reciproca e di negoziare algoritmi di crittografia e chiavi di crittografia prima dello scambio dei dati.

* **Quale sarà l’impatto dell&#39;aggiornamento?**

   A partire da maggio 2018, gli standard di sicurezza e conformità adottati da Adobe richiedono la rimozione dei protocolli più vecchi e impongono l’utilizzo di TLS 1.2 come versione aggiornata. Se il sistema non è conforme a TLS 1.2, l’accesso ad alcune app e ad alcuni servizi di Adobe è limitato.

* **In che modo TLS ti influisce?**

   Puoi interagire solo con alcune app e alcuni servizi di Adobe tramite una connessione di rete sicura. TLS garantisce che la connessione tra il browser e queste app e servizi web sia sicura e affidabile.

   Con il rilascio di nuovi browser e sistemi operativi, gli standard di sicurezza vengono aggiornati per garantire livelli più elevati di privacy e integrità dei dati. Tuttavia, le versioni precedenti di questi browser o del sistema operativo non vengono aggiornate per includere gli standard più recenti.

   Con l&#39;aumento del livello di sicurezza accettabile, queste versioni e applicazioni precedenti e meno sicure del browser vengono lasciate indietro.

   Per poterti connettere a siti sicuri, aggiorna il tuo sistema operativo e le versioni del browser.

* **TLS è vulnerabile agli hacker?**

   Ci sono stati attacchi documentati contro TLS 1.0 utilizzando un metodo di crittografia precedente e le versioni precedenti sono più vulnerabili di TLS 1.2. Per ulteriori informazioni, consulta Attacchi contro TLS/SSL.

* **Perché Adobe disabilita il supporto per TLS 1.0 e 1.1?**

   Adobe dispone di standard di conformità per la sicurezza che richiedono la disattivazione del supporto per i protocolli più vecchi. Uno di questi standard garantisce la conformità con il settore delle carte di pagamento (PCI). Il server di adattamento PCI è un insieme di standard di sicurezza che richiedono alle organizzazioni che accettano, elaborano, archiviano o trasmettono informazioni sulla carta di credito per mantenere un ambiente sicuro.

   A partire da maggio 2018, la conformità PCI impone l’utilizzo di TLS 1.1 o versione successiva.

* **Perché Adobe richiede l’utilizzo di TLS 1.2 invece di consentire TLS 1.1 o TLS 1.0?**

   La maggior parte delle richieste per app e servizi web di Adobe proviene da sistemi utente conformi a TLS 1.2, con traffico ridotto dai sistemi TLS 1.1.

   Adobe è migrato a TLS 1.2 per garantire un accesso più sicuro alle app e ai servizi web.

* **Qual è l’ultima data in cui posso utilizzare una versione precedente di TLS?**

   L’Adobe incoraggia gli utenti ad abbandonare rapidamente le versioni precedenti per evitare l’esposizione a vulnerabilità di sicurezza. Per ulteriori informazioni, contatta l’Assistenza clienti di Adobe o il tuo Customer Success Manager.

* **Quale messaggio di errore viene visualizzato se utilizzo un browser non configurato per TLS 1.2?**

   Dipende dal browser in uso. Tutti i browser menzionati in [Matrice di compatibilità di Campaign](../../rn/using/compatibility-matrix.md) sono configurati per utilizzare TLS 1.2. Se utilizzi un browser o una versione che non figura nell’elenco, aggiorna il browser.

   Adobe non controlla i messaggi di errore generati dal livello di comunicazione SSL. Il browser genera questi messaggi prima di connettersi alle app e ai servizi di Adobe. Ecco un esempio di errore che può verificarsi con Internet Explorer 11 su Windows 7:

   ![](assets/do-not-translate/page-not-displayed.png)

   TLS 1.2 è abilitato su Internet Explorer 11 per impostazione predefinita, ma se è disattivato puoi attivarlo. In questo caso, attiva TLS 1.2 dalla finestra di dialogo delle impostazioni avanzate anziché utilizzare altre scelte. Possono verificarsi anche altri errori, ad esempio:

   * Impossibile connettersi al servizio
   * Servizio non disponibile
   * Errore di connessione
