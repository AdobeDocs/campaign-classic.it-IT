---
product: campaign
title: Definire la popolazione target
description: Scopri come definire la popolazione target
feature: Audiences, Proofs
role: User
exl-id: d0ed7be7-3147-4cb8-9ce7-ea51602e9048
source-git-commit: f469689f9e8a4d805fb95a1ae120ccd35aba3731
workflow-type: tm+mt
source-wordcount: '1729'
ht-degree: 6%

---

# Definire la popolazione target {#defining-the-target-population}

Per ogni consegna, puoi definire diversi tipi di popolazioni target:

* **Pubblico principale**: profili che riceveranno messaggi. [Ulteriori informazioni](steps-defining-the-target-population.md#selecting-the-main-target)
* **Bozza**: destinatari dei messaggi di bozza, coinvolti nel ciclo di convalida. [Ulteriori informazioni](steps-defining-the-target-population.md#defining-a-specific-proof-target)
* **Indirizzi seed**: destinatari che non rientrano nel target di consegna ma che riceveranno la consegna (solo nel contesto di una campagna di marketing). [Ulteriori informazioni](about-seed-addresses.md)
* **Gruppi di controllo**: popolazione che non riceverà la consegna, utilizzata per tenere traccia del comportamento e dell&#39;impatto della campagna (solo nel contesto di una campagna di marketing). [Ulteriori informazioni](../../campaign/using/marketing-campaign-target.md#defining-a-control-group).

## Selezionare i destinatari principali della consegna {#selecting-the-main-target}

Nella maggior parte dei casi, il target principale viene estratto dal database di Adobe Campaign (modalità predefinita). Tuttavia, i destinatari possono anche essere memorizzati in un file esterno. Per ulteriori informazioni, consulta [questa sezione](steps-defining-the-target-population.md#selecting-external-recipients).

Per selezionare i destinatari di una consegna, segui i passaggi seguenti:

1. Nell&#39;editor di consegna, selezionare **[!UICONTROL To]**.
1. Se i destinatari sono memorizzati nel database, scegliere la prima opzione.

   ![](assets/s_ncs_user_wizard_email02a.png)

1. Selezionare la mappatura di destinazione nell&#39;elenco a discesa **[!UICONTROL Target mapping]**. Il mapping di destinazione predefinito di Adobe Campaign è **[!UICONTROL Recipients]**, basato sullo schema **nms:recipient**.

   Sono disponibili altre mappature di destinazione, alcune delle quali possono essere correlate alla configurazione specifica.[Ulteriori informazioni](#select-a-target-mapping).

1. Fare clic sul pulsante **[!UICONTROL Add]** per definire i filtri di restrizione.

   Puoi quindi selezionare il tipo di filtro da applicare:

   ![](assets/s_ncs_user_wizard_email02b.png)

   Puoi selezionare i destinatari utilizzando i tipi di targeting definiti nel database. Per utilizzare un tipo di destinazione, selezionarlo e fare clic su **[!UICONTROL Next]**. Per ogni destinazione, è possibile visualizzare i destinatari interessati facendo clic sulla scheda **[!UICONTROL Preview]**. Per alcuni tipi di destinazione, il pulsante **[!UICONTROL Refine target]** consente di combinare diversi criteri di targeting.

   I seguenti tipi di target sono offerti per impostazione predefinita:

   * **[!UICONTROL Filtering conditions]** : questa opzione consente di definire una query e di visualizzare il risultato. Il metodo per la definizione delle query è presentato in [questa sezione](../../platform/using/creating-filters.md#creating-an-advanced-filter).
   * **[!UICONTROL Subscribers of an information service]** : questa opzione ti consente di selezionare una newsletter a cui i destinatari devono iscriversi per essere destinatari della consegna creata.

     ![](assets/s_ncs_user_wizard_email02c.png)

   * **[!UICONTROL Recipients of a delivery]** : questa opzione consente di definire i destinatari di una consegna esistente come criterio di targeting. Seleziona quindi la consegna nell’elenco:

     ![](assets/s_ncs_user_wizard_email02d.png)

   * **[!UICONTROL Delivery recipients belonging to a folder]** : questa opzione consente di selezionare una cartella di consegna e di eseguire il targeting dei destinatari delle consegne in tale cartella.

     ![](assets/s_ncs_user_wizard_email02e.png)

     Puoi filtrare il comportamento dei destinatari selezionando dall’elenco a discesa:

     ![](assets/s_ncs_user_wizard_email02f.png)

     >[!NOTE]
     >
     >L&#39;opzione **[!UICONTROL Include sub-folders]** consente inoltre di eseguire il targeting delle consegne contenute nelle cartelle presenti nella struttura ad albero sotto il nodo selezionato.

   * **[!UICONTROL Recipients included in a folder]** : questa opzione consente di eseguire il targeting dei profili contenuti in una cartella specifica della struttura.
   * **[!UICONTROL A recipient]** : questa opzione consente di selezionare un destinatario specifico dai profili nel database.
   * **[!UICONTROL A list of recipients]** : questa opzione consente di eseguire il targeting di un elenco di destinatari. Gli elenchi sono presentati in [questa sezione](../../platform/using/creating-and-managing-lists.md).
   * **[!UICONTROL User filters]** : questa opzione consente di accedere ai filtri preconfigurati per utilizzarli come criteri di filtro per i profili nel database. I filtri preconfigurati sono presentati in [questa sezione](../../platform/using/creating-filters.md#saving-a-filter).
   * L&#39;opzione **[!UICONTROL Exclude recipients corresponding to this segment]** consente di eseguire il targeting di destinatari che non soddisfano i criteri di destinazione definiti. Per utilizzare questa opzione, seleziona la casella appropriata e quindi applica il targeting, come definito in precedenza, per escludere i profili risultanti.

     ![](assets/s_ncs_user_wizard_email02g.png)

1. Immettere un nome per il targeting nel campo **[!UICONTROL Label]**. Per impostazione predefinita, l’etichetta corrisponde al primo criterio di targeting. Per una combinazione, è meglio utilizzare un nome esplicito.
1. Fare clic su **[!UICONTROL Finish]** per convalidare la destinazione configurata.

   I criteri di targeting definiti sono riepilogati nella sezione centrale della scheda di configurazione principale del target. Fai clic su un criterio per visualizzarne il contenuto (configurazione e anteprima). Per eliminare un criterio, fare clic sulla croce che si trova dopo l&#39;etichetta.

   ![](assets/s_ncs_user_wizard_email02h.png)

### Seleziona destinatari esterni {#selecting-external-recipients}

Puoi avviare una consegna per i destinatari che non sono stati salvati nel database, ma che sono stati memorizzati in un file esterno. Ad esempio, invieremo qui una consegna a destinatari importati da un file di testo.

Per eseguire questa operazione:

1. Fai clic sul collegamento **[!UICONTROL To]** per selezionare i destinatari della consegna.
1. Selezionare l&#39;opzione **[!UICONTROL Defined in an external file]**.

   ![](assets/s_ncs_user_wizard_external_recipients.png)

1. Per impostazione predefinita, i destinatari vengono importati nel database. Selezionare **[!UICONTROL Target mapping]**. [Ulteriori informazioni](#select-a-target-mapping)

   Puoi anche scegliere **[!UICONTROL Do not import the recipients into the database]**.

1. Durante l&#39;importazione dei destinatari, fare clic sul collegamento **[!UICONTROL File format definition...]** per selezionare e configurare il file esterno.

   Per ulteriori informazioni sull&#39;importazione dei dati, consultare [questa sezione](../../platform/using/executing-import-jobs.md#step-2---source-file-selection).

1. Fai clic su **[!UICONTROL Finish]** e configura la consegna come consegna standard.

>[!CAUTION]
>
>Quando definisci il contenuto del messaggio per la consegna e-mail, non includere il collegamento alla pagina speculare; non può essere generato in questa modalità di consegna.

### Definire le impostazioni di esclusione {#define-exclusion-settings}

Gli errori di indirizzo e le valutazioni della qualità vengono forniti dal provider di servizi (IAP). Queste informazioni vengono aggiornate automaticamente nel profilo del destinatario dopo le azioni di consegna e con i file restituiti dai provider di servizi. Può essere visualizzato nel profilo in sola lettura.

Puoi scegliere di escludere gli indirizzi che hanno raggiunto un certo numero di errori consecutivi o la cui valutazione della qualità è inferiore a una soglia specificata in questa finestra. Puoi anche scegliere se autorizzare o meno gli indirizzi non qualificati per i quali non sono stati restituiti dati.

>[!NOTE]
>
>Se due destinatari hanno lo stesso nome, cognome, codice postale e città in una consegna direct mailing, si verificherà un doppio errore e il duplicato non verrà preso in considerazione.

La scheda **[!UICONTROL Exclusions]** viene utilizzata per limitare il numero di messaggi.

>[!NOTE]
>
>I parametri predefiniti sono consigliati, ma puoi adattare le impostazioni in base alle tue esigenze. Tuttavia, queste opzioni devono essere modificate solo da un utente esperto per evitare abusi ed errori.

Fare clic sul collegamento **[!UICONTROL Edit...]** per modificare la configurazione predefinita.

![](assets/s_ncs_user_wizard_email02i.png)

Sono disponibili le seguenti opzioni:

* **[!UICONTROL Exclude duplicate addresses during delivery]**. Questa opzione è attiva per impostazione predefinita: ti consente di eliminare gli indirizzi e-mail duplicati durante la consegna. La strategia applicata può variare a seconda del modo in cui Adobe Campaign viene utilizzato e del tipo di dati nel database.

  Il valore predefinito dell’opzione può essere configurato per ogni modello di consegna.

  Ad esempio:

   * Consegna di una newsletter o di un documento elettronico. In alcuni casi non è prevista alcuna esclusione di duplicati se i dati non contengono duplicati nativi. Una coppia che si abbona con lo stesso indirizzo e-mail può aspettarsi di ricevere due specifici messaggi e-mail personalizzati: uno indirizzato a ogni individuo per nome. In questo caso, questa opzione può essere deselezionata.
   * Consegna di una campagna di marketing: la duplicazione dell’esclusione è essenziale per evitare di inviare troppi messaggi allo stesso destinatario. In questo caso, è possibile selezionare questa opzione.

     Se si deseleziona questa opzione, è possibile accedere a un&#39;opzione aggiuntiva: **[!UICONTROL Keep duplicate records (same identifier)]**. Ti consente di autorizzare più consegne a destinatari che soddisfano diversi criteri di targeting.

     ![](assets/s_ncs_user_wizard_email02j.png)

* **[!UICONTROL Exclude recipients who no longer want to be contacted]** , ovvero i destinatari i cui indirizzi e-mail si trovano in fase di inserisce nell&#39;elenco Bloccati (opt out) di. Questa opzione deve rimanere selezionata al fine di rispettare l&#39;etica professionale dell&#39;e-marketing e le leggi che disciplinano l&#39;e-commerce.
* **[!UICONTROL Exclude quarantined recipients]**. Questa opzione ti consente di escludere dal target tutti i profili con un indirizzo che non risponde. Si consiglia vivamente di mantenere selezionata questa opzione.

  >[!NOTE]
  >
  >Per ulteriori informazioni sulla gestione della quarantena, vedere [Informazioni sulla gestione della quarantena](understanding-quarantine-management.md).

* **[!UICONTROL Limit delivery]** a un determinato numero di messaggi. Questa opzione consente di immettere il numero massimo di messaggi da inviare. Se il contenuto del target supera il numero di messaggi indicati, viene applicata una selezione casuale.

### Ridurre la dimensione della popolazione target {#reducing-the-size-of-the-target-population}

Puoi ridurre la dimensione della popolazione target. A questo scopo, specifica il numero di destinatari da esportare nel campo **[!UICONTROL Requested quantity]**.

![](assets/s_ncs_user_edit_del_exe_tab.png)

## Selezionare i destinatari dei messaggi di bozza {#selecting-the-proof-target}

La bozza è un messaggio speciale che consente di testare una consegna prima di inviarla al target principale. I destinatari della bozza sono responsabili dell’approvazione del modulo e del contenuto del messaggio.

![](assets/do-not-localize/how-to-video.png) [Guarda il video su questa funzione](#seeds-and-proofs-video)


Per selezionare la destinazione delle bozze, segui i passaggi seguenti:

1. Fai clic sul collegamento **[!UICONTROL To]**.
1. Fare clic sulla scheda **[!UICONTROL Target of the proofs]**.
1. Fare clic sul campo **[!UICONTROL Targeting mode]** per scegliere il metodo da applicare: **[!UICONTROL Definition of a specific proof target]**, **[!UICONTROL Substitution of the address]**, **[!UICONTROL Seed addresses]** o **[!UICONTROL Specific target and seed addresses]**.

>[!NOTE]
>
>Di solito, il target della bozza può essere aggiunto al target principale. A tale scopo, selezionare l&#39;opzione appropriata nella sezione inferiore della scheda **[!UICONTROL Main target]**.

## Definire un target di bozza specifico {#defining-a-specific-proof-target}

Quando selezioni la destinazione della bozza, l&#39;opzione **[!UICONTROL Definition of a specific proof target]** ti consente di selezionare i destinatari della bozza dai profili nel database.

Selezionare questa opzione per scegliere i destinatari utilizzando il pulsante **[!UICONTROL Add]**, come nel caso della definizione della destinazione principale. Vedere [Selezionare la destinazione principale](steps-defining-the-target-population.md#selecting-the-main-target).

![](assets/s_ncs_user_wizard_email01_143.png)

Per ulteriori informazioni sull&#39;invio della bozza, consulta [questa sezione](steps-validating-the-delivery.md#sending-a-proof).

### Utilizza la sostituzione degli indirizzi nella bozza {#using-address-substitution-in-proof}

Invece di selezionare i destinatari dedicati nel database, puoi utilizzare l&#39;opzione **[!UICONTROL Substitution of the address]**.

Questa opzione ti consente di utilizzare i profili dei destinatari della consegna e di sostituire i loro indirizzi e-mail con uno o più altri indirizzi che riceveranno la bozza.

Quando questa opzione è selezionata, gli indirizzi della bozza verranno compilati tramite un editor speciale che consente di configurare le sostituzioni.

![](assets/s_ncs_user_wizard_email_bat_substitute.png)

La configurazione viene eseguita come segue:

1. Fare clic sull&#39;icona **[!UICONTROL Add]** per definire una sostituzione.
1. Immettere l&#39;indirizzo del destinatario da utilizzare o selezionarlo dall&#39;elenco.
1. Selezionare il profilo da utilizzare nella bozza: salvare il valore **[!UICONTROL Random]** nella colonna **[!UICONTROL Profile to use]** per utilizzare i dati di qualsiasi profilo della destinazione nella bozza.

   ![](assets/s_ncs_user_wizard_email_bat_substitute_choose.png)

1. Fare clic sull&#39;icona **[!UICONTROL Detail]** per selezionare un profilo dalla destinazione principale, come nell&#39;esempio seguente:

   ![](assets/s_ncs_user_wizard_email_bat_substitute_select.png)

   È possibile definire tutti gli indirizzi di sostituzione necessari.

## Utilizza indirizzi seed come bozza {#using-seed-addresses-as-proof}

È possibile utilizzare **[!UICONTROL Seed addresses]** come destinazione delle bozze: questa opzione consente di utilizzare o importare un elenco di indirizzi di seed esistenti.

![](assets/s_ncs_user_wizard_email_bat_control_address.png)

>[!NOTE]
>
>Gli indirizzi seed vengono presentati in [Informazioni sugli indirizzi seed](about-seed-addresses.md).

È possibile combinare la definizione di una destinazione di bozza specifica e l&#39;utilizzo degli indirizzi di seed utilizzando l&#39;opzione **[!UICONTROL Specific target and Seed addresses]**. Le configurazioni correlate vengono quindi definite in due schede secondarie separate.

Vedi anche:

* [Seleziona la destinazione della bozza](#selecting-the-proof-target)
* [Informazioni sugli indirizzi seed](about-seed-addresses.md)
* [Caso d’uso: selezionare gli indirizzi seed in base ai criteri](use-case-selecting-seed-addresses-on-criteria.md)

## Selezionare una mappatura di destinazione {#select-a-target-mapping}

Per impostazione predefinita, i modelli di consegna sono destinati a **[!UICONTROL Recipients]**. La mappatura di destinazione utilizza pertanto i campi della tabella **nms:recipient**. Adobe Campaign offre altre mappature di destinazione per le consegne, da utilizzare in base alle tue esigenze.

![](assets/delivery_select_mapping.png)

Queste mappature sono le seguenti:

| Nome | Utilizzare | Schema standard |
|---|---|---|
| Destinatari | Consegna ai destinatari del database di Adobe Campaign | nms:recipient |
| Visitatori | Distribuisci ai visitatori i cui profili sono stati raccolti tramite riferimento (marketing virale) o tramite social network (Facebook, X, precedentemente noto come Twitter), ad esempio. | mns:visitor |
| Abbonamenti | Consegnare ai destinatari abbonati o iscritti a un servizio informativo, ad esempio una newsletter | nms:subscription |
| Abbonamenti visitatore | Consegnare ai visitatori abbonati o iscritti a un servizio informativo | nms:visitorSub |
| Servizio | Publish a un account X o a una pagina Facebook | nms:service |
| Operatori | Consegnare agli operatori Adobe Campaign | nms:operator |
| File esterno | Consegnare tramite un file contenente tutte le informazioni necessarie per la consegna | Nessuno schema collegato, nessuna destinazione immessa |


## Video tutorial {#seeds-and-proofs-video}

Questo video illustra come aggiungere seed e bozze a un’e-mail esistente e come inviarla.

>[!VIDEO](https://video.tv.adobe.com/v/25606?quality=12)

Sono disponibili altri video dimostrativi di Campaign Classic [qui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=it).
