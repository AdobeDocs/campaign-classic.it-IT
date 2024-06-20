---
product: campaign
title: Fine del supporto per TLS 1.0 e 1.1
description: Fine del supporto per TLS 1.0 e 1.1
feature: Technote
audience: delivery
content-type: reference
topic-tags: tracking-messages
hide: true
hidefromtoc: true
exl-id: e18d43b6-2a77-4881-85e7-ca36248d4634
source-git-commit: 19b40f0b827c4b5b7b6484fe4953aebe61d00d1d
workflow-type: tm+mt
source-wordcount: '860'
ht-degree: 4%

---

# Fine del supporto per TLS 1.0 e 1.1{#eol-tls-support}



Adobe non supporta più sistemi utente e client non conformi al protocollo TLS (Transport Layer Security) 1.2. Se continui a utilizzare versioni precedenti di TLS, potresti perdere l’accesso a tutti i prodotti e servizi Adobe.

## Perché viene visualizzata questa pagina?

Se viene visualizzato il seguente messaggio: **Questa pagina non può essere visualizzata**, ciò significa che le app, la pagina web o il servizio di Adobe a cui stai tentando di accedere richiedono una connessione di rete più sicura con il browser web, il sistema operativo o l’app. È obbligatorio utilizzare **TLS 1.2** per la comunicazione di rete sicura e lo scambio di dati tra i sistemi degli utenti e le app e i servizi web di Adobe.

Adobe ha dichiarato obsoleto il supporto per le versioni inferiori di TLS (incluse TLS 1.0 e 1.1). Per informazioni tecniche sul protocollo TLS 1.2, vedi [Domande frequenti](#faq).

## Cosa posso fare per riprendere il servizio?

I browser web moderni supportano TLS 1.2. L’aggiornamento del browser può consentirti di accedere a questi servizi e app.

Puoi scaricare e installare uno dei seguenti browser più diffusi:

* [Google Chrome](https://www.google.com/chrome/)
* [Apple Safari](https://www.apple.com/safari/)
* [Firefox](https://www.mozilla.org/en-US/firefox/new/)
* [Microsoft Edge](https://www.microsoft.com/en-us/edge)

Se utilizzi un altro browser, accertati che supporti TLS 1.2.

Anche il sistema operativo e i framework dell’applicazione devono supportare TLS 1.2. Se l&#39;aggiornamento del browser non risolve il problema, verificare che il computer soddisfi i requisiti di sistema elencati in [Matrice di compatibilità di Campaign](../../rn/using/compatibility-matrix.md).

## Domande frequenti{#faq}

* **Che cos’è Transport Layer Security (TLS)?**

  [Transport Layer Security](https://en.wikipedia.org/wiki/Transport_Layer_Security) (TLS) è un protocollo di sicurezza che fornisce privacy e integrità dei dati tra due applicazioni comunicanti. È ampiamente implementato per i browser web e altre applicazioni che richiedono lo scambio sicuro dei dati all’interno di una rete.

  In base alle specifiche del protocollo, TLS include due livelli, il protocollo Record TLS e il protocollo Handshake TLS. Il protocollo Record garantisce la sicurezza della connessione. Il protocollo Handshake consente al server e al client di autenticarsi reciprocamente e di negoziare gli algoritmi di crittografia e le chiavi di crittografia prima dello scambio dei dati.

* **Quale sarà l’impatto dell&#39;aggiornamento?**

  Gli standard di sicurezza e conformità di Adobe richiedono che i protocolli più vecchi vengano resi obsoleti a maggio 2018 e richiedono l’utilizzo di TLS 1.2 come versione aggiornata. Se il sistema non è conforme a TLS 1.2, l’accesso ad alcuni servizi e app di Adobe è limitato.

* **Quali sono gli effetti di TLS su di te?**

  Puoi interagire con alcune app e servizi di Adobe solo tramite una connessione di rete sicura. TLS garantisce che la connessione tra il browser e queste app e servizi web sia sicura e affidabile.

  Con il rilascio di nuovi browser e sistemi operativi, gli standard di sicurezza vengono aggiornati per garantire livelli più elevati di privacy e integrità dei dati. Tuttavia, le versioni precedenti di questi browser o sistemi operativi non vengono aggiornate per includere gli standard più recenti.

  Con l&#39;aumento del livello di sicurezza accettabile, queste versioni e applicazioni del browser meno sicure e meno vecchie vengono lasciate indietro.

  Per connettersi con siti protetti, aggiorna il sistema operativo e le versioni del browser.

* **TLS è vulnerabile agli hacker?**

  Sono stati documentati attacchi contro TLS 1.0 che utilizzano un metodo di crittografia precedente e le versioni precedenti sono più vulnerabili di TLS 1.2. Per ulteriori informazioni, consulta Attacchi contro TLS/SSL.

* **Perché Adobe disabilita il supporto per TLS 1.0 e 1.1?**

  Adobe dispone di standard di conformità per la sicurezza che richiedono la disattivazione del supporto per i protocolli meno recenti. Uno di questi standard garantisce la conformità con il settore delle carte di pagamento (Payment Card Industry, PCI). Il server di adattamento PCI è un insieme di standard di sicurezza che richiedono alle organizzazioni che accettano, elaborano, memorizzano o trasmettono le informazioni della carta di credito per mantenere un ambiente sicuro.

  La conformità PCI impone l’utilizzo di TLS 1.1 o versione successiva a maggio 2018.

* **Perché gli Adobi impongono l’utilizzo di TLS 1.2 invece di consentire TLS 1.1 o TLS 1.0?**

  La maggior parte delle richieste per app e servizi web di Adobe proviene da sistemi utente conformi a TLS 1.2, con traffico ridotto dai sistemi TLS 1.1.

  Adobe è migrato a TLS 1.2, pertanto l’accesso alle app e ai servizi web è più sicuro.

* **Qual è l’ultima data utile per utilizzare una versione precedente di TLS?**

  L’Adobe incoraggia gli utenti ad abbandonare rapidamente le versioni precedenti per evitare l’esposizione a vulnerabilità di sicurezza. Per ulteriori informazioni, contatta l’Assistenza clienti Adobe o il tuo Customer Success Manager.

* **Quale messaggio di errore viene visualizzato se si utilizza un browser non configurato per TLS 1.2?**

  Dipende dal browser in uso. Tutti i browser menzionati in [Matrice di compatibilità di Campaign](../../rn/using/compatibility-matrix.md) sono configurati per utilizzare TLS 1.2. Se utilizzi un browser o una versione che non figura nell’elenco, aggiorna il browser.

  L’Adobe non controlla i messaggi di errore generati dal livello di comunicazione SSL. Il browser genera questi messaggi prima di connettersi alle app e ai servizi di Adobe. Di seguito è riportato un esempio di errore che può verificarsi con Internet Explorer 11 in Windows 7:

  ![](assets/do-not-translate/page-not-displayed.png)

  TLS 1.2 è attivato su Internet Explorer 11 per impostazione predefinita, ma se è disattivato, è possibile attivarlo. In questo caso, accendi TLS 1.2 dalla finestra di dialogo delle impostazioni avanzate anziché utilizzare altre opzioni. Possono inoltre verificarsi altri errori, ad esempio i seguenti:

   * Impossibile connettersi al servizio
   * Servizio non disponibile
   * Errore di connessione
