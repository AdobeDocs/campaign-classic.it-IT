---
product: campaign
title: Server di messaggistica
description: Server di messaggistica
feature: Installation, Instance Settings
badge-v7-prem: label="on-premise e ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: d9ffa58d-81e3-4291-8502-3cb7c326b666
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 4%

---

# Server di messaggistica{#messaging-server}



Adobe Campaign gestisce le e-mail in uscita in modo nativo, tuttavia è necessario un server e-mail tradizionale per ricevere i messaggi in arrivo collegati alle e-mail restituite (dai daemon di mailer). Le cassette postali configurate su questo server verranno elaborate automaticamente dall&#39;applicazione.

Tutti i server configurati per l&#39;accesso POP3 possono essere utilizzati per ricevere la posta di ritorno se conservano le intestazioni SMTP &quot;Message-ID&quot; durante il prelievo. Ad esempio, le implementazioni che utilizzano Qmail, SendMail e Microsoft Exchange sono attualmente in produzione. Tuttavia, alcune installazioni di Lotus Notes/domino hanno rivelato un problema con la gestione delle intestazioni &quot;Message-Id&quot;.

>[!CAUTION]
>
>Questo server di posta potrebbe dover gestire carichi pesanti: nelle fasi iniziali, gli elenchi tipici possono produrre tassi di mancato recapito fino al 10% (se invii 100.000 messaggi, prevedi di ricevere 10.000 mancati recapiti).
>
>Per questo motivo consigliamo di non utilizzare il server di messaggistica aziendale per questa attività, in quanto può essere fortemente interessata.
>
>È consigliabile configurare un sottodominio specifico del DNS e un server dedicato per la posta non recapitata.
