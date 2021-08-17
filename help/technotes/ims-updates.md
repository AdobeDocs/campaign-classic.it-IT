---
product: campaign
title: Aggiorna l’ambiente per connetterti ad Adobe Campaign con IMS
description: Campaign - Aggiornamenti IMS
hide: true
hidefromtoc: true
source-git-commit: 6a5253c1aa35e904635919f6c863930d376b473f
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 9%

---

# Come aggiornare l’ambiente per connettersi ad Adobe Campaign con IMS {#acc-ims-faq}

Il 30 giugno 2021 verranno apportate modifiche alle funzionalità di accesso [Adobe Identity Management System](https://helpx.adobe.com/enterprise/using/identity.html) (IMS) che potrebbero influire sulla capacità di continuare a utilizzare Adobe Campaign. Scopri come continuare a utilizzare Adobe Campaign Classic v7 senza interruzioni.

## Cosa è cambiato?

Adobe Identity Management Service (IMS) smetterà di supportare le versioni precedenti di Internet Explorer dal **30 giugno 2021**. [Ulteriori informazioni](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html).

Adobe intende preservare la funzionalità IMS per tutti i clienti a partire dal 30 giugno 2021. IMS fa parte del framework di sicurezza che consente agli utenti di accedere alla console client, quindi ad Adobe Campaign.

Per mantenere questa funzionalità, i clienti devono aggiornare la Console client sul computer di ogni utente e assicurarsi che l&#39;aggiornamento più recente della [versione di Windows](../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems), con **Internet Explorer 11** incorporato, sia installato sul computer di ogni utente.

## Sei interessato da questo problema?

Se ti connetti a Campaign [tramite un Adobe ID](../integrations/using/about-adobe-id.md), tramite Adobe Identity Management Service (IMS) ed esegui una versione di Campaign precedente a quella indicata di seguito, sei interessato.

Se è già stato eseguito l&#39;aggiornamento ma si utilizza una versione precedente di Microsoft Internet Explorer, è necessario eseguire l&#39;aggiornamento a Internet Explorer 11.

## Come si esegue l’aggiornamento?

* In qualità di cliente in hosting, Adobe ha già aggiornato le istanze alla versione più recente.

* In qualità di cliente on-premise/ibrido, è necessario eseguire l’aggiornamento a una delle versioni più recenti elencate in precedenza per beneficiare della nuova console client e garantire una transizione senza soluzione di continuità **prima del 30 giugno 2021**.

   L’aggiornamento a una delle nuove versioni elencate di seguito è obbligatorio:

   * Gold Standard 11. [Ulteriori informazioni](../rn/using/gold-standard.md)
   * Campaign versione 21.1.3. [Ulteriori informazioni](../rn/using/latest-release.md)
   * Campaign versione 20.2.5. [Ulteriori informazioni](../rn/using/release--20-2.md)
   * Campaign versione 20.1.4. [Ulteriori informazioni](../rn/using/release--20-1.md)
   * Campaign versione 19.2.4. [Ulteriori informazioni](../rn/using/release--19-2.md)
   * Campaign versione 19.1.8. [Ulteriori informazioni](../rn/using/release--19-1.md)

   Queste versioni hanno un nuovo protocollo di connessione. L’aggiornamento è obbligatorio sia per il server Campaign che per la console client: dopo l’aggiornamento di tutte le istanze, è necessario aggiornare anche la console client a questa versione per potersi connettere a Campaign dopo il **30 giugno 2021**.

Inoltre, assicurati che l&#39;ultimo aggiornamento della tua [versione di Windows](../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems), con **Internet Explorer 11** integrata, sia installato sul computer di ogni utente.

## Domande frequenti

**Come posso controllare la mia versione di Campaign?**

Scopri come controllare la versione [in questa sezione](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).


**Come posso verificare se utilizzo IMS?**

Per controllare la modalità di connessione, puoi:

* Avvia la console client di Campaign e accedi alle impostazioni di connessione dell’istanza. Se è selezionata l&#39;opzione **Connetti con un Adobe ID**, stai utilizzando Adobe IMS.

   ![](../integrations/using/assets/ims_1.png)

o

* Avvia la console client di Campaign e controlla la finestra di connessione. Se ti connetti a un Adobe ID, come mostrato nella schermata seguente, stai utilizzando IMS.

   ![](../integrations/using/assets/adobeID.png)

**Messaggio di avviso della connessione**

Gli utenti possono visualizzare il seguente messaggio di avviso se hanno bisogno di aggiornare la propria Console client o utilizzare una versione precedente di Microsoft Internet Explorer: **È necessario installare l&#39;ultimo aggiornamento a Windows e/o alle app Adobi.**

![](../integrations/using/assets/do-not-localize/errorMsg.png)

Se viene visualizzato un avviso di questo tipo, assicurarsi di installare gli aggiornamenti più recenti del sistema operativo in uso. [Ulteriori informazioni](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html)

**Dopo il 30 giugno 2021**, verrà visualizzato il seguente messaggio e non sarà più possibile connettersi ad Adobe Campaign:

![](../integrations/using/assets/do-not-localize/errorUpdateReq.png)

>[!NOTE]
>
>Per qualsiasi domanda su queste modifiche, contatta [Adobe Customer Care](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).


## Collegamenti utili

* [Aggiornare l’ambiente](../production/using/build-upgrade.md)
* [Domande frequenti sull’aggiornamento della build](../platform/using/faq-build-upgrade.md)
* [Rendere la nuova console client disponibile agli utenti](../installation/using/client-console-availability-for-windows.md)
* [Installare la console client di Campaign](../installation/using/installing-the-client-console.md)
* [Accedere alla distribuzione software di Adobe](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=en)
* [Scarica la build Campaign Classic](https://experience.adobe.com/#/downloads/content/software-distribution/it/campaign.html)