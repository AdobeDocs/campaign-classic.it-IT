---
product: campaign
title: Configurazione di IMS
description: Scopri come connettersi tramite un Adobe ID
feature: Configuration
badge-v7: label="v7" type="Informative" tooltip="Applicabile a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: b70ca220-1c81-4b23-b07a-a2cd694877fe
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 5%

---

# Configurazione di IMS{#configuring-ims}



>[!IMPORTANT]
>
>L’implementazione di Adobe IMS è rigorosamente riservata agli amministratori tecnici Adobi. Contatta il tuo responsabile di Adobe per avviare il processo di implementazione.

## Prerequisiti {#prerequisites}

Per utilizzare l’integrazione con IMS:

* È necessario disporre di un nome e di un ID organizzazione Adobe Experience Cloud. Per trovare l&#39;ID organizzazione, fare riferimento a [questa pagina](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=it){_blank}.
* Devi aggiungere degli utenti all’Experience Cloud. Per ulteriori informazioni, consulta [questa pagina](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html){_blank}.

>[!NOTE]
>
>Assicurati che gli utenti siano collegati ai gruppi di Adobe Experience Cloud che verranno sincronizzati con Adobe Campaign. [Ulteriori informazioni](#configuring-the-external-account).

## Aggiornamento della console {#updating-the-console}

Per utilizzare questa funzionalità, è fondamentale installare la versione più recente della console.

## Installazione del pacchetto {#installing-the-package}

È necessario installare il **[!UICONTROL Integration with the Adobe Experience Cloud]** pacchetto. L’installazione di un pacchetto di integrazione equivale all’installazione di un pacchetto standard, descritto in [questa pagina](../../installation/using/installing-campaign-standard-packages.md).

![](assets/ims_6.png)

## Configurazione dell’account esterno {#configuring-the-external-account}

Configurare **Adobe Experience Cloud** account esterno in **[!UICONTROL Administration > Platform > External accounts]**.

>[!CAUTION]
>
>Questa configurazione è riservata all’amministratore tecnico.

![](assets/ims_5.png)

Immettere le seguenti informazioni:

* Informazioni di connessione per il server IMS utilizzato (ID e segreto). Queste informazioni sono fornite dal supporto Adobe. Per ulteriori informazioni, consulta [Domande frequenti per gli amministratori di Adobe Experience Cloud](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/faq.html).

  Il **[!UICONTROL Callback server]** l&#39;indirizzo deve essere specificato in **https**. Questo campo corrisponde all’URL di accesso dell’istanza di Adobe Campaign.

* ID organizzazione: per trovare l’ID organizzazione, fai riferimento a [questa pagina](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=it){_blank}.
* Maschera di associazione: questo campo ti consente di definire la sintassi che consentirà la sincronizzazione dei nomi delle configurazioni nel dashboard di Enterprise con i gruppi in Adobe Campaign. Se utilizzi la sintassi &quot;Campaign - tenant_id - (.&#42;)&quot;, il gruppo di sicurezza creato in Adobe Campaign verrà collegato al nome della configurazione &quot;Campaign - tenant_id - internal_name&quot; nel dashboard di Enterprise.

  >[!CAUTION]
  >
  >La maschera di associazione è essenziale per il corretto funzionamento della connessione tramite Adobe ID.

* Informazioni sulla connessione a Adobe Experience Cloud, in particolare il nome del tenant Adobe Experience Cloud.
