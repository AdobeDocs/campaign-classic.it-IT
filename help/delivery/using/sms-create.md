---
solution: Campaign Classic
product: campaign
title: Creare un SMS con Campaign
description: Scopri come creare SMS con Campaign
audience: delivery
content-type: reference
topic-tags: sending-messages-on-mobiles
translation-type: tm+mt
source-git-commit: 5a084ebe5295d19de24cf92c721d4692f0f5deb8
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 3%

---


# Creare una consegna SMS {#creating-a-sms-delivery}

## Seleziona il canale di consegna {#selecting-the-delivery-channel}

Per creare una nuova consegna SMS, segui i passaggi seguenti:

>[!NOTE]
>
>I concetti globali sulla creazione della consegna sono descritti in [questa sezione](../../delivery/using/steps-about-delivery-creation-steps.md).

1. Crea una nuova consegna, ad esempio dal dashboard Consegna .
1. Seleziona il modello di consegna **Inviato a dispositivi mobili (SMPP)** creato in precedenza. Per ulteriori informazioni, consulta la sezione [Modifica il modello di consegna](sms-set-up.md#changing-the-delivery-template) .

   ![](assets/s_user_mobile_wizard.png)

1. Identifica la consegna con un’etichetta, un codice e una descrizione. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../delivery/using/steps-create-and-identify-the-delivery.md#identifying-the-delivery).
1. Fai clic su **[!UICONTROL Continue]** per confermare queste informazioni e visualizzare la finestra di configurazione del messaggio.

## Definisci il contenuto dell’SMS {#defining-the-sms-content}

Per creare il contenuto dell’SMS, segui i passaggi seguenti:

1. Immetti il contenuto del messaggio nella sezione **[!UICONTROL Text content]** della procedura guidata. I pulsanti della barra degli strumenti consentono di importare, salvare o cercare contenuti. L’ultimo pulsante viene utilizzato per inserire campi di personalizzazione.

   ![](assets/s_ncs_user_wizard_sms01_138.png)

   L’utilizzo dei campi di personalizzazione è presentato nella sezione [Informazioni sulla personalizzazione](../../delivery/using/about-personalization.md) .

1. Fai clic su **[!UICONTROL Preview]** nella parte inferiore della pagina per visualizzare il rendering del messaggio con la relativa personalizzazione. Per avviare l’anteprima, seleziona un destinatario utilizzando il pulsante **[!UICONTROL Test personalization]** nella barra degli strumenti. Puoi selezionare un destinatario dalle destinazioni definite o scegliere un altro destinatario.

   ![](assets/s_ncs_user_wizard_sms01_139.png)

   Puoi approvare il messaggio SMS. Puoi anche visualizzare il contenuto dell’SMS sullo schermo del telefono cellulare visualizzato a destra dell’editor dei contenuti. Fai clic sulla schermata e utilizza il mouse per scorrere il contenuto.

   ![](assets/s_ncs_user_wizard_sms01_140.png)

1. Fai clic sul collegamento **[!UICONTROL Data loaded]** per visualizzare le informazioni relative al destinatario.

   ![](assets/s_user_mobile_wizard_sms_02.png)

   >[!NOTE]
   >
   >I messaggi SMS sono limitati a una lunghezza di 160 caratteri se si utilizza la tabella codici Latin-1 (ISO-8859-1). Se il messaggio è scritto in Unicode, non deve superare i 70 caratteri. Alcuni caratteri speciali possono influenzare la lunghezza del messaggio. Per ulteriori informazioni sulla lunghezza del messaggio, consulta la sezione [Traslitterazione caratteri SMS](#about-character-transliteration) .
   >
   >Quando sono presenti campi di personalizzazione o campi di contenuto condizionale, le dimensioni del messaggio variano da un destinatario all’altro. La lunghezza del messaggio deve essere valutata al momento dell’esecuzione della personalizzazione.
   >
   >Quando avvii l’analisi, viene controllata la lunghezza dei messaggi e viene visualizzato un avviso in caso di overflow.

1. Se utilizzi il connettore NetSize o un connettore SMPP, puoi personalizzare il nome del mittente della consegna. Per ulteriori informazioni, consulta la sezione [Parametri avanzati](#advanced-parameters) .

## Selezionare la popolazione target {#selecting-the-target-population}

Il processo dettagliato durante la selezione della popolazione target di una consegna è presentato in [questa sezione](../../delivery/using/steps-defining-the-target-population.md).

Per ulteriori informazioni sull’utilizzo dei campi di personalizzazione, consulta [questa sezione](../../delivery/using/about-personalization.md).

Per ulteriori informazioni sull&#39;inclusione di un elenco di seed, consulta [questa pagina](../../delivery/using/about-seed-addresses.md).

