---
product: campaign
title: Personalizzazione dell’elenco delle emoticon
description: Scopri come personalizzare l’elenco degli emoticon quando utilizzi Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: sending-emails
exl-id: b8642df3-1960-4f2c-8273-c3988a3e85f0
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 3%

---

# Personalizzazione dell’elenco delle emoticon {#customize-emoticons}

![](../../assets/common.svg)

L’elenco di emoticon visualizzato nella finestra a comparsa è governato da un’enumerazione che consente di visualizzare i valori in un elenco per limitare le scelte dell’utente per un dato campo.
L&#39;ordine dell&#39;elenco degli emoticon può essere personalizzato, è anche possibile aggiungere altri emoticon alla tua lista.
Le emoticon sono disponibili per e-mail e per ulteriori informazioni, consulta questa [pagina](defining-the-email-content.md#inserting-emoticons).

## Aggiunta di un nuovo emoticon {#add-new-emoticon}

>[!CAUTION]
>
>L’elenco delle emoticon non può visualizzare più di 81 voci.

1. Scegli il nuovo emoticon da aggiungere da questa [pagina](https://unicode.org/emoji/charts/full-emoji-list.html). Tieni presente che deve essere compatibile con le diverse piattaforme quali browser e sistema operativo.

1. In **[!UICONTROL Explorer]**, seleziona **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Enumerations]** e fai clic sull&#39;enumerazione preconfigurata **[!UICONTROL Emoticon list]** .

   >[!NOTE]
   >
   >Le enumerazioni predefinite possono essere gestite solo da un amministratore della console Adobe Campaign Classic.

   ![](assets/emoticon_1.png)

1. Fai clic su **[!UICONTROL Add]**.

1. Compila i campi:

   * **[!UICONTROL U+]**: Codice del tuo nuovo emoticon. L&#39;elenco dei codici degli emoticon è disponibile in questa [pagina](https://unicode.org/emoji/charts/full-emoji-list.html).
Per evitare problemi di compatibilità, consigliamo di scegliere gli emoticon supportati sui browser e su ogni sistema operativo.

   * **[!UICONTROL Label]**: Etichetta del tuo nuovo emoticon.

   ![](assets/emoticon_5.png)

1. Al termine della configurazione, fai clic su **[!UICONTROL Ok]** e quindi su **[!UICONTROL Save]** .
Il nuovo emoticon verrà posizionato automaticamente nel negozio.

1. Per visualizzarlo nella finestra **[!UICONTROL Insert emoticon]** delle consegne, seleziona l’emoticon appena creato facendo doppio clic su di esso.

1. Scegli nel menu a discesa **[!UICONTROL Display order]** in quale ordine verrà visualizzato il tuo nuovo emoticon. Selezionando un ordine di visualizzazione già assegnato, l’emoticon esistente verrà automaticamente spostato nello store.

   <br>In questo esempio, abbiamo scelto il numero di ordine di visualizzazione 61, il che significa che se una voce aveva già questo ordine verrà automaticamente spostata nello store e la nostra nuova voce avrà il suo posto nell&#39;elenco di enumerazione.

   ![](assets/emoticon_2.png)

1. Il nuovo emoticon è stato aggiunto all’enumerazione predefinita **[!UICONTROL Insert emoticon list]** . È possibile modificarne **[!UICONTROL Display order]** in qualsiasi momento o spostarlo nel negozio se non è più necessario.

1. Per tenere conto delle modifiche, disconnettiti e riconnettiti da Adobe Campaign Classic. Se il nuovo emoticon non viene ancora visualizzato nella finestra a comparsa **[!UICONTROL Insert emoticon]**, potrebbe essere necessario cancellare la cache. Per ulteriori informazioni, consulta questa [sezione](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear).

1. Il nuovo emoticon si trova ora nelle consegne nella finestra a comparsa **[!UICONTROL Insert emoticon]** nella 61a posizione configurata nei passaggi precedenti. Per ulteriori informazioni su come utilizzare gli emoticon nelle consegne, consulta questa [pagina](defining-the-email-content.md#inserting-emoticons).

   ![](assets/emoticon_4.png)

1. Se nella finestra a comparsa **[!UICONTROL Insert emoticon]** sono visualizzati i seguenti emoticon, significa che non sono stati configurati correttamente. Controlla se il tuo codice **[!UICONTROL U+]** o **[!UICONTROL Display order]** è corretto in **[!UICONTROL Emoticon list]**.

   ![](assets/emoticon_6.png)
