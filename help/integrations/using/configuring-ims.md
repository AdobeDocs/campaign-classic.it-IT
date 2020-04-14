---
title: Configurazione di IMS
seo-title: Configurazione di IMS
description: Configurazione di IMS
seo-description: null
page-status-flag: never-activated
uuid: b659d29f-2a27-4a7b-b5ca-f44c3271dd4e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
discoiquuid: 279d0548-c876-4d5f-a195-48618bd5e9d1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0a4272ae13b469c7c17b8c3afa9748cbfbcf07ff

---


# Configurazione di IMS{#configuring-ims}

## Prerequisiti {#prerequisites}

Per utilizzare l&#39;integrazione con IMS:

* Devi disporre di un’organizzazione Adobe Experience Cloud e di un ID IMS (forniti al momento della prima connessione ad Adobe Experience Cloud).
* Devi aggiungere utenti in Experience Cloud. For more on this, refer to [this page](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/admin-getting-started.html).

>[!NOTE]
>
>Assicurati che i tuoi utenti siano collegati ai gruppi Adobe Experience Cloud che verranno sincronizzati con Adobe Campaign. Consultate [Configurazione dell’account](#configuring-the-external-account)esterno.

## Aggiornamento della console {#updating-the-console}

Per utilizzare questa funzionalità, è necessario installare la versione più recente della console.

## Installazione del pacchetto {#installing-the-package}

Dovete installare il **[!UICONTROL Integration with the Adobe Experience Cloud]** pacchetto. L&#39;installazione di un pacchetto di integrazione è la stessa dell&#39;installazione di un pacchetto standard, descritta in [questa pagina](../../installation/using/installing-campaign-standard-packages.md).

![](assets/ims_6.png)

## Configurazione dell’account esterno {#configuring-the-external-account}

Configura l&#39;account esterno di **Adobe Experience Cloud** in **[!UICONTROL Administration > Platform > External accounts]**.

>[!CAUTION]
>
>Questa configurazione è riservata all&#39;amministratore tecnico.

![](assets/ims_5.png)

Inserite le seguenti informazioni:

* Informazioni di connessione per il server IMS utilizzato (ID e segreto). Queste informazioni sono fornite dal supporto Adobe. Per ulteriori informazioni, consulta le [Domande frequenti per gli amministratori](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/faq.html)di Adobe Experience Cloud.

   L&#39; **[!UICONTROL Callback server]** indirizzo deve essere specificato in **https**. Questo campo corrisponde all&#39;URL di accesso dell&#39;istanza di Adobe Campaign.

* ID organizzazione IMS: queste informazioni sono disponibili in Experience Cloud (in **[!UICONTROL Administration > Experience Cloud Details]** ) e vengono fornite al momento della prima connessione ad Adobe Experience Cloud.
* Maschera di associazione: questo campo consente di definire la sintassi che consentirà la sincronizzazione dei nomi di configurazione in Enterprise Dashboard con i gruppi in Adobe Campaign. Se utilizzi la sintassi &quot;Campaign - tenant_id - (.*)&quot;, il gruppo di sicurezza creato in Adobe Campaign sarà collegato al nome di configurazione &quot;Campaign - tenant_id - internal_name&quot; nella dashboard di Enterprise.

   >[!CAUTION]
   >
   >La maschera di associazione è essenziale per il corretto funzionamento della connessione tramite l&#39;Adobe ID.

* Informazioni sulla connessione di Adobe Experience Cloud, in particolare il nome del tenant di Adobe Experience Cloud.

