---
product: campaign
title: Documenti della campagna di marketing e profili di consegna
description: Ulteriori informazioni sui documenti della campagna di marketing e sui profili di consegna
role: User
feature: Campaigns
exl-id: 891252b0-4700-4a2a-a632-63aad5ce75d7
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '755'
ht-degree: 0%

---

# Gestire i documenti associati {#managing-associated-documents}

È possibile associare vari documenti a una campagna: rapporti, foto, pagine web, diagrammi, ecc. Questi documenti possono essere in qualsiasi formato (Microsoft Word, PowerPoint, PNG, JPG, Acrobat PDF, ecc.).

>[!IMPORTANT]
>
>Questa funzionalità è riservata alle risorse e ai documenti di piccole dimensioni.

In una campagna puoi anche fare riferimento ad altri articoli, come coupon promozionali, offerte speciali relative a una marca o a un negozio specifico, ecc. Quando questi elementi sono inclusi in una struttura, possono essere associati a una consegna direct mailing. Consulta [Associa e struttura le risorse collegate tramite una struttura di consegna](#associating-and-structuring-resources-linked-via-a-delivery-outline).

>[!NOTE]
>
>Se utilizzi il modulo Gestione risorse marketing di Campaign, puoi anche gestire una libreria di risorse di marketing disponibili per più utenti per il lavoro collaborativo. [Ulteriori informazioni](../../mrm/using/managing-marketing-resources.md).

## Aggiungi documenti {#adding-documents}

I documenti possono essere associati a livello di campagna (documenti contestuali) o di programma (documenti generali).

Il **[!UICONTROL Documents]** La scheda contiene:

* L’elenco di tutti i documenti necessari per il contenuto (modello, immagini, ecc.) che possono essere scaricati localmente dagli operatori Adobe Campaign con i diritti appropriati,
* Documenti contenenti informazioni per il router, se presenti.

I documenti sono collegati al programma o alla campagna tramite **[!UICONTROL Edit > Documents]** scheda.

![](assets/s_ncs_user_op_add_document.png)

Puoi anche aggiungere un documento a una campagna tramite il collegamento offerto nella dashboard.

![](assets/add_a_document_in_op.png)

Fai clic su **[!UICONTROL Details]** per visualizzare il contenuto di un file e aggiungere informazioni:

![](assets/s_ncs_user_op_add_document_details.png)

Nel dashboard, i documenti associati alla campagna sono raggruppati nel **[!UICONTROL Document(s)]** come nell’esempio seguente:

![](assets/s_ncs_user_op_edit_document.png)

Da questa vista è possibile modificarli.

## Associa e struttura le risorse collegate tramite una struttura di consegna {#associating-and-structuring-resources-linked-via-a-delivery-outline}

>[!NOTE]
>
>I profili di consegna vengono utilizzati esclusivamente nel contesto delle campagne di direct mailing.

Una struttura di consegna indica un set strutturato di elementi (documenti, negozi, coupon promozionali, ecc.) create dall’azienda e per una determinata campagna.

Questi elementi sono raggruppati in profili di consegna e ogni profilo di consegna sarà associato a una consegna; vi verrà fatto riferimento nel file di estrazione inviato al **service provider** per essere collegato alla consegna. Ad esempio, puoi creare una struttura di consegna che faccia riferimento a un ramo e alle brochure di marketing che utilizza.

Per una campagna, i profili di consegna ti consentono di strutturare elementi esterni da associare alla consegna in base a determinati criteri: ramo correlato, offerta promozionale concessa, invito a un evento locale, ecc.

### Creare una struttura {#creating-an-outline}

Per creare una struttura, fare clic su **[!UICONTROL Delivery outlines]** scheda secondaria in **[!UICONTROL Edit > Documents]** scheda della campagna in questione.

>[!NOTE]
>
>Se questa scheda non è presente, questa funzione non è disponibile per questa campagna. Consulta la configurazione del modello della campagna.
>   
>Per ulteriori informazioni sui modelli, consulta [questa sezione](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

![](assets/s_ncs_user_op_composition_link.png)

Quindi, fai clic su **[!UICONTROL Add a delivery outline]** e creare la gerarchia di profili per la campagna:

1. Fare clic con il pulsante destro del mouse sulla radice della struttura e selezionare **[!UICONTROL New > Delivery outlines]**.
1. Fare clic con il pulsante destro del mouse sulla struttura appena creata e selezionare **[!UICONTROL New > Item]** o **[!UICONTROL New > Personalization fields]**.

![](assets/s_ncs_user_op_add_composition.png)

Una struttura può contenere elementi e campi di personalizzazione, risorse e offerte:

* Gli elementi possono essere, ad esempio, documenti fisici a cui viene fatto riferimento e che vengono descritti qui e che verranno allegati alla consegna.
* I campi di personalizzazione ti consentono di creare elementi di personalizzazione relativi alle consegne anziché ai destinatari. È quindi possibile creare valori da utilizzare nelle consegne per un target specifico (offerta di benvenuto, uno sconto, ecc.) Vengono creati in Adobe Campaign e importati nella struttura tramite **[!UICONTROL Import personalization fields...]** collegamento.

  ![](assets/s_ncs_user_op_add_composition_field.png)

  È inoltre possibile crearli direttamente nella struttura facendo clic sul pulsante **[!UICONTROL Add]** a destra della zona elenco.

  ![](assets/s_ncs_user_op_add_composition_field_button.png)

* Le risorse sono risorse di marketing generate nel dashboard delle risorse di marketing a cui si accede tramite **[!UICONTROL Resources]** collegamento del **[!UICONTROL Campaigns]** scheda.

  ![](assets/s_ncs_user_mkg_resource_ovv.png)

  >[!NOTE]
  >
  >Per ulteriori informazioni sulle risorse di marketing, consulta [questa sezione](../../mrm/using/managing-marketing-resources.md).

### Seleziona una struttura {#selecting-an-outline}

Per ogni consegna, puoi selezionare la struttura da associare dalla sezione riservata alla struttura di estrazione, come nell’esempio seguente:

![](assets/s_ncs_user_op_select_composition.png)

La struttura selezionata viene quindi visualizzata nella sezione inferiore della finestra. Può essere modificata utilizzando l’icona a destra del campo o modificata utilizzando l’elenco a discesa:

![](assets/s_ncs_user_op_select_composition_b.png)

Il **[!UICONTROL Summary]** Nella scheda della consegna vengono visualizzate anche le seguenti informazioni:

![](assets/s_ncs_user_op_select_composition_c.png)

### Risultato estrazione {#extraction-result}

Nel fascicolo estratto e inviato al prestatore di servizi, il nome della struttura e, se del caso, le sue caratteristiche (costo, descrizione, ecc.) vengono aggiunti al contenuto in base alle informazioni contenute nel modello di esportazione associato al provider di servizi.

Nell’esempio seguente, l’etichetta, il costo stimato e la descrizione della struttura associata alla consegna verranno aggiunti al file di estrazione.

![](assets/s_ncs_user_op_composition_in_export_template.png)

Il modello di esportazione deve essere associato al fornitore di servizi selezionato per la consegna interessata. Consulta [questa sezione](../../campaign/using/providers-stocks-and-budgets.md#creating-service-providers-and-their-cost-structures).

>[!NOTE]
>
>Per ulteriori informazioni sulle esportazioni, consulta [questa sezione](../../platform/using/get-started-data-import-export.md) sezione.
