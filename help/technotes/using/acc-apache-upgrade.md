---
product: campaign
title: Nota tecnica - Adobe Campaign - Aggiornamento per la sicurezza della versione Apache
description: Adobe Campaign - Aggiornamento sulla sicurezza della versione Apache
hide: true
hidefromtoc: true
exl-id: 3d2f5d1d-4b31-4cc6-b6fb-13589856e00c
source-git-commit: 7ee1cc501342aa59d1752259bf7228ea47a8cccb
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# Adobe Campaign - Aggiornamento sulla sicurezza della versione Apache {#apache-update}

>[!CAUTION]
>Il presente articolo si applica: Clienti Campaign Classic v7 Managed Services, clienti Campaign v8 e clienti Campaign Standard.

Adobe Campaign funziona con strumenti di terze parti e la compatibilità viene aggiornata regolarmente, al fine di implementare solo le versioni supportate e beneficiare delle ultime correzioni e miglioramenti.

Adobe Campaign include Apache Tomcat che funge da punto di ingresso nell&#39;application server tramite HTTP ed è integrato con il server web Apache. Apache Software Foundation ha rilasciato Apache HTTP Server 2.4.53. Questa versione risolve le vulnerabilità che potrebbero consentire a un autore remoto dell&#39;attacco di prendere il controllo di un sistema interessato. Ulteriori informazioni in [Annuncio Apache 2.4.53](https://downloads.apache.org/httpd/Announcement2.4.html){target=&quot;_blank&quot;}.

Il team Adobe Campaign eseguirà l’attività di aggiornamento della sicurezza della versione di Apache tramite **15 giugno 2022** per attenuare questa vulnerabilità di Apache e rendere l’ambiente di istanza più sicuro. Questo aggiornamento si applica a tutti i clienti Managed Services Campaign Classic v7, Campaign v8 e Campaign Standard in esecuzione su una versione vulnerabile di Apache HTTP Server. Se sei interessato, Adobe ti ha già contattato per informarti di questo aggiornamento.

Questo aggiornamento deve essere eseguito automaticamente al di fuori del normale orario di lavoro per consentire di continuare a utilizzare il servizio Campaign senza interruzioni.

Le istanze non di produzione verranno aggiornate dai nostri team prima di aggiornare le istanze di produzione. Poiché si tratta di un processo di aggiornamento automatico di proprietà di Adobe, non è necessaria alcuna azione da parte dell’utente. Tuttavia, se riscontri dei problemi, contatta [Adobe Customer Care](https://experienceleague.adobe.com/?support-solution=Campaign#support).


>[!NOTE]
>Questo aggiornamento richiede il riavvio del server web Apache. I tempi di inattività non supereranno i 10 minuti entro il periodo di tempo indicato di seguito.

## Domande frequenti {#apache-faq}

* **Perché questo è un aggiornamento obbligatorio?**

   L&#39;attuale versione di Apache è vulnerabile e presenta una potenziale minaccia per la sicurezza. È importante che le istanze Campaign siano aggiornate all’ultima versione di Apache applicabile per affrontare il rischio di sicurezza.

* **Quali clienti sono interessati agli aggiornamenti di sicurezza?**

   Tutti i clienti che utilizzano gli ambienti Campaign implementati nelle versioni precedenti di Apache vengono aggiornati alla versione più recente applicabile di Apache.

* **Quali sono i tempi di inattività previsti?**

   Il tempo di inattività previsto è inferiore a 10 minuti.

* **Il cliente deve effettuare l’aggiornamento della sicurezza?**

   Non è necessaria alcuna azione, in quanto l’aggiornamento della sicurezza verrà eseguito automaticamente.

* **Qual è l’impatto sulle campagne/flussi di lavoro in esecuzione durante la finestra di manutenzione?**

   Durante la finestra di manutenzione, il flusso di lavoro e i servizi di posta vengono entrambi interrotti e le attività pianificate non saranno in esecuzione. Tutte le attività o i processi in corso verranno interrotti durante il periodo di inattività fino al riavvio del server. Una volta completata l&#39;attività e riavviato il server, tutti i servizi riprenderanno.

* **Quali convalide devono essere eseguite dai clienti?**

   Non è necessario eseguire test specifici per questo aggiornamento della sicurezza. Nel caso in cui venga osservato un problema, contatta [Adobe Customer Care](https://experienceleague.adobe.com/?support-solution=Campaign#support)


* **Posso richiedere una modifica in data/ora allo slot di aggiornamento della sicurezza pianificato?**

   Poiché si tratta di una correzione di sicurezza, ti consigliamo vivamente di adattarti alla pianificazione esistente.


Per qualsiasi altra domanda, puoi rivolgerti a [Adobe Customer Care](https://experienceleague.adobe.com/?support-solution=Campaign#support).
