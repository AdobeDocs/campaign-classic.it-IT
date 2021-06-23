---
product: campaign
title: '"Caso di utilizzo: selezione degli indirizzi di seed in base ai criteri"'
description: '"Caso di utilizzo: selezione degli indirizzi di seed in base ai criteri"'
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
exl-id: 091648b8-bf2d-4595-8be3-287f1ac48edd
source-git-commit: a129f49d4f045433899fd7fdbd057fb16d0ed36a
workflow-type: tm+mt
source-wordcount: '838'
ht-degree: 3%

---

# Caso di utilizzo: selezione degli indirizzi di seed in base ai criteri{#use-case-selecting-seed-addresses-on-criteria}

Nel framework di una consegna o di una campagna, il collegamento **[!UICONTROL Edit the dynamic condition...]** ti consente di scegliere gli indirizzi di seed in base a criteri di selezione specifici.

In questo caso d&#39;uso, il sito **La mia libreria online** vorrebbe personalizzare le sue newsletter in base ai gusti letterari dei suoi clienti.

In collaborazione con il reparto acquisti, l&#39;utente responsabile delle consegne ha creato una newsletter per gli abbonati che hanno acquistato i romanzi della polizia.

Per condividere il risultato finale della loro collaborazione con loro, il responsabile della consegna decide di aggiungere i suoi colleghi del reparto acquisti alla consegna come indirizzi di seed. L’utilizzo di una condizione dinamica consente di risparmiare tempo sulla configurazione e l’aggiornamento degli indirizzi.

Per utilizzare la condizione dinamica, è necessario disporre di:

* una consegna pronta per essere inviata,
* indirizzi di seed con un valore comune. Questo valore può essere un campo già esistente in Adobe Campaign. In questo esempio, gli indirizzi di seed condividono il valore &quot;Purchasing&quot; nel campo &quot;Department&quot;, che per impostazione predefinita non è presente nell’applicazione.

## Passaggio 1 - Creazione di una consegna {#step-1---creating-a-delivery}

I passaggi per la creazione di una consegna sono descritti in dettaglio nella sezione [Creazione di una consegna e-mail](creating-an-email-delivery.md) .

In questo esempio, il gestore consegne ha creato la newsletter e selezionato i destinatari.

![](assets/dlv_seeds_usecase_01.png)

## Passaggio 2 - Creazione di un valore comune {#step-2---creating-a-common-value}

Per creare un valore comune come quello nel nostro esempio (reparto Acquisti), devi innanzitutto estendere lo **schema dati** degli indirizzi di seed e modificare il modulo di input associato.

### Estensione dello schema dati {#extending-the-data-schema}

Per ulteriori dettagli sulle estensioni dello schema, consulta la [Guida alla configurazione](../../configuration/using/data-schemas.md).

1. Nel nodo **[!UICONTROL Administration > Configuration > Data schemas]**, fai clic sull&#39;icona **[!UICONTROL New]**.
1. Nella finestra **[!UICONTROL Creation of a data schema]**, seleziona l’opzione **[!UICONTROL Extension of a schema]** e fai clic su **[!UICONTROL Next]**.

   ![](assets/dlv_seeds_usecase_09.png)

1. Seleziona lo schema di origine **[!UICONTROL Seed addresses]**, immetti **doc** come **[!UICONTROL Namespace]** e fai clic su **[!UICONTROL Ok]**.

   ![](assets/dlv_seeds_usecase_10.png)

1. Fai clic su **[!UICONTROL Save]**.
1. Nella finestra di modifica dello schema, copia le righe sottostanti e incollale nell’area indicata nella schermata.

   ```
     <element name="common">
       <element label="Recipient" name="custom_nms_recipient">
         <attribute label="Department" length="80" name="workField" template="nms:recipient:recipient/@company"
                    type="string" userEnum="workField"/>
       </element>
     </element>
   ```

   ![](assets/dlv_seeds_usecase_20.png)

   Quindi copia le seguenti righe e incollale sotto l’elemento **[!UICONTROL Seed to insert in the export files]** .

   ```
       <element aggregate="doc:seedMember:common">
     </element>
   ```

   ![](assets/dlv_seeds_usecase_29.png)

   In questo caso, stai specificando che una nuova enumerazione denominata **[!UICONTROL Department]** è stata creata nella tabella degli indirizzi di seed e si basa sul modello di enumerazione standard **[!UICONTROL @company]** (etichettato sotto il nome **Società** nel modulo degli indirizzi di seed).

1. Fai clic su **[!UICONTROL Save]**.
1. Nel menu **[!UICONTROL Tools > Advanced]** , seleziona l’opzione **[!UICONTROL Update database structure]** .

   ![](assets/dlv_seeds_usecase_12.png)

1. Quando viene visualizzata la procedura guidata di aggiornamento, fare clic sul pulsante **[!UICONTROL Next]** per accedere alla finestra Modifica tabelle: le modifiche eseguite nello schema dei dati dell’indirizzo di seed richiedono un aggiornamento della struttura.

   ![](assets/dlv_seeds_usecase_13.png)

1. Per eseguire l’aggiornamento, segui la procedura guidata fino alla pagina . Fai clic sul pulsante **[!UICONTROL Start]**.

   ![](assets/dlv_seeds_usecase_14.png)

   Al termine dell’aggiornamento, puoi chiudere la procedura guidata.

