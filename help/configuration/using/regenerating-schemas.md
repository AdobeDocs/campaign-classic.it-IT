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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e7ff12260d875b85256c8678fa8d100fd355398e

---


# Rigenerazione degli schemi{#regenerating-schemas}

Quando modificate uno schema e salvate le modifiche, lo schema esteso viene generato automaticamente. Tuttavia, potrebbe essere necessario rigenerare manualmente gli schemi per applicare le modifiche. Per eseguire questa operazione:

1. Selezionare gli schemi da rigenerare.
1. Fate clic con il pulsante destro del mouse e scegliete **[!UICONTROL Actions > Regenerate selected schemas...]** .
1. Fate clic **[!UICONTROL OK]** per confermare e avviare il processo.

È quindi possibile controllare la struttura dello schema generato nelle schede Anteprima e Documentazione. Per ulteriori informazioni, consulta la sezione [Principi](../../configuration/using/data-schemas.md#principles) .

>[!NOTE]
>
>Se devi forzare la rigenerazione di tutti gli schemi, ad esempio per risolvere alcuni problemi di dipendenza nei collegamenti invertiti, puoi avviare il comando seguente dal server dell’applicazione Adobe Campaign:

>**nlserver config -postupgrade -instance:`&lt;nome_istanza>&#39; -force**

>È quindi necessario riavviare il server dell&#39;applicazione Adobe Campaign e disconnettersi/riconnettersi alla console client.

