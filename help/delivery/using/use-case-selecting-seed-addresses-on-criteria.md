---
product: campaign
title: "Caso d’uso: selezionare gli indirizzi seed in base ai criteri"
description: "Caso d’uso: selezionare gli indirizzi seed in base ai criteri"
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Seed Address
exl-id: 091648b8-bf2d-4595-8be3-287f1ac48edd
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '851'
ht-degree: 2%

---

# Caso d’uso: selezionare gli indirizzi seed in base ai criteri{#use-case-selecting-seed-addresses-on-criteria}


Nel quadro di una consegna o di una campagna, l’ **[!UICONTROL Edit the dynamic condition...]** consente di scegliere gli indirizzi seed in base a criteri di selezione specifici.

In questo caso d’uso, il sito **La mia libreria online** desidera personalizzare le newsletter in base ai gusti letterari dei clienti.

In collaborazione con il reparto acquisti, l’utente responsabile delle consegne ha creato una newsletter per gli abbonati che hanno acquistato romanzi della polizia.

Per condividere il risultato finale della loro collaborazione con loro, il responsabile della consegna decide di aggiungere i colleghi del reparto acquisti alla consegna come indirizzi seed. L’utilizzo di una condizione dinamica consente di risparmiare tempo nella configurazione e nell’aggiornamento degli indirizzi.

Per utilizzare la condizione dinamica, è necessario disporre di:

* una consegna pronta per essere inviata,
* indirizzi seed con un valore comune. Questo valore può essere un campo già esistente in Adobe Campaign. In questo esempio, gli indirizzi seed condividono il valore &quot;Purchasing&quot; nel campo &quot;Department&quot;, che non è presente nell’applicazione per impostazione predefinita.

## Passaggio 1: creare una consegna {#step-1---creating-a-delivery}

I passaggi per creare una consegna sono descritti in [Creare una consegna e-mail](creating-an-email-delivery.md) sezione.

In questo esempio, il responsabile della consegna ha creato la newsletter e selezionato i destinatari.

![](assets/dlv_seeds_usecase_01.png)

## Passaggio 2: creare un valore comune {#step-2---creating-a-common-value}

Per creare un valore comune come quello del nostro esempio (reparto Acquisti), devi prima estendere il **schema dati** degli indirizzi seed e modifica il relativo modulo di input.

### Estendere lo schema dati {#extending-the-data-schema}

Per ulteriori dettagli sulle estensioni dello schema, consulta [questa sezione](../../configuration/using/data-schemas.md).

1. In **[!UICONTROL Administration > Configuration > Data schemas]** , fare clic sul pulsante **[!UICONTROL New]** icona.
1. In **[!UICONTROL Creation of a data schema]** , selezionare la **[!UICONTROL Extension of a schema]** e fai clic su **[!UICONTROL Next]**.

   ![](assets/dlv_seeds_usecase_09.png)

1. Seleziona la **[!UICONTROL Seed addresses]** schema di origine, immetti **doc** come **[!UICONTROL Namespace]** e fai clic su **[!UICONTROL Ok]**.

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

   Quindi copia le seguenti righe e incollale sotto il **[!UICONTROL Seed to insert in the export files]** elemento.

   ```
       <element aggregate="doc:seedMember:common">
     </element>
   ```

   ![](assets/dlv_seeds_usecase_29.png)

   In questo caso, si sta specificando che una nuova enumerazione denominata **[!UICONTROL Department]** è stato creato nella tabella degli indirizzi di seed e si basa sullo standard **[!UICONTROL @company]** modello di enumerazione (con etichetta sotto il nome **Azienda** nel modulo indirizzo seed).

1. Fai clic su **[!UICONTROL Save]**.
1. In **[!UICONTROL Tools > Advanced]** , selezionare il **[!UICONTROL Update database structure]** opzione.

   ![](assets/dlv_seeds_usecase_12.png)

1. Quando viene visualizzata la procedura guidata di aggiornamento, fare clic su **[!UICONTROL Next]** per accedere alla finestra Modifica tabelle: le modifiche eseguite nello schema dei dati dell’indirizzo seed richiedono un aggiornamento della struttura.

   ![](assets/dlv_seeds_usecase_13.png)

1. Segui la procedura guidata fino a visualizzare la pagina per eseguire l’aggiornamento. Fai clic sul pulsante **[!UICONTROL Start]**.

   ![](assets/dlv_seeds_usecase_14.png)

   Al termine dell’aggiornamento, puoi chiudere la procedura guidata.

