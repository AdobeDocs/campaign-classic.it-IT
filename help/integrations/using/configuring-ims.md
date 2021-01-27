---
solution: Campaign Classic
product: campaign
title: Configurazione di IMS
description: 'Scopri come connettersi tramite un Adobe ID '
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
translation-type: tm+mt
source-git-commit: db595e59f4725ba5d125e688e7bfc6d1c1a03d9f
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 2%

---


# Configurazione di IMS{#configuring-ims}

>[!IMPORTANT]
>
>&#39;implementazione IMS Adobe è strettamente riservata agli amministratori tecnici del Adobe . Contatta il responsabile del Adobe  per avviare il processo di implementazione.

## Prerequisiti {#prerequisites}

Per utilizzare l&#39;integrazione con IMS:

* È necessario disporre di un&#39;organizzazione Adobe Experience Cloud e di ID IMS (forniti al momento della prima connessione all&#39;Adobe Experience Cloud).
* È necessario aggiungere utenti nel Experience Cloud . Per ulteriori informazioni, consulta [questa pagina](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/admin-getting-started.html).

>[!NOTE]
>
>Accertatevi che gli utenti siano collegati ai gruppi Adobe Experience Cloud che verranno sincronizzati con  Adobe Campaign. Fare riferimento a [Configurazione dell&#39;account esterno](#configuring-the-external-account).

## Aggiornamento della console {#updating-the-console}

Per utilizzare questa funzionalità, è necessario installare la versione più recente della console.

## Installazione del pacchetto {#installing-the-package}

È necessario installare il pacchetto **[!UICONTROL Integration with the Adobe Experience Cloud]**. L&#39;installazione di un pacchetto di integrazione è la stessa dell&#39;installazione di un pacchetto standard, che è dettagliata in [questa pagina](../../installation/using/installing-campaign-standard-packages.md).

![](assets/ims_6.png)

## Configurazione dell&#39;account esterno {#configuring-the-external-account}

Configurare l&#39;account esterno **Adobe Experience Cloud** in **[!UICONTROL Administration > Platform > External accounts]**.

>[!CAUTION]
>
>Questa configurazione è riservata all&#39;amministratore tecnico.

![](assets/ims_5.png)

Inserite le seguenti informazioni:

* Informazioni di connessione per il server IMS utilizzato (ID e segreto). Queste informazioni sono fornite dal supporto  Adobe. Per ulteriori informazioni, consultare le [Domande frequenti per gli amministratori di Adobe Experience Cloud](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/faq.html).

   L&#39;indirizzo **[!UICONTROL Callback server]** deve essere specificato in **https**. Questo campo corrisponde all’URL di accesso dell’istanza di Adobe Campaign .

* ID organizzazione IMS: queste informazioni sono disponibili nel Experience Cloud  (in **[!UICONTROL Administration > Experience Cloud Details]** ) e vengono fornite al primo collegamento all&#39;Adobe Experience Cloud.
* Maschera di associazione: questo campo consente di definire la sintassi che consentirà la sincronizzazione dei nomi di configurazione in Enterprise Dashboard con i gruppi in  Adobe Campaign. Se utilizzi la sintassi &quot;Campaign - tenant_id - (.*)&quot;, il gruppo di sicurezza creato in  Adobe Campaign sarà collegato al nome di configurazione &quot;Campaign - tenant_id - internal_name&quot; nella dashboard di Enterprise.

   >[!CAUTION]
   >
   >La maschera di associazione è essenziale per il corretto funzionamento della connessione tramite l&#39;Adobe ID .

* Informazioni sulla connessione Adobe Experience Cloud, in particolare il nome del tenant Adobe Experience Cloud.

