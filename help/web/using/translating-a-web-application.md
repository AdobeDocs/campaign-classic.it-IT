---
product: campaign
title: Progettare un’applicazione web
description: Progettare un’applicazione web
badge-v7: label="v7" type="Informative" tooltip="Applicabile a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Web Apps
exl-id: 82c5c610-8161-4686-aa79-1b690e763765
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 5%

---

# Progettare un’applicazione web{#translating-a-web-application}



Puoi tradurre le pagine di applicazioni web create con l’editor di contenuti digitali (DCE) di Adobe Campaign.

Se selezioni almeno una lingua aggiuntiva tramite **[!UICONTROL Localization]** scheda in **[!UICONTROL Properties]** di un’applicazione web, diventa disponibile una nuova opzione quando si aggiunge un blocco di contenuto HTML in una pagina modificata con DCE.

Questa opzione ti consente di indicare se il contenuto del blocco deve essere tradotto o meno.

Le stringhe da tradurre vengono raccolte nello stesso modo delle altre stringhe dell’applicazione web, tramite **[!UICONTROL Translations]** dell&#39;applicazione. Per ulteriori informazioni, consulta [questa pagina](translating-a-web-form.md).

Per contrassegnare le stringhe da tradurre:

1. Aprire una pagina di contenuto modificata con DCE in un&#39;applicazione Web.

   ![](assets/dce_translation_3.png)

1. Seleziona un blocco di HTML.
1. Nel blocco dei parametri a destra, **[!UICONTROL Localization]** consente di contrassegnare il contenuto del blocco selezionato. Per impostazione predefinita, deve essere tradotto solo il titolo della pagina.

   ![](assets/dce_translation_1.png)

   >[!NOTE]
   >
   >Le stringhe non devono superare i 1023 caratteri.

   Esistono tre casi specifici:

   * Quando il blocco selezionato contiene più stringhe/blocchi, viene contrassegnato come una singola stringa da tradurre. La stringa contiene quindi il codice HTML degli elementi all’interno di questo blocco.
   * Se si desidera contrassegnare un blocco contenente più stringhe e almeno una di esse è già contrassegnata, viene visualizzato un avviso. Puoi quindi rimuovere il flag dalla stringa isolata e aggiungere l’intero blocco.

     ![](assets/dce_translation_4.png)

   * Quando desideri rimuovere il flag da una stringa contenuta in un blocco già contrassegnato, non puoi modificare direttamente l’opzione di traduzione della stringa. Tuttavia, puoi accedere al blocco contenente la stringa per modificarlo.

     ![](assets/dce_translation_2.png)

1. Dopo aver completato il contrassegno delle stringhe, torna all’applicazione Web e seleziona la **[!UICONTROL Translations]** scheda.
1. Seleziona **[!UICONTROL Collect the strings to translate]**. Le stringhe contrassegnate in DCE vengono aggiunte alle stringhe dell&#39;applicazione Web.

   >[!NOTE]
   >
   >Una volta raccolte le stringhe, non verranno rimosse dall&#39;elenco se rimuovi il flag di traduzione in DCE. Questo consente di mantenerli nella memoria di traduzione.

1. Traduci e approva le stringhe.

   Puoi quindi visualizzare in anteprima le traduzioni selezionando la lingua desiderata dall’ **[!UICONTROL Preview]** nell&#39;applicazione Web.
