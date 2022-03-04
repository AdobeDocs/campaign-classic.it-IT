---
product: campaign
title: '"Caso d’uso: selezionare gli indirizzi seed in base ai criteri"'
description: '"Caso d’uso: selezionare gli indirizzi seed in base ai criteri"'
feature: Seed Address
exl-id: 091648b8-bf2d-4595-8be3-287f1ac48edd
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '837'
ht-degree: 3%

---

# Caso d’uso: selezionare gli indirizzi seed in base ai criteri{#use-case-selecting-seed-addresses-on-criteria}

![](../../assets/common.svg)

Nel quadro di una consegna o di una campagna, la **[!UICONTROL Edit the dynamic condition...]** link ti consente di scegliere gli indirizzi di seed in base a criteri di selezione specifici.

In questo caso d’uso, il sito **Raccolta online personale** Vorrei personalizzare le sue newsletter in base ai gusti letterari dei suoi clienti.

In collaborazione con il reparto acquisti, l&#39;utente responsabile delle consegne ha creato una newsletter per gli abbonati che hanno acquistato i romanzi della polizia.

Per condividere il risultato finale della loro collaborazione con loro, il responsabile della consegna decide di aggiungere i propri colleghi del reparto acquisti alla consegna come indirizzi di seed. L’utilizzo di una condizione dinamica consente di risparmiare tempo sulla configurazione e l’aggiornamento degli indirizzi.

Per utilizzare la condizione dinamica, è necessario disporre di:

* una consegna pronta per essere inviata,
* indirizzi di seed con un valore comune. Questo valore può essere un campo già esistente in Adobe Campaign. In questo esempio, gli indirizzi di seed condividono il valore &quot;Purchasing&quot; nel campo &quot;Department&quot;, che per impostazione predefinita non è presente nell’applicazione.

## Passaggio 1: creare una consegna {#step-1---creating-a-delivery}

I passaggi per la creazione di una consegna sono descritti in [Creare una consegna e-mail](creating-an-email-delivery.md) sezione .

In questo esempio, il gestore consegne ha creato la newsletter e selezionato i destinatari.

![](assets/dlv_seeds_usecase_01.png)

## Passaggio 2: creare un valore comune {#step-2---creating-a-common-value}

Per creare un valore comune come quello nel nostro esempio (reparto Acquisti), devi prima estendere il **schema dati** degli indirizzi di seed e modifica il modulo di input associato.

### Estendere lo schema dati {#extending-the-data-schema}

Per ulteriori dettagli sulle estensioni dello schema, consulta [questa sezione](../../configuration/using/data-schemas.md).

1. In **[!UICONTROL Administration > Configuration > Data schemas]** fai clic sul **[!UICONTROL New]** icona.
1. In **[!UICONTROL Creation of a data schema]** seleziona la finestra **[!UICONTROL Extension of a schema]** e fai clic su **[!UICONTROL Next]**.

   ![](assets/dlv_seeds_usecase_09.png)

