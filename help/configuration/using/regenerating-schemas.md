---
product: campaign
title: Rigenera schemi
description: Scopri come rigenerare gli schemi di Campaign
feature: Custom Resources
role: Developer
exl-id: 6c48cfea-6d20-4462-a485-71e1575a08a7
TQID: https://experienceleague.adobe.com/gkWtbp4Vw-wY5yHsd4xJbDx04u3aPhdg-8kB5OXZu94
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
subfeature_v2:
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 131
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
