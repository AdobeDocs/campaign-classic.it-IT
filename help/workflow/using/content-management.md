---
product: campaign
title: Gestione dei contenuti
description: Gestione dei contenuti
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: eb92a7c7-edfa-4062-b473-6d8b50d35e5f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 2%

---

# Gestione dei contenuti{#content-management}

![](../../assets/common.svg)

Un’attività **Gestione dei contenuti** consente di creare e manipolare un contenuto e generare file in base a tale contenuto. Questo contenuto può quindi essere consegnato tramite un’attività &quot;Delivery&quot;.

>[!CAUTION]
>
>La gestione dei contenuti è un modulo Adobe Campaign facoltativo. Controlla il contratto di licenza.

Le proprietà dell’attività sono suddivise in tre passaggi:

* **Selezione** del contenuto: il contenuto può essere stato creato in precedenza o può essere creato tramite l’attività .
* **Aggiornamento** del contenuto: l’attività può modificare l’oggetto del contenuto o importare tutto il contenuto XML.
* **Azione**: il contenuto risultante può essere salvato o generato.

   ![](assets/content_mgmt_edit.png)

   Per ulteriori informazioni sulla configurazione e l’utilizzo della gestione dei contenuti in Adobe Campaign, consulta questa [sezione](../../delivery/using/about-content-management.md).

1. **Contenuto**

   * **[!UICONTROL Specified in the transition]**

      Questa opzione consente di utilizzare il contenuto specificato nella transizione, ovvero l’evento che attiva la gestione del contenuto deve contenere una variabile **[!UICONTROL contentId]**. Questa variabile può essere stata impostata da una gestione dei contenuti precedente o da qualsiasi script.

   * **[!UICONTROL Explicit]**

      Questa opzione consente di selezionare un contenuto già creato tramite il campo **[!UICONTROL Content]** . Questo campo è visibile solo quando è selezionata l’opzione **[!UICONTROL Explicit]** .

      ![](assets/content_mgmt_explicit.png)

   * **[!UICONTROL Calculated by a script]**

      L’identificatore del contenuto viene calcolato da uno script. Il campo **[!UICONTROL Script]** ti consente di definire un modello JavaScript per la valutazione dell’identificatore (chiave primaria) del contenuto. Questo campo è visibile solo quando è selezionata l’opzione **[!UICONTROL Calculated by a script]** .

      ![](assets/content_mgmt_script.png)

   * **[!UICONTROL New, created from a publication template]**

      Crea un nuovo contenuto da un modello di pubblicazione. Questo nuovo contenuto verrà salvato nel file specificato nel campo **[!UICONTROL String]** . Il campo **[!UICONTROL Template]** specifica il modello di pubblicazione da utilizzare per creare il contenuto.

      ![](assets/content_mgmt_new.png)

1. **Aggiorna contenuto**

   * **[!UICONTROL Subject]**

      Questo campo ti consente di modificare l’oggetto del contenuto.

   * **[!UICONTROL Access to data from an XML feed]**

      Questa opzione consente di creare il contenuto da un documento XML scaricato tramite un foglio di stile XSL. Quando questa opzione è selezionata, il campo **[!UICONTROL URL]** specifica l’URL di download del contenuto XML. **[!UICONTROL XSL stylesheet]** consente di specificare il foglio di stile da utilizzare per trasformare il documento XML scaricato. Questa proprietà è facoltativa.

      ![](assets/content_mgmt_xmlcontent.png)

1. **Azione da eseguire**

   * **[!UICONTROL Save]**

      Questa opzione consente di salvare il contenuto creato o modificato.

      La transizione in uscita viene attivata una sola volta, con il contenuto salvato nella variabile **[!UICONTROL contentId]** come parametro.

   * **[!UICONTROL Generate]**

      Questa opzione salva il contenuto, quindi genera i file di output per ogni modello di trasformazione con pubblicazione di tipo File.

      ![](assets/content_mgmt_generate.png)

      La transizione in uscita viene attivata per ogni file generato con l’identificatore del contenuto salvato nella variabile **[!UICONTROL contentId]** come parametro e il nome del file nella variabile **[!UICONTROL filename]**.

## Parametri di input {#input-parameters}

* contentId

Identificatore del contenuto da utilizzare se l’opzione **[!UICONTROL Specified in the transition]** è abilitata.

## Parametri di output {#output-parameters}

* contentId

   Identificatore del contenuto.

* nomefile

   Nome completo del file generato se l’azione selezionata è **[!UICONTROL Generate]**.

## Esempi {#examples}

Gli esempi sono forniti in questa [sezione](../../delivery/using/automating-via-workflows.md#examples).
