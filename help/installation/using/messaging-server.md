---
title: Server di messaggistica
seo-title: Server di messaggistica
description: Server di messaggistica
seo-description: null
page-status-flag: never-activated
uuid: d7de0405-23eb-4a0d-80a5-c75d661771bb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
discoiquuid: 1556e87f-9d92-4548-a75a-4f44030ab8d5
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 4%

---


# Server di messaggistica{#messaging-server}

 Adobe Campaign gestisce in modo nativo le e-mail in uscita, tuttavia è necessario un server e-mail tradizionale per ricevere i messaggi in arrivo collegati alle e-mail restituite (dai demoni della posta elettronica). Le cassette postali configurate su questo server verranno elaborate automaticamente dall&#39;applicazione.

Tutti i server configurati per l&#39;accesso POP3 possono essere utilizzati per ricevere la posta se mantengono le intestazioni SMTP &quot;Message-ID&quot; durante la raccolta della posta. Ad esempio, le implementazioni che utilizzano Qmail, SendMail e Microsoft Exchange sono attualmente in produzione. Tuttavia, alcune installazioni di Lotus Notes/domino hanno rivelato un problema con la manutenzione delle intestazioni &quot;Message-Id&quot;.

>[!CAUTION]
>
>Questo mail server potrebbe dover gestire carichi pesanti: Nelle fasi iniziali, gli elenchi tipici possono generare fino al 10% di tassi di rimbalzo (se si inviano 100.000 messaggi, si prevede di ricevere 10.000 rimbalzi).
>
>È per questo che consigliamo di non utilizzare il server di messaggistica aziendale per questa attività, in quanto può essere fortemente influenzato.
>
>È consigliabile configurare un sottodominio specifico del DNS e un server dedicato per la posta di rimbalzo.
