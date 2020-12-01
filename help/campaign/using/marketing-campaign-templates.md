---
solution: Campaign Classic
product: campaign
title: Modelli per campagne marketing
description: Modelli per campagne marketing
audience: campaign
content-type: reference
topic-tags: orchestrate-campaigns
translation-type: tm+mt
source-git-commit: 20dcdd91d71158bc373db68c3f61f6808b240bd2
workflow-type: tm+mt
source-wordcount: '1124'
ht-degree: 0%

---


# Marketing Campaign templates {#campaign-templates}

I modelli delle campagne sono centralizzati nel **[!UICONTROL Resources > Templates > Campaign templates]** nodo. Un modello predefinito viene fornito come standard. Consente di creare una nuova campagna utilizzando tutti i moduli disponibili (documenti, attività, indirizzi e così via), ma i moduli offerti dipendono dai diritti e dalla configurazione della piattaforma Adobe Campaign .

## Creazione o duplicazione di un modello di campagna {#creating-or-duplicating-a-campaign-template}

Per creare un nuovo modello, effettuate le seguenti operazioni:

1. Apri **Esplora** campagne.
1. In **Risorse > Modelli > Modelli** campagna, fai clic su **Nuovo** nella barra degli strumenti sopra l’elenco dei modelli.

   ![](assets/create_campaign_template_1.png)

1. Immettete l’etichetta del nuovo modello di campagna.
1. Fate clic su **Salva** e riaprite il modello.
1. Nella scheda **Modifica** , immettere il nome **** interno e altri valori, se necessario.
1. Selezionate Impostazioni **campagna** avanzate per aggiungere un flusso di lavoro al modello di campagna.

   ![](assets/create_campaign_template_2.png)

1. Modificate il valore **Targeting e workflow** in **Yes**.

   ![](assets/create_campaign_template_3.png)

1. Nella scheda **Targeting and workflow (Impostazione destinazione e flussi di lavoro** ), fai clic su **Add a workflow (Aggiungi flusso di lavoro).**.

   ![](assets/create_campaign_template_4.png)

1. Completate il campo **Etichetta** e fate clic su **OK**.
1. Crea il flusso di lavoro in base alle tue esigenze.
1. Fai clic su **Salva**. Il modello è ora pronto per essere utilizzato in una campagna.

Potete inoltre duplicare il modello predefinito per riutilizzarlo e adattarne la configurazione.