1. Seleziona la **[!UICONTROL Seed addresses]** schema di origine, immettere **doc** come **[!UICONTROL Namespace]** e fai clic su **[!UICONTROL Ok]**.

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

   In questo caso, stai specificando che una nuova enumerazione denominata **[!UICONTROL Department]** è stato creato nella tabella degli indirizzi di seed e si basa sullo standard **[!UICONTROL @company]** modello di enumerazione (etichettato sotto il nome **Azienda** nel modulo dell&#39;indirizzo di seed).

1. Fai clic su **[!UICONTROL Save]**.
1. In **[!UICONTROL Tools > Advanced]** seleziona il menu **[!UICONTROL Update database structure]** opzione .

   ![](assets/dlv_seeds_usecase_12.png)

1. Quando viene visualizzata la procedura guidata di aggiornamento, fai clic sul pulsante **[!UICONTROL Next]** per accedere alla finestra Modifica tabelle: le modifiche eseguite nello schema dei dati dell’indirizzo di seed richiedono un aggiornamento della struttura.

   ![](assets/dlv_seeds_usecase_13.png)

1. Per eseguire l’aggiornamento, segui la procedura guidata fino alla pagina . Fai clic sul pulsante **[!UICONTROL Start]**.

   ![](assets/dlv_seeds_usecase_14.png)

   Al termine dell’aggiornamento, puoi chiudere la procedura guidata.

1. Disconnettiti e riconnettiti ad Adobe Campaign. Le modifiche apportate nello schema dei dati dell’indirizzo di seed ora sono effettive. Affinché siano visibili dalla schermata degli indirizzi di seed, è necessario aggiornare i **[!UICONTROL Input form]**. Fai riferimento a [Aggiornare il modulo di input](#updating-the-input-form) sezione .

#### Estendere lo schema dati da una tabella collegata {#extending-the-data-schema-from-a-linked-table}

Lo schema di dati degli indirizzi di seed può utilizzare valori provenienti da una tabella collegata allo schema di dati dei destinatari: Recipient (nms).

Ad esempio, l’utente desidera integrare il **[!UICONTROL Internet Extension]** trovato nella **[!UICONTROL Country]** tabella collegata allo schema dei destinatari.

![](assets/dlv_seeds_usecase_06.png)

Devono pertanto estendere lo schema dei dati degli indirizzi di seed come descritto nella sezione . Tuttavia, le righe di codice da integrare in **passo 4** sono i seguenti:

```
<element name="country">
      <attribute label="Internet Extension" length="2" name="iana" type="string"/>
      <attribute label="Country ISO" length="2" name="countryIsoA2" type="string"/>
    </element>
```

![](assets/dlv_seeds_usecase_11.png)

Essi indicano:

* che l’utente desideri creare un nuovo elemento denominato **[!UICONTROL Internet Extension]**,
* che questo elemento proviene dal **[!UICONTROL Country]** tabella.

>[!CAUTION]
>
>Nel nome della tabella collegata è necessario specificare il **xpath-dst** di detta tabella collegata.
>
>Questa è disponibile nella sezione **[!UICONTROL Country]** nella tabella dei destinatari.

![](assets/dlv_seeds_usecase_07.png)

L&#39;utente può quindi seguire **passaggio 5** della sezione e aggiorna il **[!UICONTROL Input form]** degli indirizzi di seed.

Fai riferimento a [Aggiornare il modulo di input](#updating-the-input-form) sezione .

#### Aggiornare il modulo di input {#updating-the-input-form}

1. In **[!UICONTROL Administration > Configuration > Input forms]** nodo, trova il modulo di input degli indirizzi di seed.

   ![](assets/dlv_seeds_usecase_19.png)

1. Modificare il modulo e inserire la riga seguente nel **[!UICONTROL Recipient]** contenitore.

   ```
   <input xpath="@workField"/>
   ```

   ![](assets/dlv_seeds_usecase_21.png)

1. Salva le modifiche.
1. Apri un indirizzo di seed. La **[!UICONTROL Department]** viene visualizzato nel campo **[!UICONTROL Recipient]** tabella.

   ![](assets/dlv_seeds_usecase_22.png)

1. Modifica gli indirizzi di seed che desideri utilizzare per la consegna e immetti **Acquisti** come valore nel **[!UICONTROL Department]** campo .

## Passaggio 3: definire la condizione {#step-3---defining-the-condition}

Ora puoi specificare la condizione dinamica degli indirizzi di seed per la consegna. Per eseguire questa operazione:

1. Apri una consegna.

   ![](assets/dlv_seeds_usecase_01.png)

1. Fai clic sul pulsante **[!UICONTROL To]** il link **[!UICONTROL Seed addresses]** per accedere alla scheda **[!UICONTROL Edit the dynamic condition...]** link.

   ![](assets/dlv_seeds_usecase_02.png)

1. Seleziona l’espressione che ti consente di scegliere gli indirizzi di seed desiderati. Qui l&#39;utente seleziona il **[!UICONTROL Department (@workField)]** espressione.

   ![](assets/dlv_seeds_usecase_03.png)

1. Seleziona il valore desiderato. In questo esempio, l&#39;utente seleziona il **Acquisti** dall&#39;elenco a discesa dei valori.

   ![](assets/dlv_seeds_usecase_17.png)

   >[!NOTE]
   >
   >L&#39;estensione dello schema creata in precedenza proviene dal **destinatario** schema. I valori visualizzati nella schermata precedente provengono da un&#39;enumerazione del **destinatario** schema.

1. Fai clic su **[!UICONTROL Ok]**.

   La query viene visualizzata nella **[!UICONTROL Select target]** finestra.

   ![](assets/dlv_seeds_usecase_04.png)

1. Fai clic su **[!UICONTROL Ok]** per approvare la query.
1. Analizza la consegna, quindi fai clic sul pulsante **[!UICONTROL Delivery]** per accedere ai registri di consegna.

   Gli indirizzi di seed del reparto acquisti vengono visualizzati come consegna in sospeso, proprio come quelli dei destinatari o di altri indirizzi di seed.

   ![](assets/dlv_seeds_usecase_05.png)

1. Fai clic sul pulsante **[!UICONTROL Send]** per avviare la consegna.

   I membri del reparto acquisti fanno parte degli indirizzi di seed che riceveranno la consegna nella loro casella in entrata e-mail.

   ![](assets/dlv_seeds_usecase_18.png)
