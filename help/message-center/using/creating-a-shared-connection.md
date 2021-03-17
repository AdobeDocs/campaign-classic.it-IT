---
solution: Campaign Classic
product: campaign
title: Creazione di una connessione condivisa
description: Creazione di una connessione condivisa
audience: message-center
content-type: reference
topic-tags: instance-configuration
translation-type: tm+mt
source-git-commit: d88815e36f7be1b010dcaeee51013a5da769b4a8
workflow-type: tm+mt
source-wordcount: '999'
ht-degree: 2%

---


# Creazione di una connessione condivisa{#creating-a-shared-connection}

>[!IMPORTANT]
>
>* Le estensioni dello schema effettuate sugli schemi utilizzati da [Flussi di lavoro tecnici del Centro messaggi](../../message-center/using/technical-workflows.md) su istanze di controllo o di esecuzione devono essere duplicate sulle altre istanze utilizzate dal modulo di messaggistica transazionale di Adobe Campaign.
>* L&#39;istanza di controllo e le istanze di esecuzione devono essere installate su computer diversi. Non possono condividere la stessa istanza Campaign.

>



## Istanza di controllo {#control-instance}

Se si dispone di un’architettura suddivisa, è necessario specificare le istanze di esecuzione collegate all’istanza di controllo e collegarle. I modelli di messaggi transazionali vengono distribuiti alle istanze di esecuzione. La connessione tra l’istanza di controllo e le istanze di esecuzione viene creata configurando il tipo **[!UICONTROL Execution instance]** account esterni. È necessario creare un numero illimitato di account esterni come sono presenti istanze di esecuzione.

