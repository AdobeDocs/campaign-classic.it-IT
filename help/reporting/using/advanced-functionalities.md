---
title: Funzionalità avanzate
seo-title: Funzionalità avanzate
description: Funzionalità avanzate
seo-description: null
page-status-flag: never-activated
uuid: 4dbf4750-0226-4f96-98d8-ec49b20374ac
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 0c264783-2775-4ec6-8d49-cd9a45a18d60
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 5%

---


# Funzionalità avanzate{#advanced-functionalities}

## Aggiunta di uno script {#adding-a-script}

### Attività script {#script-activity}

Questa attività consente di elaborare i dati e creare facilmente query complesse che non abilitano SQL Language.

È sufficiente inserire la query nella finestra dello script.

La **[!UICONTROL Texts]** scheda consente di definire le stringhe di testo. Possono quindi essere utilizzati con la sintassi seguente: **$(Identifier)**. Per ulteriori informazioni sull&#39;uso dei testi, vedere [Aggiunta di un&#39;intestazione e di un piè di pagina](../../reporting/using/element-layout.md#adding-a-header-and-a-footer).

>[!CAUTION]
>
>NON è consigliabile utilizzare il codice JavaScript per creare aggregati.

Per creare una cronologia del rapporto, aggiungere la riga seguente alla query JavaScript per salvare i dati archiviati:

```
if( ctx.@_historyId.toString().length == 0 )
```

In caso contrario verranno visualizzati i dati correnti.

### Script esterno {#external-script}

È possibile utilizzare uno script esterno che verrà eseguito sul lato server e/o client. Per eseguire questa operazione:

1. Modificate le proprietà del rapporto e fate clic sul **[!UICONTROL Scripts]**.
1. Fare clic **[!UICONTROL Add]** e selezionare lo script a cui fare riferimento.
1. Selezionate quindi la modalità di esecuzione.

   Se si aggiungono diversi script, utilizzare le frecce della barra degli strumenti per definire la sequenza di esecuzione.

   ![](assets/reporting_custom_js.png)

## Chiamata di un altro rapporto {#calling-up-another-report}

### Attività Jump {#jump-activity}

Un salto è come una transizione senza una freccia: consente di passare da un&#39;attività all&#39;altra o di accedere a un altro rapporto.
