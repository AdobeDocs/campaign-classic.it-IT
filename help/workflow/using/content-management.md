---
product: campaign
title: Gestione dei contenuti
description: Gestione dei contenuti
feature: Workflows, Data Management
exl-id: eb92a7c7-edfa-4062-b473-6d8b50d35e5f
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 2%

---

# Gestione dei contenuti{#content-management}



Un&#39;attività di **gestione dei contenuti** consente di creare e manipolare un contenuto e generare file basati su tale contenuto. Questi contenuti possono quindi essere consegnati tramite un’attività &quot;Delivery&quot;.

>[!CAUTION]
>
>La gestione dei contenuti è un modulo Adobe Campaign opzionale. Controlla il contratto di licenza.

Le proprietà dell’attività sono suddivise in tre passaggi:

* **Selezione contenuto**: il contenuto può essere stato creato in precedenza o può essere creato tramite l&#39;attività.
* **Aggiornamento contenuto**: l&#39;attività può modificare l&#39;oggetto del contenuto o importare tutto il contenuto XML.
* **Azione**: il contenuto risultante può essere salvato o generato.

  ![](assets/content_mgmt_edit.png)

  Per ulteriori informazioni sulla configurazione e sull&#39;utilizzo della gestione dei contenuti in Adobe Campaign, consulta questa [sezione](../../delivery/using/about-content-management.md).

1. **Contenuto**

   * **[!UICONTROL Specified in the transition]**

     Questa opzione consente di utilizzare il contenuto specificato nella transizione, ovvero l&#39;evento che attiva content management deve contenere una variabile **[!UICONTROL contentId]**. Questa variabile può essere stata impostata da una gestione del contenuto precedente o da qualsiasi script.

   * **[!UICONTROL Explicit]**

     Questa opzione consente di selezionare un contenuto già creato tramite il campo **[!UICONTROL Content]**. Questo campo è visibile solo quando è selezionata l&#39;opzione **[!UICONTROL Explicit]**.

     ![](assets/content_mgmt_explicit.png)

   * **[!UICONTROL Calculated by a script]**

     L’identificatore del contenuto viene calcolato da uno script. Il campo **[!UICONTROL Script]** consente di definire un modello JavaScript che valuta l&#39;identificatore (chiave primaria) del contenuto. Questo campo è visibile solo quando è selezionata l&#39;opzione **[!UICONTROL Calculated by a script]**.

     ![](assets/content_mgmt_script.png)

   * **[!UICONTROL New, created from a publication template]**

     Crea un nuovo contenuto da un modello di pubblicazione. Il nuovo contenuto verrà salvato nel file specificato nel campo **[!UICONTROL String]**. Il campo **[!UICONTROL Template]** specifica il modello di pubblicazione da utilizzare per creare il contenuto.

     ![](assets/content_mgmt_new.png)

1. **Aggiorna contenuto**

   * **[!UICONTROL Subject]**

     Questo campo consente di modificare l’oggetto del contenuto.

   * **[!UICONTROL Access to data from an XML feed]**

     Questa opzione consente di creare il contenuto da un documento XML scaricato tramite un foglio di stile XSL. Quando questa opzione è selezionata, il campo **[!UICONTROL URL]** specifica l&#39;URL di download del contenuto XML. **[!UICONTROL XSL stylesheet]** consente di specificare il foglio di stile da utilizzare per trasformare il documento XML scaricato. Questa proprietà è facoltativa.

     ![](assets/content_mgmt_xmlcontent.png)

1. **Azione da eseguire**

   * **[!UICONTROL Save]**

     Questa opzione salva il contenuto creato o modificato.

     La transizione in uscita viene attivata una sola volta, con il contenuto salvato nella variabile **[!UICONTROL contentId]** come parametro.

   * **[!UICONTROL Generate]**

     Questa opzione consente di salvare il contenuto e quindi di generare i file di output per ciascun modello di trasformazione con una pubblicazione di tipo &quot;File&quot;.

     ![](assets/content_mgmt_generate.png)

     La transizione in uscita viene attivata per ogni file generato con l&#39;identificatore del contenuto salvato nella variabile **[!UICONTROL contentId]** come parametro e il nome file nella variabile **[!UICONTROL filename]**.

## Parametri di input {#input-parameters}

* contentId

Identificatore del contenuto da utilizzare se l&#39;opzione **[!UICONTROL Specified in the transition]** è abilitata.

## Parametri di output {#output-parameters}

* contentId

  Identificatore del contenuto.

* nome file

  Nome completo del file generato se l&#39;azione selezionata è **[!UICONTROL Generate]**.

## Esempi {#examples}

Esempi forniti in questa [sezione](../../delivery/using/automating-via-workflows.md#examples).
