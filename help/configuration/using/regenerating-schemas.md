---
solution: Campaign Classic
product: campaign
title: Rigenerazione degli schemi
description: Rigenerazione degli schemi
audience: configuration
content-type: reference
topic-tags: editing-schemas
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 6%

---


# Rigenerazione degli schemi{#regenerating-schemas}

Quando si modifica uno schema e si salvano le modifiche, lo schema esteso viene generato automaticamente. Tuttavia, potrebbe essere necessario rigenerare manualmente gli schemi per applicare le modifiche. Per eseguire questa operazione:

1. Selezionare gli schemi da rigenerare.
1. Fare clic con il pulsante destro del mouse e scegliere **[!UICONTROL Actions > Regenerate selected schemas...]** .
1. Fare clic su **[!UICONTROL OK]** per confermare e avviare il processo.

È quindi possibile controllare la struttura dello schema generato nelle schede Anteprima e Documentazione. Per ulteriori informazioni, consultare la sezione [Principi](../../configuration/using/data-schemas.md#principles).

>[!NOTE]
>
>Se è necessario forzare la rigenerazione di tutti gli schemi, ad esempio per risolvere alcuni problemi di dipendenza nei collegamenti invertiti, è possibile avviare il comando seguente dal server applicazione Adobe Campaign :
>
>**nlserver config -postupgrade -instance:`&lt;instance_name>&#39; -force**
>
>È quindi necessario riavviare  server applicazioni Adobe Campaign e disconnettersi/riconnettersi alla console client.