>[!NOTE]
>
>Quando le istanze di esecuzione vengono utilizzate da più istanze di controllo, i dati possono essere suddivisi per cartella e per operatore. Per ulteriori informazioni, consulta [Uso di più istanze di controllo](#using-several-control-instances).

Per creare un account esterno di tipo istanza di esecuzione, esegui i seguenti passaggi:

1. Vai alla cartella **[!UICONTROL Administration > Platform > External accounts]** .
1. Seleziona uno dei tipi di istanza di esecuzione account esterni forniti out-of-the-box con Adobe Campaign, fai clic con il pulsante destro del mouse e scegli **[!UICONTROL Duplicate]** .

   ![](assets/messagecenter_create_extaccount_001.png)

1. Modifica l’etichetta in base alle tue esigenze.

   ![](assets/messagecenter_create_extaccount_002.png)

1. Seleziona l’opzione **[!UICONTROL Enabled]** per rendere operativo l’account esterno.

   ![](assets/messagecenter_create_extaccount_003.png)

1. Specifica l&#39;indirizzo del server in cui è installata l&#39;istanza di esecuzione.

   ![](assets/messagecenter_create_extaccount_004.png)

1. L&#39;account deve corrispondere all&#39;agente del Centro messaggi come definito nella cartella dell&#39;operatore. Per impostazione predefinita, l’account predefinito fornito da Adobe Campaign è **[!UICONTROL mc]** .

   ![](assets/messagecenter_create_extaccount_005.png)

1. Immetti la password dell’account come definito nella cartella dell’operatore .

   >[!NOTE]
   >
   >Per evitare di inserire una password ogni volta che accedi all’istanza, puoi specificare l’indirizzo IP dell’istanza di controllo nell’istanza di esecuzione. Per ulteriori informazioni, consulta [Istanza di esecuzione](#execution-instance).

1. Specificare il metodo di ripristino da utilizzare per l&#39;istanza di esecuzione.

   I dati da recuperare vengono inoltrati all’istanza di controllo dall’istanza di esecuzione, per aggiungere agli archivi dei messaggi transazionali e degli eventi.

   ![](assets/messagecenter_create_extaccount_007.png)

   La raccolta dei dati avviene tramite un servizio Web che utilizza l’accesso HTTP/HTTPS o tramite il modulo Federated Data Access (FDA).

   >[!NOTE]
   >
   >Tieni presente che quando utilizzi FDA su HTTP, sono supportate solo le istanze di esecuzione che utilizzano un database PostgreSQL. I database MSSQL o Oracle non sono supportati.

   Il secondo metodo è consigliato se l’istanza di controllo ha accesso diretto al database delle istanze di esecuzione. In caso contrario, scegliere l&#39;accesso al servizio Web. L&#39;account FDA da specificare coincide con la connessione ai database delle varie istanze di esecuzione create sull&#39;istanza di controllo.

   ![](assets/messagecenter_create_extaccount_008.png)

   Per ulteriori informazioni su Federated Data Access (FDA), consulta [Accesso a un database esterno](../../installation/using/about-fda.md).

1. Fai clic su **[!UICONTROL Test the connection]** per verificare che l’istanza di controllo e l’istanza di esecuzione siano collegate.

   ![](assets/messagecenter_create_extaccount_006.png)

1. Ogni istanza di esecuzione deve essere associata a un identificatore . Questo identificatore può essere attribuito a ogni istanza di esecuzione manualmente, utilizzando la procedura guidata di distribuzione (fare riferimento a [Identificazione delle istanze di esecuzione](../../message-center/using/identifying-execution-instances.md)) o automaticamente, facendo clic sul pulsante **Inizializza connessione** dall&#39;istanza di controllo.

   ![](assets/messagecenter_create_extaccount_006bis.png)

## Istanza di esecuzione {#execution-instance}

Affinché l&#39;istanza di controllo possa connettersi all&#39;istanza di esecuzione senza dover fornire una password, è sufficiente inserire l&#39;indirizzo IP dell&#39;istanza di controllo nella sezione **Message Center** access rights . Tuttavia, le password vuote sono vietate per impostazione predefinita.

Per utilizzare una password vuota, vai alle istanze di esecuzione e definisci una zona di sicurezza limitata all’indirizzo IP del sistema di informazioni che distribuisce gli eventi. Questa zona di sicurezza deve consentire password vuote e accettare connessioni di tipo `<identifier> / <password>`. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../installation/using/security-zones.md).

>[!NOTE]
>
>Quando le istanze di esecuzione vengono utilizzate da più istanze di controllo, i dati possono essere suddivisi per cartella e per operatore. Per ulteriori informazioni, consulta [Uso di più istanze di controllo](#using-several-control-instances).

1. Vai alla cartella dell’operatore nell’istanza di esecuzione ( **[!UICONTROL Administration > Access management > Operators]** ).
1. Selezionare l&#39;agente **Centro messaggi**.

   ![](assets/messagecenter_operator_001.png)

1. Seleziona la scheda **[!UICONTROL Edit]** , fai clic su **[!UICONTROL Access rights]** , quindi fai clic sul collegamento **[!UICONTROL Edit the access parameters...]** .

   ![](assets/messagecenter_operator_002.png)

1. Nella finestra **[!UICONTROL Access settings]**, fai clic sul collegamento **[!UICONTROL Add a trusted IP mask]** e aggiungi l’indirizzo IP dell’istanza di controllo.

   ![](assets/messagecenter_operator_003.png)

## Utilizzo di più istanze di controllo {#using-several-control-instances}

È possibile condividere un cluster di esecuzione con varie istanze di controllo. Questo tipo di architettura richiede la seguente configurazione.

Ad esempio, se la tua azienda gestisce due marchi, ciascuno con la propria istanza di controllo: **Controllare 1** e **controllare 2**. Vengono inoltre utilizzate due istanze di esecuzione. È necessario immettere un operatore Message Center diverso per ogni istanza di controllo: un operatore **mc1** per l&#39;istanza **Control 1** e un operatore **mc2** per l&#39;istanza **Control 2**.

Nella struttura di tutte le istanze di esecuzione, crea una cartella per operatore (**Cartella 1** e **Cartella 2**) e limita l&#39;accesso ai dati di ciascun operatore alla propria cartella.

### Configurazione delle istanze di controllo {#configuring-control-instances}

1. Nell&#39;istanza di controllo **Control 1**, crea un account esterno per istanza di esecuzione e immetti l&#39;operatore **mc1** in ciascun account esterno. L’operatore **mc1** verrà in seguito creato su tutte le istanze di esecuzione (consulta [Configurazione delle istanze di esecuzione](#configuring-execution-instances)).

   ![](assets/messagecenter_multi_control_1.png)

1. Nell&#39;istanza di controllo **Control 2**, crea un account esterno per istanza di esecuzione e immetti l&#39;operatore **mc2** in ciascun account esterno. L’operatore **mc2** verrà in seguito creato su tutte le istanze di esecuzione (consulta [Configurazione delle istanze di esecuzione](#configuring-execution-instances)).

   ![](assets/messagecenter_multi_control_2.png)

   >[!NOTE]
   >
   >Per ulteriori informazioni sulla configurazione di un&#39;istanza di controllo, consulta [Istanza di controllo](#control-instance).

### Configurazione delle istanze di esecuzione {#configuring-execution-instances}

Per utilizzare più istanze di controllo, questa configurazione deve essere eseguita su TUTTE le istanze di esecuzione.

1. Crea una cartella per operatore nel nodo **[!UICONTROL Administration > Production > Message Center]**: **Cartella 1** e **Cartella 2**. Per ulteriori informazioni sulla creazione di cartelle e visualizzazioni, consulta [questa pagina](../../platform/using/access-management-folders.md).

   ![](assets/messagecenter_multi_control_3.png)

1. Crea gli operatori **mc1** e **mc2** duplicando l&#39;operatore del Centro messaggi fornito per impostazione predefinita (**mc**). Per ulteriori informazioni sulla creazione di operatori, consulta [questa sezione](../../platform/using/access-management-operators.md).

   ![](assets/messagecenter_multi_control_4.png)

   >[!NOTE]
   >
   >**Gli operatori mc1** e  **mc2** devono disporre  **[!UICONTROL Message Center execution]** dei diritti e non possono accedere alla console client di Adobe Campaign. Un operatore deve sempre essere collegato a una zona di sicurezza. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../installation/using/security-zones.md).

1. Per ciascun operatore, seleziona la casella **[!UICONTROL Restrict to information found in sub-folders of]** e la cartella corrispondente (**Cartella 1** per l&#39;operatore **mc1** e **Cartella 2** per l&#39;operatore **mc2**).

   ![](assets/messagecenter_multi_control_5.png)

1. Assegnare ad ogni operatore le autorizzazioni di lettura e scrittura per la propria cartella. A questo scopo, fai clic con il pulsante destro del mouse sulla cartella e seleziona **[!UICONTROL Properties]** . Quindi seleziona la scheda **[!UICONTROL Security]** e aggiungi l&#39;operatore pertinente (**mc1** per **Cartella 1** e **mc2** per **Cartella 2**). Assicurati che le caselle **[!UICONTROL Read/Write data]** siano selezionate.

   ![](assets/messagecenter_multi_control_6.png)

