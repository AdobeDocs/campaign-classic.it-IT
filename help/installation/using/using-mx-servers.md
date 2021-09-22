---
product: campaign
title: Utilizzo dei server MX con Campaign
description: Scopri come funzionano i server MX con Adobe Campaign Classic.
audience: installation
content-type: reference
topic-tags: additional-configurations
hidefromtoc: true
exl-id: 47f50bf5-4d5b-4c07-af71-de4390177cf5
source-git-commit: 32f55d02920b0104198f809b1be0a91306a4d9e4
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 1%

---

# Utilizzo dei server MX con Campaign {#using-mx-servers}

![](../../assets/v7-only.svg)

Scopri come funzionano i server MX con Adobe Campaign Classic.

## Server MX {#mx-servers}

### Che cos&#39;è un server MX?

Un record di scambiatore di posta (record MX) è un tipo di record di risorse nel DNS (Domain Name System) che specifica un server di posta responsabile dell&#39;accettazione dei messaggi di posta elettronica per conto di un dominio.

### Come funziona un server MX?

Quando si invia un&#39;e-mail, il server software stabilirà una connessione con il server del dominio destinatario. La comunicazione tra i due server utilizza la lingua SMTP e un dominio può avere più di un server MX. La connessione a questo dominio partirà dalla priorità più alta (figura più piccola) e altri server sono chiamati server di backup. Il protocollo di connessione deve essere rispettato.

### Come funziona un server MX con Adobe Campaign?

Nel protocollo di connessione devono essere rispettate le norme per impedire lo spamming e il monopolio dei server. I più importanti sono i seguenti:

* **Numero massimo di connessioni consentite**: Se questo numero viene rispettato, gli IP non vengono inseriti nel elenco Bloccati e le e-mail non vengono rifiutate a causa di connessioni aggiuntive.
* **Numero massimo di messaggi**: Durante la connessione, è necessario definire il numero di messaggi consentiti per l’invio. Se questo numero non è definito, il server ne invierà il maggior numero possibile. Questo comporta l&#39;identificazione come spammer e l&#39;aggiunta al elenco Bloccati da parte dell&#39;ISP.
* **Messaggi all&#39;ora**: Al fine di soddisfare la tua e-reputazione, Adobe Campaign controllerà il numero di e-mail che gli IP possono inviare all’ora. Questo sistema ti proteggerà dal rifiuto o/e-mail e dal elenco Bloccati.

## E-mail non recapitate

### Cos’è un messaggio e-mail non recapitato?

È il processo utilizzato da Adobe Campaign per elaborare gli errori durante le comunicazioni sul server.

### Come funziona un messaggio e-mail non recapitato?

L&#39;indirizzo di errore elabora i rimbalzi inviati dagli ISP. Il processo analizzerà diversi codici di errore SMTP e applicherà l&#39;azione corretta in base allo standard RegEx.

Ad esempio, un indirizzo e-mail ha un feedback &quot;550 Utente sconosciuto&quot; inviato da un ISP. Questo codice di errore viene elaborato dall’indirizzo di errore Adobe Campaign (indirizzo del percorso restituito). Questo errore viene quindi confrontato con lo standard RegEx e la regola corretta verrà applicata. L’e-mail viene considerata un *rimbalzo rigido* (corrispondente al tipo) e quindi *Utente sconosciuto* (corrispondente al motivo) e viene messa in quarantena dopo il primo ciclo nel sistema.

### Come viene gestita da Adobe Campaign?

Adobe Campaign gestisce questo processo con una corrispondenza tra un tipo di errore e un motivo:

* **[!UICONTROL User Unknown]**: Indirizzo corretto dal punto di vista sintattico ma non esistente. Questo errore viene classificato come rimbalzo duro e messo in quarantena all’interno del primo errore.
* **[!UICONTROL Mailbox full]**: Cassetta postale che ha raggiunto la capacità massima. Questo errore può anche indicare che l&#39;utente non utilizza più questa cassetta postale. Questo errore viene classificato come rimbalzo morbido e messo in quarantena entro il terzo errore e rimosso dalla quarantena dopo un periodo di 30 giorni.
* **[!UICONTROL Inactive User]**: La cassetta postale è stata disattivata dall&#39;ISP a causa di un utente inattivo negli ultimi 6 mesi. Questo errore viene classificato come rimbalzo morbido e messo in quarantena all’interno del terzo errore.
* **[!UICONTROL Invalid domain]**: Il dominio nell&#39;indirizzo e-mail non esiste. Questo errore viene classificato come rimbalzo morbido e messo in quarantena all’interno del terzo errore.
* **[!UICONTROL Refused]**: L&#39;ISP si è rifiutato di inviare l&#39;e-mail ai suoi utenti. Questo errore è classificato come messaggio non recapitato e non viene messo in quarantena in quanto l’errore non è collegato all’indirizzo e-mail ma alla reputazione dell’IP o di un dominio.

>[!NOTE]
>
>Per ulteriori informazioni sui tipi e i motivi di errori di consegna, consulta questa [sezione](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons).

## Istanza di recapito messaggi

Un aggiornamento giornaliero delle regole MX e delle regole di rimbalzo è gestito da un flusso di lavoro specifico nell&#39;istanza client collegato al proprietario dell&#39;istanza di recapito di queste regole.

Questo aggiornamento giornaliero è in esecuzione per tutti i clienti che desiderano mantenere aggiornata la propria istanza attraverso un processo di trasparenza.

Le regole MX hanno 6 diversi livelli di throughput utilizzati principalmente durante il processo di rampa:

![](assets/mx-rules-throughput.png)

La modalità personalizzata è per i clienti avanzati che desiderano impostare le proprie regole MX. Quando la modalità Personalizzato è attivata, il client non verrà aggiornato dall’istanza di recapito messaggi, in quanto la sincronizzazione verrà disattivata.

## Esempi di mancato recapito

* **Utente sconosciuto**  (rimbalzo rigido): 550 5.1.1 ... Utente sconosciuto {mx003}
* **Cassetta postale piena**  (rimbalzo morbido): 550 5.2.2 Superata la quota degli utenti
* **Cassetta postale**  inattiva (rimbalzo morbido): 550 5.7.1 : Indirizzo destinatario rifiutato: MailBox inattiva, non in poping per più di 6 mesi
* **Dominio non valido**  (rimbalzo morbido): Query DNS non riuscita per &#39;ourdan.com&#39;
* **Rifiutato**  (rimbalzo morbido): Messaggio e-mail non recapitato in entrata (la regola &#39;Feedback_loop_Hotmail&#39; corrisponde a questo messaggio non recapitato)
* **Non raggiungibile**  (rimbalzo morbido): 421 4.16.55  [TS01] Messaggi da x.x.x.x temporaneamente differiti a causa di reclami degli utenti eccessivi

**Argomenti correlati:**
* [Configurazione MX](../../installation/using/email-deliverability.md#mx-configuration)
* [Configurazione e-mail tecnica](../../installation/using/email-deliverability.md)
* [Comprendere gli errori di consegna](../../delivery/using/understanding-delivery-failures.md)
* [Campaign Classic - Recommendations tecnico](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/campaign/acc-technical-recommendations.html)
