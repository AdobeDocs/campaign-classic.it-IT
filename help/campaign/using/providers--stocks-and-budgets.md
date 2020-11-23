---
solution: Campaign Classic
product: campaign
title: Fornitori, scorte e budget
description: Fornitori, scorte e budget
audience: campaign
content-type: reference
topic-tags: orchestrate-campaigns
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1902'
ht-degree: 0%

---


# Fornitori, scorte e budget{#providers-stocks-and-budgets}

 Adobe Campaign consente di definire i provider di servizi che saranno coinvolti nei processi svolti all&#39;interno delle campagne. Le informazioni relative ai fornitori di servizi e alle relative strutture di costi sono definite dall&#39;amministratore di Adobe Campaign  dalla vista principale. Il fornitore di servizi è indicato dalla fornitura e le sue strutture di costo consentono il calcolo dei costi associati a tale consegna nonché la gestione delle scorte in questione.

## Creazione di fornitori di servizi e relative strutture di costo {#creating-service-providers-and-their-cost-structures}

Ogni provider di servizi viene salvato in un file con i dati di contatto, i modelli di servizio e i processi correlati.

I provider di servizi sono configurati nel **[!UICONTROL Administration > Campaign management]** nodo della struttura.

I lavori svolti durante le consegne sono eseguiti dai prestatori di servizi, in particolare per la posta diretta e i canali mobili. Questi fornitori di servizi possono, ad esempio, essere coinvolti nella stampa o nella distribuzione di messaggi. Tali processi comportano configurazioni e costi specifici per ciascun fornitore di servizi. La configurazione dei fornitori di servizi comporta quattro fasi:

