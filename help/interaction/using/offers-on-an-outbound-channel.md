---
product: campaign
title: Offerte su un canale in uscita
description: Offerte su un canale in uscita
audience: interaction
content-type: reference
topic-tags: case-study
exl-id: 77fee343-09d1-4d60-be43-efe02953a70c
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 3%

---

# Offerte su un canale in uscita{#offers-on-an-outbound-channel}

![](../../assets/v7-only.svg)

## Email delivery {#email-offer-delivery}

Nel nostro database c&#39;è una categoria di offerte di viaggio per l&#39;Africa. Sono stati configurati l’idoneità, i contesti e le rappresentazioni di ogni offerta. Ora vogliamo creare una campagna per presentare le nostre offerte via e-mail.

1. Crea una campagna di marketing e un flusso di lavoro di targeting.

   ![](assets/offer_delivery_example_001.png)

1. Modifica la consegna e-mail e fai clic sull’icona **[!UICONTROL Offers]** .

   ![](assets/offer_delivery_example_002.png)

1. Scegli lo spazio e-mail per l’ambiente delle offerte che corrisponde alle festività.

   ![](assets/offer_delivery_example_003.png)

1. Scegli la categoria che contiene le offerte di viaggio in Africa.

   ![](assets/offer_delivery_example_004.png)

1. Imposta il numero di offerte nella consegna su due.

   ![](assets/offer_delivery_example_005.png)

1. Chiudi la finestra di gestione delle offerte e crea il contenuto della consegna.

   ![](assets/offer_delivery_example_006.png)

1. Utilizza i menu per inserire una prima proposta di offerta e scegli la funzione di rendering HTML.

   ![](assets/offer_delivery_example_007.png)

1. Inserisci la seconda proposta di offerta.

   ![](assets/offer_delivery_example_008.png)

1. Fai clic su **[!UICONTROL Preview]** per visualizzare in anteprima le offerte nella consegna, quindi seleziona un destinatario per visualizzare in anteprima le offerte così come le riceverà.

   ![](assets/offer_delivery_example_009.png)

1. Salva la consegna e avvia il flusso di lavoro di targeting.
1. Apri la consegna e fai clic sulla scheda **[!UICONTROL Audit]** della consegna: puoi vedere che il motore di offerte ha selezionato le proposte da creare dalle varie offerte del catalogo.

   ![](assets/offer_delivery_example_010.png)

## Eseguire una simulazione di offerta {#perform-an-offer-simulation}

1. Nella scheda **[!UICONTROL Profiles and Targets]** , fai clic sul collegamento **[!UICONTROL Simulations]** , quindi sul pulsante **[!UICONTROL Create]** .

   ![](assets/offer_simulation_001.png)

1. Scegli un’etichetta e specifica le impostazioni di esecuzione, se necessario.

   ![](assets/offer_simulation_example_002.png)

1. Salva la simulazione. Viene quindi aperta in una nuova scheda.

   ![](assets/offer_simulation_example_003.png)

1. Fare clic sulla scheda **[!UICONTROL Edit]**, quindi **[!UICONTROL Scope]**.

   ![](assets/offer_simulation_example_004.png)

1. Scegli la categoria per la quale simulare le offerte.

   ![](assets/offer_simulation_example_005.png)

1. Scegli lo spazio di offerta da utilizzare per la simulazione.

   ![](assets/offer_simulation_example_006.png)

1. Immettere le date di validità. Immettere almeno una data di inizio. Questo consente al motore di offerta di filtrare le offerte e scegliere quelle valide in una data specificata.
1. Se necessario, specifica uno o più temi per limitare il numero di offerte a quelli che contengono questa parola chiave nelle loro impostazioni.

   Nel nostro esempio, la categoria **Viaggi** contiene due sottocategorie con due temi separati. Vogliamo eseguire una simulazione per le offerte con il tema **Clienti>1 anno**.

   ![](assets/offer_simulation_example_007.png)

1. Scegli i destinatari a cui desideri rivolgerti.

   ![](assets/offer_simulation_example_008.png)

1. Configura il numero di offerte da inviare a ciascun destinatario.

   Nel nostro esempio, il motore di offerta sceglierà le 3 offerte con il peso più elevato per ciascun destinatario.

   ![](assets/offer_simulation_example_009.png)

1. Salva le impostazioni, quindi fai clic su **[!UICONTROL Start]** nella scheda **[!UICONTROL Dashboard]** per eseguire la simulazione.

   ![](assets/offer_simulation_example_010.png)

1. Al termine della simulazione, consulta la sezione **[!UICONTROL Results]** per una suddivisione dettagliata delle proposte per offerta.

   Nel nostro esempio, il motore di offerta ha basato la suddivisione dell’offerta su 3 proposte.

   ![](assets/offer_simulation_example_011.png)

1. Visualizza l’ **[!UICONTROL Breakdown of offers by rank]** per visualizzare l’elenco delle offerte selezionate dal motore di offerta.

   ![](assets/offer_simulation_example_012.png)

1. Se necessario, puoi modificare le impostazioni dell&#39;ambito ed eseguire nuovamente la simulazione facendo clic su **[!UICONTROL Start simulation]**.

   ![](assets/offer_simulation_example_010.png)

1. Per salvare i dati di simulazione, utilizza la cronologia o le funzioni di esportazione disponibili nel rapporto.

   ![](assets/offer_simulation_example_013.png)
