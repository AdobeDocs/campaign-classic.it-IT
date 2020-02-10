---
title: Avvio di una nuova piattaforma con Adobe Campaign Classic
description: Scopri di più sulla gestione della recapito quando avvii una nuova piattaforma con Adobe Campaign Classic.
page-status-flag: never-activated
uuid: 2681042b-3018-42ae-b252-2367b56616bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 6a394eeb-fbe1-4712-bb13-db5d7965fb73
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 68756f920fbc8658cff552615adbf023b4c5e3aa

---


# Avvio di una nuova piattaforma {#starting-new-platform}

Mantenere la reputazione del dominio e dell&#39;indirizzo IP è fondamentale. Di seguito troverete alcuni consigli per la configurazione di una nuova piattaforma.

L&#39;invio di e-mail su una nuova piattaforma è un passaggio sensibile in quanto la piattaforma non dispone di alcuna cronologia di utilizzo e non ha alcuna reputazione (quando gli IP di invio non sono mai stati utilizzati a questo scopo). Gli ISP sono naturalmente sospettosi degli indirizzi IP che non sono mai stati utilizzati per inviare email e che improvvisamente iniziano a inviare grandi volumi di traffico email. In effetti, gli spammer generalmente utilizzano indirizzi IP &quot;sconosciuti&quot; (cioè indirizzi che non sono mai stati inseriti in blacklist) per inviare il maggior numero possibile di messaggi prima del rilevamento.

Non ci si può aspettare di raggiungere la velocità operativa in termini di output all&#39;inizio della fase di produzione. Inoltre, non si dovrebbe tentare di inviare messaggi a questo tasso, in quanto potrebbe indurre gli ISP a bloccare gli indirizzi di invio e a compromettere gravemente il resto della fase di avvio.

L&#39;avvio di una piattaforma spesso avviene quando si utilizza per la prima volta un elenco di indirizzi che potrebbero non essere completi. Se invii a indirizzi non validi o a indirizzi in honeypot, ciò contribuirà a ridurre la reputazione della piattaforma. Se si dispone di un elenco di indirizzi non validi, è nell&#39;interesse dell&#39;utente importarlo nella tabella di quarantena (**[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**) prima di inviarlo per la prima volta. Se, comunque, si desidera riqualificare gli indirizzi non validi, è di gran lunga preferibile farlo una volta che la reputazione della piattaforma è stabilita e un po&#39; alla volta, al fine di &quot;diluire&quot; l&#39;uso di indirizzi cattivi nel tempo.

Per riassumere i principi da seguire all&#39;avvio:

* Importazione di indirizzi non validi nella tabella di quarantena (se si dispone di tali informazioni)
* Limitazione della velocità effettiva (impostazione tecnica: limitazione del numero di campioni)
* Incremento progressivo dei volumi inviati: Non eseguire il targeting dell&#39;intero database fin dall&#39;inizio, ma aggiungere una frazione extra dell&#39;elenco ogni volta che si invia; questo dovrebbe consentire di aumentare il volume in ogni fase, riducendo al contempo il tasso complessivo di indirizzi non validi
* Invio regolare: In una certa misura è meglio inviare regolarmente piccole riprese rispetto alle campagne più grandi
* Presta particolare attenzione ai rapporti di consegna: indicatori di errore elevati possono indicare che un&#39;impostazione tecnica non è configurata correttamente.