---
title: Rigenerazione degli schemi
seo-title: Rigenerazione degli schemi
description: Rigenerazione degli schemi
seo-description: null
page-status-flag: never-activated
uuid: 455c37f1-cbaf-4503-b2e9-5eec7fad6e97
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 0f7c835e-b429-422b-87ae-1234c7dd8fe6
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 8%

---


# Rigenerazione degli schemi{#regenerating-schemas}

Quando si modifica uno schema e si salvano le modifiche, lo schema esteso viene generato automaticamente. Tuttavia, potrebbe essere necessario rigenerare manualmente gli schemi per applicare le modifiche. Per eseguire questa operazione:

1. Selezionare gli schemi da rigenerare.
1. Fate clic con il pulsante destro del mouse e scegliete **[!UICONTROL Actions > Regenerate selected schemas...]** .
1. Fate clic **[!UICONTROL OK]** per confermare e avviare il processo.

È quindi possibile controllare la struttura dello schema generato nelle schede Anteprima e Documentazione. For more on this, refer to the [Principles](../../configuration/using/data-schemas.md#principles) section.

>[!NOTE]
>
>Se è necessario forzare la rigenerazione di tutti gli schemi, ad esempio per risolvere alcuni problemi di dipendenza nei collegamenti invertiti, è possibile avviare il comando seguente dal server applicazione Adobe Campaign :
>
>**nlserver config -postupgrade -instance:`&lt;nome_istanza>&#39; -force**
>
>È quindi necessario riavviare  server applicazioni Adobe Campaign e disconnettersi/riconnettersi alla console client.
