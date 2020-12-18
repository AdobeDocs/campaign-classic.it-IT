---
solution: Campaign Classic
product: campaign
title: Traduzione di un’applicazione web
description: Traduzione di un’applicazione web
audience: web
content-type: reference
topic-tags: web-applications
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 5%

---


# Traduzione di un’applicazione web{#translating-a-web-application}

È possibile tradurre le pagine dell&#39;applicazione Web create con l&#39;editor di contenuti digitali  Adobe Campaign (DCE).

Se si seleziona almeno una lingua aggiuntiva tramite la scheda **[!UICONTROL Localization]** di un&#39;applicazione Web, una nuova opzione diventa disponibile quando si aggiunge un blocco di contenuto HTML in una pagina modificata con DCE.**[!UICONTROL Properties]**

Questa opzione consente di indicare se il contenuto del blocco deve essere convertito o meno.

Le stringhe da convertire vengono raccolte nello stesso modo delle altre stringhe dell&#39;applicazione Web, tramite la scheda **[!UICONTROL Translations]** dell&#39;applicazione. Per ulteriori informazioni, consulta [questa pagina](../../web/using/translating-a-web-form.md).

Per contrassegnare le stringhe da convertire:

1. Aprite una pagina di contenuto modificata con DCE in un’applicazione Web.

   ![](assets/dce_translation_3.png)

1. Selezionare un blocco HTML.
1. Nel blocco dei parametri a destra, l&#39;opzione **[!UICONTROL Localization]** consente di contrassegnare il contenuto del blocco selezionato. Per impostazione predefinita, solo il titolo della pagina deve essere convertito.

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

1. Dopo aver contrassegnato le stringhe, tornare all&#39;applicazione Web e selezionare la scheda **[!UICONTROL Translations]**.
1. Seleziona **[!UICONTROL Collect the strings to translate]**. Le stringhe contrassegnate in DCE vengono aggiunte alle stringhe dell&#39;applicazione Web.

   >[!NOTE]
   >
   >Una volta raccolte, le stringhe non verranno rimosse dall&#39;elenco se si rimuove il flag di traduzione in DCE. Questo permette di mantenerli nella memoria di traduzione.

1. Traduci e approva le stringhe.

   Potete quindi visualizzare l&#39;anteprima delle traduzioni selezionando la lingua desiderata dalla scheda **[!UICONTROL Preview]** dell&#39;applicazione Web.

