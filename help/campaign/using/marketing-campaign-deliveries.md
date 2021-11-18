---
product: campaign
title: Consegne di campagne di marketing
description: Ulteriori informazioni sulle consegne delle campagne di marketing
audience: campaign
content-type: reference
topic-tags: orchestrate-campaigns
exl-id: 1dd3c080-444d-45f8-9562-d2d01a9d2860
source-git-commit: f000cb8bae164c22d1ede15db4e763cf50530674
workflow-type: tm+mt
source-wordcount: '1487'
ht-degree: 3%

---

# Consegne di campagne di marketing {#marketing-campaign-deliveries}

![](../../assets/common.svg)

Le consegne possono essere create tramite il dashboard della campagna, un flusso di lavoro della campagna o direttamente tramite la panoramica delle consegne.

Una volta create da una campagna, le consegne saranno collegate a questa campagna e consolidate a livello di campagna.

![](assets/do-not-localize/how-to-video.png)[ Scopri questa funzione nel video](#create-email-video)

## Creazione di consegne {#creating-deliveries}

Per creare una consegna collegata a una campagna, fai clic sul pulsante **[!UICONTROL Add a delivery]** nel dashboard della campagna.

![](assets/campaign_op_add_delivery.png)

Le configurazioni suggerite sono adatte ai diversi tipi di consegna: direct mailing, e-mail, canali mobili. [Ulteriori informazioni](../../delivery/using/steps-about-delivery-creation-steps.md).

## Avvio di una consegna {#starting-a-delivery}

Una volta concesse tutte le approvazioni, la consegna è pronta per essere avviata. La procedura di consegna dipende quindi dal tipo di consegna. Per le consegne e-mail o di canali mobili, consulta [Avvio di una consegna online](#starting-an-online-delivery), e per le consegne di direct mailing, vedi [Avvio di una consegna offline](#starting-an-offline-delivery).

### Avvio di una consegna online {#starting-an-online-delivery}

Una volta concesse tutte le richieste di approvazione, lo stato di consegna cambia in **[!UICONTROL Pending confirmation]** e può essere avviato da un operatore . Se del caso, all’operatore Adobe Campaign (o al gruppo di operatori) designato come revisore per avviare la consegna viene notificato che una consegna è pronta per essere avviata.

>[!NOTE]
>
>Se un operatore o un gruppo specifico di operatori è designato per avviare una consegna nelle proprietà della consegna, puoi anche consentire all’operatore responsabile della consegna di confermare l’invio. Per eseguire questa operazione, attiva il **NMS_ActivateOwnerConfirmation** opzione immettendo **1** come valore. Le opzioni vengono gestite dal **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]** in Adobe Campaign Explorer.
>  
>Per disattivare questa opzione, immetti **0** come valore. Il processo di conferma dell’invio funzionerà quindi come impostazione predefinita: solo l’operatore o il gruppo di operatori designati per l’invio nelle proprietà di consegna (o un amministratore) sarà in grado di confermare ed eseguire l’invio.

![](assets/s_ncs_user_edit_del_to_start_from_del.png)

Le informazioni vengono visualizzate anche sul dashboard della campagna. La **[!UICONTROL Confirm delivery]** consente di avviare la consegna.

![](assets/s_ncs_user_edit_del_to_start.png)

Un messaggio di conferma ti consente di proteggere questa azione.

### Avvio di una consegna offline {#starting-an-offline-delivery}

Una volta concesse tutte le approvazioni, lo stato di consegna cambia in **[!UICONTROL Pending extraction]**. I file di estrazione vengono creati tramite un flusso di lavoro speciale che, in una configurazione predefinita, viene avviato automaticamente quando una consegna direct mailing è in attesa di estrazione. Quando un processo è in corso, viene visualizzato nel dashboard e può essere modificato tramite il relativo collegamento.

>[!NOTE]
>
>I flussi di lavoro tecnici relativi al pacchetto Campaign sono presentati in [Elenco dei flussi di lavoro tecnici](../../workflow/using/about-technical-workflows.md).

**Passaggio 1 - Approvazione dei file**

Una volta eseguito correttamente il flusso di lavoro di estrazione, il file di estrazione deve essere approvato (a condizione che l’approvazione del file di estrazione sia stata selezionata nelle impostazioni di consegna).

Per ulteriori informazioni, consulta [Approvazione di un file di estrazione](../../campaign/using/marketing-campaign-approval.md#approving-an-extraction-file).

**Passaggio 2 - Approvazione del messaggio al provider di servizi**

* Una volta approvato il file di estrazione, puoi generare la bozza dell’e-mail di notifica del router. Questo messaggio e-mail viene creato in base a un modello di consegna. Deve essere approvato.

   >[!NOTE]
   >
   >Questo passaggio è disponibile solo se l’invio e l’approvazione delle bozze è stato abilitato nella finestra delle approvazioni.

![](assets/s_ncs_user_file_valid_select_BAT.png)


* Fai clic sul pulsante **[!UICONTROL Send a proof]** per creare le bozze.

   Il target della bozza deve essere definito in anticipo.

   Puoi creare tutte le prove necessarie. Sono accessibili tramite il **[!UICONTROL Direct mail...]** collegamento dei dettagli di consegna.

   ![](assets/s_ncs_user_file_notif_submit_proof.png)

* Lo stato di consegna cambia in **[!UICONTROL To submit]**. Fai clic sul pulsante **[!UICONTROL Submit proofs]** per avviare il processo di approvazione.

   ![](assets/s_ncs_user_file_notif_submit_proof_validation.png)

* Lo stato di consegna cambia in **[!UICONTROL Proof to validate]** e un pulsante consente di accettare o rifiutare l’approvazione.

   ![](assets/s_ncs_user_file_notif_supplier_link.png)

   Puoi accettare o rifiutare questa approvazione o tornare al passaggio di estrazione.

   ![](assets/s_ncs_user_file_notif_supplier_link_confirm.png)

* Il file di estrazione viene inviato al router e la consegna è terminata.

### Calcolo dei costi e delle scorte {#calculation-of-costs-and-stocks}

L’estrazione del file avvia due operazioni: calcolo del budget e calcolo delle scorte. Le voci di budget vengono aggiornate.

* La **[!UICONTROL Budget]** consente di gestire i budget per la campagna. Il totale delle voci di costo è indicato nella variabile **[!UICONTROL Calculates cost]** campo della scheda principale della campagna e del programma a cui appartiene. Gli importi si riflettono anche nel bilancio della campagna.

   Il costo reale sarà calcolato in base alle informazioni fornite dal router. Vengono fatturati solo i messaggi effettivamente inviati.

* Le consistenze sono definite nella **[!UICONTROL Administration > Campaign management > Stocks]** nodo della struttura e strutture di costo nel **[!UICONTROL Administration > Campaign management > Service providers]** nodo.

   Le linee di scorta sono visibili nella sezione di scorta. Per definire il magazzino iniziale, aprire una linea di magazzino. Lo stock viene ridotto ogni volta che si verifica una consegna. Puoi definire un livello di avviso e le notifiche.

>[!NOTE]
>
>Per ulteriori informazioni sul calcolo dei costi e sulla gestione delle scorte, vedi [Fornitori, scorte e budget](../../campaign/using/providers--stocks-and-budgets.md).

## Gestione dei documenti associati {#managing-associated-documents}

È possibile associare vari documenti a una campagna: report, foto, pagina web, diagramma, ecc. Questi documenti possono essere in qualsiasi formato (Microsoft Word, PowerPoint, PNG, JPG, Acrobat PDF, ecc.). Scopri come collegare documenti a una campagna [in questa sezione](../../campaign/using/marketing-campaign-assets.md).

>[!IMPORTANT]
>
>Questa modalità è riservata ai documenti di piccole dimensioni.

In una campagna puoi anche fare riferimento ad altri articoli, come coupon promozionali, offerte speciali relative a un ramo o un negozio specifico, ecc. Quando questi elementi sono inclusi in una struttura, possono essere associati a una consegna direct mailing. [Ulteriori informazioni](#associating-and-structuring-resources-linked-via-a-delivery-outline).

>[!NOTE]
>
>Se utilizzi MRM, puoi anche gestire una libreria di risorse di marketing disponibili per diversi partecipanti per lavori collaborativi. Vedi [Gestione delle risorse di marketing](../../mrm/using/managing-marketing-resources.md).

### Aggiunta di documenti {#adding-documents}

I documenti possono essere associati a livello di campagna (documenti contestuali) o a livello di programma (documenti generali).

La **[!UICONTROL Documents]** la scheda contiene:

* Elenco di tutti i documenti richiesti per il contenuto (modello, immagini, ecc.) che possono essere scaricati localmente dagli operatori Adobe Campaign con diritti adeguati,
* Documenti contenenti informazioni relative al router, se presenti.

I documenti sono collegati al programma o alla campagna tramite il **[!UICONTROL Edit > Documents]** scheda .

![](assets/s_ncs_user_op_add_document.png)

Puoi anche aggiungere un documento a una campagna tramite il collegamento offerto nel dashboard.

![](assets/add_a_document_in_op.png)

Fai clic sul pulsante **[!UICONTROL Details]** per visualizzare il contenuto di un file e aggiungere informazioni:

![](assets/s_ncs_user_op_add_document_details.png)

Nel dashboard, i documenti associati alla campagna sono raggruppati nel **[!UICONTROL Document(s)]** come nell’esempio seguente:

![](assets/s_ncs_user_op_edit_document.png)

È inoltre possibile modificarli e modificarli da questa visualizzazione.

### Associazione e strutturazione delle risorse collegate tramite una struttura di consegna {#associating-and-structuring-resources-linked-via-a-delivery-outline}

>[!NOTE]
>
>I profili di consegna sono utilizzati esclusivamente nel contesto delle campagne di direct mailing.

Un profilo di consegna indica un insieme strutturato di elementi (documenti, filiali/negozi, promozionali coupon, ecc.) creato nell&#39;azienda e per una particolare campagna.

Tali elementi sono raggruppati in profili di consegna e un particolare profilo di consegna sarà associato a una consegna; nel file di estrazione inviato al **fornitore di servizi** da allegare alla consegna. Ad esempio, puoi creare una struttura di consegna che fa riferimento a un ramo e alle brochure di marketing utilizzate.

Per una campagna, i profili di consegna ti consentono di strutturare elementi esterni da associare alla consegna in base a determinati criteri: filiale correlata, offerta promozionale concessa, invito a un evento locale, ecc.

#### Creazione di una struttura {#creating-an-outline}

Per creare una struttura, fai clic sul pulsante **[!UICONTROL Delivery outlines]** sottoscheda in **[!UICONTROL Edit > Documents]** scheda della campagna interessata.

>[!NOTE]
>
>Se questa scheda non è presente, questa funzione non è disponibile per questa campagna. Consulta la configurazione del modello della campagna.
>   
>Per ulteriori informazioni, consulta [Modelli di campagna](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

![](assets/s_ncs_user_op_composition_link.png)

Quindi, fai clic su **[!UICONTROL Add a delivery outline]** e crea la gerarchia di profili per la campagna:

1. Fare clic con il pulsante destro del mouse sulla radice dell&#39;albero e selezionare **[!UICONTROL New > Delivery outlines]**.
1. Fai clic con il pulsante destro del mouse sul profilo appena creato e seleziona **[!UICONTROL New > Item]** o **[!UICONTROL New > Personalization fields]**.

![](assets/s_ncs_user_op_add_composition.png)

Una struttura può contenere elementi e campi di personalizzazione, risorse e offerte:

* Gli elementi possono essere documenti fisici, ad esempio, a cui viene fatto riferimento e descritto qui e che verranno allegati alla consegna.
* I campi di personalizzazione ti consentono di creare elementi di personalizzazione relativi alle consegne anziché ai destinatari. È quindi possibile creare valori da utilizzare nelle consegne per un target specifico (offerta di benvenuto, uno sconto, ecc.) Vengono creati in Adobe Campaign e importati nella struttura tramite il **[!UICONTROL Import personalization fields...]** link.

   ![](assets/s_ncs_user_op_add_composition_field.png)

   È inoltre possibile crearli direttamente nel profilo facendo clic sul pulsante **[!UICONTROL Add]** a destra della zona elenco.

   ![](assets/s_ncs_user_op_add_composition_field_button.png)

* Le risorse sono risorse di marketing generate nel dashboard delle risorse di marketing accessibile tramite il **[!UICONTROL Resources]** collegamento **[!UICONTROL Campaigns]** scheda .

   ![](assets/s_ncs_user_mkg_resource_ovv.png)

   >[!NOTE]
   >
   >Per ulteriori informazioni sulle risorse di marketing, consulta [Gestione delle risorse di marketing](../../mrm/using/managing-marketing-resources.md).

#### Selezione di una struttura {#selecting-an-outline}

Per ogni consegna, puoi selezionare il profilo da associare dalla sezione riservata al profilo di estrazione, come nell’esempio seguente:

![](assets/s_ncs_user_op_select_composition.png)

Il profilo selezionato viene quindi visualizzato nella sezione inferiore della finestra. Può essere modificato utilizzando l’icona a destra del campo o utilizzando l’elenco a discesa:

![](assets/s_ncs_user_op_select_composition_b.png)

La **[!UICONTROL Summary]** La scheda della consegna visualizza anche queste informazioni:

![](assets/s_ncs_user_op_select_composition_c.png)

#### Risultato estrazione {#extraction-result}

Nel file estratto e inviato al fornitore di servizi, il nome del profilo e, se del caso, le sue caratteristiche (costo, descrizione, ecc.) vengono aggiunti al contenuto in base alle informazioni nel modello di esportazione associato al provider di servizi.

Nell’esempio seguente, l’etichetta, il costo stimato e la descrizione del profilo associato alla consegna verranno aggiunti al file di estrazione.

![](assets/s_ncs_user_op_composition_in_export_template.png)

Il modello di esportazione deve essere associato al fornitore di servizi selezionato per la consegna in questione. Vedi [Creazione di fornitori di servizi e relative strutture di costo](../../campaign/using/providers--stocks-and-budgets.md#creating-service-providers-and-their-cost-structures).

>[!NOTE]
>
>Per ulteriori informazioni sulle esportazioni, consulta la sezione [Introduzione](../../platform/using/get-started-data-import-export.md) sezione .

#### Video tutorial {#create-email-video}

In questo video viene illustrato come creare una campagna e un messaggio e-mail in Adobe Campaign.

>[!VIDEO](https://video.tv.adobe.com/v/25604?quality=12)

Sono disponibili ulteriori video dimostrativi relativi a Campaign [qui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=it).
