---
product: campaign
title: Utilizzo dei server MX con Campaign
description: Scopri come funzionano i server MX con Adobe Campaign Classic
feature: Installation, Instance Settings
badge-v7-prem: label="on-premise e ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: installation
content-type: reference
topic-tags: additional-configurations
hidefromtoc: true
exl-id: 47f50bf5-4d5b-4c07-af71-de4390177cf5
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '823'
ht-degree: 1%

---

# Utilizzo dei server MX con Campaign {#using-mx-servers}



Scopri come funzionano i server MX con Adobe Campaign Classic.

## Server MX {#mx-servers}

### Che cos&#39;è un server MX?

Un record di scambio di posta (record MX) è un tipo di record di risorse nel DNS (Domain Name System) che specifica un server di posta responsabile dell&#39;accettazione dei messaggi di posta elettronica per conto di un dominio.

### Come funziona un server MX?

Quando si invia un&#39;e-mail, il server software stabilisce una connessione con il server del dominio destinatario. La comunicazione tra i due server utilizza la lingua SMTP e un dominio può avere più di un server MX. La connessione a questo dominio inizierà dalla priorità più alta (cifra più piccola) e altri server sono chiamati server di &quot;backup&quot;. Il protocollo di connessione deve essere rispettato.

### Come funziona un server MX con Adobe Campaign?

Nel protocollo di connessione devono essere rispettate le norme per prevenire lo spamming e il monopolio dei server. I più importanti sono i seguenti:

* **Numero massimo di connessioni consentite**: quando questo numero viene rispettato, gli IP non sono nel inserisco nell&#39;elenco Bloccati di e le e-mail non vengono rifiutate a causa di connessioni aggiuntive.
* **Numero massimo di messaggi**: durante la connessione, è necessario definire il numero di messaggi consentiti da inviare. Se questo numero non è definito, il server ne invierà il maggior numero possibile. Questo comporta l’identificazione come spammer e l’aggiunta al elenco Bloccati da parte dell’ISP.
* **Messaggi all&#39;ora**: per corrispondere alla tua e-reputazione, Adobe Campaign controllerà il numero di e-mail che gli IP saranno in grado di inviare all’ora. Questo sistema ti proteggerà dal rifiuto delle e-mail e/o dal inserisco nell&#39;elenco Bloccati di posta elettronica.

## E-mail in entrata

### Cos’è un’e-mail in entrata?

È il processo utilizzato da Adobe Campaign per elaborare gli errori durante le comunicazioni con il server.

### Come funziona un’e-mail in entrata?

L’indirizzo di errore elaborerà i mancati recapiti inviati dagli ISP. Il processo analizza diversi codici di errore SMTP e applica l’azione giusta secondo lo standard RegEx.

Ad esempio, un indirizzo e-mail ha un feedback &quot;550 Utente sconosciuto&quot; inviato da un ISP. Questo codice di errore viene elaborato dall’indirizzo di errore di Adobe Campaign (indirizzo del percorso di ritorno). Questo errore viene quindi confrontato con lo standard RegEx e verrà applicata la regola giusta. L’e-mail è considerata *Mancato recapito permanente* (corrispondente al tipo) e quindi *Utente sconosciuto* (corrispondente al motivo) e messo in quarantena dopo il primo ciclo nel sistema.

### Come viene gestita da Adobe Campaign?

Adobe Campaign gestisce questo processo con una corrispondenza tra un tipo di errore e un motivo:

* **[!UICONTROL User Unknown]**: indirizzo corretto dal punto di vista sintattico, ma inesistente. Questo errore viene classificato come mancato recapito permanente e messo in quarantena all’interno del primo errore.
* **[!UICONTROL Mailbox full]**: cassetta postale che ha raggiunto la capacità massima. Questo errore può anche indicare che l&#39;utente non utilizza più questa cassetta postale. Questo errore viene classificato come messaggio non recapitato e messo in quarantena entro il terzo errore, quindi rimosso dalla quarantena dopo un periodo di 30 giorni.
* **[!UICONTROL Inactive User]**: la cassetta postale è stata disattivata dall’ISP a causa di un utente inattivo negli ultimi 6 mesi. Questo errore viene classificato come messaggio non recapitato e messo in quarantena all’interno del terzo errore.
* **[!UICONTROL Invalid domain]**: il dominio nell’indirizzo e-mail non esiste. Questo errore viene classificato come messaggio non recapitato e messo in quarantena all’interno del terzo errore.
* **[!UICONTROL Refused]**: l’ISP si è rifiutato di inviare l’e-mail ai propri utenti. Questo errore è classificato come messaggio non recapitato e non viene messo in quarantena poiché non è collegato all’indirizzo e-mail ma all’IP o alla reputazione di un dominio.

>[!NOTE]
>
>Per ulteriori informazioni sui tipi e sui motivi di errori di consegna, consulta questa [sezione](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons).

## Istanza di recapito messaggi {#deliveratbility-env}

Un aggiornamento giornaliero delle regole MX e delle regole in entrata viene gestito da un flusso di lavoro specifico nell’istanza client connessa al proprietario dell’istanza Deliverability di tali regole.

Questo aggiornamento giornaliero è in esecuzione per tutti i clienti che desiderano mantenere aggiornata la propria istanza attraverso un processo di trasparenza.

Le regole MX hanno 6 diversi livelli di velocità effettiva che sono utilizzati principalmente durante il processo di incremento:

![](assets/mx-rules-throughput.png)

La modalità personalizzata è per i client avanzati che desiderano impostare le proprie regole MX. Quando viene attivata la modalità personalizzata, il client non verrà aggiornato dall’istanza del recapito messaggi in quanto la sincronizzazione verrà disattivata.

## Esempi di mancato recapito

* **Utente sconosciuto** (mancato recapito permanente): 550 5.1.1 ... Utente sconosciuto {mx003}
* **Cassetta postale piena** (mancati recapiti non permanenti): 550 5.2.2 Quota utente superata
* **Cassetta postale inattiva** (messaggio non recapitato): 550 5.7.1 : indirizzo del destinatario rifiutato: MailBox inattiva, non aperto per più di 6 mesi
* **Dominio non valido** (mancati recapiti non permanenti): query DNS non riuscita per &#39;ourdan.com&#39;
* **Rifiutato** (mancato recapito non permanente): mancato recapito e-mail in entrata (la regola &#39;Feedback_loop_Hotmail&#39; ha restituito un mancato recapito corrispondente)
* **Non raggiungibile** (mancati recapiti non permanenti): 421 4.16.55 [TS01] Messaggi da x.x.x.x temporaneamente differiti a causa di eccessivi reclami degli utenti

**Argomenti correlati:**
* [Configurazione MX](../../installation/using/email-deliverability.md#mx-configuration)
* [Configurazione tecnica delle e-mail](../../installation/using/email-deliverability.md)
* [Errori di consegna](../../delivery/using/understanding-delivery-failures.md)
* [Campaign Classic - Recommendations tecnico](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/campaign/acc-technical-recommendations.html)
