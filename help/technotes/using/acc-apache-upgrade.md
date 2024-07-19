---
product: campaign
title: Nota tecnica - Adobe Campaign - Aggiornamento sulla sicurezza della versione di Apache
description: Adobe Campaign - Aggiornamento sulla sicurezza della versione di Apache
feature: Technote, Upgrade
hide: true
hidefromtoc: true
exl-id: 3d2f5d1d-4b31-4cc6-b6fb-13589856e00c
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 0%

---

# Adobe Campaign - Aggiornamento sulla sicurezza della versione di Apache {#apache-update}

>[!CAUTION]
>Questo articolo si applica a: **clienti Campaign Classic v7 Managed Services**, **clienti Campaign v8** e **clienti Campaign Standard**.

Adobe Campaign funziona con strumenti di terze parti e la compatibilità viene aggiornata regolarmente, al fine di implementare solo le versioni supportate e beneficiare delle correzioni e dei miglioramenti più recenti.

Adobe Campaign include Apache Tomcat che funge da punto di ingresso nel server applicazioni tramite HTTP ed è integrato con il server web Apache. Apache Software Foundation ha rilasciato Apache HTTP Server 2.4.53. Questa versione affronta le vulnerabilità che possono consentire a un utente malintenzionato remoto di prendere il controllo di un sistema interessato. Ulteriori informazioni sono disponibili nell&#39;annuncio di [Apache 2.4.53](https://downloads.apache.org/httpd/Announcement2.4.html){target="_blank"}.

Il team di Adobe Campaign eseguirà l’attività di aggiornamento della sicurezza della versione di Apache entro il **15 giugno 2022** per mitigare questa vulnerabilità di Apache e rendere più sicuro l’ambiente delle istanze. Questo aggiornamento si applica a tutti i clienti Campaign Classic v7 Managed Services, Campaign v8 e Campaign Standard che eseguono su una versione vulnerabile di Apache HTTP Server. Se sei interessato, Adobe ti ha già contattato per informarti su questo aggiornamento.

Questo aggiornamento dovrebbe essere eseguito automaticamente al di fuori del normale orario di lavoro per consentire di continuare a utilizzare il servizio Campaign senza interruzioni.

Le istanze non di produzione verranno aggiornate prima da Adobe, quindi le istanze di produzione verranno aggiornate. Poiché si tratta di un processo di aggiornamento automatico di proprietà di Adobe, non è necessaria alcuna azione da parte tua. Tuttavia, in caso di problemi, contatta [l&#39;Assistenza clienti Adobe](https://experienceleague.adobe.com/?support-solution=Campaign#support).


>[!NOTE]
>Questo aggiornamento richiede il riavvio del server web Apache. I tempi di inattività non superano i 10 minuti nell&#39;intervallo indicato di seguito.
> 

## Domande frequenti {#apache-faq}

* **Perché si tratta di un aggiornamento obbligatorio?**

  L’attuale versione di Apache è vulnerabile e presenta una potenziale minaccia per la sicurezza. È importante che le istanze di Campaign siano aggiornate alla versione di Apache più recente applicabile per evitare rischi per la sicurezza.

* **Quali clienti sono destinatari degli aggiornamenti di sicurezza?**

  Tutti i clienti che utilizzano ambienti Campaign implementati su versioni precedenti di Apache vengono aggiornati all’ultima versione di Apache applicabile.

* **Quali sono i tempi di inattività previsti?**

  Il tempo di inattività previsto è inferiore a 10 minuti.

* **Sono richieste azioni dal cliente per questo aggiornamento della sicurezza?**

  Non è richiesta alcuna azione poiché l&#39;aggiornamento della sicurezza verrà eseguito automaticamente.

* **Qual è l&#39;impatto sulle campagne/flussi di lavoro in esecuzione durante l&#39;intervallo di manutenzione?**

  Durante la finestra di manutenzione, il flusso di lavoro e i servizi di posta verranno entrambi arrestati e le attività pianificate non saranno in esecuzione. Tutte le attività in corso o i processi in esecuzione verranno interrotti durante il tempo di inattività fino al riavvio del server. Una volta completata l’attività e riavviato il server, tutti i servizi riprenderanno.

* **Quali convalide devono essere eseguite dai clienti?**

  Non sono necessari test specifici per questo aggiornamento della sicurezza. In caso di problemi, contatta [l&#39;Assistenza clienti Adobe](https://experienceleague.adobe.com/?support-solution=Campaign#support).


* **Posso richiedere una modifica di data/ora nello slot di aggiornamento della sicurezza pianificato?**

  Poiché si tratta di una correzione di sicurezza, si consiglia vivamente di adattarsi alla pianificazione esistente.


Per qualsiasi altra domanda, puoi contattare [l&#39;Assistenza clienti Adobe](https://experienceleague.adobe.com/?support-solution=Campaign#support).
