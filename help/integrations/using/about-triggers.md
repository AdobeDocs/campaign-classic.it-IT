---
product: campaign
title: Informazioni su Adobe Experience Cloud Triggers
description: Introduzione all’implementazione di Adobe Experience Cloud Triggers
feature: Triggers
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
audience: integrations
content-type: reference
exl-id: 0e337620-a49f-4e14-8c67-9279d74736f1
source-git-commit: 8de62db2499449fc9966b6464862748e2514a774
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 7%

---

# Utilizzo di Campaign e Triggers Experience Cloud{#about-adobe-experience-triggers}

[!DNL Triggers] è un’integrazione tra Adobe Campaign e Adobe Analytics che utilizza la pipeline. La pipeline recupera le azioni o i trigger degli utenti dal sito web. L’abbandono del carrello è un esempio di trigger. Gli attivatori vengono elaborati in Adobe Campaign per inviare e-mail quasi in tempo reale.

>[!CAUTION]
>
>Questa funzionalità non è disponibile come funzione predefinita del prodotto. Per questa implementazione, rivolgiti al tuo rappresentante Adobe/all’Assistenza clienti. Potrai quindi seguire i passaggi descritti in questo [pagina](../../integrations/using/configuring-pipeline.md#prerequisites).

[!DNL Triggers] eseguire azioni di marketing entro un breve intervallo di tempo dopo l’azione di un utente. Il tempo di risposta tipico è inferiore a un&#39;ora.

Consente integrazioni più agili, in quanto la configurazione è minima e non è coinvolta una terza parte.
Supporta inoltre elevati volumi di traffico senza influire sulle prestazioni delle attività di marketing. Ad esempio, l’integrazione può elaborare un milione di trigger all’ora.

![](assets/do-not-localize/book.png) Scopri come [creazione di un trigger di Experience Cloud](https://experienceleague.adobe.com/docs/experience-cloud/triggers/create.html) e identificare, definire e monitorare i comportamenti critici dei consumatori.

## [!DNL Triggers] architettura {#triggers-architecture}

Il [!DNL pipelined] Il processo è sempre in esecuzione sul server di marketing Adobe Campaign. Si connette alla pipeline, recupera gli eventi ed li elabora immediatamente.

![](assets/triggers_2.png)

Il [!DNL pipelined] process accede all’Experience Cloud utilizzando un servizio di autenticazione e invia una chiave privata. Il servizio di autenticazione restituisce un token. Il token viene utilizzato per l’autenticazione durante il recupero degli eventi.

## Prerequisiti {#adobe-io-prerequisites}

Prima di iniziare questa implementazione, verifica di disporre di:

* un valore valido **Identificatore organizzazione**: l’ID organizzazione è l’identificatore univoco all’interno di Adobe Experience Cloud, utilizzato ad esempio per il servizio VisitorID e l’accesso Single Sign-On (SSO) di IMS. [Ulteriori informazioni](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=it)
* a **Accesso per sviluppatori** alla tua organizzazione. L’amministratore di sistema dell’organizzazione deve seguire la procedura **Aggiungere sviluppatori a un singolo profilo di prodotto** procedura dettagliata [in questa pagina](https://helpx.adobe.com/enterprise/using/manage-developers.html) per fornire agli sviluppatori l&#39;accesso per `Analytics - {tenantID}` Profilo prodotto del prodotto Adobe Analytics associato a Triggers.

## Passaggi di implementazione {#implement}

Per implementare Campaign e Triggers Experience Cloud, segui i passaggi seguenti:

1. Crea un progetto OAuth. [Ulteriori informazioni](oauth-technical-account.md#oauth-service)

1. Aggiungi le credenziali del progetto OAuth in Adobe Campaign. [Ulteriori informazioni](oauth-technical-account.md#add-credentials)

1. Aggiorna il tipo di autenticazione al progetto Developer Console nel file di configurazione **config-&lt; nome-istanza >.xml** come segue:

   ```
   <pipelined ... authType="imsJwtToken"  ... />
   ```

   Quindi, esegui una `config -reload` e il riavvio del [!DNL pipelined] affinché le modifiche siano prese in considerazione.

