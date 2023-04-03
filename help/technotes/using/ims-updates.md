---
product: campaign
title: 'Nota tecnica: aggiorna l’ambiente per collegarti ad Adobe Campaign con IMS'
description: Campaign - Aggiornamenti IMS
exl-id: ecb5a258-a150-46a3-8b83-2b2c06d873ee
source-git-commit: bdccc4ee7cbb8c765d488879f99677b2302d32e7
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 9%

---

# Come aggiornare l’ambiente per connettersi ad Adobe Campaign con IMS {#acc-ims-faq}

![](../../assets/v7-only.svg)

Il 30 giugno 2021 sono state apportate modifiche a [Adobe Identity Management System](https://helpx.adobe.com/enterprise/using/identity.html) (IMS) funzionalità di accesso che potrebbero influire sulla tua capacità di continuare a utilizzare Adobe Campaign. Scopri come continuare a utilizzare Adobe Campaign Classic v7 senza interruzioni.

## Cosa è cambiato?

Adobe Identity Management Service (IMS) ha smesso di supportare le vecchie versioni di Internet Explorer in **30 giugno 2021**. [Ulteriori informazioni](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html).

Adobe intende preservare la funzionalità IMS per tutti i clienti a partire dal 30 giugno 2021. IMS fa parte del framework di sicurezza che consente agli utenti di accedere alla console client, quindi ad Adobe Campaign.

Per mantenere questa funzionalità, i clienti devono aggiornare la console client sul computer di ogni utente e assicurarsi che l’aggiornamento più recente del [Versione di Windows](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)con **Internet Explorer 11** incorporato, è installato sul computer di ogni utente.

## Sei interessato da questo problema?

Se ti connetti a Campaign [tramite un Adobe ID](../../integrations/using/about-adobe-id.md), l’impatto è causato dall’esecuzione di una versione di Campaign precedente a quella indicata di seguito, tramite Adobe Identity Management Service (IMS) e da una versione di Campaign precedente.

Se è già stato eseguito l&#39;aggiornamento ma si utilizza una versione precedente di Microsoft Internet Explorer, è necessario eseguire l&#39;aggiornamento a Internet Explorer 11.

## Come si esegue l’aggiornamento?

* In qualità di cliente in hosting, Adobe ha già aggiornato le istanze alla versione più recente.

* In qualità di cliente on-premise/ibrido, è necessario effettuare l’aggiornamento a una delle versioni più recenti elencate sopra per beneficiare della nuova console Client e garantire una transizione senza soluzione di continuità **prima del 30 giugno 2021**.

   L’aggiornamento a una delle nuove versioni elencate di seguito è obbligatorio:

   * Gold Standard 11. [Ulteriori informazioni](../../rn/using/gold-standard.md)
   * Campaign versione 21.1.3. [Ulteriori informazioni](../../rn/using/latest-release.md)
   * Campaign versione 20.2.5. [Ulteriori informazioni](../../rn/using/release--2020.md#release-20-2-5-build-9188)
   * Campaign versione 20.1.4. [Ulteriori informazioni](../../rn/using/release--2020.md#release-20-1-4-build-9126)
   * Campaign versione 19.2.4. [Ulteriori informazioni](../../rn/using/release--2019.md#release-19-2-4-build-9082)

   Queste versioni hanno un nuovo protocollo di connessione. L’aggiornamento è obbligatorio sia per il server Campaign che per la console client: una volta aggiornate tutte le istanze, è necessario aggiornare anche la console client a questa versione per potersi connettere a Campaign dopo l’aggiornamento **30 giugno 2021**.

Inoltre, assicurati l&#39;ultimo aggiornamento della [Versione di Windows](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)con **Internet Explorer 11** incorporato, è installato sul computer di ogni utente.

## Domande frequenti

**Come posso controllare la mia versione di Campaign?**

Scopri come controllare la versione [in questa sezione](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).


**Come posso verificare se utilizzo IMS?**

Per controllare la modalità di connessione, puoi:

* Avvia la console client di Campaign e accedi alle impostazioni di connessione dell’istanza. Se la **Connettersi con un Adobe ID** è selezionata, stai utilizzando Adobe IMS.

   ![](../../integrations/using/assets/ims_1.png)

o

* Avvia la console client di Campaign e controlla la finestra di connessione. Se ti connetti a un Adobe ID, come mostrato nella schermata seguente, stai utilizzando IMS.

   ![](../../integrations/using/assets/adobeID.png)

**Messaggio di avviso della connessione**

Gli utenti possono visualizzare il seguente messaggio di avviso se hanno bisogno di aggiornare la propria console Client o utilizzare una versione precedente di Microsoft Internet Explorer: **È necessario installare l&#39;ultimo aggiornamento a Windows e/o alle app di Adobe.**

![](../../integrations/using/assets/do-not-localize/errorMsg.png)

Se viene visualizzato un avviso di questo tipo, assicurarsi di installare gli aggiornamenti più recenti del sistema operativo in uso. [Ulteriori informazioni](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html)

Se la versione di Internet Explorer non è stata aggiornata, viene visualizzato il seguente messaggio e non è più possibile connettersi ad Adobe Campaign:

![](../../integrations/using/assets/do-not-localize/errorUpdateReq.png)

>[!NOTE]
>
>Per qualsiasi domanda su queste modifiche, contatta [Adobe Customer Care](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Collegamenti utili

* [Aggiornare l’ambiente](../../production/using/build-upgrade.md)
* [Domande frequenti sull’aggiornamento della build](../../platform/using/faq-build-upgrade.md)
* [Rendere la nuova console client disponibile agli utenti](../../installation/using/client-console-availability-for-windows.md)
* [Installare la console client di Campaign](../../installation/using/installing-the-client-console.md)
* [Accedere alla distribuzione software di Adobe](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=en)
* [Scarica la build Campaign Classic](https://experience.adobe.com/#/downloads/content/software-distribution/it/campaign.html)
