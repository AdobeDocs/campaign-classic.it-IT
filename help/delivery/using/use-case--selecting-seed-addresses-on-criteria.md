---
solution: Campaign Classic
product: campaign
title: '"Caso di utilizzo: selezione degli indirizzi di seed in base ai criteri"'
description: '"Caso di utilizzo: selezione degli indirizzi di seed in base ai criteri"'
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '838'
ht-degree: 3%

---


# Caso di utilizzo: selezione degli indirizzi di seed in base ai criteri{#use-case-selecting-seed-addresses-on-criteria}

Nel quadro di una consegna o di una campagna, il **[!UICONTROL Edit the dynamic condition...]** collegamento consente di scegliere gli indirizzi iniziali in base a criteri di selezione specifici.

In questo caso d&#39;uso, il sito **My online library** vorrebbe personalizzare le sue newsletter in base ai gusti letterari dei suoi clienti.

Insieme al reparto acquisti, l&#39;utente responsabile delle consegne ha creato una newsletter per gli abbonati che hanno acquistato i romanzi della polizia.

Per condividere il risultato finale della loro collaborazione con loro, il responsabile consegna decide di aggiungere i suoi colleghi del reparto acquisti alla consegna come indirizzi di partenza. L&#39;utilizzo di una condizione dinamica consente di risparmiare tempo sulla configurazione e l&#39;aggiornamento degli indirizzi.

Per utilizzare la condizione dinamica, è necessario disporre di:

* una consegna pronta per essere inviata,
* indirizzi seed con un valore comune. Questo valore può essere un campo già esistente in  Adobe Campaign. In questo esempio, gli indirizzi iniziali condividono il valore &quot;Purchasing&quot; nel campo &quot;Dipartimento&quot;, che per impostazione predefinita non è presente nell&#39;applicazione.

## Passaggio 1 - Creazione di una consegna {#step-1---creating-a-delivery}

I passaggi per la creazione di una consegna sono descritti in dettaglio nella sezione [Creazione di una consegna](../../delivery/using/creating-an-email-delivery.md) e-mail.

In questo esempio, il manager consegna ha creato la newsletter e selezionato i destinatari.

![](assets/dlv_seeds_usecase_01.png)

## Passaggio 2 - Creazione di un valore comune {#step-2---creating-a-common-value}

Per creare un valore comune come quello nel nostro esempio (reparto Acquisti), è necessario innanzitutto estendere lo schema **** dati degli indirizzi iniziali e modificare il modulo di input associato.

### Estensione dello schema dati {#extending-the-data-schema}

Per ulteriori dettagli sulle estensioni dello schema, consultare la guida [alla](../../configuration/using/data-schemas.md)configurazione.

1. Nel **[!UICONTROL Administration > Configuration > Data schemas]** nodo fare clic sull&#39; **[!UICONTROL New]** icona.
1. Nella **[!UICONTROL Creation of a data schema]** finestra, selezionate l’ **[!UICONTROL Extension of a schema]** opzione e fate clic su **[!UICONTROL Next]**.

   ![](assets/dlv_seeds_usecase_09.png)

1. Selezionare lo schema di **[!UICONTROL Seed addresses]** origine, immettere **doc** come **[!UICONTROL Namespace]** e fare clic su **[!UICONTROL Ok]**.

   ![](assets/dlv_seeds_usecase_10.png)

