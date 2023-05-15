---
product: campaign
title: Modelli di campagna di marketing
description: Modelli di campagna di marketing
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Campaigns, Templates
exl-id: d272d4b9-f1b2-4fb2-9ed9-91a4aea7eca3
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1128'
ht-degree: 4%

---

# Creare e configurare modelli di campagna {#campaign-templates}

Tutte le campagne di marketing si basano su un modello, che memorizza le caratteristiche e le funzionalità principali. I modelli di campagna sono centralizzati nella **[!UICONTROL Resources > Templates > Campaign templates]** nodo. Un modello predefinito viene fornito come standard. Ti consente di creare una nuova campagna utilizzando tutti i moduli disponibili (Documenti, Attività, Indirizzi di seed, ecc.), ma i moduli offerti dipendono dai tuoi diritti e dalla configurazione della piattaforma Adobe Campaign.

![](assets/s_ncs_user_campaign_op_template_node.png)

>[!NOTE]
>
>La struttura ad albero viene visualizzata quando si fa clic sul pulsante **[!UICONTROL Explorer]** nella home page.

Viene fornito un modello integrato al fine di creare una campagna per la quale non è stata definita alcuna configurazione specifica. Puoi creare e configurare i modelli della campagna e quindi creare campagne a partire da questi modelli.

