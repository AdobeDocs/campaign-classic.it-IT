---
product: campaign
title: Creare un SMS con Campaign
description: Scopri come creare SMS con Campaign
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: SMS
role: User
exl-id: 94aa4628-d973-433d-b963-b078e2d6672b
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 2%

---

# Creare una consegna SMS {#creating-a-sms-delivery}

## Seleziona il canale di consegna {#selecting-the-delivery-channel}

Per creare una nuova consegna SMS, segui i passaggi seguenti:

>[!NOTE]
>
>I concetti globali sulla creazione della consegna sono presentati in [questa sezione](steps-about-delivery-creation-steps.md).

1. Crea una nuova consegna, ad esempio dal dashboard Consegna.
1. Seleziona il modello di consegna **Inviato a dispositivi mobili (SMPP)** creato in precedenza. Per ulteriori informazioni, consulta [Modificare il modello di consegna](sms-set-up.md#changing-the-delivery-template) sezione.

   ![](assets/s_user_mobile_wizard.png)

1. Identifica la consegna con un’etichetta, un codice e una descrizione. Per ulteriori informazioni al riguardo, consulta [questa sezione](steps-create-and-identify-the-delivery.md#identifying-the-delivery).
1. Clic **[!UICONTROL Continue]** per confermare queste informazioni e visualizzare la finestra configurazione messaggio.

## Definire il contenuto dell’SMS {#defining-the-sms-content}

Per creare il contenuto dell’SMS, segui i passaggi seguenti:

1. Inserisci il contenuto del messaggio in **[!UICONTROL Text content]** sezione della procedura guidata. I pulsanti della barra degli strumenti consentono di importare, salvare o eseguire ricerche nel contenuto. L’ultimo pulsante viene utilizzato per inserire campi di personalizzazione.

   ![](assets/s_ncs_user_wizard_sms01_138.png)

   L’utilizzo dei campi di personalizzazione è presentato nel [Informazioni sulla personalizzazione](about-personalization.md) sezione.

1. Clic **[!UICONTROL Preview]** nella parte inferiore della pagina per visualizzare il rendering del messaggio con la relativa personalizzazione. Per avviare l’anteprima, seleziona un destinatario utilizzando **[!UICONTROL Test personalization]** nella barra degli strumenti. Puoi selezionare un destinatario dalle destinazioni definite o scegliere un altro destinatario.

   ![](assets/s_ncs_user_wizard_sms01_139.png)

   Puoi approvare il messaggio SMS. Puoi anche visualizzare il contenuto dell’SMS sullo schermo del telefono cellulare visualizzato a destra dell’editor di contenuti. Fai clic sulla schermata e utilizza il mouse per scorrere il contenuto.

   ![](assets/s_ncs_user_wizard_sms01_140.png)

1. Fai clic su **[!UICONTROL Data loaded]** link per visualizzare le informazioni relative al destinatario.

   ![](assets/s_user_mobile_wizard_sms_02.png)

   >[!NOTE]
   >
   >I messaggi SMS sono limitati a una lunghezza di 160 caratteri se viene utilizzata la tabella codici Latin-1 (ISO-8859-1). Se il messaggio è scritto in Unicode, non deve superare i 70 caratteri. Alcuni caratteri speciali possono influenzare la lunghezza del messaggio. Per ulteriori informazioni sulla lunghezza dei messaggi, consulta [Traslitterazione di caratteri SMS](#about-character-transliteration) sezione.
   >
   >Quando sono presenti campi di personalizzazione o campi di contenuto condizionale, la dimensione del messaggio varia da un destinatario all’altro. La lunghezza del messaggio deve essere valutata una volta eseguita la personalizzazione.
   >
   >Quando avvii l’analisi, viene controllata la lunghezza dei messaggi e viene visualizzato un avviso in caso di overflow.

1. Se utilizzi il connettore NetSize o un connettore SMPP, puoi personalizzare il nome del mittente della consegna. Per ulteriori informazioni, consulta [Parametri avanzati](#advanced-parameters) sezione.

## Selezionare la popolazione target {#selecting-the-target-population}

Il processo dettagliato durante la selezione della popolazione target di una consegna è presentato in [questa sezione](steps-defining-the-target-population.md).

Per ulteriori informazioni sull’utilizzo dei campi di personalizzazione, consulta [questa sezione](about-personalization.md).

Per ulteriori informazioni sull’inclusione di un elenco di seed, consulta [questa pagina](about-seed-addresses.md).
