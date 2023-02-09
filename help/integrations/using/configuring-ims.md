---
product: campaign
title: Configurazione di IMS
description: Scopri come connettersi tramite un Adobe ID
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: b70ca220-1c81-4b23-b07a-a2cd694877fe
source-git-commit: 02eebe83de49ee97e573b0c47ca1fddb2195b991
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 4%

---

# Configurazione di IMS{#configuring-ims}

![](../../assets/common.svg)

>[!IMPORTANT]
>
>L’implementazione di Adobe IMS è strettamente riservata agli amministratori tecnici di Adobe. Contatta il tuo responsabile Adobe per avviare il processo di implementazione.

## Prerequisiti {#prerequisites}

Per utilizzare l’integrazione con IMS:

* Devi disporre di un nome organizzazione e di un ID Adobe Experience Cloud. Per trovare l&#39;ID organizzazione, fai riferimento a [questa pagina](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=it){_blank}.
* Devi aggiungere utenti nell’Experience Cloud. Per ulteriori informazioni, consulta [questa pagina](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html){_blank}.

>[!NOTE]
>
>Assicurati che i tuoi utenti siano collegati ai gruppi Adobe Experience Cloud che verranno sincronizzati con Adobe Campaign. [Ulteriori informazioni](#configuring-the-external-account).

## Aggiornamento della console {#updating-the-console}

Per utilizzare questa funzionalità, è fondamentale installare la versione più recente della console.

## Installazione del pacchetto {#installing-the-package}

È necessario installare il **[!UICONTROL Integration with the Adobe Experience Cloud]** pacchetto. L’installazione di un pacchetto di integrazione è la stessa dell’installazione di un pacchetto standard, descritta in [questa pagina](../../installation/using/installing-campaign-standard-packages.md).

![](assets/ims_6.png)

## Configurazione dell’account esterno {#configuring-the-external-account}

Configura le **Adobe Experience Cloud** account esterno in **[!UICONTROL Administration > Platform > External accounts]**.

>[!CAUTION]
>
>Questa configurazione è riservata all’amministratore tecnico.

![](assets/ims_5.png)

Immetti le seguenti informazioni:

* Informazioni di connessione per il server IMS utilizzato (ID e segreto). Queste informazioni sono fornite dal supporto Adobe. Per ulteriori informazioni, consulta la [Domande frequenti per gli amministratori di Adobe Experience Cloud](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/faq.html).

   La **[!UICONTROL Callback server]** l&#39;indirizzo deve essere specificato in **https**. Questo campo corrisponde all’URL di accesso dell’istanza Adobe Campaign.

* ID organizzazione: per trovare l&#39;ID organizzazione, fai riferimento a [questa pagina](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=it){_blank}.
* Maschera associazione: questo campo ti consente di definire la sintassi che consentirà la sincronizzazione dei nomi di configurazione in Enterprise Dashboard con i gruppi in Adobe Campaign. Se utilizzi la sintassi &quot;Campaign - tenant_id - (.&#42;)&quot;, il gruppo di sicurezza creato in Adobe Campaign verrà collegato al nome di configurazione &quot;Campaign - tenant_id - internal_name&quot; nella dashboard di Enterprise.

   >[!CAUTION]
   >
   >La maschera di associazione è essenziale per il corretto funzionamento della connessione tramite Adobe ID.

* Informazioni sulla connessione Adobe Experience Cloud, in particolare il nome del tenant Adobe Experience Cloud.
