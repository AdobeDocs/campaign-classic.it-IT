---
product: campaign
title: Rigenera schemi
description: Scopri come rigenerare gli schemi di Campaign
feature: Custom Resources
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
exl-id: 6c48cfea-6d20-4462-a485-71e1575a08a7
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 2%

---

# Rigenera schemi{#regenerating-schemas}

Quando modifichi uno schema e salvi le modifiche, lo schema esteso viene generato automaticamente. Tuttavia, potrebbe essere necessario rigenerare manualmente gli schemi per applicare le modifiche. Per eseguire questa operazione:

1. Seleziona gli schemi da rigenerare.
1. Fai clic con il pulsante destro del mouse e scegli **[!UICONTROL Actions > Regenerate selected schemas...]** .
1. Clic **[!UICONTROL OK]** per confermare e avviare il processo.

Puoi quindi controllare la struttura dello schema generato nelle schede Anteprima e Documentazione. Per ulteriori informazioni, consulta [Principi](../../configuration/using/data-schemas.md#principles) sezione.

>[!NOTE]
>
>Se devi forzare la rigenerazione di tutti gli schemi, ad esempio per risolvere alcuni problemi di dipendenza nei collegamenti inversi, puoi avviare il seguente comando dal server applicazioni di Adobe Campaign:
>
> `nlserver config -postupgrade -instance:`&lt;instance_name>` -force`
>
>È quindi necessario riavviare il server applicazioni Adobe Campaign e disconnettersi/riconnettersi alla console client.
