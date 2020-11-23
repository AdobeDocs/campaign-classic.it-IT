---
solution: Campaign Classic
product: campaign
title: Avvio di una nuova piattaforma con Adobe Campaign Classic
description: Scopri di più sulla gestione del recapito quando si avvia una nuova piattaforma con Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 1%

---


# Avvio di una nuova piattaforma {#starting-new-platform}

Mantenere la reputazione del dominio e dell&#39;indirizzo IP è fondamentale quando si configura una nuova piattaforma.

* L&#39;invio di e-mail è un passaggio sensibile in quanto la piattaforma non dispone di alcuna cronologia di utilizzo e, quando gli IP di invio non sono mai stati utilizzati a questo scopo, non ha alcuna reputazione.

* Gli ISP sono naturalmente sospettosi degli indirizzi IP che non sono mai stati utilizzati per inviare email e che improvvisamente iniziano a inviare grandi volumi di traffico email. Infatti, gli spammer generalmente utilizzano indirizzi IP &quot;sconosciuti&quot; (indirizzi che non sono mai stati elenco Bloccati) per inviare il maggior numero possibile di messaggi prima del rilevamento.

* Non ci si può aspettare di raggiungere la velocità operativa in termini di output all&#39;inizio della fase di produzione. Inoltre, non si dovrebbe tentare di inviare messaggi a questo tasso, in quanto potrebbe indurre gli ISP a bloccare gli indirizzi di invio e a compromettere gravemente il resto della fase di avvio.

Di seguito sono elencati i principi principali da seguire per l&#39;avvio di una nuova piattaforma:

* Se si dispone di queste informazioni, **importare indirizzi non validi nella tabella**di quarantena.
L&#39;avvio di una piattaforma spesso avviene quando si utilizza per la prima volta un elenco di indirizzi che potrebbero non essere completi. Se si inviano indirizzi non validi o a indirizzi in honeypot, ciò contribuirà a ridurre la reputazione della piattaforma.

   * Se si dispone di un elenco di indirizzi non validi, è nell&#39;interesse dell&#39;utente importarlo nella tabella di quarantena (disponibile tramite il **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]** menu) prima di inviarlo per la prima volta.
   * Se, comunque, si desidera riqualificare gli indirizzi non validi, è di gran lunga preferibile farlo una volta che la reputazione della piattaforma è stabilita e un po&#39; alla volta, al fine di &quot;diluire&quot; l&#39;uso di indirizzi cattivi nel tempo.

   Per ulteriori informazioni, consulta [Ottimizzazione della consegna tramite quarantena](../../delivery/using/understanding-quarantine-management.md#optimizing-your-delivery-through-quarantines).
* **Limita la velocità** effettiva limitando il numero di schede. Per ulteriori informazioni sulla regolazione di tale impostazione tecnica, contattate il vostro amministratore  Adobe Campaign.
* **Aumentare progressivamente i volumi inviati** per evitare di essere contrassegnati come spam. Non eseguite il targeting dell&#39;intero database fin dall&#39;inizio, ma aggiungete una frazione extra dell&#39;elenco ogni volta che inviate. Questo dovrebbe consentire di aumentare il volume in ogni fase, riducendo al contempo il tasso complessivo di indirizzi non validi. Per garantire uno sviluppo uniforme della fase di avvio, è possibile utilizzare le onde. Per ulteriori informazioni, consultate [Invio con più onde](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves).
* **Invia regolarmente**. In una certa misura è meglio inviare regolarmente piccole riprese piuttosto che campagne di grandi dimensioni sporadicamente.
* **Presta particolare attenzione ai rapporti** di consegna. Indicatori di errore elevati possono indicare che un&#39;impostazione tecnica è configurata male. Per ulteriori informazioni, consulta [Monitoraggio della distribuzione](../../delivery/using/monitoring-a-delivery.md).

**Argomenti correlati**:
* [Aumenta la tua reputazione di email con il riscaldamento IP](https://helpx.adobe.com/campaign/kb/increase-email-rep-ip-warming.html)
* [Tutte le trappole dello spam](https://helpx.adobe.com/campaign/kb/spam-traps.html)