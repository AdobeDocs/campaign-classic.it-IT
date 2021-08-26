---
product: campaign
title: Modelli di campagna di marketing
description: Modelli di campagna di marketing
audience: campaign
content-type: reference
topic-tags: orchestrate-campaigns
exl-id: d272d4b9-f1b2-4fb2-9ed9-91a4aea7eca3
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1128'
ht-degree: 3%

---

# Creare e configurare modelli di campagna {#campaign-templates}

![](../../assets/common.svg)

Tutte le campagne di marketing si basano su un modello, che memorizza le caratteristiche e le funzionalità principali. I modelli di campagna sono centralizzati nel nodo **[!UICONTROL Resources > Templates > Campaign templates]** . Un modello predefinito viene fornito come standard. Ti consente di creare una nuova campagna utilizzando tutti i moduli disponibili (Documenti, Attività, Indirizzi di seed, ecc.), ma i moduli offerti dipendono dai tuoi diritti e dalla configurazione della piattaforma Adobe Campaign.

![](assets/s_ncs_user_campaign_op_template_node.png)

>[!NOTE]
>
>La struttura ad albero viene visualizzata quando fai clic sull&#39;icona **[!UICONTROL Explorer]** nella home page.

Viene fornito un modello integrato al fine di creare una campagna per la quale non è stata definita alcuna configurazione specifica. Puoi creare e configurare i modelli della campagna e quindi creare campagne a partire da questi modelli.