1. Disconnettiti e riconnettiti ad Adobe Campaign. Le modifiche apportate nello schema dei dati dell’indirizzo di seed ora vengono applicate. Affinché siano visibili dalla schermata dell’indirizzo di seed, devi aggiornare il associato **[!UICONTROL Input form]**. Consulta la sezione [Aggiornare il modulo di input](#updating-the-input-form) sezione.

#### Estendere lo schema dati da una tabella collegata {#extending-the-data-schema-from-a-linked-table}

Lo schema dati degli indirizzi seed può utilizzare valori provenienti da una tabella collegata allo schema dati del destinatario - Destinatario (nms).

Ad esempio, l’utente desidera integrare il **[!UICONTROL Internet Extension]** trovato in **[!UICONTROL Country]** tabella collegata allo schema dei destinatari.

![](assets/dlv_seeds_usecase_06.png)

Pertanto, devono estendere lo schema dati degli indirizzi seed come descritto nella sezione. Tuttavia, le righe di codice da integrare **passaggio 4** sono i seguenti:

```
<element name="country">
      <attribute label="Internet Extension" length="2" name="iana" type="string"/>
      <attribute label="Country ISO" length="2" name="countryIsoA2" type="string"/>
    </element>
```

![](assets/dlv_seeds_usecase_11.png)

Essi indicano:

* che l’utente desideri creare un nuovo elemento denominato **[!UICONTROL Internet Extension]**,
* che questo elemento proviene da **[!UICONTROL Country]** tabella.

>[!CAUTION]
>
>Nel nome della tabella collegata è necessario specificare **xpath-dst** di tale tabella collegata.
>
>Questo è disponibile nella sezione **[!UICONTROL Country]** nella tabella dei destinatari.

![](assets/dlv_seeds_usecase_07.png)

L’utente può quindi seguire da **passaggio 5** della sezione e aggiorna il **[!UICONTROL Input form]** degli indirizzi di seed.

Consulta la sezione [Aggiornare il modulo di input](#updating-the-input-form) sezione.

#### Aggiornare il modulo di input {#updating-the-input-form}

1. In **[!UICONTROL Administration > Configuration > Input forms]** trova il modulo di input degli indirizzi di seed.

   ![](assets/dlv_seeds_usecase_19.png)

1. Modifica il modulo e inserisci la seguente riga nel **[!UICONTROL Recipient]** contenitore.

   ```
   <input xpath="@workField"/>
   ```

   ![](assets/dlv_seeds_usecase_21.png)

1. Salva le modifiche.
1. Apri un indirizzo di seed. Il **[!UICONTROL Department]** viene visualizzato nel **[!UICONTROL Recipient]** tabella.

   ![](assets/dlv_seeds_usecase_22.png)

1. Modifica gli indirizzi di seed che desideri utilizzare per la consegna e immetti **Acquisti** come valore nella **[!UICONTROL Department]** campo.

## Passaggio 3: definire la condizione {#step-3---defining-the-condition}

Ora puoi specificare la condizione dinamica degli indirizzi di seed per la consegna. Per eseguire questa operazione:

1. Apri una consegna.

   ![](assets/dlv_seeds_usecase_01.png)

1. Fai clic su **[!UICONTROL To]** quindi collega **[!UICONTROL Seed addresses]** per accedere alla scheda **[!UICONTROL Edit the dynamic condition...]** collegamento.

   ![](assets/dlv_seeds_usecase_02.png)

1. Selezionare l&#39;espressione che consente di scegliere gli indirizzi di seed desiderati. In questo punto l’utente seleziona il **[!UICONTROL Department (@workField)]** espressione.

   ![](assets/dlv_seeds_usecase_03.png)

1. Seleziona il valore desiderato. In questo esempio l’utente seleziona il **Acquisti** reparto dall&#39;elenco a discesa dei valori.

   ![](assets/dlv_seeds_usecase_17.png)

   >[!NOTE]
   >
   >L&#39;estensione dello schema creata in precedenza proviene da **destinatario** schema. I valori visualizzati nella schermata precedente derivano da un’enumerazione del **destinatario** schema.

1. Fai clic su **[!UICONTROL Ok]**.

   La query viene visualizzata in **[!UICONTROL Select target]** finestra.

   ![](assets/dlv_seeds_usecase_04.png)

1. Clic **[!UICONTROL Ok]** per approvare la query.
1. Analizza la consegna, quindi fai clic sul pulsante **[!UICONTROL Delivery]** per accedere ai registri di consegna.

   Gli indirizzi seed del reparto acquisti vengono visualizzati come consegna in sospeso, proprio come quelli dei destinatari o altri indirizzi seed.

   ![](assets/dlv_seeds_usecase_05.png)

1. Fai clic su **[!UICONTROL Send]** per avviare la consegna.

   I membri del reparto acquisti compongono una parte degli indirizzi seed che riceveranno la consegna nella loro casella di posta elettronica.

   ![](assets/dlv_seeds_usecase_18.png)
