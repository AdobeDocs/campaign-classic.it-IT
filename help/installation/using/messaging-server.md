---
product: campaign
title: Server di messaggistica
description: Server di messaggistica
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: d9ffa58d-81e3-4291-8502-3cb7c326b666
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 3%

---

# Server di messaggistica{#messaging-server}



Adobe Campaign gestisce le e-mail in uscita in modo nativo, tuttavia è necessario un server e-mail tradizionale per ricevere i messaggi in arrivo collegati alle e-mail restituite (dai daemon del mailer). Le cassette postali configurate su questo server verranno elaborate automaticamente dall&#39;applicazione.

Tutti i server configurati per l&#39;accesso POP3 possono essere utilizzati per ricevere la posta di ritorno se mantengono le intestazioni SMTP &quot;Message-ID&quot; durante il prelievo della posta. Ad esempio, le implementazioni che utilizzano Qmail, SendMail e Microsoft Exchange sono attualmente in produzione. Tuttavia, alcune installazioni di Lotus Notes/domino hanno rivelato un problema con la manutenzione delle intestazioni &quot;Message-Id&quot;.

>[!CAUTION]
>
>Questo server di posta potrebbe dover gestire carichi pesanti: Nelle fasi iniziali, gli elenchi tipici possono produrre fino al 10% di tassi non raggiunti (se invii 100.000 messaggi, riceverai 10.000 messaggi non recapitati).
>
>Per questo motivo sconsigliamo di utilizzare il server di messaggistica aziendale per questa attività in quanto può essere fortemente influenzato.
>
>È consigliabile configurare un sottodominio specifico del DNS e un server dedicato per la posta non recapitata.
