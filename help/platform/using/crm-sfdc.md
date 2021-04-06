---
solution: Campaign Classic
product: campaign
title: Campaign - Connettore CRM Salesforce
description: Connetti Campaign e Salesforce.com
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 94a1f00d-e952-4edd-9012-f71c87b897ca
translation-type: tm+mt
source-git-commit: 3b5a6e6f03d9cb26ed372c3df069cbada36756a2
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# Connetti Campaign e Microsoft Dynamics 365{#connect-to-msdyn}

In questa pagina verrà illustrato come collegare Campaign Classic a **Salesforce**.

La sincronizzazione dei dati viene eseguita tramite un’attività del flusso di lavoro dedicata. [Ulteriori informazioni](../../platform/using/crm-data-sync.md).


L’account esterno ti consente di importare ed esportare i dati di Salesforce in Adobe Campaign.
Per configurare il connettore di gestione delle relazioni con i clienti per Salesforce, segui i passaggi seguenti:

1. Crea un nuovo account esterno tramite il nodo **[!UICONTROL Administration > Platform > External accounts]** della struttura di Adobe Campaign.
1. Seleziona **[!UICONTROL Salesforce.com]**.
1. Immettere le impostazioni per abilitare la connessione.

   ![](assets/ext_account_17.png)

   Per configurare l&#39;account esterno di gestione delle relazioni con i clienti Salesforce affinché funzioni con Adobe Campaign, devi fornire i seguenti dettagli:

   * **[!UICONTROL Account]**
Account utilizzato per accedere a CRM Salesforce.

   * **[!UICONTROL Password]**
Password utilizzata per accedere a CRM Salesforce.

   * **[!UICONTROL Client identifier]**
Per sapere dove trovare l’identificatore client, consulta questa  [pagina](https://help.salesforce.com/articleView?id=000205876&amp;type=1).

   * **[!UICONTROL Security token]**
Per sapere dove trovare il token di sicurezza, consulta questa  [pagina](https://help.salesforce.com/articleView?id=000205876&amp;type=1).

   * **[!UICONTROL API version]**
Seleziona la versione dell’API.
1. Esegui la procedura guidata di configurazione per generare la tabella CRM disponibile: la procedura guidata di configurazione consente di raccogliere le tabelle e creare lo schema corrispondente.

   ![](assets/crm_connectors_sfdc_launch.png)

   >[!NOTE]
   >
   >Per approvare la configurazione, è necessario disconnettersi e accedere nuovamente alla console Adobe Campaign.

1. Controlla lo schema generato in Adobe Campaign nel nodo **[!UICONTROL Administration > Configuration > Data schemas]** .

   Esempio per lo schema **Salesforce**:

   ![](assets/crm_connectors_sfdc_table.png)

1. Una volta creato lo schema, puoi sincronizzare automaticamente le enumerazioni da Salesforce ad Adobe Campaign.

   A questo scopo, fai clic sul collegamento **[!UICONTROL Synchronizing enumerations...]** e seleziona l’enumerazione Adobe Campaign che corrisponde all’enumerazione Salesforce.



   ![](assets/crm_connectors_sfdc_enum.png)

   >[!NOTE]
   >
   >Puoi sostituire tutti i valori di un&#39;enumerazione Adobe Campaign con quelli del CRM: a questo scopo, seleziona **[!UICONTROL Yes]** nella colonna **[!UICONTROL Replace]** .


   Fare clic su **[!UICONTROL Next]** e quindi su **[!UICONTROL Start]** per iniziare a importare l&#39;elenco.

1. Controlla i valori importati nel menu **[!UICONTROL Administration > Platform > Enumerations]** .

   ![](assets/crm_connectors_sfdc_exe.png)

   >[!NOTE]
   >
   > Le enumerazioni di selezione multiple non sono supportate.

Campaign e Salesforce.com sono ora connessi. È possibile impostare la sincronizzazione dei dati tra i due sistemi.

Per sincronizzare i dati tra i dati di Adobe Campaign e SFDC, devi creare un flusso di lavoro e utilizzare l’attività **[!UICONTROL CRM connector]** .

![](assets/crm_connectors_sfdc_wf.png)

Ulteriori informazioni sulla sincronizzazione dei dati [in questa pagina](../../platform/using/crm-data-sync.md).
