---
product: campaign
title: Coupon personalizzati
description: Scopri come creare e inserire coupon personalizzati
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Personalization
role: User
hide: true
hidefromtoc: true
exl-id: 182939bb-7aff-4667-bda9-c5d48be3b946
source-git-commit: 0507e0372a81351adc145dafdd3cbe5d5422dc00
workflow-type: tm+mt
source-wordcount: '910'
ht-degree: 1%

---

# Coupon personalizzati{#personalized-coupons}

L’aggiunta di coupon alle consegne può fornire ai destinatari un valore aggiunto per prodotti e servizi. Puoi utilizzare il modulo coupon di Campaign per creare un set di coupon da aggiungere alle prossime offerte di marketing. Quando sei pronto a creare una consegna, assegna i coupon applicabili. Poiché i coupon sono validi per un periodo selezionato, un coupon assegnato è collegato in modo univoco al relativo messaggio di consegna. Inoltre, Campaign conferma che sono presenti coupon sufficienti per il numero di messaggi prima dell’invio della consegna.

>[!AVAILABILITY]
>
>La gestione dei coupon non è disponibile in Campaign v8 nel contesto di una distribuzione Enterprise (FFDA). Ulteriori informazioni sono disponibili nella [documentazione di Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/config/architecture/ffda/enterprise-deployment){target="_blank"}.

La gestione dei coupon si basa su un pacchetto che deve essere installato. Per confermare che hai la gestione del coupon, seleziona **[!UICONTROL Administration > Configuration > Package management > Installed packages.]**

I dati del coupon possono essere importati ed esportati utilizzando i formati CSV e XML. [Ulteriori informazioni](../../platform/using/get-started-data-import-export.md).

## Crea un coupon {#creating-a-coupon}

Il modulo Gestione coupon offre due opzioni per la creazione di coupon:

* **Anonimo**: coupon generico per destinatari selezionati o elenchi di destinatari.
* **Singolo**: un coupon personalizzato per alcuni destinatari.

Prima di seguire i passaggi seguenti, assicurati di conoscere il tipo di coupon che desideri creare.

1. Nella struttura Campaign, vai a **[!UICONTROL Resources > Campaign management > Coupons]**.

   ![](assets/deliv_coup_01.png)

1. Fai clic sul pulsante **[!UICONTROL New]**.
1. Immettere il nome del coupon nel campo **[!UICONTROL Label]**. Un codice univoco è stato immesso automaticamente in **[!UICONTROL Coupon code]**. Puoi conservare il codice o immetterne uno nuovo.

   ![](assets/deliv_coup_02.png)

