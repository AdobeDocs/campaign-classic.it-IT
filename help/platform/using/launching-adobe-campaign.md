---
product: campaign
title: Avvio di Adobe Campaign
description: Avvio di Adobe Campaign
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 4d9c5b24-83a2-4495-a56c-5bc376d69703
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 11%

---

# Avviare Adobe Campaign{#launching-adobe-campaign}

La console Client di Campaign è un client avanzato che consente di connettersi ai server delle applicazioni Campaign. Scopri come scaricare e configurare la console client in [questa pagina](../../installation/using/installing-the-client-console.md).


>[!CAUTION]
>
>Verifica la compatibilità del sistema e degli strumenti con la console client di Adobe Campaign nella [Matrice di compatibilità](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)

## Avvia Adobe Campaign {#starting-adobe-campaign}

Puoi avviare Adobe Campaign selezionando **[!UICONTROL Start / All Programs / Adobe Campaign v.X / Adobe Campaign client console]**.

La finestra di connessione della console client consente di selezionare o configurare i database esistenti e di connettersi ad essi utilizzando un nome utente e una password:

![](assets/acc-logon.png)

## Connessione ad Adobe Campaign {#connecting-to-adobe-campaign}

Puoi connetterti ad Adobe Campaign utilizzando il tuo Adobe ID. Per ulteriori informazioni, consulta [questa pagina](../../integrations/using/about-adobe-id.md).

Puoi anche effettuare la connessione con un login/password dedicato:

1. Immetti l’identificatore dell’account operatore nel campo **[!UICONTROL Login]** .

   L’amministratore della piattaforma Adobe Campaign fornisce l’identificatore .

1. Immetti la password nel campo **[!UICONTROL Password]** .

   La prima volta che accedi al database, la password viene fornita dall&#39;amministratore. Una volta connesso, è possibile modificare la password tramite il menu **[!UICONTROL Tools > Change password...]**. I dettagli sugli operatori e le connessioni sono disponibili in [Gestione accessi](../../platform/using/access-management.md).

1. Fare clic su **[!UICONTROL LOG IN]** per confermare.<!--You can also press the **Enter** key to launch connection.-->

Ora è possibile accedere a [Area di lavoro Adobe Campaign](../../platform/using/adobe-campaign-workspace.md).

Alcune scelte rapide da tastiera sono disponibili in **[!UICONTROL Sign in screen]**:
* Tutti gli elementi utilizzabili sono selezionabili tramite i tasti **Tab** (dall&#39;alto verso il basso) o **Tab** + **Maiusc** (dal basso verso l&#39;alto).
* Per avviare la connessione, puoi anche premere il tasto **Invio**.
* Puoi usare il tasto **Esc** per reimpostare i campi **[!UICONTROL Login]** e **[!UICONTROL Password]** sugli ultimi valori di connessione riusciti.

## Imposta connessioni {#setting-up-connections}

Puoi accedere alle impostazioni di connessione al server tramite il collegamento situato sopra la zona di input.

![](assets/s_ncs_user_connections_management.png)

Nella finestra **[!UICONTROL Connections]**, fai clic su **[!UICONTROL Add > Connection]**.

È quindi necessario definire le impostazioni di connessione. Per eseguire questa operazione:

1. Immettere un **[!UICONTROL Label]** per assegnare un nome alla connessione al database.

1. Aggiungi l&#39;indirizzo dell&#39;application server nel campo **[!UICONTROL URL]** . Se non conosci l’URL di connessione, contatta l’amministratore.

1. Controlla **[!UICONTROL Connect with an Adobe ID]** che gli operatori si connettano alla console utilizzando il proprio Adobe ID. Per ulteriori informazioni, consulta [questa pagina](../../integrations/using/about-adobe-id.md).

1. Fai clic su **[!UICONTROL OK]** per convalidare.

## Operatori e autorizzazioni {#operators-and-permissions}

Gli identificatori e le password degli operatori con accesso al software e alle relative autorizzazioni sono definiti dall’amministratore di sistema di Adobe Campaign nel nodo **[!UICONTROL Administration > Access management > Operators]** della struttura Adobe Campaign.

Questa funzionalità è descritta nella sezione [Gestione accessi](../../platform/using/access-management.md) .

## Disconnetti da Adobe Campaign {#disconnecting-from-adobe-campaign}

Per disconnettersi da Adobe Campaign, utilizza la prima icona nella barra delle icone.

![](assets/s_ncs_user_deconnexion.png)

>[!NOTE]
>
>È inoltre possibile chiudere l&#39;applicazione senza prima disconnettersi.

## Scarica la tua versione Adobe Campaign {#getting-your-campaign-version}

Il menu **[!UICONTROL Help > About...]** ti consente di accedere alle seguenti informazioni:

* **Numero di versione** per la console del client Campaign e il server applicazioni
* **Numero build** per la console del client Campaign e il server applicazioni
* un collegamento per contattare l’Assistenza clienti di Adobe
* collegamenti alla Policy per i cookie, alle Condizioni d’uso e all’Informativa sulla privacy di Adobe

![](assets/about-acc.png)

Ogni volta che ti rivolgi al team di assistenza clienti di Adobe, devi fornire il numero di versione e il numero di build della console client e del server applicazioni di Adobe Campaign.

Se utilizzi [Campaign [!DNL Gold Standard] version](../../rn/using/gold-standard.md), devi anche condividere i caratteri SHA/1 visualizzati nella casella **[!UICONTROL About]**. Ad esempio, per la versione Gold **Standard 10**, il numero di build mostrerà **build 9032@efd8a94**, come illustrato di seguito:

![](assets/about-acc-gs.png)

Ulteriori informazioni su [!DNL Gold Standard] [in questo articolo](../../rn/using/gs-overview.md)).

**Argomenti correlati**:

* [Guida e opzioni di supporto per Adobe Campaign](../../support.md)
* [Distribuzione di software Adobe Campaign](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
* [Sessioni Adobe Experience Cloud Support ed Expert](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)