1. Disconnettiti e riconnettiti ad Adobe Campaign. Le modifiche apportate nello schema dei dati dell’indirizzo di seed ora sono effettive. Affinché siano visibili dalla schermata degli indirizzi di seed, è necessario aggiornare il **[!UICONTROL Input form]** associato. Consulta la sezione [Aggiornamento del modulo di input](#updating-the-input-form) .

#### Estensione dello schema dati da una tabella collegata {#extending-the-data-schema-from-a-linked-table}

Lo schema di dati degli indirizzi di seed può utilizzare valori provenienti da una tabella collegata allo schema di dati dei destinatari: Recipient (nms).

Ad esempio, l’utente desidera integrare il **[!UICONTROL Internet Extension]** trovato nella tabella **[!UICONTROL Country]** collegata allo schema dei destinatari.

![](assets/dlv_seeds_usecase_06.png)

Devono pertanto estendere lo schema dei dati degli indirizzi di seed come descritto nella sezione . Tuttavia, le righe di codice da integrare al **passaggio 4** sono le seguenti:

```
<element name="country">
      <attribute label="Internet Extension" length="2" name="iana" type="string"/>
      <attribute label="Country ISO" length="2" name="countryIsoA2" type="string"/>
    </element>
```

![](assets/dlv_seeds_usecase_11.png)

Essi indicano:

* che l’utente desideri creare un nuovo elemento denominato **[!UICONTROL Internet Extension]**,
* che questo elemento provenga dalla tabella **[!UICONTROL Country]**.

>[!CAUTION]
>
>Nel nome della tabella collegata è necessario specificare **xpath-dst** di tale tabella collegata.
>
>Questo si trova nell’elemento **[!UICONTROL Country]** nella tabella dei destinatari.

![](assets/dlv_seeds_usecase_07.png)

L’utente può quindi seguire il **passaggio 5** della sezione e aggiornare **[!UICONTROL Input form]** degli indirizzi di seed.

Consulta la sezione [Aggiornamento del modulo di input](#updating-the-input-form) .

#### Aggiornamento del modulo di input {#updating-the-input-form}

1. Nel nodo **[!UICONTROL Administration > Configuration > Input forms]**, trova il modulo di immissione degli indirizzi di seed.

   ![](assets/dlv_seeds_usecase_19.png)

1. Modifica il modulo e inserisci la riga seguente nel contenitore **[!UICONTROL Recipient]** .

   ```
   <input xpath="@workField"/>
   ```

   ![](assets/dlv_seeds_usecase_21.png)

1. Salva le modifiche.
1. Apri un indirizzo di seed. Il campo **[!UICONTROL Department]** viene visualizzato nella tabella **[!UICONTROL Recipient]**.

   ![](assets/dlv_seeds_usecase_22.png)

1. Modifica gli indirizzi di seed che desideri utilizzare per la consegna e immetti **Purchasing** come valore nel campo **[!UICONTROL Department]** .

## Passaggio 3 - Definizione della condizione {#step-3---defining-the-condition}

Ora puoi specificare la condizione dinamica degli indirizzi di seed per la consegna. Per eseguire questa operazione:

1. Apri una consegna.

   ![](assets/dlv_seeds_usecase_01.png)

1. Fai clic sul collegamento **[!UICONTROL To]** e quindi sulla scheda **[!UICONTROL Seed addresses]** per accedere al collegamento **[!UICONTROL Edit the dynamic condition...]**.

   ![](assets/dlv_seeds_usecase_02.png)

1. Seleziona l’espressione che ti consente di scegliere gli indirizzi di seed desiderati. Qui l&#39;utente seleziona l&#39;espressione **[!UICONTROL Department (@workField)]**.

   ![](assets/dlv_seeds_usecase_03.png)

1. Seleziona il valore desiderato. In questo esempio l&#39;utente seleziona il reparto **Purchasing** dall&#39;elenco a discesa dei valori.

   ![](assets/dlv_seeds_usecase_17.png)

   >[!NOTE]
   >
   >L&#39;estensione dello schema creata in precedenza proviene dallo schema **recipient** . I valori visualizzati nella schermata precedente provengono da un&#39;enumerazione dello schema **recipient** .

1. Fai clic su **[!UICONTROL Ok]**.

   La query viene visualizzata nella finestra **[!UICONTROL Select target]**.

   ![](assets/dlv_seeds_usecase_04.png)

1. Fai clic su **[!UICONTROL Ok]** per approvare la query.
1. Analizza la consegna, quindi fai clic sulla scheda **[!UICONTROL Delivery]** per accedere ai registri di consegna.

   Gli indirizzi di seed del reparto acquisti vengono visualizzati come consegna in sospeso, proprio come quelli dei destinatari o di altri indirizzi di seed.

   ![](assets/dlv_seeds_usecase_05.png)

1. Fai clic sul pulsante **[!UICONTROL Send]** per avviare la consegna.

   I membri del reparto acquisti fanno parte degli indirizzi di seed che riceveranno la consegna nella loro casella in entrata e-mail.

   ![](assets/dlv_seeds_usecase_18.png)
