---
title: Traduzione di un’applicazione Web
seo-title: Traduzione di un’applicazione Web
description: Traduzione di un’applicazione Web
seo-description: null
page-status-flag: never-activated
uuid: 7b24a872-d3d1-4473-a6f9-96ba2a0eee8b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-applications
discoiquuid: 328e5b2f-8596-4eda-8ac5-57cb29bfb691
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c9c9d5f96856ce9e19571bad032d2bf04eaa60bd

---


# Traduzione di un’applicazione Web{#translating-a-web-application}

Puoi tradurre le pagine dell&#39;applicazione Web create con Adobe Campaign Digital Content Editor (DCE).

Se si seleziona almeno una lingua aggiuntiva tramite la **[!UICONTROL Localization]** **[!UICONTROL Properties]** scheda di un&#39;applicazione Web, diventa disponibile una nuova opzione quando si aggiunge un blocco di contenuto HTML in una pagina modificata con DCE.

Questa opzione consente di indicare se il contenuto del blocco deve essere convertito o meno.

Le stringhe da convertire vengono raccolte nello stesso modo delle altre stringhe dell&#39;applicazione Web, tramite la **[!UICONTROL Translations]** scheda dell&#39;applicazione. For more on this, refer to [this page](../../web/using/translating-a-web-form.md).

Per contrassegnare le stringhe da convertire:

1. Aprire una pagina di contenuto modificata con DCE in un&#39;applicazione Web.

   ![](assets/dce_translation_3.png)

1. Selezionare un blocco HTML.
1. Nel blocco dei parametri a destra, l&#39; **[!UICONTROL Localization]** opzione consente di contrassegnare il contenuto del blocco selezionato. Per impostazione predefinita, solo il titolo della pagina deve essere convertito.

   ![](assets/dce_translation_1.png)

   >[!NOTE]
   >
   >Le stringhe non devono superare i 1023 caratteri.

   Esistono tre casi specifici:

   * Quando il blocco selezionato contiene più stringhe/blocchi, viene contrassegnato come una singola stringa da convertire. La stringa contiene quindi il codice HTML degli elementi all&#39;interno del blocco.
   * Se si desidera contrassegnare un blocco contenente più stringhe e se almeno una di queste stringhe è già segnalata, viene visualizzato un avviso. È quindi possibile rimuovere il flag dalla stringa isolata e aggiungere l&#39;intero blocco.

      ![](assets/dce_translation_4.png)

   * Se si desidera rimuovere il flag da una stringa contenuta in un blocco già contrassegnato, non è possibile modificare direttamente l&#39;opzione di conversione delle stringhe. Tuttavia, è possibile accedere al blocco contenente la stringa per modificarla.

      ![](assets/dce_translation_2.png)

1. Dopo aver contrassegnato le stringhe, tornare all&#39;applicazione Web e selezionare la **[!UICONTROL Translations]** scheda.
1. Selezionare **[!UICONTROL Collect the strings to translate]**. Le stringhe contrassegnate in DCE vengono aggiunte alle stringhe dell&#39;applicazione Web.

   >[!NOTE]
   >
   >Una volta raccolte, le stringhe non verranno rimosse dall&#39;elenco se si rimuove il flag di traduzione in DCE. Questo permette di mantenerli nella memoria di traduzione.

1. Traduci e approva le stringhe.

   Potete quindi visualizzare l&#39;anteprima delle traduzioni selezionando la lingua desiderata dalla **[!UICONTROL Preview]** scheda nell&#39;applicazione Web.

