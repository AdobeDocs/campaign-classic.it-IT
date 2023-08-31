---
product: campaign
title: Punti chiave durante la gestione del recapito messaggi in Adobe Campaign Classic
description: Scopri i punti chiave da verificare durante la gestione del recapito messaggi in Adobe Campaign
badge-v7: label="v7" type="Informative" tooltip="Applicabile a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Deliverability, Troubleshooting
role: User
exl-id: f94897c1-b44c-4100-ac50-a89b13fa6f2f
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 2%

---

# Risoluzione dei problemi di recapito{#deliverability-faq}

Si è verificato un problema di recapito messaggi? La soluzione potrebbe essere disponibile qui.

## Errore regola MX {#mx-rule-error}

**Cosa significa il messaggio di errore &quot;quote soddisfatte&quot;?**

Questo messaggio indica che hai raggiunto il limite di quota per un MX specifico e che devi attendere per poter inviare un’altra e-mail a questo provider.

In Adobe Campaign esiste una configurazione relativa al numero di e-mail all’ora che possono essere inviate. Questa configurazione deve essere utilizzata con cautela, in quanto il numero definito nell’istanza riguarda il numero di connessioni effettuate con l’ISP e non il numero di e-mail effettivamente inviate.

Ciò significa che una connessione può utilizzare una regola MX senza inviare correttamente un’e-mail. In questo caso, una configurazione con un IP o un dominio con una reputazione bassa dovrà provare diverse connessioni prima di inviare un’e-mail. Per ogni tentativo, verrà utilizzato un credito di messaggi all’ora. Di conseguenza, le prestazioni della campagna di marketing saranno influenzate in modo significativo.

Pertanto, le &quot;quote soddisfatte&quot; non sono solo un problema di configurazione, ma possono anche essere collegate alla reputazione. È importante analizzare i messaggi di errore nel [Registro SMTP](../../production/using/monitoring-processes.md#smtp-errors-per-domain).

Per ulteriori informazioni sulla configurazione MX, consulta [questa sezione](../../installation/using/email-deliverability.md#mx-configuration).

## Stesso messaggio di errore per un ISP {#same-error-for-an-isp}

**Perché viene sempre visualizzato lo stesso messaggio di errore per un ISP specifico?**

Se ricevi sempre lo stesso messaggio di errore per un ISP, l’e-mail o l’IP potrebbero essere stati rilevati come difettosi dall’ISP. Effettua le seguenti raccomandazioni:
* Controlla se ricevi un’ampia percentuale di errori collegati a indirizzi e-mail inesistenti (**Utente sconosciuto** errori).
* Aggiorna i moduli di abbonamento per rilevare eventuali errori nei nomi di dominio immessi (ad esempio: gmaul.com o yaho.com).
* Se noti errori che indicano che i tuoi messaggi sono dichiarati come spam o che i tuoi messaggi sono costantemente bloccati, prova ad escludere dal target i destinatari che non hanno aperto o cliccato in uno dei tuoi messaggi negli ultimi 12 mesi.

Se il problema persiste, contattare il servizio commerciale o di consegna, [Assistenza clienti Adobe](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Inserisco nell&#39;elenco Bloccati rispetto alla quarantena {#denylist-versus-quarantine}

* **Qual è la differenza tra un indirizzo e-mail nel inserisco nell&#39;elenco Bloccati di e un indirizzo e-mail in quarantena?**

   * Stato **[!UICONTROL Denylisted]** è il risultato di un ciclo di feedback (quando una persona segnala un messaggio come spam).

   * Stato **[!UICONTROL Quarantined]** è il risultato di un mancato recapito morbido o permanente.

  Per ulteriori informazioni, consulta [questa sezione](understanding-quarantine-management.md#quarantine-vs-denylist).

* **Cosa significano i diversi motivi di errore di quarantena?**

  10 possibili motivi: non definito, utente sconosciuto, dominio non valido, in inserita nell&#39;elenco Bloccati di accesso, rifiutato, errore ignorato, non raggiungibile, account disabilitato, cassetta postale piena, non connesso.

  Per ulteriori informazioni, consulta [Informazioni sulla gestione della quarantena](understanding-quarantine-management.md).

## Rimozione dal inserisco nell&#39;elenco Bloccati {#remove-from-denylist}

* **Uno dei miei destinatari è stato aggiunto per inserire nell&#39;elenco Bloccati per errore. Come è possibile rimuoverli dal denyist in modo da poter iniziare a inviare nuovamente i messaggi?**

   * Vai a **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**.
   * Nei dettagli del record corrispondente, imposta il valore del **[!UICONTROL Status]** campo a **[!UICONTROL Valid]**.
   * Salvare il record.

* **Come posso scoprire se uno dei miei IP si trova su un inserisco nell&#39;elenco Bloccati di? Come posso rimuovere gli IP da un inserisco nell&#39;elenco Bloccati di?**

  Per verificare se l’indirizzo IP si trova su un inserisco nell&#39;elenco Bloccati di, puoi utilizzare vari siti web per verificarlo, ad esempio:
   * [Casella degli strumenti MX](https://mxtoolbox.com/)
   * [Qual è il mio indirizzo IP](https://whatismyipaddress.com)

  In genere, il risultato della verifica dell’indirizzo IP restituirà un elenco contenente i dettagli del inserisco nell&#39;elenco Bloccati di e anche il nome del sito web che ha negato l’indirizzo IP.

  Facendo clic sul collegamento corrispondente, è possibile accedere ai dettagli del sito Web. Quindi puoi richiedere che il tuo sito web venga cancellato dal sito web che ha aggiunto l’indirizzo IP al suo inserisco nell&#39;elenco Bloccati di.

  >[!NOTE]
  >
  >Il processo di cancellazione dall’elenco può variare a seconda del sito web. Alcuni siti richiedono la creazione di un account, mentre altri richiedono solo che tu fornisca l’indirizzo IP.
