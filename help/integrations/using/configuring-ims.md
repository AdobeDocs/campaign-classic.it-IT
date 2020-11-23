---
solution: Campaign Classic
product: campaign
title: Configurazione di IMS
description: 'Scopri come connettersi tramite un Adobe ID '
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 2%

---


# Configuring IMS{#configuring-ims}

## Prerequisiti {#prerequisites}

Per utilizzare l&#39;integrazione con IMS:

* È necessario disporre di un&#39;organizzazione Adobe Experience Cloud e di ID IMS (forniti al momento della prima connessione all&#39;Adobe Experience Cloud).
* È necessario aggiungere utenti nel Experience Cloud . Per ulteriori informazioni, consulta [questa pagina](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/admin-getting-started.html).

>[!NOTE]
>
>Accertatevi che gli utenti siano collegati ai gruppi Adobe Experience Cloud che verranno sincronizzati con  Adobe Campaign. Consultate [Configurazione dell’account](#configuring-the-external-account)esterno.

## Aggiornamento della console {#updating-the-console}

Per utilizzare questa funzionalità, è necessario installare la versione più recente della console.

## Installazione del pacchetto {#installing-the-package}

Dovete installare il **[!UICONTROL Integration with the Adobe Experience Cloud]** pacchetto. L&#39;installazione di un pacchetto di integrazione è la stessa dell&#39;installazione di un pacchetto standard, descritta in [questa pagina](../../installation/using/installing-campaign-standard-packages.md).

![](assets/ims_6.png)

## Configurazione dell’account esterno {#configuring-the-external-account}

Configurare l&#39;account esterno **Adobe Experience Cloud** in **[!UICONTROL Administration > Platform > External accounts]**.

>[!CAUTION]
>
>Questa configurazione è riservata all&#39;amministratore tecnico.

![](assets/ims_5.png)

Inserite le seguenti informazioni:

* Informazioni di connessione per il server IMS utilizzato (ID e segreto). Queste informazioni sono fornite dal supporto  Adobe. Per ulteriori informazioni, consultate le [Domande frequenti per gli amministratori](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/faq.html)di Adobe Experience Cloud.

   L&#39; **[!UICONTROL Callback server]** indirizzo deve essere specificato in **https**. Questo campo corrisponde all’URL di accesso dell’istanza di Adobe Campaign .

* ID organizzazione IMS: queste informazioni sono disponibili nel Experience Cloud  (in **[!UICONTROL Administration > Experience Cloud Details]** ) e vengono fornite al primo collegamento all’Adobe Experience Cloud.
* Maschera di associazione: questo campo consente di definire la sintassi che consentirà la sincronizzazione dei nomi di configurazione in Enterprise Dashboard con i gruppi in  Adobe Campaign. Se utilizzi la sintassi &quot;Campaign - tenant_id - (.*)&quot;, il gruppo di sicurezza creato in  Adobe Campaign sarà collegato al nome di configurazione &quot;Campaign - tenant_id - internal_name&quot; nella dashboard di Enterprise.

   >[!CAUTION]
   >
   >La maschera di associazione è essenziale per il corretto funzionamento della connessione tramite l&#39;Adobe ID .

* Informazioni sulla connessione Adobe Experience Cloud, in particolare il nome del tenant Adobe Experience Cloud.