1. Scegliere **[!UICONTROL Start date]** e **[!UICONTROL End date]** per impostare il periodo di validità del coupon.
1. In **[!UICONTROL Coupon type]**, scegliere Anonimo o Individuale.

   **[!UICONTROL Anonymous coupons]**: un coupon anonimo è identico per tutti i destinatari. Conferma che Anonimo è selezionato nel menu **Tipo coupon** e fai clic su **Salva** per generare il coupon.

   **[!UICONTROL Individual coupons]** : un singolo coupon può essere ulteriormente personalizzato con codici coupon aggiuntivi. Ad esempio, viene creato un singolo coupon per la vendita in un negozio di attrezzatura sportiva. Tuttavia, la lista dei destinatari è lunga e non condividono lo stesso entusiasmo per un singolo sport. Puoi aggiungere nomi in codice per il singolo coupon in base a uno sport (ad esempio, calcio, calcio, baseball ecc.) e inviare ciascun codice ai destinatari applicabili.

   1. Quando si sceglie Individuale, in basso a sinistra viene visualizzata una nuova scheda, Coupon. Passare alla scheda **[!UICONTROL Coupons]** e fare clic su **[!UICONTROL Add]**.
   1. Inserire un codice univoco per il singolo coupon quando richiesto dalla finestra popup.
   1. Fare clic su **[!UICONTROL Save]** per generare il coupon.

   Per ulteriori dettagli sulla scheda Coupon, consulta [Configurare i singoli coupon](#configuring-individual-coupons).

   >[!NOTE]
   >
   >I singoli coupon possono essere importati in blocco. Per informazioni dettagliate sull&#39;importazione e l&#39;esportazione, consultare [questa sezione](../../platform/using/get-started-data-import-export.md).

### Configurare singoli coupon {#configuring-individual-coupons}

![](assets/deliv_coup_03.png)

La scheda Coupon è disponibile solo con i singoli coupon. Dopo aver associato un coupon a una consegna, la scheda Coupon fornisce i seguenti dettagli:

* **[!UICONTROL Status]**: disponibilità coupon.
* **[!UICONTROL Redeemed on]**: data di riscatto del coupon.
* **[!UICONTROL Channel]** : canale utilizzato per inviare il coupon.
* **[!UICONTROL Address]** : indirizzi e-mail dei destinatari.

I valori per **[!UICONTROL status]**, **[!UICONTROL channel]** e **[!UICONTROL address]** vengono completati automaticamente. Tuttavia, i valori per **[!UICONTROL redeemed on]** non vengono recuperati da Campaign. Possono essere completati importando un file con i dettagli per il rimborso del coupon.

## Inserire un coupon in una consegna e-mail {#inserting-a-coupon-into-an-email-delivery}

Nell’esempio seguente, la consegna viene creata dalla pagina Home. Per istruzioni dettagliate su come creare una consegna, consulta [questa sezione](about-email-channel.md). Puoi anche aggiungere un coupon a una consegna in un flusso di lavoro.

1. Vai a **[!UICONTROL Campaigns]** e scegli **[!UICONTROL Deliveries]**.
1. Fai clic su **[!UICONTROL Create]**.

   ![](assets/deliv_coup_04.png)

1. Immettere un nome in **[!UICONTROL Label]** e fare clic su **[!UICONTROL Continue]**.
1. Fare clic su **[!UICONTROL To]** per aggiungere i destinatari.
1. Fare clic su **[!UICONTROL Add]** per scegliere i destinatari per la consegna. Dopo aver selezionato i destinatari, fare clic su **[!UICONTROL Ok]** per tornare alla consegna.

   ![](assets/deliv_coup_05.png)

1. Inserisci un oggetto e aggiungi il contenuto al messaggio.

   ![](assets/deliv_coup_06.png)

1. Nella barra degli strumenti fare clic su **[!UICONTROL Properties]** e scegliere la scheda **[!UICONTROL Advanced]**.
1. Fare clic sull&#39;icona della cartella per **[!UICONTROL Coupon management]**.

   ![](assets/deliv_coup_07.png)

1. Scegliere il coupon e fare clic su **[!UICONTROL Ok]**. Fare di nuovo clic su **[!UICONTROL Ok]**.

   ![](assets/deliv_coup_08.png)

1. Fai clic sul messaggio per scegliere dove posizionare il coupon.

   ![](assets/deliv_coup_09.png)

1. Fai clic sull’icona di personalizzazione per scegliere una delle seguenti opzioni in base al tipo di coupon:

   * Coupon anonimo: **[!UICONTROL Coupon > Coupon code]**

     ![](assets/deliv_coup_10.png)

   * Singolo coupon: **[!UICONTROL Coupon value > Coupon code]**

     ![](assets/deliv_coup_11.png)

     Il coupon viene inserito nel messaggio come codice anziché come nome assegnato. Il codice viene utilizzato all’interno del modello dati di Campaign ootb.

   ![](assets/deliv_coup_12.png)

1. Esegui un test per confermare il nome assegnato al coupon. Passare alla scheda **[!UICONTROL Preview]** e fare clic su **[!UICONTROL Test personalization]**. Scegli un destinatario per il test.

   ![](assets/deliv_coup_13.png)

   Dopo il test, il coupon deve essere visualizzato come nome assegnato anziché come codice.

   ![](assets/deliv_coup_14.png)

1. Nella barra degli strumenti, fai clic su **[!UICONTROL Send]** (in alto a sinistra) e scegli come desideri inviare la consegna.

   ![](assets/deliv_coup_15.png)

1. Fai clic su **[!UICONTROL Analyze]**. Se il log di analisi conferma che sono presenti coupon sufficienti per tutti i destinatari, fare clic su **[!UICONTROL Confirm delivery]** per inviarlo.

   ![](assets/deliv_coup_16.png)

>[!NOTE]
>
>Per istruzioni su come gestire coupon insufficienti per una consegna, vedere [Gestire coupon insufficienti](#managing-insufficient-coupons)

Per confermare che la consegna è avvenuta correttamente:

1. Vai a **[!UICONTROL Explorer > Resources > Campaign management > Coupons]**.
1. Fare clic sulla scheda **[!UICONTROL Deliveries]**.

   ![](assets/deliv_coup_17.png)

   Lo stato è **[!UICONTROL Finished]** per una consegna riuscita.

>[!NOTE]
>
>Per impostazione predefinita, il modulo di gestione dei coupon utilizza una tabella **nms:recipient**. [Ulteriori informazioni](../../configuration/using/about-data-model.md#default-recipient-table).
>
>Scopri come utilizzare una tabella dei destinatari personalizzata [in questa pagina](../../configuration/using/about-custom-recipient-table.md).

## Gestisci coupon insufficienti {#managing-insufficient-coupons}

L’analisi della consegna si interrompe se il numero di coupon è inferiore a quello dei messaggi. In questo caso, puoi importare più coupon o limitare il numero di messaggi. Per limitare il numero di messaggi, segui le istruzioni riportate di seguito.

1. Vai alla finestra di consegna e-mail.
1. Fai clic su **[!UICONTROL To]**.
1. In **[!UICONTROL Select target]**, passare alla scheda **[!UICONTROL Exclusions]**.

   ![](assets/deliv_coup_18.png)

1. Nella sezione delle impostazioni di esclusione, fare clic su **[!UICONTROL Edit]**.
1. Immettere il numero di messaggi da inviare in **[!UICONTROL Limit delivery to...messages]** e fare clic su **[!UICONTROL Ok]**. Puoi inviare la consegna.

   ![](assets/deliv_coup_19.png)

>[!NOTE]
>
>Quando gestisci un numero limitato di coupon, un flusso di lavoro di consegna ti consente di suddividere la consegna in base ai criteri. È una buona opzione se desideri inviare coupon a una popolazione selezionata senza limitare il target.
