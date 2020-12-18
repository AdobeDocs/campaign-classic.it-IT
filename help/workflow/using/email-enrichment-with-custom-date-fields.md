---
solution: Campaign Classic
product: campaign
title: Arricchimento delle e-mail con campi data personalizzati
description: Informazioni su come arricchire le e-mail con campi data personalizzati
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 3%

---


# Arricchimento delle e-mail con campi data personalizzati{#email-enrichment-with-custom-date-fields}

In questo esempio, desideriamo inviare un&#39;e-mail con campi di dati personalizzati ai destinatari che festeggeranno i compleanni di questo mese. L&#39;e-mail includerà un coupon valido una settimana prima e dopo i compleanni.

Dobbiamo indirizzare i destinatari da una lista che festeggerà i loro compleanni questo mese con un&#39;attività **[!UICONTROL Split]**. Quindi, utilizzando l&#39;attività **[!UICONTROL Enrichment]**, il campo dati personalizzato fungerà da date di validità nell&#39;e-mail per l&#39;offerta speciale del cliente.

![](assets/uc_enrichment.png)

Per creare questo esempio, procedere come segue:

1. Nella scheda **[!UICONTROL Targeting and workflows]** della campagna, trascina e rilascia un&#39;attività **[!UICONTROL Read list]** per eseguire il targeting dell&#39;elenco dei destinatari.
1. L&#39;elenco da elaborare può essere specificato esplicitamente, calcolato da uno script o localizzato dinamicamente, in base alle opzioni selezionate e ai parametri definiti qui.

   ![](assets/uc_enrichment_1.png)

1. Aggiungi un&#39;attività **[!UICONTROL Split]** per distinguere i destinatari che festeggeranno i loro compleanni questo mese dagli altri destinatari.
1. Per dividere l&#39;elenco, nella categoria **[!UICONTROL Filtering of selected records]** selezionare **[!UICONTROL Add a filtering condition on the inbound population]**. Quindi, fare clic su **[!UICONTROL Edit]**.

   ![](assets/uc_enrichment_2.png)

1. Selezionare **[!UICONTROL Filtering conditions]**, quindi fare clic sul pulsante **[!UICONTROL Edit expression]** per filtrare il mese del compleanno del destinatario.

   ![](assets/uc_enrichment_3.png)

1. Fare clic su **[!UICONTROL Advanced Selection]**, quindi **[!UICONTROL Edit the formula using an expression]** e aggiungere la seguente espressione: Mese(@nascitaDate).
1. Nella colonna **[!UICONTROL Operator]**, selezionare **[!UICONTROL equal to]**.
1. Filtra ulteriormente la condizione, aggiungendo il mese **[!UICONTROL Value]** della data corrente: Month(GetDate()).

   Questo consente di eseguire una query sui destinatari il cui mese di compleanno corrisponde al mese corrente.

   ![](assets/uc_enrichment_4.png)

1. Fai clic su **[!UICONTROL Finish]**. Quindi, nella scheda **[!UICONTROL General]** dell&#39;attività **[!UICONTROL Split]**, fare clic su **[!UICONTROL Generate complement]** nella categoria **[!UICONTROL Results]**.

   Con il risultato **[!UICONTROL Complement]**, potete aggiungere un&#39;attività di consegna o aggiornare un elenco. Qui abbiamo appena aggiunto un&#39;attività **[!UICONTROL End]**.

   ![](assets/uc_enrichment_6.png)

È ora necessario configurare l&#39;attività **[!UICONTROL Enrichment]**:

1. Aggiungi un&#39;attività **[!UICONTROL Enrichment]** dopo il tuo sottoinsieme per aggiungere i campi data personalizzati.

   ![](assets/uc_enrichment_7.png)

1. Aprite l&#39;attività **[!UICONTROL Enrichment]**. Nella categoria **[!UICONTROL Complementary information]**, fare clic su **[!UICONTROL Add data]**.

   ![](assets/uc_enrichment_8.png)

1. Selezionare **[!UICONTROL Data linked to the filtering dimension]**, quindi **[!UICONTROL Data of the filtering dimension]**.
1. Fai clic sul pulsante **[!UICONTROL Add]**.

   ![](assets/uc_enrichment_9.png)

1. Aggiungete un elemento **[!UICONTROL Label]**. Quindi, nella colonna **[!UICONTROL Expression]**, fare clic su **[!UICONTROL Edit expression]**.

   ![](assets/uc_enrichment_10.png)

1. In primo luogo, è necessario eseguire il targeting della settimana prima della data di nascita come **Data di inizio validità** con la seguente **[!UICONTROL Expression]**: `SubDays([target/@birthDate], 7)`.

   ![](assets/uc_enrichment_11.png)

1. Quindi, per creare il campo data personalizzato **Data fine validità** che verrà utilizzato la settimana successiva alla data di nascita, è necessario aggiungere la **[!UICONTROL Expression]**: `AddDays([target/@birthDate], 7)`.

   È possibile aggiungere un&#39;etichetta all&#39;espressione.

   ![](assets/uc_enrichment_12.png)

1. Fai clic su **[!UICONTROL Ok]**. Il vostro arricchimento è pronto.

Dopo l&#39;attività **[!UICONTROL Enrichment]**, potete aggiungere una consegna. In questo caso, abbiamo aggiunto un&#39;e-mail di consegna per inviare ai destinatari un&#39;offerta speciale con date di validità ai clienti che festeggiano i compleanni di questo mese.

1. Trascinare un&#39;attività **[!UICONTROL Email delivery]** dopo l&#39;attività **[!UICONTROL Enrichment]**.

   ![](assets/uc_enrichment_15.png)

1. Fate doppio clic sull&#39;attività **[!UICONTROL Email delivery]** per iniziare a personalizzare la distribuzione.
1. Aggiungi un **[!UICONTROL Label]** alla consegna e fai clic su **[!UICONTROL Continue]**.
1. Fate clic su **[!UICONTROL Save]** per creare la consegna del messaggio e-mail.
1. Controllare nella scheda **[!UICONTROL Approval]** della consegna dell&#39;e-mail **[!UICONTROL Properties]** che l&#39;elemento **[!UICONTROL Confirm delivery before sending option]** sia selezionato.

   Quindi avviate il flusso di lavoro per arricchire la transizione in uscita con le informazioni di destinazione.

   ![](assets/uc_enrichment_18.png)

È ora possibile iniziare a progettare la distribuzione delle e-mail con i campi data personalizzati creati nell&#39;attività **[!UICONTROL Enrichment]**.

1. Fate doppio clic sull&#39;attività **[!UICONTROL Email delivery]**.
1. Aggiungete le estensioni di destinazione al messaggio e-mail. Deve trovarsi all&#39;interno della seguente espressione per configurare il formato delle date di validità:

   ```
   <%=
           formatDate(targetData.alias of your expression,"%2D.%2M")  %>
   ```

1. Fai clic su ![](assets/uc_enrichment_16.png) . Selezionare **[!UICONTROL Target extension]**, quindi le date di validità personalizzate create in precedenza con l&#39;attività **[!UICONTROL Enrichment]** per aggiungere l&#39;estensione all&#39;espressione formatDate.

   ![](assets/uc_enrichment_19.png)

1. Configura il contenuto dell’e-mail in base alle esigenze.

   ![](assets/uc_enrichment_17.png)

1. Visualizzare l&#39;anteprima del messaggio e-mail per verificare se i campi data personalizzati sono stati configurati correttamente

   ![](assets/uc_enrichment_20.png)

La tua e-mail è ora pronta. Potete iniziare a inviare le prove e confermare la consegna per inviare le e-mail di compleanno.