![](assets/do-not-localize/how-to-video.png) Per ulteriori informazioni sulla creazione di campagne, consulta [questo video](../../campaign/using/marketing-campaign-deliveries.md#create-email-video).

## Creare un modello di campagna {#creating-or-duplicating-a-campaign-template}

Per creare un modello di campagna, segui i passaggi seguenti:

1. Apri campagna **Esplora risorse**.
1. In **Risorse > Modelli > Modelli di campagna**, fai clic su **Nuovo** nella barra degli strumenti sopra l’elenco dei modelli.

   ![](assets/create_campaign_template_1.png)

1. Inserisci l’etichetta del nuovo modello di campagna.
1. Fai clic su **Salva** e riapri il modello.
1. In **Modifica** , immetti **Nome interno** e altri valori, se necessario.
1. Seleziona **Impostazioni avanzate della campagna** per aggiungere un flusso di lavoro al modello della campagna.

   ![](assets/create_campaign_template_2.png)

1. Modificare la **Targeting e flussi di lavoro** valore a **Sì**.

   ![](assets/create_campaign_template_3.png)

1. In **Targeting e flussi di lavoro** scheda , fai clic su **Aggiungi un flusso di lavoro...**.

   ![](assets/create_campaign_template_4.png)

1. Completa il **Etichetta** campo e fai clic su **Ok**.
1. Crea il flusso di lavoro in base alle tue esigenze.
1. Fai clic su **Salva**. Il modello è ora pronto per essere utilizzato in una campagna.

È inoltre possibile **duplicato** il modello predefinito da riutilizzare e adattare la sua configurazione.

Le varie schede e schede secondarie del modello della campagna consentono di accedere alle relative impostazioni, descritte in [Configurazione generale](#general-configuration).

![](assets/s_ncs_user_new_op_template_duplicate.png)

## Seleziona moduli {#select-modules}

La **[!UICONTROL Advanced campaign settings...]** link ti consente di abilitare e disabilitare i lavori per le campagne basate su questo modello. Seleziona le funzionalità da abilitare nelle campagne create in base a questo modello.

![](assets/s_ncs_user_op_template_tab1.3.png)

Se una funzionalità non è selezionata, gli elementi relativi al processo (menu, icone, opzioni, schede, schede secondarie, ecc.) non verrà visualizzato nell’interfaccia del modello o nelle campagne basate su questo modello. Le schede a sinistra dei dettagli della campagna in genere coincidono con i processi selezionati nel modello. Ad esempio, se **Spese e obiettivi** non è selezionato, il corrispondente **[!UICONTROL Budget]** La scheda non verrà visualizzata nelle campagne basate su questo modello.

Inoltre, i collegamenti alle finestre di configurazione vengono aggiunti al dashboard della campagna. Quando una funzionalità è abilitata, un collegamento diretto vi permette di accedervi dal dashboard della campagna.

Ad esempio, con la configurazione seguente:

![](assets/s_ncs_user_op_template_tab1.4.png)

I seguenti collegamenti vengono visualizzati nel dashboard della campagna (il **[!UICONTROL Add a task]** link mancante):

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

   Quando questo modulo è selezionato, viene aggiunta una scheda aggiuntiva al **[!UICONTROL Edition]** scheda del modello e delle campagne basate su questo modello. I documenti allegati possono essere aggiunti dal modello o singolarmente per ogni campagna. Ulteriori informazioni sui documenti in [questa sezione](../../campaign/using/marketing-campaign-deliveries.md#managing-associated-documents).

   ![](assets/s_ncs_user_op_template_activate_3.png)

* **Struttura**

   Quando questo modulo è selezionato, un **[!UICONTROL Delivery outlines]** la sottoscheda viene aggiunta al **[!UICONTROL Documents]** per definire i contorni di consegna per la campagna. Ulteriori informazioni sui profili di consegna in [questa sezione](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

   ![](assets/s_ncs_user_op_template_activate_4.png)

* **Targeting e flussi di lavoro**

   Quando selezioni la **[!UICONTROL Targeting and workflows]** modulo , viene aggiunta una scheda per consentire la creazione di uno o più flussi di lavoro per campagne basate su questo modello. I flussi di lavoro possono anche essere configurati singolarmente per ogni campagna basata su questo modello.Ulteriori informazioni sui flussi di lavoro delle campagne in [questa sezione](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow).

   ![](assets/s_ncs_user_op_template_activate_5.png)

   Quando questo modulo è abilitato, viene aggiunta una scheda alle impostazioni avanzate della campagna per definire la sequenza di esecuzione del processo.

   ![](assets/s_ncs_user_op_template_activate_5a.png)

* **Approvazione**

   Se selezioni la **[!UICONTROL Approval]**, puoi selezionare i processi da approvare e gli operatori responsabili delle approvazioni. Ulteriori informazioni sulle approvazioni in [questa sezione](../../campaign/using/marketing-campaign-approval.md#selecting-reviewers).

   ![](assets/s_ncs_user_op_template_activate_5b.png)

   Puoi scegliere se abilitare o meno l&#39;approvazione del processo tramite il **[!UICONTROL Approvals]** scheda della sezione delle impostazioni avanzate dei modelli. I processi per i quali è selezionata l’approvazione devono essere approvati per consentire la consegna dei messaggi.

   È necessario associare un operatore revisore o un gruppo di operatori a ogni approvazione abilitata.

* **Spese e obiettivi**

   Quando questo modulo è selezionato, un **[!UICONTROL Budget]** viene aggiunta una scheda ai dettagli del modello e delle campagne basate su questo modello in modo che sia possibile selezionare il budget associato.

   ![](assets/s_ncs_user_op_template_activate_7.png)

## Proprietà ed esecuzione {#general-configuration}

### Proprietà del modello {#template-properties}

![](assets/s_ncs_user_op_new_template.png)

Quando crei un modello di campagna, devi immettere le seguenti informazioni:

* Inserisci il **etichetta** del modello: questa etichetta verrà assegnata per impostazione predefinita a tutte le campagne create tramite questo modello.
* Seleziona la campagna **natura** dall’elenco a discesa. I valori disponibili in questo elenco sono quelli salvati in **[!UICONTROL natureOp]** enumerazione.

   >[!NOTE]
   >
   >Per ulteriori informazioni sulle enumerazioni, consulta [Introduzione](../../platform/using/managing-enumerations.md) sezione .

* Seleziona la **tipo di campagna**: unico, ricorrente o periodico. Per impostazione predefinita, i modelli di campagna si applicano a campagne univoche. Le campagne ricorrenti e periodiche sono descritte in [questa sezione](../../campaign/using/setting-up-marketing-campaigns.md#recurring-and-periodic-campaigns).
* Specifica la durata della campagna, ovvero il numero di giorni in cui avrà luogo la campagna. Quando crei una campagna basata su questo modello, le date di inizio e di fine della campagna verranno compilate automaticamente.

   Se la campagna è ricorrente, devi specificare le date di inizio e fine della campagna direttamente nel modello.

* Specifica la **programma correlato** del modello: le campagne basate su questo modello saranno collegate al programma selezionato.

### Parametri di esecuzione del modello {#template-execution-parameters}

La **[!UICONTROL Advanced campaign settings...]** link ti consente di configurare le opzioni avanzate del modello per l’elaborazione del target di consegna (gruppo di controllo, indirizzi di seed, ecc.) e la configurazione della misurazione della campagna e dell’esecuzione del flusso di lavoro.

![](assets/s_ncs_user_op_template_tab1.2.png)

## Tracciare l’esecuzione di una campagna{#campaign-reverse-scheduling}

Puoi creare una pianificazione per una campagna e tenere traccia dei risultati, ad esempio per preparare una pianificazione dell’evento per una data specifica. I modelli di campagna ora consentono di calcolare la data di inizio di un’attività in base alla data di fine di una campagna.

Nella casella di configurazione dell’attività, vai alla **[!UICONTROL Implementation schedule]** e controlla la **[!UICONTROL The start date is calculated based on the campaign end date]** scatola. (In questo caso, &quot;data di inizio&quot; è la data di inizio dell’attività). Vai a **[!UICONTROL Start]** e immetti un intervallo: l’attività verrà avviata molto prima della data di fine della campagna. Se immetti un periodo più lungo di quello impostato per l’ultima campagna, l’attività inizia prima della campagna.

![](assets/mrm_task_in_template_start_date.png)

Quando si crea una campagna utilizzando questo modello, la data di inizio dell&#39;attività viene calcolata automaticamente. Tuttavia, è sempre possibile modificarlo in un secondo momento.
