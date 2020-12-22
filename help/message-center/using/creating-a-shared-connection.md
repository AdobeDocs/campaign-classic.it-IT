---
solution: Campaign Classic
product: campaign
title: Creazione di una connessione condivisa
description: Creazione di una connessione condivisa
audience: message-center
content-type: reference
topic-tags: instance-configuration
translation-type: tm+mt
source-git-commit: 5bc6c8a824929c6a61cf562fc961e5bdd1867837
workflow-type: tm+mt
source-wordcount: '998'
ht-degree: 2%

---


# Creazione di una connessione condivisa{#creating-a-shared-connection}

>[!IMPORTANT]
>
>* Le estensioni dello schema eseguite sugli schemi utilizzati dai flussi di lavoro tecnici [Message Center](../../message-center/using/technical-workflows.md) nelle istanze di controllo o di esecuzione devono essere duplicate sulle altre istanze utilizzate  modulo di messaggistica transazionale Adobe Campaign.
>* L&#39;istanza di controllo e le istanze di esecuzione devono essere installate su computer diversi. Non possono condividere la stessa istanza Campaign.

>



## Istanza di controllo {#control-instance}

Se si dispone di un&#39;architettura suddivisa, è necessario specificare le istanze di esecuzione collegate all&#39;istanza di controllo e collegarle. I modelli di messaggi transazionali vengono distribuiti alle istanze di esecuzione. La connessione tra l&#39;istanza di controllo e le istanze di esecuzione viene creata configurando gli account esterni di tipo **[!UICONTROL Execution instance]**. È necessario creare un numero illimitato di account esterni, al pari delle istanze di esecuzione.

