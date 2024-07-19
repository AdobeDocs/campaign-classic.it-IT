---
product: campaign
title: Fornitori, scorte e budget
description: Fornitori, scorte e budget
role: User
feature: Budget Management, Campaigns
exl-id: c60c4f86-a957-4c44-a0fe-39b6e3f0e5d6
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1918'
ht-degree: 0%

---

# Fornitori, scorte e budget{#providers-stocks-and-budgets}

Adobe Campaign consente di definire i provider di servizi che saranno coinvolti nei processi eseguiti all’interno delle campagne. Le informazioni relative ai fornitori di servizi e alle relative strutture di costo sono definite dall’amministratore di Adobe Campaign a partire dalla visualizzazione principale. Il fornitore di servizi è indicato dalla consegna e la sua struttura dei costi consente il calcolo dei costi associati a tale consegna e la gestione delle scorte in questione.

## Creazione di fornitori di servizi e delle relative strutture dei costi {#creating-service-providers-and-their-cost-structures}

Ogni provider di servizi viene salvato in un file con i dettagli dei contatti, i modelli di servizio e i processi correlati.

I provider di servizi sono configurati nel nodo **[!UICONTROL Administration > Campaign management]** della struttura.

I lavori svolti durante le consegne sono svolti da fornitori di servizi, in particolare per la direct mailing e i canali mobili. Questi fornitori di servizi possono, ad esempio, essere coinvolti nella stampa o nella distribuzione di messaggi. Questi lavori comportano configurazioni e costi specifici per ciascun fornitore di servizi. La configurazione dei prestatori di servizi prevede quattro fasi:

