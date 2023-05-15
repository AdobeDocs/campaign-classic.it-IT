---
product: campaign
title: Documenti e linee di consegna della campagna di marketing
description: Ulteriori informazioni sui documenti e i profili di consegna delle campagne di marketing
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Campaigns
exl-id: 891252b0-4700-4a2a-a632-63aad5ce75d7
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '755'
ht-degree: 1%

---

# Gestire i documenti associati {#managing-associated-documents}

È possibile associare vari documenti a una campagna: rapporti, foto, pagine web, diagrammi, ecc. Questi documenti possono essere in qualsiasi formato (Microsoft Word, PowerPoint, PNG, JPG, Acrobat PDF, ecc.).

>[!IMPORTANT]
>
>Questa funzionalità è riservata alle risorse e ai documenti di piccole dimensioni.

In una campagna puoi anche fare riferimento ad altri articoli, come coupon promozionali, offerte speciali relative a uno specifico marchio o negozio, ecc. Quando questi elementi sono inclusi in una struttura, possono essere associati a una consegna direct mailing. Vedi [Associare e strutturare le risorse collegate tramite una struttura di consegna](#associating-and-structuring-resources-linked-via-a-delivery-outline).

>[!NOTE]
>
>Se utilizzi il modulo Gestione risorse di marketing per Campaign, puoi anche gestire una libreria di risorse di marketing disponibili per diversi utenti per il lavoro collaborativo. [Ulteriori informazioni](../../mrm/using/managing-marketing-resources.md).

## Aggiungi documenti {#adding-documents}

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

## Associare e strutturare le risorse collegate tramite una struttura di consegna {#associating-and-structuring-resources-linked-via-a-delivery-outline}

>[!NOTE]
>
>I profili di consegna sono utilizzati esclusivamente nel contesto delle campagne di direct mailing.

Un profilo di consegna indica un insieme strutturato di elementi (documenti, negozi, promozionali coupon, ecc.) creato dalla società e per una campagna particolare.

Tali elementi sono raggruppati in profili di consegna e ogni profilo di consegna sarà associato a una consegna; nel file di estrazione inviato al **fornitore di servizi** da allegare alla consegna. Ad esempio, puoi creare una struttura di consegna che fa riferimento a un ramo e alle brochure di marketing utilizzate.

Per una campagna, i profili di consegna ti consentono di strutturare elementi esterni da associare alla consegna in base a determinati criteri: filiale correlata, offerta promozionale concessa, invito a un evento locale, ecc.

### Creare una struttura {#creating-an-outline}

Per creare una struttura, fai clic sul pulsante **[!UICONTROL Delivery outlines]** sottoscheda in **[!UICONTROL Edit > Documents]** scheda della campagna interessata.

>[!NOTE]
>
>Se questa scheda non è presente, questa funzione non è disponibile per questa campagna. Consulta la configurazione del modello della campagna.
>   
>Per ulteriori informazioni sui modelli, consulta [questa sezione](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

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
   >Per ulteriori informazioni sulle risorse di marketing, consulta [questa sezione](../../mrm/using/managing-marketing-resources.md).

### Selezionare una struttura {#selecting-an-outline}

Per ogni consegna, puoi selezionare il profilo da associare dalla sezione riservata al profilo di estrazione, come nell’esempio seguente:

![](assets/s_ncs_user_op_select_composition.png)

Il profilo selezionato viene quindi visualizzato nella sezione inferiore della finestra. Può essere modificato utilizzando l’icona a destra del campo o utilizzando l’elenco a discesa:

![](assets/s_ncs_user_op_select_composition_b.png)

La **[!UICONTROL Summary]** La scheda della consegna visualizza anche queste informazioni:

![](assets/s_ncs_user_op_select_composition_c.png)

### Risultato estrazione {#extraction-result}

Nel file estratto e inviato al fornitore di servizi, il nome del profilo e, se del caso, le sue caratteristiche (costo, descrizione, ecc.) vengono aggiunti al contenuto in base alle informazioni nel modello di esportazione associato al provider di servizi.

Nell’esempio seguente, l’etichetta, il costo stimato e la descrizione del profilo associato alla consegna verranno aggiunti al file di estrazione.

![](assets/s_ncs_user_op_composition_in_export_template.png)

Il modello di esportazione deve essere associato al fornitore di servizi selezionato per la consegna in questione. Vedi [questa sezione](../../campaign/using/providers--stocks-and-budgets.md#creating-service-providers-and-their-cost-structures).

>[!NOTE]
>
>Per ulteriori informazioni sulle esportazioni, consulta [questa sezione](../../platform/using/get-started-data-import-export.md) sezione .
