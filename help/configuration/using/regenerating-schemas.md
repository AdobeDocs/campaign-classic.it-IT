---
product: campaign
title: Rigenera schemi
description: Scopri come rigenerare gli schemi di Campaign
feature: Custom Resources
role: Developer
exl-id: 6c48cfea-6d20-4462-a485-71e1575a08a7
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 2%

---

# Rigenera schemi{#regenerating-schemas}

Quando modifichi uno schema e salvi le modifiche, lo schema esteso viene generato automaticamente. Tuttavia, potrebbe essere necessario rigenerare manualmente gli schemi per applicare le modifiche. Per eseguire questa operazione:

1. Seleziona gli schemi da rigenerare.
1. Fare clic con il pulsante destro del mouse e scegliere **[!UICONTROL Actions > Regenerate selected schemas...]**.
1. Fare clic su **[!UICONTROL OK]** per confermare e avviare il processo.

Puoi quindi controllare la struttura dello schema generato nelle schede Anteprima e Documentazione. Per ulteriori informazioni, consulta la sezione [Principi](../../configuration/using/data-schemas.md#principles).

>[!NOTE]
>
>Se devi forzare la rigenerazione di tutti gli schemi, ad esempio per risolvere alcuni problemi di dipendenza nei collegamenti inversi, puoi avviare il seguente comando dal server applicazioni di Adobe Campaign:
>
> `nlserver config -postupgrade -instance:`&lt;nome_istanza>` -force`
>
>È quindi necessario riavviare il server applicazioni Adobe Campaign e disconnettersi/riconnettersi alla console client.
