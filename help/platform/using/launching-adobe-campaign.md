---
product: campaign
title: Avvio di Adobe Campaign
description: Avvio di Adobe Campaign
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 4d9c5b24-83a2-4495-a56c-5bc376d69703
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 12%

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

## Connettersi ad Adobe Campaign {#connecting-to-adobe-campaign}

Puoi connetterti ad Adobe Campaign utilizzando il tuo Adobe ID. Per ulteriori informazioni, consulta [questa pagina](../../integrations/using/about-adobe-id.md).

Puoi anche effettuare la connessione con un login/password dedicato:

1. Immetti l’identificatore dell’account operatore nel **[!UICONTROL Login]** campo .

   L’amministratore della piattaforma Adobe Campaign fornisce l’identificatore .

1. Immetti la password nel **[!UICONTROL Password]** campo .

   La prima volta che accedi al database, la password viene fornita dall&#39;amministratore. Una volta connesso, è possibile modificare la password tramite il **[!UICONTROL Tools > Change password...]** menu. I dettagli sugli operatori e le connessioni sono disponibili in [Gestione degli accessi](../../platform/using/access-management.md).

1. Fai clic su **[!UICONTROL LOG IN]** per confermare.<!--You can also press the **Enter** key to launch connection.-->

Ora puoi accedere a [Area di lavoro di Adobe Campaign](../../platform/using/adobe-campaign-workspace.md).

Alcune scelte rapide da tastiera sono disponibili nella **[!UICONTROL Sign in screen]**:
* Tutti gli elementi utilizzabili sono selezionabili tramite **Scheda** key (dall&#39;alto verso il basso) o **Scheda** + **Maiusc** tasti (dal basso all&#39;alto).
* Per avviare la connessione, puoi anche premere il pulsante **Invio** chiave.
* È possibile utilizzare **Esc** per reimpostare la **[!UICONTROL Login]** e **[!UICONTROL Password]** all&#39;ultimo valore di connessione riuscito.

## Configurare le connessioni {#setting-up-connections}

Puoi accedere alle impostazioni di connessione al server tramite il collegamento situato sopra la zona di input.

![](assets/s_ncs_user_connections_management.png)

In **[!UICONTROL Connections]** finestra, fai clic su **[!UICONTROL Add > Connection]**.

È quindi necessario definire le impostazioni di connessione. Per eseguire questa operazione:

1. Inserisci un **[!UICONTROL Label]** per assegnare un nome alla connessione al database.

1. Aggiungi l&#39;indirizzo dell&#39;application server nel **[!UICONTROL URL]** campo . Se non conosci l’URL di connessione, contatta l’amministratore.

1. Controlla **[!UICONTROL Connect with an Adobe ID]** per consentire agli operatori di connettersi alla console utilizzando il proprio Adobe ID. Per ulteriori informazioni, consulta [questa pagina](../../integrations/using/about-adobe-id.md).

1. Fai clic su **[!UICONTROL OK]** da convalidare.

## Operatori e autorizzazioni {#operators-and-permissions}

Gli identificatori e le password degli operatori con accesso al software e le rispettive autorizzazioni sono definiti dall&#39;amministratore di sistema di Adobe Campaign nella sezione **[!UICONTROL Administration > Access management > Operators]** nodo della struttura Adobe Campaign.

Questa funzionalità è descritta in [Gestione degli accessi](../../platform/using/access-management.md) sezione .

## Disconnetti da Adobe Campaign {#disconnecting-from-adobe-campaign}

Per disconnettersi da Adobe Campaign, utilizza la prima icona nella barra delle icone.

![](assets/s_ncs_user_deconnexion.png)

>[!NOTE]
>
>È inoltre possibile chiudere l&#39;applicazione senza prima disconnettersi.

## Scarica la tua versione di Adobe Campaign {#getting-your-campaign-version}

La **[!UICONTROL Help > About...]** consente di accedere alle seguenti informazioni:

* **version** numero per la console del client Campaign e il server applicazioni
* **build** numero per la console del client Campaign e il server applicazioni
* un collegamento per contattare l’Assistenza clienti di Adobe
* collegamenti alla Policy per i cookie, alle Condizioni d’uso e all’Informativa sulla privacy di Adobe

![](assets/about-acc.png)

Ogni volta che ti rivolgi al team di assistenza clienti di Adobe, devi fornire il numero di versione e il numero di build della console client e del server applicazioni di Adobe Campaign.

**Argomenti correlati**:

* [Guida e opzioni di supporto per Adobe Campaign](../../support.md)
* [Distribuzione di software Adobe Campaign](https://experience.adobe.com/#/downloads/content/software-distribution/it/campaign.html)
* [Sessioni Adobe Experience Cloud Support ed Expert](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)