1. Creazione di un provider di servizi in  Adobe Campaign

   Consultate [Aggiunta di un provider](#adding-a-service-provider)di servizi.

1. Definizione delle categorie di costi e delle strutture dei modelli di servizio associati

   Vedere [Definizione delle categorie](#defining-cost-categories) di costi e [Definizione della struttura](#defining-the-cost-structure)dei costi.

1. Configurazione dei processi

   Consultate [Configurazione dei processi associati a un servizio](#configuring-processes-associated-with-a-service).

1. Riferimento al provider di servizi a livello di campagna

   Consultate [Associazione di un servizio a una campagna](#associating-a-service-with-a-campaign).

### Creazione di un provider di servizi e relative categorie di costi {#creating-a-service-provider-and-its-cost-categories}

#### Aggiunta di un provider di servizi {#adding-a-service-provider}

Puoi creare tutti i provider di servizi necessari per le consegne. La procedura per aggiungere un fornitore di servizi è la seguente:

1. Fare clic con il pulsante destro del mouse sull&#39;elenco dei provider di servizi e selezionare **[!UICONTROL New]** oppure fare clic sul **[!UICONTROL New]** pulsante sopra l&#39;elenco dei provider di servizi.
1. Nella sezione inferiore della finestra, specificate il nome e i recapiti del fornitore del servizio.

   ![](assets/s_ncs_user_supplier_node_01.png)

1. Fare clic sul **[!UICONTROL Save]** pulsante per aggiungere il provider di servizi all&#39;elenco.

#### Definizione delle categorie di costi {#defining-cost-categories}

È necessario associare i modelli di servizio a ciascun provider di servizi. In questi modelli è innanzitutto necessario identificare le categorie di costi e, se necessario, le scorte interessate. È quindi necessario creare le regole di calcolo dei costi per ciascuna categoria, tramite le strutture dei costi.

>[!NOTE]
>
>For more on this, refer to [Defining the cost structure](#defining-the-cost-structure).

Una categoria di costi è un&#39;entità contenente un insieme di costi ammissibili per un tipo di consegna (e-mail, posta diretta, ecc.) o per un’attività. Le categorie di costi sono raggruppate nei modelli di servizi associati ai fornitori di servizi. Ogni provider di servizi può fare riferimento a uno o più modelli di servizio.

Per creare un modello di servizio e definirne il contenuto, effettuate le seguenti operazioni:

1. Nella **[!UICONTROL Services]** scheda del provider di servizi, fate clic sul **[!UICONTROL Add]** pulsante e denominate il modello di servizio.

   ![](assets/s_ncs_user_supplier_node_create_template.png)

1. Creare le categorie di costi per ciascun tipo di processo (consegna per posta diretta/e-mail/ecc. o attività). A questo scopo, fare clic sulla **[!UICONTROL Cost categories]** scheda e quindi sul **[!UICONTROL Add]** pulsante, quindi inserire i parametri di ciascuna categoria di costo.

   ![](assets/s_ncs_user_supplier_node_03.png)

   * Inserire un&#39;etichetta per questa categoria di costi e selezionare il tipo di processo interessato: Consegna tramite **[!UICONTROL Direct mail]**, **[!UICONTROL E-mail]**, **[!UICONTROL Mobile]**, **[!UICONTROL Telephone]** o **[!UICONTROL Task]**.
   * Fare clic sul **[!UICONTROL Add]** pulsante per definire i tipi di costo associati a questa categoria.
   * Se necessario, ha associato una linea di magazzino a ciascun tipo di costo in modo che i quantitativi utilizzati siano automaticamente correlati alle scorte esistenti.

      >[!NOTE]
      >
      >Le linee di magazzino sono definite nel **[!UICONTROL Stock management]** nodo.\
      >Per ulteriori informazioni, consulta Gestione [scorte e ordini](#stock-and-order-management).

1. È possibile pre-selezionare un valore per questa categoria di costi, che verrà offerta per impostazione predefinita nelle categorie di costi del provider di servizi (invece di un valore vuoto). A tal fine, selezionate l’opzione nella **[!UICONTROL Selected]** colonna relativa al tipo di categoria in questione:

   ![](assets/s_ncs_user_supplier_cost_structure_defaut.png)

   A livello di consegna, il valore verrà selezionato per impostazione predefinita:

   ![](assets/s_ncs_user_supplier_default_cost.png)

### Defining the cost structure {#defining-the-cost-structure}

Per ciascun tipo di costo, una struttura di costi specifica le regole di calcolo da applicare.

Fare clic sulla **[!UICONTROL Cost structure]** scheda per configurare il calcolo dei costi per ogni categoria e tipo di costo. Fare clic **[!UICONTROL Add]** e inserire la struttura dei costi.

![](assets/s_ncs_user_supplier_node_04.png)

* Per creare la struttura dei costi, selezionare il tipo di messaggio e la categoria di costi interessati dagli elenchi a discesa, nonché il tipo di costo a cui si applicherà la regola di calcolo. Il contenuto di questi elenchi a discesa deriva dalle informazioni inserite tramite la **[!UICONTROL Cost categories]** scheda.

   È necessario assegnare un&#39;etichetta alla struttura dei costi. Per impostazione predefinita, il modello di consegna è il seguente: **Categoria di costo - Tipo di costo**.

   È tuttavia possibile rinominarlo: immettere il valore desiderato direttamente nel **[!UICONTROL Label]** campo.

* La formula di calcolo del costo è definita nella sezione inferiore della finestra.

   Questa formula può essere fissa (per qualsiasi numero di messaggi) o calcolata in base al numero di messaggi.

   Quando dipende dal numero di messaggi, la struttura di calcolo dei costi può essere **[!UICONTROL Linear]**, **[!UICONTROL Linear by threshold]** o **[!UICONTROL Constant by threshold]**.

#### Struttura lineare {#linear-structure}

Se l&#39;importo è sempre lo stesso per un messaggio (o un batch di messaggi) indipendentemente dal numero totale di messaggi, selezionare **[!UICONTROL Linear]** e inserire il costo di ciascun messaggio.

![](assets/s_ncs_user_supplier_cost_structure_calc_01.png)

Se questo importo si applica a un batch di messaggi, specifica il numero di messaggi in questione nel **[!UICONTROL for]** campo.

![](assets/s_ncs_user_supplier_cost_structure_calc_02.png)

#### Struttura lineare per soglia {#linear-structure-by-threshold}

Se l&#39;importo viene applicato per soglia per ogni messaggio, è necessario definire una struttura di **[!UICONTROL Linear by threshold]** calcolo. In questo tipo di struttura dei costi, ogni messaggio costerà 0,13, ad esempio, se il numero totale di messaggi è compreso tra 1 e 100 e costerà 0,12 da 100 a 1000 messaggi inviati, o 0,11 oltre 1000 messaggi.

La configurazione sarà la seguente:

![](assets/s_ncs_user_supplier_cost_structure_calc_03.png)

Per aggiungere una soglia, fate clic sul **[!UICONTROL Add]** pulsante a destra dell’elenco.

#### Struttura costante per soglia {#constant-structure-by-threshold}

Infine, puoi configurare un calcolo dei costi in base al numero totale di messaggi. A tal fine, selezionare una struttura di **[!UICONTROL Constant by threshold]** calcolo. Ad esempio, il costo verrà fissato a un importo fisso di 12,00 per 1 a 100 messaggi e a 100,00 per una consegna di 101 a 1000 messaggi e a 500,00 per ogni consegna su 1000 messaggi, indipendentemente dal numero totale.

![](assets/s_ncs_user_supplier_cost_structure_calc_04.png)

### Configurazione dei processi associati a un servizio {#configuring-processes-associated-with-a-service}

È possibile associare informazioni sui processi associati al servizio tramite la **[!UICONTROL Processes]** scheda.

A questo scopo, fare clic sulla **[!UICONTROL Processes]** scheda per configurare l&#39;invio di informazioni al router.

![](assets/s_ncs_user_supplier_node_02.png)

* La **[!UICONTROL File extraction]** sezione indica il modello di esportazione utilizzato per la consegna quando il servizio è selezionato. È possibile indicare il nome del file di output nel **[!UICONTROL Extraction file]** campo. Il pulsante a destra del campo consente di inserire le variabili.

   ![](assets/s_ncs_user_supplier_node_02a.png)

* La **[!UICONTROL Notification e-mail]** sezione consente di specificare il modello da inviare ai provider di servizi dopo l’invio dei file. Selezionate il modello utilizzato per creare il messaggio di avviso e il gruppo di destinatari.

   Per impostazione predefinita, i modelli di consegna per i messaggi di notifica vengono salvati nel **[!UICONTROL Administration > Campaign management > Technical delivery templates]** nodo, accessibile dalla vista generale.

* La **[!UICONTROL Post-processing]** sezione consente di selezionare il flusso di lavoro da avviare dopo che la consegna è stata approvata. Se viene immesso un modello di workflow, verrà automaticamente creata un&#39;istanza del flusso di lavoro e quindi avviata non appena l&#39;approvazione avrà effetto. Questo flusso di lavoro può inviare il file di estrazione a un provider di servizi esterno per l&#39;elaborazione, ad esempio.

### Associazione di un servizio a una campagna {#associating-a-service-with-a-campaign}

I servizi sono associati alle campagne tramite consegne o attività. I fornitori di servizi sono collegati ai modelli di consegna per offrire i propri servizi nelle consegne create tramite questo modello.

Quando un servizio è selezionato, le categorie di costi corrispondenti al tipo di consegna (posta diretta, e-mail, ecc.) sono indicate automaticamente nella tabella centrale insieme alle opzioni di elaborazione definite.

>[!NOTE]
>
>Se non viene visualizzata alcuna categoria di costi quando un servizio è selezionato, significa che non è stata definita alcuna categoria di costi per questo tipo di processo. Ad esempio, per una consegna tramite e-mail, se non è stata definita alcuna categoria di costi di **[!UICONTROL E-mail]** tipo, non verrà visualizzata alcuna categoria e la selezione del servizio non avrà alcun effetto.

* Per la consegna diretta, potete selezionare il servizio dalla finestra di configurazione.

   ![](assets/s_ncs_user_supplier_mail_delivery_select.png)

* Per la distribuzione su canali mobili o telefonici, si applica la stessa modalità di selezione.
* Per una consegna tramite e-mail, il servizio viene selezionato dalla **[!UICONTROL Advanced]** scheda nelle proprietà di consegna, come nell&#39;esempio seguente:

   ![](assets/s_ncs_user_supplier_email_delivery_select.png)

La **[!UICONTROL Amount to surcharge]** colonna consente di aggiungere un costo per questa categoria nel contesto della consegna o dell&#39;attività in questione.

È possibile imporre la selezione obbligatoria di un tipo di costo durante la definizione delle categorie di costi per una consegna. A tale scopo, selezionare **[!UICONTROL A cost type must be selected]**.

![](assets/s_ncs_user_supplier_cost_structure_select.png)

## Gestione di scorte e ordini {#stock-and-order-management}

I tipi di costo possono essere associati alle linee di magazzino per gestire avvisi, tenere traccia delle forniture e degli ordini di avvio.

La procedura per la costituzione della gestione delle scorte e degli ordini in  Adobe Campaign e gli operatori avvisatori in caso di scorte insufficienti per la consegna è la seguente:

1. Creazione di scorte e riferimento a fornitori di servizi associati

   Consultate [Creazione di una risorsa](#creating-a-stock).

1. Aggiunta di linee di azione

   Vedere [Aggiunta di linee](#adding-stock-lines)di magazzino.

1. Notifica agli operatori in caso di segnalazione

   Vedere [Operatori](#alerting-operators)di avvisi.

1. Ordini e forniture.

   Fare riferimento a [Ordini](#orders).

### Gestione delle scorte {#stock-management}

 Adobe Campaign può avvisare un gruppo di operatori se le scorte sono esaurite o hanno raggiunto una soglia minima. I livelli delle scorte sono accessibili attraverso il **[!UICONTROL Stocks]** collegamento dell&#39; **[!UICONTROL Campaigns]** universo attraverso il **[!UICONTROL Other choices]** collegamento dell&#39;area di navigazione.

![](assets/s_ncs_user_stocks_view.png)

#### Creazione di una risorsa {#creating-a-stock}

Per creare un nuovo stock, effettuate le seguenti operazioni:

1. Fare clic sul **[!UICONTROL Create]** pulsante sopra l&#39;elenco delle scorte.
1. Immettete l&#39;etichetta del magazzino e selezionate il provider di servizi a cui è associato dall&#39;elenco a discesa.

   ![](assets/s_ncs_user_stocks_add.png)

   >[!NOTE]
   >
   >Per ulteriori informazioni, vedere [Creazione di provider di servizi e relative strutture](#creating-service-providers-and-their-cost-structures)di costo.

#### Aggiunta di linee di azione {#adding-stock-lines}

Una scorta comprende varie linee di magazzino. Una linea di magazzino contiene una quantità iniziale di risorse che verranno consumate dalle consegne. Ogni linea di magazzino indica la quantità consumata, la quantità in magazzino e la quantità ordinata.

Quando create una risorsa, fate clic sulla **[!UICONTROL Stock lines]** scheda per aggiungere nuove righe.

![](assets/s_ncs_user_stocks_display_line.png)

Una volta creata la risorsa, fate clic su di essa per modificarla e utilizzate il dashboard per creare e visualizzare le linee della risorsa.

Fate clic sul **[!UICONTROL Create]** pulsante per definire i parametri di magazzino.

![](assets/s_ncs_user_stocks_new_line.png)

* Indicare la quantità inizialmente in magazzino nel **[!UICONTROL Initial stock]** campo. I campi **[!UICONTROL Consumed]** e **[!UICONTROL In stock]** vengono calcolati automaticamente e aggiornati man mano che le campagne avanzano.

   ![](assets/s_ncs_user_stocks_create_line.png)

* Indicare la soglia a partire dalla quale gli operatori devono essere avvisati per ordinare le scorte nel **[!UICONTROL Alert level]** campo. Quando viene raggiunto il livello di avviso, nella finestra di approvazione delle consegne che utilizzano questo stock viene visualizzato un messaggio di avviso.

#### Associazione di un&#39;azione a categorie di costi {#associating-a-stock-with-cost-categories}

Per un determinato fornitore di servizi, in un servizio, una delle categorie di costi può fare riferimento a una linea di azioni, come segue:

![](assets/s_ncs_user_stocks_select_from_supplier.png)

### Tracciamento delle scorte {#stock-tracking}

#### Avvisi degli operatori {#alerting-operators}

Viene visualizzato un avviso quando una scorta cui viene fatto riferimento in una consegna è insufficiente. Ad esempio, quando viene approvato un file di estrazione, viene visualizzato il seguente avviso:

![](assets/s_ncs_user_stocks_valid_alert.png)

#### Ordini {#orders}

La **[!UICONTROL Orders]** sottoscheda consente di visualizzare gli ordini correnti e salvare i nuovi ordini.

![](assets/s_ncs_user_stocks_edit_from_board.png)

Per salvare un ordine, modificare la linea di magazzino di destinazione, fare clic sul **[!UICONTROL Add]** pulsante e specificare la data di consegna e la quantità ordinata.

![](assets/s_ncs_user_stocks_node_06.png)

>[!NOTE]
>
>Una volta raggiunta la data di consegna, la linea ordinata scompare automaticamente e la quantità inserita nel **[!UICONTROL Volume on order]** campo viene aggiunta alla **[!UICONTROL Tracking]** scheda. Questa quantità viene aggiunta automaticamente al volume delle scorte.

![](assets/s_ncs_user_stocks_node_08.png)

La **[!UICONTROL Consumptions]** scheda contiene il volume utilizzato per campagna. Le informazioni di questa scheda vengono immesse automaticamente in base alle consegne eseguite. Fate clic sul **[!UICONTROL Edit]** pulsante per aprire la campagna in questione.

![](assets/s_ncs_user_stocks_edit_from_board_consumed.png)

## Calcolo dei budget {#calculating-budgets}

### Principio {#principle}

I costi vengono gestiti per consegne e campagne. In base ai progressi compiuti, tali costi sono assegnati ai bilanci.

I costi di consegna per una campagna sono consolidati a livello di campagna e i costi di tutte le campagne di un programma sono trasferiti al programma a cui sono associati. I report dedicati consentono di tenere traccia dei budget per l&#39;intera piattaforma o per ciascun piano e ciascun programma.

### Implementazione {#implementation}

In una campagna, quando si seleziona il budget è necessario inserire l&#39;importo iniziale. I costi calcolati saranno aggiornati automaticamente in base al livello di impegno degli importi inseriti (spese sostenute, attese, riservate, impegnate). Vedere [Calcolo degli importi](../../campaign/using/controlling-costs.md#calculating-amounts).

>[!NOTE]
>
>La procedura per la creazione di budget è presentata in [Creazione di un budget](../../campaign/using/controlling-costs.md#creating-a-budget).

