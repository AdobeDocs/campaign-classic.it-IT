---
solution: Campaign Classic
product: campaign
title: Avvio di Adobe Campaign
description: Avvio di Adobe Campaign
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 8%

---


# Avvio di Adobe Campaign{#launching-adobe-campaign}

La console Client campagna è un client avanzato che consente di connettersi ai server delle applicazioni Campaign. Scopri come scaricare e configurare la console client in [questa pagina](../../installation/using/installing-the-client-console.md).

## Avvio  Adobe Campaign {#starting-adobe-campaign}

È possibile avviare  Adobe Campaign selezionando **[!UICONTROL Start / All Programs / Adobe Campaign v.X / Adobe Campaign client console]**.

La finestra di connessione della console client consente di selezionare o configurare i database esistenti e di collegarli utilizzando un nome utente e una password:

![](assets/acc-logon.png)

## Connessione a  Adobe Campaign {#connecting-to-adobe-campaign}

È possibile connettersi a  Adobe Campaign utilizzando l&#39;Adobe ID . Per ulteriori informazioni, consulta [questa pagina](../../integrations/using/about-adobe-id.md).

È inoltre possibile connettersi con un login/password dedicato:

1. Immettere l&#39;identificatore dell&#39;account dell&#39;operatore nel campo **[!UICONTROL login]**.

   L’identificatore viene fornito dall’amministratore della piattaforma  Adobe Campaign.

1. Immettere la password nel campo **[!UICONTROL Password]**.

   La prima volta che accedete al database, la password è quella fornita dall&#39;amministratore. Una volta connessi, è possibile cambiare la password tramite il menu **[!UICONTROL Tools > Change password...]**. Informazioni sugli operatori e le connessioni sono disponibili in [Gestione degli accessi](../../platform/using/access-management.md).

1. Fare clic su **[!UICONTROL LOG IN]** per confermare.

È ora possibile accedere a [ area di lavoro Adobe Campaign](../../platform/using/adobe-campaign-workspace.md).

## Configurazione delle connessioni {#setting-up-connections}

È possibile accedere alle impostazioni di connessione del server tramite il collegamento situato sopra la zona di input.

![](assets/s_ncs_user_connections_management.png)

Nella finestra **[!UICONTROL Connections]**, fare clic su **[!UICONTROL Add > Connection]**.

È quindi necessario definire le impostazioni di connessione. Per eseguire questa operazione:

1. Immettete un **[!UICONTROL Label]** per assegnare un nome alla connessione al database.

1. Aggiungete l&#39;indirizzo del server applicazione nel campo **[!UICONTROL URL]**. Se non conoscete l’URL della connessione, rivolgetevi all’amministratore.

1. Verificare **[!UICONTROL Connect with an Adobe ID]** che gli operatori possano connettersi alla console utilizzando il proprio Adobe ID . Per ulteriori informazioni, consulta [questa pagina](../../integrations/using/about-adobe-id.md).

1. Fare clic su **[!UICONTROL OK]** per eseguire la convalida.

## Operatori e autorizzazioni {#operators-and-permissions}

Gli identificatori e le password degli operatori con accesso al software e le rispettive autorizzazioni sono definiti dall&#39;amministratore di sistema Adobe Campaign  nel nodo **[!UICONTROL Administration > Access management > Operators]** della struttura  Adobe Campaign.

Questa funzionalità è dettagliata nella sezione [Gestione degli accessi](../../platform/using/access-management.md).

## Disconnessione da  Adobe Campaign {#disconnecting-from-adobe-campaign}

Per disconnettersi da  Adobe Campaign, utilizzate la prima icona nella barra delle icone.

![](assets/s_ncs_user_deconnexion.png)

>[!NOTE]
>
>È inoltre possibile chiudere l&#39;applicazione senza prima disconnettersi.

## Ottenimento della versione Adobe Campaign  {#getting-your-campaign-version}

Il menu **[!UICONTROL Help > About...]** consente di accedere alle informazioni seguenti:

* **Numero di** versione per la console client Campaign e il server applicazione
* **Numero** build per la console client di Campaign e il server applicazione
* un collegamento per contattare &#39;Assistenza clienti del Adobe
* collegamenti  Informativa sulla privacy del Adobe, Termini d&#39;uso e Informativa sui cookie

![](assets/about-acc.png)

Ogni volta che contattate  team di assistenza clienti di Adobe, dovete fornire il numero di versione e il numero di build della console client e del server applicazioni di Adobe Campaign .

Se si è in esecuzione su [Campaign Gold Standard version](../../rn/using/gold-standard.md), è inoltre necessario condividere i caratteri SHA/1 visualizzati nella casella **[!UICONTROL About]**. Ad esempio, per Gold **Standard 10 release**, il numero di build mostrerà **build 9032@efd8a94**, come illustrato di seguito:

![](assets/about-acc-gs.png)

Ulteriori informazioni su Gold Standard [in questo articolo](https://helpx.adobe.com/it/campaign/kb/gold-standard.html).

**Argomenti correlati**:

* [ opzioni di Guida e supporto di Adobe Campaign](https://helpx.adobe.com/it/campaign/kb/ac-support.html#acc-support)
* [Distribuzione software  Adobe](https://docs.adobe.com/content/help/en/experience-cloud/software-distribution/home.html)
* [Sessioni Adobe Experience Cloud Support ed Expert](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)
