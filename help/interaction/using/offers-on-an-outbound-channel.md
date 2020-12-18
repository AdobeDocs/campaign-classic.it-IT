---
solution: Campaign Classic
product: campaign
title: Offerte su un canale in uscita
description: Offerte su un canale in uscita
audience: interaction
content-type: reference
topic-tags: case-study
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 3%

---


# Offerte su un canale in uscita{#offers-on-an-outbound-channel}

## Invio offerta e-mail {#email-offer-delivery}

Nel nostro database c&#39;è una categoria di offerte di viaggio per l&#39;Africa. L&#39;idoneità, i contesti e le rappresentazioni di ciascuna offerta sono stati configurati. Ora vogliamo creare una campagna per presentare le nostre offerte via e-mail.

1. Crea una campagna di marketing e un flusso di lavoro di targeting.

   ![](assets/offer_delivery_example_001.png)

1. Modificate la consegna e fate clic sull&#39;icona **[!UICONTROL Offers]**.

   ![](assets/offer_delivery_example_002.png)

1. Scegliete lo spazio e-mail per l’ambiente delle offerte che corrisponde alle festività.

   ![](assets/offer_delivery_example_003.png)

1. Scegliete la categoria che contiene le offerte di viaggio africane.

   ![](assets/offer_delivery_example_004.png)

1. Impostate il numero di offerte nella consegna su due.

   ![](assets/offer_delivery_example_005.png)

1. Chiudete la finestra di gestione delle offerte e create il contenuto della distribuzione.

   ![](assets/offer_delivery_example_006.png)

1. Usate i menu per inserire una prima proposta di offerta e scegliete la funzione di rendering HTML.

   ![](assets/offer_delivery_example_007.png)

1. Inserite la seconda proposta di offerta.

   ![](assets/offer_delivery_example_008.png)

1. Fate clic su **[!UICONTROL Preview]** per visualizzare l&#39;anteprima delle offerte, quindi selezionate un destinatario per visualizzare l&#39;anteprima delle offerte così come verranno ricevute.

   ![](assets/offer_delivery_example_009.png)

1. Salvate la consegna e avviate il flusso di lavoro di targeting.
1. Aprite la consegna e fate clic sulla scheda **[!UICONTROL Audit]** della consegna: potete vedere che il motore delle offerte ha selezionato le proposte da creare dalle varie offerte del catalogo.

   ![](assets/offer_delivery_example_010.png)

## Eseguire una simulazione di offerta {#perform-an-offer-simulation}

1. Nell&#39;universo **[!UICONTROL Profiles and Targets]** fare clic sul collegamento **[!UICONTROL Simulations]**, quindi fare clic sul pulsante **[!UICONTROL Create]**.

   ![](assets/offer_simulation_001.png)

1. Scegliete un&#39;etichetta e specificate le impostazioni di esecuzione, se necessario.

   ![](assets/offer_simulation_example_002.png)

1. Salvate la simulazione. Viene quindi aperta in una nuova scheda.

   ![](assets/offer_simulation_example_003.png)

1. Fare clic sulla scheda **[!UICONTROL Edit]**, quindi **[!UICONTROL Scope]**.

   ![](assets/offer_simulation_example_004.png)

1. Scegliete la categoria per la quale desiderate simulare le offerte.

   ![](assets/offer_simulation_example_005.png)

1. Scegliete lo spazio dell’offerta da usare per la simulazione.

   ![](assets/offer_simulation_example_006.png)

1. Immettere le date di validità. È necessario immettere almeno una data di inizio. Questo consente al filtro del motore delle offerte di scegliere le offerte valide in una data specificata.
1. Se necessario, specificate uno o più temi per limitare il numero di offerte a quelli che contengono questa parola chiave nelle relative impostazioni.

   Nel nostro esempio, la categoria **Travel** contiene due sottocategorie con due temi separati. Vogliamo eseguire una simulazione per le offerte con il tema **Customers>1 year**.

   ![](assets/offer_simulation_example_007.png)

1. Scegliete i destinatari da destinare.

   ![](assets/offer_simulation_example_008.png)

1. Configura il numero di offerte da inviare a ogni destinatario.

   Nel nostro esempio, il motore delle offerte sceglierà le 3 offerte con il peso più alto per ciascun destinatario.

   ![](assets/offer_simulation_example_009.png)

1. Salvate le impostazioni, quindi fate clic su **[!UICONTROL Start]** nella scheda **[!UICONTROL Dashboard]** per eseguire la simulazione.

   ![](assets/offer_simulation_example_010.png)

1. Una volta terminata la simulazione, consultate la sezione **[!UICONTROL Results]** per una descrizione dettagliata delle proposte per offerta.

   Nel nostro esempio, il motore delle offerte ha basato la suddivisione dell&#39;offerta su 3 proposte.

   ![](assets/offer_simulation_example_011.png)

1. Visualizza la **[!UICONTROL Breakdown of offers by rank]** per visualizzare l&#39;elenco delle offerte selezionate dal motore delle offerte.

   ![](assets/offer_simulation_example_012.png)

1. Se necessario, puoi modificare le impostazioni dell&#39;ambito ed eseguire di nuovo la simulazione facendo clic su **[!UICONTROL Start simulation]**.

   ![](assets/offer_simulation_example_010.png)

1. Per salvare i dati di simulazione, usa la cronologia o le funzioni di esportazione disponibili nel rapporto.

   ![](assets/offer_simulation_example_013.png)

