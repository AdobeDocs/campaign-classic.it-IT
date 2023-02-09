---
product: campaign
title: Gestione dei contenuti
description: Gestione dei contenuti
feature: Workflows, Data Management
exl-id: eb92a7c7-edfa-4062-b473-6d8b50d35e5f
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 3%

---

# Gestione dei contenuti{#content-management}

![](../../assets/v7-only.svg)

A **Gestione dei contenuti** consente di creare e manipolare un contenuto e generare file in base a tale contenuto. Questo contenuto può quindi essere consegnato tramite un’attività &quot;Delivery&quot;.

>[!CAUTION]
>
>La gestione dei contenuti è un modulo Adobe Campaign facoltativo. Controlla il contratto di licenza.

Le proprietà dell’attività sono suddivise in tre passaggi:

* **Selezione del contenuto**: il contenuto può essere stato creato in precedenza o può essere creato tramite l’attività .
* **Aggiornamento del contenuto**: l’attività può modificare l’oggetto del contenuto o importare tutto il contenuto XML.
* **Azione**: il contenuto risultante può essere salvato o generato.

   ![](assets/content_mgmt_edit.png)

   Per ulteriori informazioni sulla configurazione e l’utilizzo della gestione dei contenuti in Adobe Campaign, consulta [sezione](../../delivery/using/about-content-management.md).

1. **Contenuto**

   * **[!UICONTROL Specified in the transition]**

      Questa opzione consente di utilizzare il contenuto specificato nella transizione, ovvero l’evento che attiva la gestione del contenuto deve contenere un **[!UICONTROL contentId]** variabile. Questa variabile può essere stata impostata da una gestione dei contenuti precedente o da qualsiasi script.

   * **[!UICONTROL Explicit]**

      Questa opzione consente di selezionare un contenuto già creato tramite **[!UICONTROL Content]** campo . Questo campo è visibile solo quando **[!UICONTROL Explicit]** è selezionata.

      ![](assets/content_mgmt_explicit.png)

   * **[!UICONTROL Calculated by a script]**

      L’identificatore del contenuto viene calcolato da uno script. La **[!UICONTROL Script]** consente di definire un modello JavaScript per la valutazione dell’identificatore (chiave primaria) del contenuto. Questo campo è visibile solo quando **[!UICONTROL Calculated by a script]** è selezionata.

      ![](assets/content_mgmt_script.png)

   * **[!UICONTROL New, created from a publication template]**

      Crea un nuovo contenuto da un modello di pubblicazione. Il nuovo contenuto verrà salvato nel file specificato nel **[!UICONTROL String]** campo . La **[!UICONTROL Template]** specifica il modello di pubblicazione da utilizzare per creare il contenuto.

      ![](assets/content_mgmt_new.png)

1. **Aggiorna contenuto**

   * **[!UICONTROL Subject]**

      Questo campo ti consente di modificare l’oggetto del contenuto.

   * **[!UICONTROL Access to data from an XML feed]**

      Questa opzione consente di creare il contenuto da un documento XML scaricato tramite un foglio di stile XSL. Quando questa opzione è selezionata, la **[!UICONTROL URL]** specifica l’URL di download del contenuto XML. La **[!UICONTROL XSL stylesheet]** consente di specificare il foglio di stile da utilizzare per la trasformazione del documento XML scaricato. Questa proprietà è facoltativa.

      ![](assets/content_mgmt_xmlcontent.png)

1. **Azione da eseguire**

   * **[!UICONTROL Save]**

      Questa opzione consente di salvare il contenuto creato o modificato.

      La transizione in uscita viene attivata una sola volta, con il contenuto salvato nel **[!UICONTROL contentId]** come parametro.

   * **[!UICONTROL Generate]**

      Questa opzione salva il contenuto, quindi genera i file di output per ogni modello di trasformazione con pubblicazione di tipo File.

      ![](assets/content_mgmt_generate.png)

      La transizione in uscita viene attivata per ogni file generato con l’identificatore del contenuto salvato nel **[!UICONTROL contentId]** come parametro e come nome del file nel **[!UICONTROL filename]** variabile.

## Parametri di input {#input-parameters}

* contentId

Identificatore del contenuto da utilizzare se la **[!UICONTROL Specified in the transition]** è abilitata.

## Parametri di output {#output-parameters}

* contentId

   Identificatore di contenuto.

* nomefile

   Nome completo del file generato se l’azione selezionata è **[!UICONTROL Generate]**.

## Esempi {#examples}

Gli esempi sono forniti in questo [sezione](../../delivery/using/automating-via-workflows.md#examples).