1. Fai clic su **[!UICONTROL Save]**.
1. Nella finestra di modifica dello schema, copiare le righe sottostanti e incollarle nell&#39;area indicata nello screenshot.

   ```
     <element name="common">
       <element label="Recipient" name="custom_nms_recipient">
         <attribute label="Department" length="80" name="workField" template="nms:recipient:recipient/@company"
                    type="string" userEnum="workField"/>
       </element>
     </element>
   ```

   ![](assets/dlv_seeds_usecase_20.png)

   Copiate quindi le seguenti righe e incollatele sotto l’ **[!UICONTROL Seed to insert in the export files]** elemento .

   ```
       <element aggregate="doc:seedMember:common">
     </element>
   ```

   ![](assets/dlv_seeds_usecase_29.png)

   In questo caso, state specificando che una nuova enumerazione denominata **[!UICONTROL Department]** è stata creata nella tabella degli indirizzi iniziali, e si basa sul modello di **[!UICONTROL @company]** enumerazione standard (etichettata sotto il nome **Società** nel modulo dell&#39;indirizzo e-mail).

1. Fai clic su **[!UICONTROL Save]**.
1. In the **[!UICONTROL Tools > Advanced]** menu, select the **[!UICONTROL Update database structure]** option.

   ![](assets/dlv_seeds_usecase_12.png)

1. Quando viene visualizzata la procedura guidata di aggiornamento, fare clic sul **[!UICONTROL Next]** pulsante per accedere alla finestra Modifica tabelle: le modifiche effettuate nello schema di dati dell&#39;indirizzo di base richiedono un aggiornamento della struttura.

   ![](assets/dlv_seeds_usecase_13.png)

1. Seguite la procedura guidata fino a visualizzare la pagina per eseguire l&#39;aggiornamento. Fai clic sul pulsante **[!UICONTROL Start]**.

   ![](assets/dlv_seeds_usecase_14.png)

   Al termine dell&#39;aggiornamento, è possibile chiudere la procedura guidata.

1. Disconnettetevi quindi di nuovo a  Adobe Campaign. Le modifiche apportate nello schema di dati dell&#39;indirizzo di base ora sono effettive. Affinché siano visibili dalla schermata dell&#39;indirizzo di base, è necessario aggiornare il relativo **[!UICONTROL Input form]**. Fare riferimento alla sezione [Aggiornamento del modulo](#updating-the-input-form) di input.

#### Estensione dello schema di dati da una tabella collegata {#extending-the-data-schema-from-a-linked-table}

Lo schema di dati degli indirizzi iniziali può utilizzare valori provenienti da una tabella collegata allo schema di dati del destinatario - Recipient (nms).

Ad esempio, l&#39;utente desidera integrare il contenuto **[!UICONTROL Internet Extension]** trovato nella **[!UICONTROL Country]** tabella collegata allo schema destinatari.

![](assets/dlv_seeds_usecase_06.png)

Devono pertanto estendere lo schema di dati degli indirizzi iniziali come descritto nella sezione. Tuttavia, le righe di codice da integrare al **punto 4** sono le seguenti:

```
<element name="country">
      <attribute label="Internet Extension" length="2" name="iana" type="string"/>
      <attribute label="Country ISO" length="2" name="countryIsoA2" type="string"/>
    </element>
```

![](assets/dlv_seeds_usecase_11.png)

Esse indicano:

* che l&#39;utente desidera creare un nuovo elemento denominato **[!UICONTROL Internet Extension]**,
* che questo elemento proviene dalla **[!UICONTROL Country]** tabella.

>[!CAUTION]
>
>Nel nome della tabella collegata, è necessario specificare l&#39; **xpath-dst** di tale tabella collegata.
>
>Questo si trova nell&#39; **[!UICONTROL Country]** elemento nella tabella dei destinatari.

![](assets/dlv_seeds_usecase_07.png)

L&#39;utente può quindi seguire il **passaggio 5** della sezione e aggiornare gli indirizzi **[!UICONTROL Input form]** di base.

Fare riferimento alla sezione [Aggiornamento del modulo](#updating-the-input-form) di input.

#### Aggiornamento del modulo di input {#updating-the-input-form}

1. Nel **[!UICONTROL Administration > Configuration > Input forms]** nodo, individuare il modulo di immissione degli indirizzi iniziali.

   ![](assets/dlv_seeds_usecase_19.png)

1. Modificare il modulo e inserire la riga seguente nel **[!UICONTROL Recipient]** contenitore.

   ```
   <input xpath="@workField"/>
   ```

   ![](assets/dlv_seeds_usecase_21.png)

1. Salva le modifiche.
1. Aprite un indirizzo seed. Il **[!UICONTROL Department]** campo viene visualizzato nella **[!UICONTROL Recipient]** tabella.

   ![](assets/dlv_seeds_usecase_22.png)

1. Modificate gli indirizzi iniziali che desiderate utilizzare per la consegna e immettete **Purchasing** come valore nel **[!UICONTROL Department]** campo.

## Passaggio 3 - Definizione della condizione {#step-3---defining-the-condition}

È ora possibile specificare la condizione dinamica degli indirizzi iniziali per la consegna. Per eseguire questa operazione:

1. Aprite una consegna.

   ![](assets/dlv_seeds_usecase_01.png)

1. Fai clic sul **[!UICONTROL To]** collegamento, quindi sulla **[!UICONTROL Seed addresses]** scheda per accedere al **[!UICONTROL Edit the dynamic condition...]** collegamento.

   ![](assets/dlv_seeds_usecase_02.png)

1. Selezionare l&#39;espressione che consente di scegliere gli indirizzi iniziali desiderati. Qui l&#39;utente seleziona l&#39; **[!UICONTROL Department (@workField)]** espressione.

   ![](assets/dlv_seeds_usecase_03.png)

1. Selezionare il valore desiderato. In questo esempio l&#39;utente seleziona il reparto **Acquisti** dall&#39;elenco a discesa dei valori.

   ![](assets/dlv_seeds_usecase_17.png)

   >[!NOTE]
   >
   >L&#39;estensione dello schema creata in precedenza proviene dallo schema **destinatario** . I valori visualizzati sullo schermo sopra provengono da un&#39;enumerazione dello schema **destinatario** .

1. Fai clic su **[!UICONTROL Ok]**.

   La query viene visualizzata nella **[!UICONTROL Select target]** finestra.

   ![](assets/dlv_seeds_usecase_04.png)

1. Click **[!UICONTROL Ok]** to approve the query.
1. Analizza la consegna, quindi fai clic sulla **[!UICONTROL Delivery]** scheda per accedere ai log di consegna.

   Gli indirizzi iniziali del reparto acquisti vengono visualizzati come consegna in sospeso, come quelli dei destinatari o di altri indirizzi iniziali.

   ![](assets/dlv_seeds_usecase_05.png)

1. Click the **[!UICONTROL Send]** button to start the delivery.

   I membri del reparto acquisti fanno parte dei vostri indirizzi di base che riceveranno la consegna nella loro casella in entrata e-mail.

   ![](assets/dlv_seeds_usecase_18.png)