>[!NOTE]
>
>Quando le istanze di esecuzione vengono utilizzate da più istanze di controllo, i dati possono essere divisi per cartella e per operatore. Per ulteriori informazioni, fare riferimento a [Utilizzo di più istanze di controllo](#using-several-control-instances).

Per creare un account esterno di tipo istanza di esecuzione, procedere come segue:

1. Andate alla cartella **[!UICONTROL Administration > Platform > External accounts]**.
1. Selezionate uno dei tipi di account esterni forniti con Adobe Campaign &#39;istanza di esecuzione, fate clic con il pulsante destro del mouse e scegliete **[!UICONTROL Duplicate]** .

   ![](assets/messagecenter_create_extaccount_001.png)

1. Modificate l’etichetta in base alle vostre esigenze.

   ![](assets/messagecenter_create_extaccount_002.png)

1. Selezionare l&#39;opzione **[!UICONTROL Enabled]** per rendere operativo il conto esterno.

   ![](assets/messagecenter_create_extaccount_003.png)

1. Specificate l&#39;indirizzo del server in cui è installata l&#39;istanza di esecuzione.

   ![](assets/messagecenter_create_extaccount_004.png)

1. L&#39;account deve corrispondere all&#39;agente del Centro messaggi come definito nella cartella dell&#39;operatore. Per impostazione predefinita, l&#39;account out-of-the-box fornito da  Adobe Campaign è **[!UICONTROL mc]** .

   ![](assets/messagecenter_create_extaccount_005.png)

1. Immettete la password dell’account come definito nella cartella dell’operatore.

   >[!NOTE]
   >
   >Per evitare di immettere una password ogni volta che si accede all&#39;istanza, è possibile specificare l&#39;indirizzo IP dell&#39;istanza di controllo nell&#39;istanza di esecuzione. Per ulteriori informazioni, fare riferimento a [Istanza di esecuzione](#execution-instance).

1. Specificare il metodo di ripristino da utilizzare per l&#39;istanza di esecuzione.

   I dati da recuperare vengono inoltrati all&#39;istanza di controllo dall&#39;istanza di esecuzione, da aggiungere agli archivi dei messaggi e degli eventi transazionali.

   ![](assets/messagecenter_create_extaccount_007.png)

   La raccolta dei dati avviene tramite un servizio Web che utilizza l&#39;accesso HTTP/HTTPS, oppure tramite il modulo FDA (Federated Data Access).

   >[!NOTE]
   >
   >Tenere presente che quando si utilizza FDA su HTTP, sono supportate solo le istanze di esecuzione che utilizzano un database PostgreSQL. MSSQL o  database Oracle non sono supportati.

   Il secondo metodo è consigliato se l&#39;istanza di controllo ha accesso diretto al database delle istanze di esecuzione. In caso contrario, scegliete l&#39;accesso al servizio Web. L&#39;account FDA da specificare coincide con la connessione ai database delle varie istanze di esecuzione create nell&#39;istanza di controllo.

   ![](assets/messagecenter_create_extaccount_008.png)

   Per ulteriori informazioni su Federated Data Access (FDA), fare riferimento a [Accesso a un database esterno](../../installation/using/about-fda.md).

1. Fare clic su **[!UICONTROL Test the connection]** per assicurarsi che l&#39;istanza di controllo e l&#39;istanza di esecuzione siano collegate.

   ![](assets/messagecenter_create_extaccount_006.png)

1. Ogni istanza di esecuzione deve essere associata a un identificatore. Questo identificatore può essere attribuito a ogni istanza di esecuzione manualmente, utilizzando la procedura guidata di distribuzione (fare riferimento a [Identificazione delle istanze di esecuzione](../../message-center/using/identifying-execution-instances.md)) oppure automaticamente, facendo clic sul pulsante **Inizializza connessione** dall&#39;istanza di controllo.

   ![](assets/messagecenter_create_extaccount_006bis.png)

## Istanza di esecuzione {#execution-instance}

Affinché l&#39;istanza di controllo possa connettersi all&#39;istanza di esecuzione senza dover fornire una password, è sufficiente immettere l&#39;indirizzo IP dell&#39;istanza di controllo nella sezione dei diritti di accesso **Centro messaggi**. Tuttavia, per impostazione predefinita le password vuote sono vietate.

Per utilizzare una password vuota, andate alle istanze di esecuzione e definite una zona di protezione limitata all&#39;indirizzo IP del sistema di informazione che distribuisce gli eventi. Questa area di protezione deve consentire password vuote e accettare connessioni di tipo `<identifier> / <password>`. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../installation/using/configuring-campaign-server.md#defining-security-zones).

>[!NOTE]
>
>Quando le istanze di esecuzione vengono utilizzate da più istanze di controllo, i dati possono essere divisi per cartella e per operatore. Per ulteriori informazioni, fare riferimento a [Utilizzo di più istanze di controllo](#using-several-control-instances).

1. Passate alla cartella dell&#39;operatore nell&#39;istanza di esecuzione ( **[!UICONTROL Administration > Access management > Operators]** ).
1. Selezionare l&#39;agente **Message Center**.

   ![](assets/messagecenter_operator_001.png)

1. Selezionare la scheda **[!UICONTROL Edit]**, fare clic su **[!UICONTROL Access rights]**, quindi fare clic sul collegamento **[!UICONTROL Edit the access parameters...]**.

   ![](assets/messagecenter_operator_002.png)

1. Nella finestra **[!UICONTROL Access settings]**, fare clic sul collegamento **[!UICONTROL Add a trusted IP mask]** e aggiungere l&#39;indirizzo IP dell&#39;istanza di controllo.

   ![](assets/messagecenter_operator_003.png)

## Uso di più istanze di controllo {#using-several-control-instances}

È possibile condividere un cluster di esecuzione con diverse istanze di controllo. Questo tipo di architettura richiede la seguente configurazione.

Ad esempio, se la società gestisce due marchi, ciascuno con una propria istanza di controllo: **Controllo 1** e **Controllo 2**. Vengono utilizzate anche due istanze di esecuzione. È necessario immettere un operatore del Centro messaggi diverso per ogni istanza di controllo: un operatore **mc1** per l&#39;istanza **Control 1** e un operatore **mc2** per l&#39;istanza **Control 2**.

Nella struttura ad albero di tutte le istanze di esecuzione, creare una cartella per operatore (**Cartella 1** e **Cartella 2**) e limitare l&#39;accesso ai dati di ciascun operatore alla propria cartella.

### Configurazione delle istanze di controllo {#configuring-control-instances}

1. Nell&#39;istanza di controllo **Control 1**, creare un account esterno per istanza di esecuzione e immettere l&#39;operatore **mc1** in ciascun account esterno. L&#39;operatore **mc1** verrà successivamente creato su tutte le istanze di esecuzione (fare riferimento a [Configurazione delle istanze di esecuzione](#configuring-execution-instances)).

   ![](assets/messagecenter_multi_control_1.png)

1. Nell&#39;istanza di controllo **Control 2**, creare un account esterno per istanza di esecuzione e immettere l&#39;operatore **mc2** in ciascun account esterno. L&#39;operatore **mc2** verrà successivamente creato su tutte le istanze di esecuzione (fare riferimento a [Configurazione delle istanze di esecuzione](#configuring-execution-instances)).

   ![](assets/messagecenter_multi_control_2.png)

   >[!NOTE]
   >
   >Per ulteriori informazioni sulla configurazione di un&#39;istanza di controllo, fare riferimento a [istanza di controllo](#control-instance).

### Configurazione delle istanze di esecuzione {#configuring-execution-instances}

Per utilizzare più istanze di controllo, questa configurazione deve essere eseguita su TUTTE le istanze di esecuzione.

1. Crea una cartella per operatore nel nodo **[!UICONTROL Administration > Production > Message Center]**: **Cartella 1** e **Cartella 2**. Per ulteriori informazioni sulla creazione di cartelle e viste, vedere [Piattaforma](../../platform/using/access-management.md#folders-and-views).

   ![](assets/messagecenter_multi_control_3.png)

1. Creare gli operatori **mc1** e **mc2** duplicando l&#39;operatore del Centro messaggi fornito per impostazione predefinita (**mc**). Per ulteriori informazioni sulla creazione di operatori, consultare [questa sezione](../../platform/using/access-management.md#operators).

   ![](assets/messagecenter_multi_control_4.png)

   >[!NOTE]
   >
   >**gli** operatori mc1 e  **mc2** devono disporre  **[!UICONTROL Message Center execution]** dei diritti e non possono accedere alla console client Adobe Campaign . Un operatore deve sempre essere collegato a una zona di sicurezza. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../installation/using/configuring-campaign-server.md#defining-security-zones).

1. Per ciascun operatore, selezionate la casella **[!UICONTROL Restrict to information found in sub-folders of]** e la cartella corrispondente (**Cartella 1** per l&#39;operatore **mc1** e **Cartella 2** per l&#39;operatore **mc2**).

   ![](assets/messagecenter_multi_control_5.png)

1. Consentire a ciascun operatore di leggere e scrivere le autorizzazioni per la propria cartella. A tale scopo, fare clic con il pulsante destro del mouse sulla cartella e selezionare **[!UICONTROL Properties]** . Selezionare la scheda **[!UICONTROL Security]** e aggiungere l&#39;operatore appropriato (**mc1** per **Cartella 1** e **mc2** per **Cartella 2**). Assicurarsi che le caselle **[!UICONTROL Read/Write data]** siano selezionate.

   ![](assets/messagecenter_multi_control_6.png)