![](assets/do-not-localize/how-to-video.png) Per ulteriori informazioni sulla creazione di campagne, consulta  [questo video](../../campaign/using/marketing-campaign-deliveries.md#create-email-video).

## Creare un modello di campagna {#creating-or-duplicating-a-campaign-template}

Per creare un modello di campagna, segui i passaggi seguenti:

1. Apri Campaign **Explorer**.
1. In **Risorse > Modelli > Modelli di campagna**, fai clic su **Nuovo** nella barra degli strumenti sopra l’elenco dei modelli.

   ![](assets/create_campaign_template_1.png)

1. Inserisci l’etichetta del nuovo modello di campagna.
1. Fai clic su **Salva** e riapri il modello.
1. Nella scheda **Modifica**, immetti il **Nome interno** e altri valori, se necessario.
1. Seleziona **Impostazioni avanzate della campagna** per aggiungere un flusso di lavoro al modello della campagna.

   ![](assets/create_campaign_template_2.png)

1. Modifica il valore **Targeting e flussi di lavoro** in **Sì**.

   ![](assets/create_campaign_template_3.png)

1. Nella scheda **Targeting e flussi di lavoro** , fai clic su **Aggiungi un flusso di lavoro...**.

   ![](assets/create_campaign_template_4.png)

1. Completa il campo **Etichetta** e fai clic su **Ok**.
1. Crea il flusso di lavoro in base alle tue esigenze.
1. Fai clic su **Salva**. Il modello è ora pronto per essere utilizzato in una campagna.

Puoi anche **duplicare** il modello predefinito per riutilizzare e adattare la relativa configurazione.

Le varie schede e schede secondarie del modello della campagna consentono di accedere alle relative impostazioni, descritte in [Configurazione generale](#general-configuration).

![](assets/s_ncs_user_new_op_template_duplicate.png)

## Seleziona moduli {#select-modules}

Il collegamento **[!UICONTROL Advanced campaign settings...]** ti consente di abilitare e disabilitare i lavori per le campagne basate su questo modello. Seleziona le funzionalità da abilitare nelle campagne create in base a questo modello.

![](assets/s_ncs_user_op_template_tab1.3.png)

Se una funzionalità non è selezionata, gli elementi relativi al processo (menu, icone, opzioni, schede, schede secondarie, ecc.) non verrà visualizzato nell’interfaccia del modello o nelle campagne basate su questo modello. Le schede a sinistra dei dettagli della campagna in genere coincidono con i processi selezionati nel modello. Ad esempio, se **Spese e obiettivi** non è selezionato, la scheda corrispondente **[!UICONTROL Budget]** non verrà visualizzata nelle campagne basate su questo modello.

Inoltre, i collegamenti alle finestre di configurazione vengono aggiunti al dashboard della campagna. Quando una funzionalità è abilitata, un collegamento diretto vi permette di accedervi dal dashboard della campagna.

Ad esempio, con la configurazione seguente:

![](assets/s_ncs_user_op_template_tab1.4.png)

I seguenti collegamenti vengono visualizzati nel dashboard della campagna (manca il collegamento **[!UICONTROL Add a task]** ):

![](assets/s_ncs_user_op_template_tab1.3ex.png)

Verranno visualizzate solo le seguenti schede:

![](assets/s_ncs_user_op_template_tab1.4ex.png)

Tuttavia, con questo tipo di configurazione:

![](assets/s_ncs_user_op_template_tab2.2ex.png)

Verranno visualizzati i seguenti collegamenti e schede:

![](assets/s_ncs_user_op_template_tab2.3ex.png)

## Tipologia dei moduli {#typology-of-enabled-modules}

* **Gruppo di controllo**

   Quando questo modulo è selezionato, viene aggiunta una scheda aggiuntiva alle impostazioni avanzate del modello e alle campagne basate su questo modello. La configurazione può essere definita tramite il modello o singolarmente per ogni campagna. Ulteriori informazioni sui gruppi di controllo in [questa sezione](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).

   ![](assets/s_ncs_user_op_template_activate_1.png)

* **Indirizzi di seed**

   Quando questo modulo è selezionato, viene aggiunta una scheda aggiuntiva alle impostazioni avanzate del modello e alle campagne basate su questo modello. La configurazione può essere definita tramite il modello o singolarmente per ogni campagna. Ulteriori informazioni sugli indirizzi di seed in [questa sezione](../../delivery/using/about-seed-addresses.md).

   ![](assets/s_ncs_user_op_template_activate_2.png)

* **Documenti**

   Quando questo modulo è selezionato, viene aggiunta una scheda aggiuntiva alla scheda **[!UICONTROL Edition]** del modello e alle campagne basate su questo modello. I documenti allegati possono essere aggiunti dal modello o singolarmente per ogni campagna. Ulteriori informazioni sui documenti in [questa sezione](../../campaign/using/marketing-campaign-deliveries.md#managing-associated-documents).

   ![](assets/s_ncs_user_op_template_activate_3.png)

* **Struttura**

   Quando questo modulo è selezionato, alla scheda **[!UICONTROL Documents]** viene aggiunta una sottoscheda **[!UICONTROL Delivery outlines]** per definire i contorni di consegna per la campagna. Ulteriori informazioni sui contorni di consegna in [questa sezione](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

   ![](assets/s_ncs_user_op_template_activate_4.png)

* **Targeting e flussi di lavoro**

   Quando selezioni il modulo **[!UICONTROL Targeting and workflows]** , viene aggiunta una scheda per consentire di creare uno o più flussi di lavoro per le campagne basate su questo modello. I flussi di lavoro possono anche essere configurati singolarmente per ogni campagna basata su questo modello.Ulteriori informazioni sui flussi di lavoro delle campagne in [questa sezione](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow).

   ![](assets/s_ncs_user_op_template_activate_5.png)

   Quando questo modulo è abilitato, viene aggiunta una scheda alle impostazioni avanzate della campagna per definire la sequenza di esecuzione del processo.

   ![](assets/s_ncs_user_op_template_activate_5a.png)

* **Approvazione**

   Se selezioni **[!UICONTROL Approval]**, puoi selezionare i processi da approvare e gli operatori responsabili delle approvazioni. Ulteriori informazioni sulle approvazioni in [questa sezione](../../campaign/using/marketing-campaign-approval.md#selecting-reviewers).

   ![](assets/s_ncs_user_op_template_activate_5b.png)

   Puoi scegliere se abilitare o meno l’approvazione del processo tramite la scheda **[!UICONTROL Approvals]** della sezione delle impostazioni avanzate dei modelli. I processi per i quali è selezionata l’approvazione devono essere approvati per consentire la consegna dei messaggi.

   È necessario associare un operatore revisore o un gruppo di operatori a ogni approvazione abilitata.

* **Spese e obiettivi**

   Quando questo modulo è selezionato, viene aggiunta una scheda **[!UICONTROL Budget]** ai dettagli del modello e delle campagne basate su questo modello in modo che sia possibile selezionare il budget associato.

   ![](assets/s_ncs_user_op_template_activate_7.png)

## Proprietà ed esecuzione {#general-configuration}

### Proprietà del modello {#template-properties}

![](assets/s_ncs_user_op_new_template.png)

Quando crei un modello di campagna, devi immettere le seguenti informazioni:

* Inserisci l’ **etichetta** del modello: questa etichetta verrà assegnata per impostazione predefinita a tutte le campagne create tramite questo modello.
* Seleziona la campagna **natura** dall’elenco a discesa. I valori disponibili in questo elenco sono quelli salvati nell&#39;enumerazione **[!UICONTROL natureOp]**.

   >[!NOTE]
   >
   >Per ulteriori informazioni sulle enumerazioni, consulta la sezione [Guida introduttiva](../../platform/using/managing-enumerations.md) .

* Seleziona il **tipo di campagna**: unico, ricorrente o periodico. Per impostazione predefinita, i modelli di campagna si applicano a campagne univoche. Le campagne ricorrenti e periodiche sono descritte in [questa sezione](../../campaign/using/setting-up-marketing-campaigns.md#recurring-and-periodic-campaigns).
* Specifica la durata della campagna, ovvero il numero di giorni in cui avrà luogo la campagna. Quando crei una campagna basata su questo modello, le date di inizio e di fine della campagna verranno compilate automaticamente.

   Se la campagna è ricorrente, devi specificare le date di inizio e fine della campagna direttamente nel modello.

* Specifica il **programma correlato** del modello: le campagne basate su questo modello saranno collegate al programma selezionato.

### Parametri di esecuzione del modello {#template-execution-parameters}

Il collegamento **[!UICONTROL Advanced campaign settings...]** ti consente di configurare le opzioni avanzate del modello per l’elaborazione della destinazione di consegna (gruppo di controllo, indirizzi di seed, ecc.) e la configurazione della misurazione della campagna e dell’esecuzione del flusso di lavoro.

![](assets/s_ncs_user_op_template_tab1.2.png)

## Tracciare l’esecuzione di una campagna{#campaign-reverse-scheduling}

Puoi creare una pianificazione per una campagna e tenere traccia dei risultati, ad esempio per preparare una pianificazione dell’evento per una data specifica. I modelli di campagna ora consentono di calcolare la data di inizio di un’attività in base alla data di fine di una campagna.

Nella casella di configurazione dell&#39;attività, passare all&#39;area **[!UICONTROL Implementation schedule]** e selezionare la casella **[!UICONTROL The start date is calculated based on the campaign end date]**. (In questo caso, &quot;data di inizio&quot; è la data di inizio dell’attività). Vai al campo **[!UICONTROL Start]** e inserisci un intervallo: l’attività verrà avviata molto prima della data di fine della campagna. Se immetti un periodo più lungo di quello impostato per l’ultima campagna, l’attività inizia prima della campagna.

![](assets/mrm_task_in_template_start_date.png)

Quando si crea una campagna utilizzando questo modello, la data di inizio dell&#39;attività viene calcolata automaticamente. Tuttavia, è sempre possibile modificarlo in un secondo momento.
