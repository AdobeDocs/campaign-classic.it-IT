---
product: campaign
title: Configurazione di IMS
description: Scopri come connettersi tramite un Adobe ID
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: b70ca220-1c81-4b23-b07a-a2cd694877fe
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 2%

---

# Configurazione di IMS{#configuring-ims}

![](../../assets/common.svg)

>[!IMPORTANT]
>
>L’implementazione di Adobe IMS è strettamente riservata agli amministratori tecnici di Adobe. Contatta il tuo responsabile Adobe per avviare il processo di implementazione.

## Prerequisiti {#prerequisites}

Per utilizzare l’integrazione con IMS:

* Devi disporre di un’organizzazione Adobe Experience Cloud e degli ID IMS (forniti la prima volta che ti connetti a Adobe Experience Cloud).
* Devi aggiungere utenti nell’Experience Cloud. Per ulteriori informazioni, consulta [questa pagina](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/admin-getting-started.html).

>[!NOTE]
>
>Assicurati che i tuoi utenti siano collegati ai gruppi Adobe Experience Cloud che verranno sincronizzati con Adobe Campaign. Fai riferimento a [Configurazione dell&#39;account esterno](#configuring-the-external-account).

## Aggiornamento della console {#updating-the-console}

Per utilizzare questa funzionalità, è fondamentale installare la versione più recente della console.

## Installazione del pacchetto {#installing-the-package}

È necessario installare il pacchetto **[!UICONTROL Integration with the Adobe Experience Cloud]**. L&#39;installazione di un pacchetto di integrazione è la stessa dell&#39;installazione di un pacchetto standard, che è descritto in [questa pagina](../../installation/using/installing-campaign-standard-packages.md).

![](assets/ims_6.png)

## Configurazione dell’account esterno {#configuring-the-external-account}

Configura l&#39;account esterno **Adobe Experience Cloud** in **[!UICONTROL Administration > Platform > External accounts]**.

>[!CAUTION]
>
>Questa configurazione è riservata all’amministratore tecnico.

![](assets/ims_5.png)

Immetti le seguenti informazioni:

* Informazioni di connessione per il server IMS utilizzato (ID e segreto). Queste informazioni sono fornite dal supporto Adobe. Per ulteriori informazioni, consulta le [Domande frequenti per gli amministratori di Adobe Experience Cloud](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/faq.html).

   L&#39;indirizzo **[!UICONTROL Callback server]** deve essere specificato in **https**. Questo campo corrisponde all’URL di accesso dell’istanza Adobe Campaign.

* ID organizzazione IMS: queste informazioni sono disponibili nell’Experience Cloud (in **[!UICONTROL Administration > Experience Cloud Details]** ) e vengono fornite al primo momento della connessione a Adobe Experience Cloud.
* Maschera associazione: questo campo ti consente di definire la sintassi che consentirà la sincronizzazione dei nomi di configurazione in Enterprise Dashboard con i gruppi in Adobe Campaign. Se utilizzi la sintassi &quot;Campaign - tenant_id - (.*)&quot;, il gruppo di sicurezza creato in Adobe Campaign sarà collegato al nome di configurazione &quot;Campaign - tenant_id - internal_name&quot; nella dashboard di Enterprise.

   >[!CAUTION]
   >
   >La maschera di associazione è essenziale per il corretto funzionamento della connessione tramite Adobe ID.

* Informazioni sulla connessione Adobe Experience Cloud, in particolare il nome del tenant Adobe Experience Cloud.