1. Creazione di un provider di servizi in Adobe Campaign

   Vedere [Aggiunta di un provider di servizi](#adding-a-service-provider).

1. Definizione delle categorie di costo e delle strutture dei modelli di servizio associati

   Vedere [Definizione delle categorie di costo](#defining-cost-categories) e [Definizione della struttura di costo](#defining-the-cost-structure).

1. Configurazione dei processi

   Vedere [Configurazione dei processi associati a un servizio](#configuring-processes-associated-with-a-service).

1. Riferimento al fornitore di servizi a livello di campagna

   Vedere [Associazione di un servizio a una campagna](#associating-a-service-with-a-campaign).

### Creazione di un fornitore di servizi e delle relative categorie di costo {#creating-a-service-provider-and-its-cost-categories}

#### Aggiunta di un provider di servizi {#adding-a-service-provider}

Puoi creare tutti i provider di servizi necessari per le consegne. La procedura per aggiungere un fornitore di servizi è la seguente:

1. Fare clic con il pulsante destro del mouse sull&#39;elenco dei provider di servizi e selezionare **[!UICONTROL New]** oppure fare clic sul pulsante **[!UICONTROL New]** sopra l&#39;elenco dei provider di servizi.
1. Nella sezione inferiore della finestra specificare il nome e i recapiti del provider di servizi.

   ![](assets/s_ncs_user_supplier_node_01.png)

1. Fare clic sul pulsante **[!UICONTROL Save]** per aggiungere il provider di servizi all&#39;elenco.

#### Definizione delle categorie di costo {#defining-cost-categories}

È necessario associare i modelli di servizio a ciascun provider di servizi. In questi modelli, è necessario innanzitutto identificare le categorie di costo e, se necessario, lo stock interessato. È quindi necessario creare le regole di calcolo dei costi per ogni categoria tramite le strutture dei costi.

>[!NOTE]
>
>Per ulteriori informazioni, consulta [Definizione della struttura dei costi](#defining-the-cost-structure).

Una categoria di costi è un’entità contenente una serie di costi ammissibili per un tipo di consegna (e-mail, direct mailing, ecc.) o per un&#39;attività. Le categorie di costo sono raggruppate nei modelli dei servizi associati ai fornitori di servizi. Ogni provider di servizi può fare riferimento a uno o più modelli di servizio.

Per creare un modello di servizio e definirne il contenuto, attenersi alla procedura descritta di seguito.

1. Nella scheda **[!UICONTROL Services]** del provider di servizi, fare clic sul pulsante **[!UICONTROL Add]** e denominare il modello di servizio.

   ![](assets/s_ncs_user_supplier_node_create_template.png)

1. Crea le categorie di costo per ogni tipo di processo (consegna tramite direct mailing/e-mail/ecc.). o attività). A tale scopo, fare clic sulla scheda **[!UICONTROL Cost categories]**, quindi sul pulsante **[!UICONTROL Add]** e immettere i parametri di ciascuna categoria di costo.

   ![](assets/s_ncs_user_supplier_node_03.png)

   * Immettere un&#39;etichetta per questa categoria di costi e selezionare il tipo di processo interessato: Consegna da **[!UICONTROL Direct mail]**, **[!UICONTROL Email]**, **[!UICONTROL Mobile]**, **[!UICONTROL Telephone]** o **[!UICONTROL Task]**.
   * Fare clic sul pulsante **[!UICONTROL Add]** per definire i tipi di costi associati a questa categoria.
   * Se necessario, associare una linea di magazzino a ciascun tipo di costo in modo che le quantità utilizzate vengano automaticamente correlate alle scorte esistenti.

     >[!NOTE]
     >
     >Le linee di magazzino sono definite nel nodo **[!UICONTROL Stock management]**.\
     >Per ulteriori informazioni, consulta [Gestione scorte e ordini](#stock-and-order-management).

1. È possibile preselezionare un valore per questa categoria di costo, che verrà offerta per impostazione predefinita nelle categorie di costo fornitore di servizi (anziché una vuota). A questo scopo, selezionare l&#39;opzione nella colonna **[!UICONTROL Selected]** per il tipo di categoria interessata:

   ![](assets/s_ncs_user_supplier_cost_structure_defaut.png)

   A livello di consegna, il valore viene selezionato per impostazione predefinita:

   ![](assets/s_ncs_user_supplier_default_cost.png)

### Definizione della struttura dei costi {#defining-the-cost-structure}

Per ogni tipo di costo, una struttura di costo specifica le regole di calcolo da applicare.

Fare clic sulla scheda **[!UICONTROL Cost structure]** per configurare il calcolo dei costi per ogni categoria e tipo di costo. Fare clic su **[!UICONTROL Add]** e immettere la struttura dei costi.

![](assets/s_ncs_user_supplier_node_04.png)

* Per creare la struttura dei costi, selezionare il tipo di messaggio e la categoria di costo interessati dagli elenchi a discesa, nonché il tipo di costo a cui verrà applicata la regola di calcolo. Il contenuto di questi elenchi a discesa proviene dalle informazioni immesse tramite la scheda **[!UICONTROL Cost categories]**.

  È necessario assegnare un&#39;etichetta alla struttura dei costi. Per impostazione predefinita, presenta la seguente struttura di consegna: **Categoria di costo - Tipo di costo**.

  È tuttavia possibile rinominarlo: immettere il valore desiderato direttamente nel campo **[!UICONTROL Label]**.

* La formula di calcolo dei costi è definita nella sezione inferiore della finestra.

  Questa formula può essere corretta (per qualsiasi numero di messaggi) o calcolata in base al numero di messaggi.

  Quando dipende dal numero di messaggi, la struttura di calcolo dei costi può essere **[!UICONTROL Linear]**, **[!UICONTROL Linear by threshold]** o **[!UICONTROL Constant by threshold]**.

#### Struttura lineare {#linear-structure}

Se l&#39;importo è sempre lo stesso per un messaggio (o un batch di messaggi) indipendentemente dal numero totale di messaggi, selezionare **[!UICONTROL Linear]** e immettere il costo di ogni messaggio.

![](assets/s_ncs_user_supplier_cost_structure_calc_01.png)

Se questo importo si applica a un batch di messaggi, specificare il numero di messaggi interessati nel campo **[!UICONTROL for]**.

![](assets/s_ncs_user_supplier_cost_structure_calc_02.png)

#### Struttura lineare per soglia {#linear-structure-by-threshold}

Se l&#39;importo si applica per soglia per ogni messaggio, è necessario definire una struttura di calcolo **[!UICONTROL Linear by threshold]**. In questo tipo di struttura di costo, ogni messaggio costerà 0,13, ad esempio, se il numero totale di messaggi è compreso tra 1 e 100, e costerà 0,12 da 100 a 1000 messaggi inviati, oppure 0,11 da 1000 messaggi.

La configurazione sarà la seguente:

![](assets/s_ncs_user_supplier_cost_structure_calc_03.png)

Per aggiungere una soglia, fare clic sul pulsante **[!UICONTROL Add]** a destra dell&#39;elenco.

#### Struttura costante per soglia {#constant-structure-by-threshold}

Infine, puoi configurare un calcolo dei costi in base al numero totale di messaggi. A tale scopo, selezionare una struttura di calcolo **[!UICONTROL Constant by threshold]**. Ad esempio, il costo verrà impostato su un importo fisso di 12.00 per 1-100 messaggi e su 100.00 per una consegna di 101-1000 messaggi e su 500.00 per una consegna superiore a 1000 messaggi, indipendentemente dal numero totale.

![](assets/s_ncs_user_supplier_cost_structure_calc_04.png)

### Configurazione dei processi associati a un servizio {#configuring-processes-associated-with-a-service}

È possibile associare informazioni sui processi associati al servizio tramite la scheda **[!UICONTROL Processes]**.

A tale scopo, fare clic sulla scheda **[!UICONTROL Processes]** per configurare l&#39;invio di informazioni al router.

![](assets/s_ncs_user_supplier_node_02.png)

* La sezione **[!UICONTROL File extraction]** indica il modello di esportazione utilizzato per la consegna quando questo servizio è selezionato. È possibile indicare il nome del file di output nel campo **[!UICONTROL Extraction file]**. Il pulsante a destra del campo consente di inserire le variabili.

  ![](assets/s_ncs_user_supplier_node_02a.png)

* La sezione **[!UICONTROL Notification email]** consente di specificare il modello per la notifica ai provider di servizi dopo l&#39;invio dei file. Selezionare il modello utilizzato per creare il messaggio di avviso e il gruppo di destinatari.

  Per impostazione predefinita, i modelli di consegna per i messaggi di notifica vengono salvati nel nodo **[!UICONTROL Administration > Campaign management > Technical delivery templates]**, accessibile dalla visualizzazione generale.

* La sezione **[!UICONTROL Post-processing]** ti consente di selezionare il flusso di lavoro da avviare dopo l&#39;approvazione della consegna. Se viene immesso un modello di flusso di lavoro, viene creata automaticamente un’istanza di flusso di lavoro e quindi viene avviata non appena l’approvazione diventa effettiva. Questo flusso di lavoro può inviare il file di estrazione a un provider di servizi esterno, ad esempio per l’elaborazione.

### Associazione di un servizio a una campagna {#associating-a-service-with-a-campaign}

I servizi sono associati alle campagne tramite consegne o attività. I provider di servizi sono collegati a modelli di consegna per offrire i propri servizi nelle consegne create tramite questo modello.

Quando viene selezionato un servizio, le categorie di costo corrispondenti al tipo di consegna (direct mailing, e-mail, ecc.) vengono indicate automaticamente nella tabella centrale insieme alle opzioni di elaborazione definite.

>[!NOTE]
>
>Se quando si seleziona un servizio non viene visualizzata alcuna categoria di costo, significa che per questo tipo di processo non è stata definita alcuna categoria di costo. Ad esempio, per una consegna e-mail, se non è stata definita alcuna categoria di costo di tipo **[!UICONTROL Email]**, non verrà visualizzata alcuna categoria e la selezione del servizio non avrà alcun effetto.

* Per una consegna direct mailing, puoi selezionare il servizio dalla finestra di configurazione.

  ![](assets/s_ncs_user_supplier_mail_delivery_select.png)

* Per le consegne su canali mobili o telefono, si applica la stessa modalità di selezione.
* Per una consegna e-mail, il servizio è selezionato dalla scheda **[!UICONTROL Advanced]** nelle proprietà di consegna, come nell&#39;esempio seguente:

  ![](assets/s_ncs_user_supplier_email_delivery_select.png)

La colonna **[!UICONTROL Amount to surcharge]** consente di aggiungere un costo per questa categoria nel contesto della consegna o dell&#39;attività interessata.

È possibile imporre la selezione obbligatoria di un tipo di costo durante la definizione delle categorie di costo per una consegna. A tale scopo, selezionare **[!UICONTROL A cost type must be selected]**.

![](assets/s_ncs_user_supplier_cost_structure_select.png)

## Gestione di scorte e ordini {#stock-and-order-management}

I tipi di costo possono essere associati alle linee delle scorte per gestire gli avvisi, tenere traccia delle forniture e avviare gli ordini.

La procedura per impostare la gestione delle scorte e degli ordini in Adobe Campaign e avvisare gli operatori in caso di forniture insufficienti per una consegna è la seguente:

1. Creazione di scorte e riferimento di prestatori di servizi associati

   Vedi [Creazione di un titolo](#creating-a-stock).

1. Aggiunta di linee di magazzino

   Vedere [Aggiunta di righe di magazzino](#adding-stock-lines).

1. Notifica agli operatori in caso di avviso

   Vedere [Avvisi sugli operatori](#alerting-operators).

1. Ordini e forniture.

   Consulta [Ordini](#orders).

### Gestione delle scorte {#stock-management}

Adobe Campaign può avvisare un gruppo di operatori se le scorte sono esaurite o hanno raggiunto una soglia minima. I livelli azionari sono accessibili tramite il collegamento **[!UICONTROL Stocks]** della scheda **[!UICONTROL Campaigns]** tramite il collegamento **[!UICONTROL Other choices]** dell&#39;area di navigazione.

![](assets/s_ncs_user_stocks_view.png)

#### Creazione di un grezzo {#creating-a-stock}

Per creare un nuovo materiale grezzo, applicate le seguenti operazioni:

1. Fare clic sul pulsante **[!UICONTROL Create]** sopra l&#39;elenco delle scorte.
1. Immettere l&#39;etichetta del titolo e selezionare dall&#39;elenco a discesa il fornitore di servizi a cui è associato.

   ![](assets/s_ncs_user_stocks_add.png)

   >[!NOTE]
   >
   >Per ulteriori informazioni, vedere [Creazione di provider di servizi e relative strutture di costo](#creating-service-providers-and-their-cost-structures).

#### Aggiunta di linee di magazzino {#adding-stock-lines}

Un magazzino comprende varie linee di magazzino. Una linea magazzino contiene una quantità iniziale di risorse che verranno consumate dalle consegne. Ogni linea magazzino indica la quantità consumata, la quantità in magazzino e la quantità ordinata.

Quando si crea un titolo, fare clic sulla scheda **[!UICONTROL Stock lines]** per aggiungere nuove righe.

![](assets/s_ncs_user_stocks_display_line.png)

Una volta creato il grezzo, fate clic su di esso per modificarlo e utilizzate il relativo quadro comandi per creare e visualizzare le linee del grezzo.

Fare clic sul pulsante **[!UICONTROL Create]** per definire i parametri del materiale.

![](assets/s_ncs_user_stocks_new_line.png)

* Indicare la quantità inizialmente in magazzino nel campo **[!UICONTROL Initial stock]**. I campi **[!UICONTROL Consumed]** e **[!UICONTROL In stock]** vengono calcolati automaticamente e aggiornati con l&#39;avanzamento delle campagne.

  ![](assets/s_ncs_user_stocks_create_line.png)

* Indicare la soglia dalla quale gli operatori devono essere avvisati di ordinare le scorte nel campo **[!UICONTROL Alert level]**. Quando viene raggiunto il livello di avviso, nella finestra di approvazione delle consegne che utilizzano questo stock viene visualizzato un messaggio di avviso.

#### Associazione di un magazzino a categorie di costo {#associating-a-stock-with-cost-categories}

Per un determinato fornitore di servizi, in un servizio, una linea di magazzino può essere referenziata da una delle categorie di costo, come segue:

![](assets/s_ncs_user_stocks_select_from_supplier.png)

### Tracciamento magazzino {#stock-tracking}

#### Avvisi degli operatori {#alerting-operators}

Viene visualizzato un avviso quando una scorta a cui si fa riferimento in una consegna è insufficiente. Ad esempio, quando viene approvato un file di estrazione, viene visualizzato il seguente avviso:

![](assets/s_ncs_user_stocks_valid_alert.png)

#### Ordini {#orders}

La scheda secondaria **[!UICONTROL Orders]** consente di visualizzare gli ordini correnti e salvare i nuovi ordini.

![](assets/s_ncs_user_stocks_edit_from_board.png)

Per salvare un ordine, modificare la linea delle scorte di destinazione, fare clic sul pulsante **[!UICONTROL Add]** e specificare la data di consegna e la quantità ordinata.

![](assets/s_ncs_user_stocks_node_06.png)

>[!NOTE]
>
>Una volta raggiunta la data di consegna, la linea magazzino ordinata scompare automaticamente e la quantità immessa nel campo **[!UICONTROL Volume on order]** viene aggiunta alla scheda **[!UICONTROL Tracking]**. Questa quantità viene aggiunta automaticamente al volume delle scorte.

![](assets/s_ncs_user_stocks_node_08.png)

La scheda **[!UICONTROL Consumptions]** contiene il volume utilizzato per campagna. Le informazioni di questa scheda vengono immesse automaticamente in base alle consegne eseguite. Fare clic sul pulsante **[!UICONTROL Edit]** per aprire la campagna interessata.

![](assets/s_ncs_user_stocks_edit_from_board_consumed.png)

## Calcolo dei budget {#calculating-budgets}

### Principio {#principle}

I costi vengono gestiti per consegne e campagne. In funzione dei progressi compiuti, tali costi sono imputati ai bilanci.

I costi di consegna di una campagna sono consolidati a livello di campagna e i costi di tutte le campagne di un programma vengono trasferiti al programma a cui sono associati. I rapporti dedicati consentono di tenere traccia dei budget per l’intera piattaforma o per ciascun piano e programma.

### Implementazione {#implementation}

In una campagna, quando selezioni il budget devi inserire l&#39;importo iniziale. I costi calcolati vengono aggiornati automaticamente in base al livello di impegno degli importi inseriti (spese effettuate, previste, impegnate, impegnate). Vedere [Calcolo degli importi](../../mrm/using/controlling-costs.md#calculating-amounts).

>[!NOTE]
>
>La procedura per la creazione dei budget è presentata in [Creazione di un budget](../../mrm/using/controlling-costs.md#creating-a-budget).
