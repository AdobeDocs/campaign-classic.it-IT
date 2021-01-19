---
solution: Campaign Classic
product: campaign
title: Connettori di gestione delle relazioni con i clienti
description: Guida introduttiva ai connettori CRM in Campaign
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 2838ced5f5d562914c0791e6a0b8f02dd61006b4
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 24%

---


# Connettori di gestione delle relazioni con i clienti{#crm-connectors}

## Introduzione ai connettori CRM {#about-crm-connectors}

Adobe Campaign fornisce diversi connettori di gestione delle relazioni con i clienti per collegare la piattaforma Adobe Campaign ai sistemi di terze parti. Questi connettori di gestione delle relazioni con i clienti ti consentono di sincronizzare contatti, account, acquisti, ecc. Facilitano l’integrazione dell’applicazione con varie applicazioni di terze parti e aziendali.

Questi connettori consentono un’integrazione rapida e semplice dei dati: Adobe Campaign offre una procedura guidata dedicata per la raccolta e la selezione dalle tabelle disponibili nella gestione delle relazioni con i clienti. Ciò garantisce la sincronizzazione bidirezionale per far sì che i dati siano sempre aggiornati in tutti i sistemi.

>[!NOTE]
>
>Questa funzione è disponibile in  Adobe Campaign tramite il **pacchetto dedicato dei connettori CRM**.


### Sistemi compatibili {#compatible-crm-systems-and-limitations}

CRM e versioni supportate sono descritti dettagliatamente in Campaign [Matrice di compatibilità](../../rn/using/compatibility-matrix.md).

>[!NOTE]
>
>I connettori CRM funzionano solo con un URL sicuro (https).

### Passaggi di implementazione {#crm-implementation-steps}

Scopri la procedura dettagliata per collegare Campaign e Microsoft Dynamics [in questa sezione](../../platform/using/crm-ms-dynamics.md)

In generale, per utilizzare i connettori CRM in  Adobe Campaign, attenetevi alla seguente procedura:

1. Create un nuovo account esterno tramite il nodo **[!UICONTROL Administration > Platform > External accounts]** della struttura di Adobe Campaign .
1. Seleziona il sistema CRM a cui devi connettere Campaign.
1. Immettere le impostazioni per abilitare la connessione.
1. Eseguire la procedura guidata di configurazione per generare la tabella CRM disponibile: la procedura guidata di configurazione consente di raccogliere le tabelle e creare lo schema corrispondente.

   Esempio di configurazione guidata di **Salesforce**:

   ![](assets/crm_connectors_sfdc_launch.png)

   >[!NOTE]
   >
   >Per approvare la configurazione, dovete disconnettervi e tornare alla  console Adobe Campaign.

1. Controllare lo schema generato in  Adobe Campaign nel nodo **[!UICONTROL Administration > Configuration > Data schemas]**.

   Esempio per lo schema **Salesforce**:

   ![](assets/crm_connectors_sfdc_table.png)

1. Una volta creato lo schema, puoi sincronizzare automaticamente le enumerazioni tramite CRM a  Adobe Campaign.

   A tal fine, fare clic sul collegamento **[!UICONTROL Synchronizing enumerations...]** e selezionare l&#39;enumerazione Adobe Campaign  che corrisponde all&#39;enumerazione CRM.

   >[!NOTE]
   >
   >Puoi sostituire tutti i valori di un&#39;enumerazione Adobe Campaign  con quelli di CRM: a tal fine, selezionare **[!UICONTROL Yes]** nella colonna **[!UICONTROL Replace]**.

   Esempio per le enumerazioni **Salesforce**:

   ![](assets/crm_connectors_sfdc_enum.png)

   Fare clic su **[!UICONTROL Next]**, quindi su **[!UICONTROL Start]** per iniziare a importare l&#39;elenco.

1. Controllate i valori importati nel menu **[!UICONTROL Administration > Platform > Enumerations]**.

   ![](assets/crm_connectors_sfdc_exe.png)

   >[!NOTE]
   >
   > Le enumerazioni di selezione multiple in Salesforce non sono supportate.

1. Per sincronizzare i dati tra  dati Adobe Campaign e il sistema CRM, è necessario creare un flusso di lavoro e utilizzare l&#39;attività **[!UICONTROL CRM connector]**.

   ![](assets/crm_connectors_sfdc_wf.png)

   Ulteriori informazioni sulla sincronizzazione dei dati [in questa pagina](../../platform/using/crm-data-sync.md).
