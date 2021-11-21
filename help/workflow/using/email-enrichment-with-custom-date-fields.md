---
product: campaign
title: Arricchimento delle e-mail con campi data personalizzati
description: Scopri come arricchire le e-mail con campi data personalizzati
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: 85e0ec2a-b7cb-4d0b-a281-9ad72594403a
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 3%

---

# Arricchimento delle e-mail con campi data personalizzati{#email-enrichment-with-custom-date-fields}

![](../../assets/common.svg)

In questo esempio, vogliamo inviare un’e-mail con campi di dati personalizzati ai destinatari che questo mese festeggiano i loro compleanni. L&#39;e-mail includerà un coupon valido una settimana prima e dopo i loro compleanni.

Dobbiamo indirizzare i destinatari da una lista che festeggerà i loro compleanni questo mese con un **[!UICONTROL Split]** attività. Quindi, utilizzando **[!UICONTROL Enrichment]** attività , il campo dati personalizzato fungerà da data di validità nell’e-mail per l’offerta speciale del cliente.

![](assets/uc_enrichment.png)

Per creare questo esempio, esegui i seguenti passaggi:

1. In **[!UICONTROL Targeting and workflows]** scheda della campagna, trascina e rilascia una **[!UICONTROL Read list]** attività per eseguire il targeting dell’elenco di destinatari.
1. L’elenco da elaborare può essere specificato esplicitamente, calcolato da uno script o localizzato dinamicamente, in base alle opzioni selezionate e ai parametri qui definiti.

   ![](assets/uc_enrichment_1.png)

1. Aggiungi un **[!UICONTROL Split]** attività per differenziare i destinatari che questo mese festeggeranno i loro compleanni da altri destinatari.
1. Per dividere l&#39;elenco, nella **[!UICONTROL Filtering of selected records]** categoria, seleziona **[!UICONTROL Add a filtering condition on the inbound population]**. Quindi, fai clic su **[!UICONTROL Edit]**.

   ![](assets/uc_enrichment_2.png)

1. Seleziona **[!UICONTROL Filtering conditions]** quindi fai clic su **[!UICONTROL Edit expression]** per filtrare il mese del compleanno del destinatario.

   ![](assets/uc_enrichment_3.png)

1. Fai clic su **[!UICONTROL Advanced Selection]** then **[!UICONTROL Edit the formula using an expression]** e aggiungi la seguente espressione: Month(@datadinascita).
1. In **[!UICONTROL Operator]** seleziona la colonna **[!UICONTROL equal to]**.
1. Per filtrare ulteriormente la condizione, aggiungi la **[!UICONTROL Value]** mese della data corrente: Month(GetDate()).

   Verranno eseguiti query sui destinatari il cui mese di compleanno corrisponde al mese corrente.

   ![](assets/uc_enrichment_4.png)

1. Fai clic su **[!UICONTROL Finish]**. Quindi, nella **[!UICONTROL General]** scheda **[!UICONTROL Split]** fai clic su **[!UICONTROL Generate complement]** in **[!UICONTROL Results]** categoria.

   Con la **[!UICONTROL Complement]** di conseguenza, puoi aggiungere un’attività di consegna o aggiornare un elenco. Qui abbiamo appena aggiunto un **[!UICONTROL End]** attività.

   ![](assets/uc_enrichment_6.png)

È ora necessario configurare il **[!UICONTROL Enrichment]** attività:

1. Aggiungi un **[!UICONTROL Enrichment]** dopo il sottoinsieme per aggiungere campi data personalizzati.

   ![](assets/uc_enrichment_7.png)

1. Apri il tuo **[!UICONTROL Enrichment]** attività. In **[!UICONTROL Complementary information]** categoria, fai clic su **[!UICONTROL Add data]**.

   ![](assets/uc_enrichment_8.png)

1. Seleziona **[!UICONTROL Data linked to the filtering dimension]** then **[!UICONTROL Data of the filtering dimension]**.
1. Fai clic sul pulsante **[!UICONTROL Add]**.

   ![](assets/uc_enrichment_9.png)

1. Aggiungi un **[!UICONTROL Label]**. Quindi, nella **[!UICONTROL Expression]** colonna, fai clic su **[!UICONTROL Edit expression]**.

   ![](assets/uc_enrichment_10.png)

1. Per prima cosa, dobbiamo eseguire il targeting della settimana prima della data di nascita come **Data di inizio validità** con i seguenti **[!UICONTROL Expression]**: `SubDays([target/@birthDate], 7)`.

   ![](assets/uc_enrichment_11.png)

1. Quindi, per creare il campo data personalizzato **Data di fine validità** che eseguirà il targeting della settimana dopo la data di nascita, è necessario aggiungere il **[!UICONTROL Expression]**: `AddDays([target/@birthDate], 7)`.

   Puoi aggiungere un’etichetta all’espressione.

   ![](assets/uc_enrichment_12.png)

1. Fai clic su **[!UICONTROL Ok]**. L&#39;arricchimento è ora pronto.

Dopo il **[!UICONTROL Enrichment]** puoi aggiungere una consegna. In questo caso, abbiamo aggiunto una consegna e-mail per inviare ai destinatari un’offerta speciale con date di validità ai clienti che festeggiano il compleanno questo mese.

1. Trascina e rilascia una **[!UICONTROL Email delivery]** dopo la **[!UICONTROL Enrichment]** attività.

   ![](assets/uc_enrichment_15.png)

1. Fai doppio clic sul **[!UICONTROL Email delivery]** per iniziare a personalizzare la consegna.
1. Aggiungi un **[!UICONTROL Label]** alla consegna e fai clic su **[!UICONTROL Continue]**.
1. Fai clic su **[!UICONTROL Save]** per creare la consegna e-mail.
1. Archivia i **[!UICONTROL Approval]** scheda della consegna e-mail **[!UICONTROL Properties]** che **[!UICONTROL Confirm delivery before sending option]** è controllata.

   Quindi, avvia il flusso di lavoro per arricchire la transizione in uscita con le informazioni mirate.

   ![](assets/uc_enrichment_18.png)

Ora puoi iniziare a progettare la consegna e-mail con i campi data personalizzati creati nella **[!UICONTROL Enrichment]** attività.

1. Fai doppio clic sul **[!UICONTROL Email delivery]** attività.
1. Aggiungi le estensioni di destinazione all’e-mail. Deve trovarsi all’interno della seguente espressione per configurare il formato delle date di validità:

   ```
   <%=
           formatDate(targetData.alias of your expression,"%2D.%2M")  %>
   ```

1. Fai clic su ![](assets/uc_enrichment_16.png) . Seleziona **[!UICONTROL Target extension]** quindi le date di validità personalizzate create in precedenza con **[!UICONTROL Enrichment]** per aggiungere l&#39;estensione all&#39;espressione formatDate.

   ![](assets/uc_enrichment_19.png)

1. Configura il contenuto dell’e-mail in base alle esigenze.

   ![](assets/uc_enrichment_17.png)

1. Visualizza l’anteprima del messaggio e-mail per verificare se i campi data personalizzati sono stati configurati correttamente

   ![](assets/uc_enrichment_20.png)

L’e-mail è ora pronta. Puoi iniziare a inviare le bozze e confermare la consegna per inviare le e-mail di compleanno.
