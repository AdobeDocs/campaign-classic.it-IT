---
product: campaign
title: Personalizzare l’elenco delle emoticon
description: Scopri come personalizzare l’elenco degli emoticon quando utilizzi Adobe Campaign Classic
feature: Email, Push
exl-id: b8642df3-1960-4f2c-8273-c3988a3e85f0
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 3%

---

# Personalizzare l’elenco delle emoticon {#customize-emoticons}

![](../../assets/common.svg)

L’elenco di emoticon visualizzato nella finestra a comparsa è governato da un’enumerazione che consente di visualizzare i valori in un elenco per limitare le scelte dell’utente per un dato campo.
L&#39;ordine dell&#39;elenco degli emoticon può essere personalizzato, è anche possibile aggiungere altri emoticon alla tua lista.
Le e-mail sono disponibili per e-mail e per ulteriori informazioni, consulta questo articolo [page](defining-the-email-content.md#inserting-emoticons).

## Aggiunta di un nuovo emoticon {#add-new-emoticon}

>[!CAUTION]
>
>L’elenco delle emoticon non può visualizzare più di 81 voci.

1. Scegli la tua nuova emoticon da aggiungere da questo [page](https://unicode.org/emoji/charts/full-emoji-list.html). Tieni presente che deve essere compatibile con le diverse piattaforme quali browser e sistema operativo.

1. Da **[!UICONTROL Explorer]**, seleziona **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Enumerations]** e fai clic su **[!UICONTROL Emoticon list]** enumerazione standard.

   >[!NOTE]
   >
   >Le enumerazioni predefinite possono essere gestite solo da un amministratore della console Adobe Campaign Classic.

   ![](assets/emoticon_1.png)

1. Fai clic su **[!UICONTROL Add]**.

1. Compila i campi:

   * **[!UICONTROL U+]**: Codice del tuo nuovo emoticon. Trovi l&#39;elenco dei codici degli emoticon in questo [page](https://unicode.org/emoji/charts/full-emoji-list.html).
Per evitare problemi di compatibilità, consigliamo di scegliere gli emoticon supportati sui browser e su ogni sistema operativo.

   * **[!UICONTROL Label]**: Etichetta del tuo nuovo emoticon.

   ![](assets/emoticon_5.png)

1. Fai clic su **[!UICONTROL Ok]** then **[!UICONTROL Save]** al termine della configurazione.
Il nuovo emoticon verrà posizionato automaticamente nel negozio.

1. Per visualizzarlo nel **[!UICONTROL Insert emoticon]** finestra delle consegne, seleziona l’emoticon appena creato facendo doppio clic su di esso.

1. Scegli nella **[!UICONTROL Display order]** elenco a discesa in cui viene visualizzato l’ordine del nuovo emoticon. Selezionando un ordine di visualizzazione già assegnato, l’emoticon esistente verrà automaticamente spostato nello store.

   <br>In questo esempio, abbiamo scelto il numero di ordine di visualizzazione 61, il che significa che se una voce aveva già questo ordine verrà automaticamente spostata nello store e la nostra nuova voce avrà il suo posto nell&#39;elenco di enumerazione.

   ![](assets/emoticon_2.png)

1. Il tuo nuovo emoticon è stato aggiunto al **[!UICONTROL Insert emoticon list]** enumerazione standard. È possibile modificarne la **[!UICONTROL Display order]** in qualsiasi momento o spostalo al negozio se non ne hai più bisogno.

1. Per tenere conto delle modifiche, disconnettiti e riconnettiti da Adobe Campaign Classic. Se il tuo nuovo emoticon continua a non apparire nel **[!UICONTROL Insert emoticon]** finestra a comparsa, potrebbe essere necessario cancellare la cache. Per ulteriori informazioni, consulta questa [sezione](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear).

1. Il nuovo emoticon si trova ora nelle consegne nel **[!UICONTROL Insert emoticon]** finestra a comparsa nella 61a posizione configurata nei passaggi precedenti. Per ulteriori informazioni su come utilizzare gli emoticon nelle consegne, consulta questo [page](defining-the-email-content.md#inserting-emoticons).

   ![](assets/emoticon_4.png)

1. Se i seguenti emoticon appaiono nel tuo **[!UICONTROL Insert emoticon]** finestra a comparsa, ciò significa che non sono stati configurati correttamente. Controlla se la tua **[!UICONTROL U+]** codice o **[!UICONTROL Display order]** è corretto in **[!UICONTROL Emoticon list]**.

   ![](assets/emoticon_6.png)
