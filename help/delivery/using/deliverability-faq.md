---
solution: Campaign Classic
product: campaign
title: Punti chiave nella gestione del recapito messaggi in Adobe Campaign Classic
description: Quali sono i punti chiave da verificare durante la gestione del recapito messaggi in Adobe Campaign Classic?
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 5d1a653a9a164c34bb70efcc86ff2d7bdf1130a2
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 1%

---


# Risoluzione dei problemi di recapito{#deliverability-faq}

Si verifica un problema di recapito messaggi? Puoi trovare la soluzione qui.

## Errore della regola MX {#mx-rule-error}

**Cosa significa il messaggio di errore &quot;quote soddisfatte&quot;?**

Questo messaggio indica che è stato raggiunto il limite di quota per un MX specifico e che è necessario attendere per poter inviare un altro messaggio e-mail a questo provider.

In Adobe Campaign, esiste una configurazione relativa al numero di e-mail all’ora che possono essere inviate. Questa configurazione deve essere utilizzata con attenzione, in quanto il numero definito nell&#39;istanza riguarda il numero di connessioni effettuate con l&#39;ISP e non il numero di e-mail effettivamente inviate.

Ciò significa che una connessione può utilizzare una regola MX senza inviare correttamente un’e-mail. In questo caso, una configurazione con un IP o un dominio con una reputazione bassa dovrà provare diverse connessioni prima di inviare un’e-mail. Per ogni tentativo, verrà utilizzato un messaggio di credito orario. Di conseguenza, le prestazioni della campagna di marketing saranno significativamente influenzate.

Pertanto, il &quot;rispetto delle quote&quot; non è solo un problema di configurazione, ma può anche essere collegato alla reputazione. È importante analizzare i messaggi di errore nel [registro SMTP](../../production/using/monitoring-processes.md#smtp-errors-per-domain).

Per ulteriori informazioni sulla configurazione MX, consulta [questa sezione](../../installation/using/email-deliverability.md#mx-configuration).

## Stesso messaggio di errore per un ISP {#same-error-for-an-isp}

**Perché ricevo sempre lo stesso messaggio di errore per un particolare ISP?**

Se ricevi sempre lo stesso messaggio di errore per un ISP, l&#39;e-mail o l&#39;IP potrebbe essere stato rilevato come difettoso dall&#39;ISP. Eseguite le seguenti raccomandazioni:
* Controlla se ricevi una grande percentuale di errori collegati a indirizzi e-mail inesistenti (**Utente sconosciuto** non riusciti).
* Aggiorna i moduli di abbonamento per rilevare eventuali errori nei nomi di dominio immessi (ad esempio: gmaul.com o yaho.com).
* Se noti degli errori che indicano che i messaggi sono dichiarati come spam o che i messaggi sono costantemente bloccati, prova ad escludere i destinatari che non hanno aperto o fatto clic in uno dei tuoi messaggi negli ultimi 12 mesi dal target.

Se il problema persiste, contatta il servizio commerciale o di recapito messaggi [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Elenco Bloccati a confronto {#denylist-versus-quarantine}

* **Qual è la differenza tra un indirizzo e-mail elenco Bloccati e un indirizzo e-mail messo in quarantena?**

   * Lo stato **[!UICONTROL Denylisted]** è il risultato di un ciclo di feedback (quando una persona segnala un messaggio come spam).

   * Lo stato **[!UICONTROL Quarantined]** è il risultato di un messaggio non recapitato morbido o rigido.
   Per ulteriori informazioni, consulta [questa sezione](../../delivery/using/understanding-quarantine-management.md#quarantine-vs-denylist).

* **Cosa significano i diversi motivi di errore di quarantena?**

   Ecco 10 possibili ragioni: non definito, utente sconosciuto, dominio non valido, al elenco Bloccati, rifiutato, errore ignorato, non raggiungibile, account disabilitato, cassetta postale piena, non connesso.

   Per ulteriori informazioni, consulta [Informazioni sulla gestione della quarantena](../../delivery/using/understanding-quarantine-management.md).

## Rimozione dal elenco Bloccati {#remove-from-denylist}

* **Uno dei miei destinatari è stato aggiunto al elenco Bloccati per errore. Come posso rimuoverli dal denyist in modo da poter iniziare a inviarli nuovamente?**

   * Vai a **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**.
   * Nei dettagli del record corrispondente, imposta il valore del campo **[!UICONTROL Status]** su **[!UICONTROL Valid]**.
   * Salvare il record.

* **Come posso sapere se uno dei miei IP è su un elenco Bloccati? Come posso rimuovere gli IP da un elenco Bloccati?**

   Per verificare se l&#39;indirizzo IP si trova in un elenco Bloccati, puoi utilizzare vari siti web per verificarlo, ad esempio:
   * [Casella degli strumenti MX](https://mxtoolbox.com/)
   * [Qual è il mio indirizzo IP?](https://whatismyipaddress.com)

   Generalmente, il risultato del controllo dell&#39;indirizzo IP restituirà un elenco contenente i dettagli del elenco Bloccati e anche il nome del sito web che ha negato l&#39;indirizzo IP.

   Facendo clic sul collegamento corrispondente, puoi accedere ai dettagli del sito web. Quindi, puoi richiedere che il tuo sito web venga cancellato dal sito web che ha aggiunto l&#39;indirizzo IP al suo elenco Bloccati.

   >[!NOTE]
   >
   >Il processo di eliminazione può variare a seconda del sito web. Alcuni siti richiedono la creazione di un account, mentre altri richiedono solo che tu fornisca l’indirizzo IP.
