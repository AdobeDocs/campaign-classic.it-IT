---
product: campaign
title: 'Nota tecnica: aggiorna l’ambiente per la connessione ad Adobe Campaign con IMS'
description: Campaign - Aggiornamenti IMS
feature: Technote, Upgrade
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
exl-id: ecb5a258-a150-46a3-8b83-2b2c06d873ee
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '569'
ht-degree: 6%

---

# Aggiornare l’ambiente per connettersi ad Adobe Campaign con IMS {#acc-ims-faq}



Il 30 giugno 2021 sono state apportate modifiche a [Adobe di sistema Identity Management](https://helpx.adobe.com/it/enterprise/using/users.html) Funzionalità di accesso (IMS) che potrebbero influire sulla capacità di continuare a utilizzare Adobe Campaign. Scopri come continuare a utilizzare Adobe Campaign Classic v7 senza interruzioni.

## Cosa è cambiato?

Adobe Il servizio Identity Management (IMS) non supporta più le versioni precedenti di Internet Explorer in **30 giugno 2021**. [Ulteriori informazioni](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html).

Adobe vuole preservare la funzionalità IMS per tutti i clienti oltre il 30 giugno 2021. IMS fa parte del framework di sicurezza che consente agli utenti di accedere alla console client, e quindi ad Adobe Campaign.

Per mantenere questa funzionalità, i clienti devono aggiornare la console client sul computer di ogni utente e garantire l’ultimo aggiornamento della [Versione di Windows](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems), con **Internet Explorer 11** incorporato, è installato sul computer di ogni utente.

## Sei interessato?

Se ti connetti a Campaign [tramite un Adobe ID](../../integrations/using/about-adobe-id.md), tramite Identity Management Service (IMS) di Adobe ed eseguendo una versione di Campaign precedente a quelle elencate di seguito, sei interessato.

Se è già stato eseguito l&#39;aggiornamento ma si utilizza una versione precedente di Microsoft Internet Explorer, è necessario eseguire l&#39;aggiornamento a Internet Explorer 11.

## Come si esegue l’aggiornamento?

* In qualità di cliente in hosting, Adobe ha già aggiornato le istanze alla versione più recente.

* In qualità di cliente on-premise/ibrido, devi effettuare l’aggiornamento a una delle versioni più recenti elencate in precedenza per beneficiare della nuova Client Console e garantire una transizione fluida **prima del 30 giugno 2021**.

  L’aggiornamento a una delle nuove versioni elencate di seguito è obbligatorio:

   * Voce principale: Gold Standard 11. [Ulteriori informazioni](../../rn/using/gold-standard.md)
   * Campaign versione 21.1.3. [Ulteriori informazioni](../../rn/using/latest-release.md)
   * Campaign versione 20.2.5.
   * Campaign versione 20.1.4.
   * Campaign versione 19.2.4.

  Queste versioni sono dotate di un nuovo protocollo di connessione. L’aggiornamento è obbligatorio sia per il server Campaign che per la console client: una volta aggiornate tutte le istanze, anche la console client deve essere aggiornata a questa versione per poter connettersi a Campaign dopo **30 giugno 2021**.

Inoltre, assicurati di aver aggiornato [Versione di Windows](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems), con **Internet Explorer 11** incorporato, è installato sul computer di ogni utente.

## Domande frequenti

**Come posso controllare la versione di Campaign?**

Scopri come controllare la versione [in questa sezione](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).


**Come posso verificare se utilizzo IMS?**

Per controllare la modalità di connessione, è possibile:

* Avvia la console client di Campaign e accedi alle impostazioni di connessione dell’istanza. Se il **Connettersi con un Adobe ID** è selezionata, stai utilizzando Adobe IMS.

  ![](../../integrations/using/assets/ims_1.png)

o

* Avvia Campaign Client Console e controlla la finestra di connessione. Se ti connetti a un’Adobe ID, come mostrato nella schermata seguente, stai utilizzando IMS.

  ![](../../integrations/using/assets/adobeID.png)

**Messaggio di avviso di connessione**

Il seguente messaggio di avviso è visibile agli utenti che devono aggiornare la console client o utilizzare una versione precedente di Microsoft Internet Explorer: **Devi installare la versione più recente aggiornata a Windows e/o alle tue app di Adobe.**

![](../../integrations/using/assets/do-not-localize/errorMsg.png)

Se viene visualizzato questo avviso, assicurarsi di installare gli aggiornamenti più recenti del sistema operativo in uso. [Ulteriori informazioni](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html)

Se la versione di Internet Explorer non è stata aggiornata, viene visualizzato il seguente messaggio e non è più possibile connettersi a Adobe Campaign:

![](../../integrations/using/assets/do-not-localize/errorUpdateReq.png)

>[!NOTE]
>
>Per qualsiasi domanda su queste modifiche, contatta [Adobe Customer Care](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).
>

## Collegamenti utili

* [Aggiornare l’ambiente](../../production/using/build-upgrade.md)
* [Domande frequenti sull’aggiornamento della build](../../platform/using/faq-build-upgrade.md)
* [Rendi la nuova Client Console disponibile agli utenti](../../installation/using/client-console-availability-for-windows.md)
* [Installare la console client di Campaign](../../installation/using/installing-the-client-console.md)
* [Accedere a Distribuzione di software Adobe](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=it)
* [Scarica build Campaign Classic](https://experience.adobe.com/#/downloads/content/software-distribution/it/campaign.html)
