---
product: campaign
title: Rigenerare gli schemi
description: Scopri come generare gli schemi di Campaign
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 6c48cfea-6d20-4462-a485-71e1575a08a7
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 2%

---

# Rigenerare gli schemi{#regenerating-schemas}

Quando modifichi uno schema e salvi le modifiche, lo schema esteso viene generato automaticamente. Tuttavia, potrebbe essere necessario rigenerare manualmente gli schemi per applicare le modifiche. Per eseguire questa operazione:

1. Seleziona gli schemi da rigenerare.
1. Fai clic con il pulsante destro del mouse e scegli **[!UICONTROL Actions > Regenerate selected schemas...]** .
1. Fai clic su **[!UICONTROL OK]** per confermare e avviare il processo.

Puoi quindi controllare la struttura dello schema generato nelle schede Anteprima e Documentazione . Per ulteriori informazioni, consulta la sezione [Principi](../../configuration/using/data-schemas.md#principles) sezione .

>[!NOTE]
>
>Se è necessario forzare la rigenerazione di tutti gli schemi, ad esempio per risolvere alcuni problemi di dipendenza nei collegamenti inversi, è possibile avviare il seguente comando dal server dell&#39;applicazione Adobe Campaign:
>
> `nlserver config -postupgrade -instance:`&lt;instance_name>` -force`
>
>È quindi necessario riavviare l&#39;application server di Adobe Campaign e disconnettersi/riconnettersi alla console client.
