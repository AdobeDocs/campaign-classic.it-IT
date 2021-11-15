---
product: campaign
title: Inserire un codice a barre in un messaggio e-mail
description: Inserire un codice a barre in un messaggio e-mail
audience: delivery
content-type: reference
topic-tags: sending-emails
source-git-commit: 3b8d685642fc74d918a0e312c66d5e4f7b424192
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 0%

---


# Inserire un codice a barre in un messaggio e-mail{#insert-a-barcode-in-an-email}

![](../../assets/common.svg)

Il modulo di generazione dei codici a barre consente di creare diversi tipi di codici a barre conformi a numerosi standard comuni, inclusi i codici a barre 2D.

È possibile generare in modo dinamico un codice a barre come bitmap utilizzando un valore definito utilizzando i criteri del cliente. I codici a barre personalizzati possono essere inclusi nelle campagne e-mail. Il destinatario può stampare il messaggio e mostrarlo alla società emittente per la scansione (ad esempio durante il check-out).

Per inserire un codice a barre in un messaggio e-mail, posiziona il cursore nel contenuto in cui desideri visualizzarlo, quindi fai clic sul pulsante di personalizzazione. Seleziona **[!UICONTROL Include > Barcode...]**.

![](assets/barcode_insert_14.png)

Quindi configura i seguenti elementi in base alle tue esigenze:

1. Selezionare il tipo di codice a barre.

   * Per il formato 1D, in Adobe Campaign sono disponibili i seguenti tipi: Codabar, Codice 128, GS1-128 (precedentemente EAN-128), UPC-A, UPC-E, ISBN, EAN-8, Code39, Interleaved 2 di 5, POSTNET e Royal Mail (RM4SCC).

      Esempio di codice a barre 1D:

      ![](assets/barcode_insert_08.png)

   * I tipi DataMatrix e PDF417 riguardano il formato 2D.

      Esempio di codice a barre 2D:

      ![](assets/barcode_insert_09.png)

   * Per inserire un codice QR, selezionare questo tipo e immettere il tasso di correzione errori da applicare. Questo tasso definisce la quantità di informazioni ripetute e la tolleranza al deterioramento.

      ![](assets/barcode_insert_06.png)

      Esempio di codice QR:

      ![](assets/barcode_insert_12.png)

1. Immettere le dimensioni del codice a barre da inserire nell&#39;e-mail: la configurazione della scala consente di aumentare o ridurre le dimensioni del codice a barre da x1 a x10.
1. La **[!UICONTROL Value]** consente di definire il valore del codice a barre. Un valore può corrispondere a un&#39;offerta speciale e può essere la funzione di un criterio, può essere il valore di un campo di database collegato ai clienti.

   Questo esempio mostra un codice a barre di tipo EAN-8 a cui è stato aggiunto il numero di account di un destinatario. Per aggiungere questo numero di account, fai clic sul pulsante di personalizzazione a destra di **[!UICONTROL Value]** campo e seleziona **[!UICONTROL Recipient > Account number]**.

   ![](assets/barcode_insert_15.png)

1. La **[!UICONTROL Height]** consente di configurare l’altezza del codice a barre senza modificarne la larghezza, modificando la quantità di spazio tra ciascuna barra.

   Non esiste un controllo di ingresso restrittivo a seconda del tipo di codice a barre. Se un valore di codice a barre non è corretto, sarà visibile solo in **Anteprima** modalità in cui il codice a barre viene barrato in rosso.

   >[!NOTE]
   >
   >Il valore assegnato a un codice a barre dipende dal relativo tipo. Ad esempio, un tipo EAN-8 deve avere esattamente 8 numeri.
   >
   >Pulsante di personalizzazione a destra della **[!UICONTROL Value]** consente di aggiungere dati oltre al valore stesso. Questo arricchisce il codice a barre, purché sia accettato dallo standard.
   >
   >Ad esempio, se si utilizza un codice a barre di tipo GS1-128 e si desidera immettere il numero di conto di un destinatario oltre al valore, fare clic sul pulsante di personalizzazione e selezionare **[!UICONTROL Recipient > Account number]**. Se il numero di conto del destinatario selezionato viene immesso correttamente, il codice a barre ne tiene conto.

Una volta configurati questi elementi, puoi finalizzare l’e-mail e inviarla. Per evitare errori, assicurati sempre che il contenuto sia visualizzato correttamente prima di eseguire una consegna facendo clic sul pulsante **[!UICONTROL Preview]** scheda .

![](assets/barcode_insert_10.png)

>[!NOTE]
>
>Se il valore di un codice a barre non è corretto, la relativa bitmap viene visualizzata in rosso.

![](assets/barcode_insert_11.png)
