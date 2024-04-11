---
product: campaign
title: Campaign - Connettore CRM Salesforce
description: Scopri come collegare Campaign e Salesforce
feature: Salesforce Integration
exl-id: 94a1f00d-e952-4edd-9012-f71c87b897ca
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---

# Collegare Campaign e Salesforce.com{#connect-to-sfdc}



In questa pagina imparerai a collegare Campaign Classic a **Salesforce**.

La sincronizzazione dei dati viene eseguita tramite un’attività del flusso di lavoro dedicata. [Ulteriori informazioni](../../platform/using/crm-data-sync.md).


L’account esterno ti consente di importare ed esportare i dati di Salesforce in Adobe Campaign.
Per configurare il connettore di gestione delle relazioni con i clienti per Salesforce, effettua le seguenti operazioni:

1. Creare un nuovo account esterno tramite **[!UICONTROL Administration > Platform > External accounts]** della struttura Adobe Campaign.
1. Seleziona **[!UICONTROL Salesforce.com]**.
1. Immettere le impostazioni per abilitare la connessione.

   ![](assets/ext_account_17.png)

   Per configurare l’account esterno del sistema di gestione delle relazioni con i clienti di Salesforce affinché funzioni con Adobe Campaign, è necessario fornire i seguenti dettagli:

   * **[!UICONTROL Account]**
Account utilizzato per accedere a Salesforce CRM.

   * **[!UICONTROL Password]**
Password utilizzata per accedere a Salesforce CRM.

   * **[!UICONTROL Client identifier]**
Per sapere dove trovare l’identificatore del client, consulta questa [pagina](https://help.salesforce.com/articleView?id=000205876&amp;type=1).

   * **[!UICONTROL Security token]**
Per sapere dove trovare il token di sicurezza, consulta questa [pagina](https://help.salesforce.com/articleView?id=000205876&amp;type=1).

   * **[!UICONTROL API version]**
Seleziona la versione dell’API.
1. Esegui la procedura guidata di configurazione per generare la tabella CRM disponibile: la procedura guidata di configurazione ti consente di raccogliere tabelle e creare lo schema corrispondente.

   ![](assets/crm_connectors_sfdc_launch.png)

   >[!NOTE]
   >
   >Per approvare la configurazione, devi disconnetterti e accedere di nuovo alla console Adobe Campaign.

1. Controlla lo schema generato in Adobe Campaign nel **[!UICONTROL Administration > Configuration > Data schemas]** nodo.

   Esempio di **Salesforce** schema:

   ![](assets/crm_connectors_sfdc_table.png)

1. Una volta creato lo schema, puoi sincronizzare automaticamente le enumerazioni da Salesforce ad Adobe Campaign.

   A questo scopo, fai clic su **[!UICONTROL Synchronizing enumerations...]** collega e seleziona l’enumerazione Adobe Campaign che corrisponde a quella Salesforce.



   ![](assets/crm_connectors_sfdc_enum.png)

   >[!NOTE]
   >
   >Puoi sostituire tutti i valori di un’enumerazione Adobe Campaign con quelli del CRM: a questo scopo, seleziona **[!UICONTROL Yes]** nel **[!UICONTROL Replace]** colonna.


   Clic **[!UICONTROL Next]** e poi **[!UICONTROL Start]** per avviare l&#39;importazione dell&#39;elenco.

1. Controlla i valori importati nella **[!UICONTROL Administration > Platform > Enumerations]** menu.

   ![](assets/crm_connectors_sfdc_exe.png)

   >[!NOTE]
   >
   > Le enumerazioni di selezione multiple non sono supportate.

Campaign e Salesforce.com sono ora connessi. È possibile impostare la sincronizzazione dei dati tra i due sistemi.

Per sincronizzare i dati tra i dati di Adobe Campaign e SFDC, è necessario creare un flusso di lavoro e utilizzare **[!UICONTROL CRM connector]** attività.

![](assets/crm_connectors_sfdc_wf.png)

Ulteriori informazioni sulla sincronizzazione dei dati [in questa pagina](../../platform/using/crm-data-sync.md).