Le varie schede e schede secondarie del modello di campagna consentono di accedere alle relative impostazioni, descritte nella configurazione [](#general-configuration)Generale.

![](assets/s_ncs_user_new_op_template_duplicate.png)

## Configurazione di un modello di campagna {#configuring-a-campaign-template}

Le campagne si basano su modelli che condividono una serie di parametri predefiniti.

In una configurazione predefinita, i modelli di campagna sono centralizzati nel **[!UICONTROL Resources > Templates > Campaign templates]** nodo della struttura di Adobe Campaign .

![](assets/s_ncs_user_campaign_op_template_node.png)

>[!NOTE]
>
>La struttura ad albero viene visualizzata quando fate clic sull&#39; **[!UICONTROL Explorer]** icona nella pagina principale.

Per creare una campagna per la quale non è stata definita alcuna configurazione specifica, viene fornito un modello out-of-the-box. Potete creare e configurare i modelli delle campagne e quindi creare campagne a partire da questi modelli.

La creazione e la configurazione di modelli di campagna sono presentati nei modelli [di](#campaign-templates)campagna.

![](assets/do-not-localize/how-to-video.png) Per ulteriori informazioni sulla creazione di campagne, consultate [questo video](../../campaign/using/marketing-campaign-deliveries.md#create-email-video).

## Configurazione dei moduli disponibili {#configuration-of-the-available-modules}

### Selezione del modulo {#module-selection}

Il **[!UICONTROL Advanced campaign settings...]** collegamento consente di abilitare e disabilitare i processi per le campagne basate su questo modello. Selezionate le funzioni che desiderate abilitare nelle campagne create in base a questo modello.

![](assets/s_ncs_user_op_template_tab1.3.png)

Se una funzionalità non è selezionata, gli elementi relativi al processo (menu, icone, opzioni, schede, sottoschede, ecc.) non verranno visualizzate nell&#39;interfaccia del modello o nelle campagne basate su questo modello. Le schede a sinistra dei dettagli della campagna generalmente coincidono con i processi selezionati nel modello. Ad esempio, se **Spese e obiettivi** non sono selezionati, la **[!UICONTROL Budget]** scheda corrispondente non verrà visualizzata nelle campagne basate su questo modello.

Inoltre, al dashboard della campagna vengono aggiunti collegamenti alle finestre di configurazione. Quando una funzionalità è attivata, un collegamento diretto vi permette di accedervi dal dashboard della campagna.

Ad esempio, con la configurazione seguente:

![](assets/s_ncs_user_op_template_tab1.4.png)

Nel dashboard della campagna sono visualizzati i seguenti collegamenti (manca il **[!UICONTROL Add a task]** collegamento):

![](assets/s_ncs_user_op_template_tab1.3ex.png)

Vengono visualizzate solo le seguenti schede:

![](assets/s_ncs_user_op_template_tab1.4ex.png)

Tuttavia, con questo tipo di configurazione:

![](assets/s_ncs_user_op_template_tab2.2ex.png)

Verranno visualizzati i seguenti collegamenti e schede:

![](assets/s_ncs_user_op_template_tab2.3ex.png)

### Tipologia dei moduli abilitati {#typology-of-enabled-modules}

* **Gruppo di controllo**

   Quando il modulo è selezionato, alle impostazioni avanzate del modello e alle campagne basate su questo modello viene aggiunta una scheda aggiuntiva. La configurazione può essere definita tramite il modello o singolarmente per ogni campagna.

   ![](assets/s_ncs_user_op_template_activate_1.png)

* **Indirizzi di seed**

   Quando il modulo è selezionato, alle impostazioni avanzate del modello e alle campagne basate su questo modello viene aggiunta una scheda aggiuntiva. La configurazione può essere definita tramite il modello o singolarmente per ogni campagna.

   ![](assets/s_ncs_user_op_template_activate_2.png)

* **Documenti**

   Quando il modulo è selezionato, viene aggiunta una scheda aggiuntiva alla **[!UICONTROL Edition]** scheda del modello e alle campagne basate su questo modello. I documenti allegati possono essere aggiunti dal modello o singolarmente per ogni campagna.

   ![](assets/s_ncs_user_op_template_activate_3.png)

* **Struttura**

   Quando il modulo è selezionato, alla **[!UICONTROL Delivery outlines]** scheda viene aggiunta una **[!UICONTROL Documents]** sottoscheda per definire i contorni di consegna per la campagna.

   ![](assets/s_ncs_user_op_template_activate_4.png)

* **Targeting e flussi di lavoro**

   Quando selezionate il **[!UICONTROL Targeting and workflows]** modulo, viene aggiunta una scheda che consente di creare uno o più flussi di lavoro per le campagne basate su questo modello. I flussi di lavoro possono essere configurati singolarmente per ogni campagna in base a questo modello.

   ![](assets/s_ncs_user_op_template_activate_5.png)

   Quando questo modulo è abilitato, alle impostazioni avanzate della campagna viene aggiunta una scheda per definire la sequenza di esecuzione del processo.

   ![](assets/s_ncs_user_op_template_activate_5a.png)

* **Approvazione**

   Se si seleziona questa opzione, è possibile selezionare i processi da approvare e gli operatori responsabili delle approvazioni. **[!UICONTROL Approval]**

   ![](assets/s_ncs_user_op_template_activate_5b.png)

* **Spese e obiettivi**

   Quando il modulo è selezionato, ai dettagli del modello e delle campagne viene aggiunta una **[!UICONTROL Budget]** scheda in base a questo modello, in modo che sia possibile selezionare il budget associato.

   ![](assets/s_ncs_user_op_template_activate_7.png)

### Approvazione dei lavori {#approval-of-jobs}

È possibile scegliere se abilitare o meno l&#39;approvazione del processo tramite la **[!UICONTROL Approvals]** scheda della sezione delle impostazioni avanzate dei modelli. I processi per i quali è selezionata l&#39;approvazione devono essere approvati per l&#39;autorizzazione della consegna dei messaggi.

È necessario associare un operatore revisore o un gruppo di operatori a ciascuna approvazione abilitata.

## Configurazione generale {#general-configuration}

### Proprietà dei modelli {#template-properties}

![](assets/s_ncs_user_op_new_template.png)

Quando create un modello di campagna, dovete immettere le seguenti informazioni:

* Immettete l’ **etichetta** del modello: questa etichetta verrà assegnata per impostazione predefinita a tutte le campagne create tramite questo modello.
* Selezionate la **natura** della campagna dall&#39;elenco a discesa. I valori disponibili in questo elenco sono quelli salvati nell&#39; **[!UICONTROL natureOp]** enumerazione.

   >[!NOTE]
   >
   >Per ulteriori informazioni sulle enumerazioni, consulta la sezione [Guida introduttiva](../../platform/using/managing-enumerations.md) .

* Selezionate il **tipo di campagna**: univoci, ricorrenti o periodici. Per impostazione predefinita, i modelli di campagna si applicano a campagne univoche. Le campagne periodiche sono descritte di seguito: [Campagne](../../campaign/using/setting-up-marketing-campaigns.md#recurring-and-periodic-campaigns)ricorrenti e periodiche.
* Specificate la durata della campagna, ossia il numero di giorni in cui avrà luogo la campagna. Quando si crea una campagna basata su questo modello, le date di inizio e di fine della campagna vengono popolate automaticamente.

   Se la campagna è ricorrente, è necessario specificare le date di inizio e fine della campagna direttamente nel modello.

* Specificare il programma **** correlato del modello: le campagne basate su questo modello saranno collegate al programma selezionato.

### Parametri di esecuzione del modello {#template-execution-parameters}

Il **[!UICONTROL Advanced campaign settings...]** collegamento consente di configurare le opzioni avanzate del modello per l&#39;elaborazione della destinazione di consegna (gruppo di controllo, indirizzi iniziali, ecc.) e la configurazione della misurazione della campagna e dell&#39;esecuzione del flusso di lavoro.

![](assets/s_ncs_user_op_template_tab1.2.png)

## Pianificazione invertita campagna {#campaign-reverse-scheduling}

Potete creare una pianificazione inversa per una campagna, ad esempio per preparare un evento la cui data è nota in anticipo. I modelli di campagna ora consentono di calcolare la data di inizio di un&#39;attività in base alla data di fine di una campagna.

Nella casella di configurazione dell&#39;attività, passare all&#39; **[!UICONTROL Implementation schedule]** area e selezionare la **[!UICONTROL The start date is calculated based on the campaign end date]** casella. (In questo caso, &quot;data di inizio&quot; è la data di inizio dell&#39;attività). Vai al **[!UICONTROL Start]** campo e immetti un intervallo: l&#39;attività verrà avviata molto prima della data di fine della campagna. Se immettete un periodo più lungo di quello impostato per l&#39;ultima campagna, l&#39;attività inizierà prima della campagna.

![](assets/mrm_task_in_template_start_date.png)

Quando create una campagna utilizzando questo modello, la data di inizio dell&#39;attività viene calcolata automaticamente. Tuttavia, è sempre possibile modificarlo in un secondo momento.
