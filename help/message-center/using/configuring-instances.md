---
product: campaign
title: Configurare le istanze
description: Scopri come configurare le istanze di esecuzione e controllo della messaggistica transazionale in Adobe Campaign Classic
feature: Transactional Messaging, Message Center
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 23a384d1-27ce-46c2-98c3-0fb60a5c50ee
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '1243'
ht-degree: 2%

---


# Configurare le istanze {#creating-a-shared-connection}



Per utilizzare le funzionalità di messaggistica transazionale, devi configurare le istanze di controllo ed esecuzione. Puoi utilizzare:
* [Un’istanza di controllo](#control-instance) associata a una o più istanze di esecuzione
* [Diverse istanze di controllo](#using-several-control-instances) associata a più istanze di esecuzione

>[!IMPORTANT]
>
>Le estensioni dello schema hanno interessato le risorse utilizzate da [Flussi di lavoro tecnici del Centro messaggi](../../message-center/using/additional-configurations.md#technical-workflows) sulle istanze di controllo o di esecuzione devono essere duplicate sulle altre istanze utilizzate dal modulo di messaggistica transazionale.

È inoltre necessario specificare e connettere le istanze di esecuzione alle istanze di controllo.

In questa sezione sono descritti tutti i passaggi necessari per configurare e connettere le istanze di controllo ed esecuzione.

>[!IMPORTANT]
>
>L&#39;istanza di controllo e le istanze di esecuzione devono essere installate su computer diversi. Non possono condividere la stessa istanza di Campaign.

## Configurare l’istanza di controllo {#control-instance}

Per connettere l’istanza di controllo e le istanze di esecuzione, devi innanzitutto creare e configurare un’ **[!UICONTROL Execution instance]** digita account esterno **sull’istanza di controllo**. Pertanto, una volta [pubblicato](../../message-center/using/publishing-message-templates.md#template-publication), i modelli di messaggi transazionali possono essere distribuiti nelle istanze di esecuzione.

Se utilizzi più istanze di esecuzione, devi creare tanti account esterni quanti sono le istanze di esecuzione.

>[!NOTE]
>
>Quando le istanze di esecuzione vengono utilizzate da più istanze di controllo, i dati possono essere suddivisi per cartella e per operatore. Per ulteriori informazioni, consulta [Utilizzare più istanze di controllo](#using-several-control-instances).

### Creare un account esterno

>[!NOTE]
>
>Devono essere eseguiti i passaggi seguenti **sull’istanza di controllo**.

Per creare un **[!UICONTROL Execution instance]** digita account esterno, applica quanto segue:

1. Vai a **[!UICONTROL Administration > Platform > External accounts]** cartella.
1. Seleziona uno degli account esterni di tipo istanza di esecuzione forniti con Adobe Campaign, fai clic con il pulsante destro del mouse e scegli **[!UICONTROL Duplicate]** .

   ![](assets/messagecenter_create_extaccount_001.png)

1. Modifica l’etichetta in base alle tue esigenze.

   ![](assets/messagecenter_create_extaccount_002.png)

1. Seleziona la **[!UICONTROL Enabled]** per rendere operativo l’account esterno.

   ![](assets/messagecenter_create_extaccount_003.png)

1. Specificare l&#39;indirizzo del server in cui è installata l&#39;istanza di esecuzione.

   ![](assets/messagecenter_create_extaccount_004.png)

1. L&#39;account deve corrispondere all&#39;agente del Centro messaggi definito nella cartella dell&#39;operatore. Per impostazione predefinita, l’account predefinito fornito da Adobe Campaign è **[!UICONTROL mc]** .

   ![](assets/messagecenter_create_extaccount_005.png)

1. Immetti la password dell’account come definito nella cartella dell’operatore.

   >[!NOTE]
   >
   >Per evitare di immettere una password ogni volta che si accede all&#39;istanza, è possibile specificare l&#39;indirizzo IP dell&#39;istanza di controllo nell&#39;istanza di esecuzione. Per ulteriori informazioni, consulta [Configurare le istanze di esecuzione](#execution-instance).

1. Specificare il metodo di ripristino da utilizzare per l&#39;istanza di esecuzione. I dati da recuperare vengono inoltrati all’istanza di controllo dall’istanza di esecuzione, per essere aggiunti agli archivi dei messaggi transazionali e degli eventi.

   ![](assets/messagecenter_create_extaccount_007.png)

   La raccolta dei dati avviene tramite un servizio web che utilizza l’accesso HTTP/HTTPS o tramite il modulo Federated Data Access (FDA).

   >[!NOTE]
   >
   >Tieni presente che quando utilizzi FDA su HTTP, sono supportate solo le istanze di esecuzione che utilizzano un database PostgreSQL. MSSQL o database Oracle non supportati.

   Il secondo metodo (FDA) è consigliato se l’istanza di controllo ha accesso diretto al database delle istanze di esecuzione. In caso contrario, scegliere l&#39;accesso al servizio Web. L’account FDA da specificare coincide con la connessione ai database delle varie istanze di esecuzione create nell’istanza di controllo.

   ![](assets/messagecenter_create_extaccount_008.png)

   Per ulteriori informazioni su Federated Data Access (FDA), consulta [questa sezione](../../installation/using/about-fda.md).

1. Clic **[!UICONTROL Test the connection]** per assicurarsi che l’istanza di controllo e l’istanza di esecuzione siano collegate.

   ![](assets/messagecenter_create_extaccount_006.png)

Quando utilizzi più istanze di esecuzione, ripeti questi passaggi per creare tanti account esterni quanti sono le istanze di esecuzione.

### Identificare le istanze di esecuzione {#identifying-execution-instances}

Ogni istanza di esecuzione deve essere associata a un identificatore univoco per differenziare la cronologia di ogni istanza di esecuzione durante la visualizzazione nell’istanza di controllo.

Questo identificatore può essere attribuito a ogni istanza di esecuzione **manualmente**. In questo caso, è necessario eseguire questo passaggio **su ogni istanza di esecuzione**. A questo scopo, utilizza la procedura guidata di distribuzione come descritto di seguito:

1. Aprire la procedura guidata di distribuzione in un&#39;istanza di esecuzione.
1. Vai a **[!UICONTROL Message Center]** finestra.
1. Assegna l’identificatore scelto all’istanza.

   ![](assets/messagecenter_id_execinstance_001.png)

1. Ripeti i passaggi precedenti per ogni istanza di esecuzione.

L’identificatore può anche essere **automaticamente** attribuiti. Per eseguire questa operazione, passare al **istanza di controllo**, quindi fare clic su **[!UICONTROL Initialize connection]** pulsante.

![](assets/messagecenter_create_extaccount_006bis.png)

## Configurare le istanze di esecuzione {#execution-instance}

>[!NOTE]
>
>Devono essere eseguiti i passaggi seguenti **sulle istanze di esecuzione**.

Per collegare le istanze di esecuzione all’istanza di controllo, segui i passaggi seguenti.

Affinché l’istanza di controllo possa connettersi all’istanza di esecuzione senza dover fornire una password, è sufficiente immettere l’indirizzo IP dell’istanza di controllo in **Centro messaggi** sezione diritti di accesso. Le password vuote non sono tuttavia consentite per impostazione predefinita.

Per utilizzare una password vuota, vai alle istanze di esecuzione e definisci un’area di sicurezza limitata all’indirizzo IP del sistema informativo che distribuisce gli eventi. Questa area di sicurezza deve consentire password vuote e accettare `<identifier> / <password>` digitare le connessioni. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../installation/using/security-zones.md).

>[!NOTE]
>
>Quando le istanze di esecuzione vengono utilizzate da più istanze di controllo, i dati possono essere suddivisi per cartella e per operatore. Per ulteriori informazioni, consulta [Utilizzare più istanze di controllo](#using-several-control-instances).

1. In un’istanza di esecuzione, passa alla cartella dell’operatore ( **[!UICONTROL Administration > Access management > Operators]** ).
1. Seleziona la **Centro messaggi** agente.

   ![](assets/messagecenter_operator_001.png)

1. Seleziona la **[!UICONTROL Edit]** , fare clic su **[!UICONTROL Access rights]** , quindi fare clic su **[!UICONTROL Edit the access parameters...]** collegamento.

   ![](assets/messagecenter_operator_002.png)

1. In **[!UICONTROL Access settings]** , fare clic sul pulsante **[!UICONTROL Add a trusted IP mask]** e aggiungi l’indirizzo IP dell’istanza di controllo.

   ![](assets/messagecenter_operator_003.png)

Quando utilizzi più istanze di esecuzione, ripeti questi passaggi per ogni istanza di esecuzione.

## Utilizzare più istanze di controllo {#using-several-control-instances}

È possibile condividere un cluster di esecuzione con varie istanze di controllo. Questo tipo di architettura richiede la seguente configurazione.

Ad esempio, immagina che la tua azienda gestisca due marchi, ciascuno con la propria istanza di controllo: **Controllo 1** e **Controllo 2**. Vengono utilizzate anche due istanze di esecuzione. È necessario immettere un operatore del Centro messaggi diverso per ogni istanza di controllo: **mc1** operatore per **Controllo 1** e un **mc2** operatore per **Controllo 2** dell&#39;istanza.

Nella struttura di tutte le istanze di esecuzione, crea una cartella per operatore (**Cartella 1** e **Cartella 2**) e limitare l’accesso ai dati di ogni operatore alla propria cartella.

### Configurare le istanze di controllo {#configuring-control-instances}

>[!NOTE]
>
>Devono essere eseguiti i passaggi seguenti **sulle istanze di controllo**.

1. Il giorno **Controllo 1** istanza di controllo, crea un account esterno per ogni istanza di esecuzione e immetti **mc1** in ciascun account esterno. Il **mc1** verrà quindi creato su tutte le istanze di esecuzione (vedi [Configurare le istanze di esecuzione](#configuring-execution-instances)).

   ![](assets/messagecenter_multi_control_1.png)

1. Il giorno **Controllo 2** istanza di controllo, crea un account esterno per ogni istanza di esecuzione e immetti **mc2** in ciascun account esterno. Il **mc2** verrà quindi creato su tutte le istanze di esecuzione (vedi [Configurare le istanze di esecuzione](#configuring-execution-instances)).

   ![](assets/messagecenter_multi_control_2.png)

   >[!NOTE]
   >
   >Per ulteriori informazioni sulla configurazione di un’istanza di controllo, consulta [questa sezione](#control-instance).

### Configurare le istanze di esecuzione {#configuring-execution-instances}

>[!NOTE]
>
>Devono essere eseguiti i passaggi seguenti **sulle istanze di esecuzione**.

Per utilizzare più istanze di controllo, questa configurazione deve essere eseguita su TUTTE le istanze di esecuzione.

1. Crea una cartella per operatore nel **[!UICONTROL Administration > Production > Message Center]** nodo: **Cartella 1** e **Cartella 2**. Per ulteriori informazioni sulla creazione di cartelle e visualizzazioni, consulta [questa pagina](../../platform/using/access-management-folders.md).

   ![](assets/messagecenter_multi_control_3.png)

1. Creare **mc1** e **mc2** duplicando l&#39;operatore del Centro messaggi fornito per impostazione predefinita (**mc**). Per ulteriori informazioni sulla creazione di operatori, consulta [questa sezione](../../platform/using/access-management-operators.md).

   ![](assets/messagecenter_multi_control_4.png)

   >[!NOTE]
   >
   >**mc1** e **mc2** gli operatori devono avere **[!UICONTROL Message Center execution]** e non possono avere accesso alla console client di Adobe Campaign. Un operatore deve sempre essere collegato a un’area di sicurezza. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../installation/using/security-zones.md).

1. Per ogni operatore, controlla **[!UICONTROL Restrict to information found in sub-folders of]** e selezionare la cartella pertinente (**Cartella 1** per **mc1** operatore e **Cartella 2** per **mc2** operatore).

   ![](assets/messagecenter_multi_control_5.png)

1. Assegna a ogni operatore autorizzazioni di lettura e scrittura per la propria cartella. A tale scopo, fai clic con il pulsante destro del mouse sulla cartella e seleziona (Copia negli Appunti) **[!UICONTROL Properties]** . Quindi seleziona la **[!UICONTROL Security]** e aggiungi l’operatore pertinente (**mc1** per **Cartella 1** e **mc2** per **Cartella 2**). Assicurati che il **[!UICONTROL Read/Write data]** le caselle sono selezionate.

   ![](assets/messagecenter_multi_control_6.png)
