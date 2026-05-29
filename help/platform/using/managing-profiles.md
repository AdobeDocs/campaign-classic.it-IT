---
product: campaign
title: Gestione dei profili
description: Gestione dei profili
feature: Profiles
audience: platform
content-type: reference
topic-tags: profile-management
exl-id: e1d0556a-6f30-4863-9025-eb9c1b8b53d3
hide: true
TQID: https://experienceleague.adobe.com/cdeZeLKKuMwxLq0uvsh5yrYSyLGN5wkzhDsUukb885c
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: afa4204e-6d08-4e29-bc35-26aafb656d48
subfeature_v2: id: f529d0bd-1401-4c88-9833-43228cc1d40fid: d6330382-c886-4f7a-a4f7-74e3f36c0d9cid: f5293531-9312-4099-bfa3-9e67df6a8750id: efa38731-2723-4334-8d8b-a778af834835
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 160
ht-degree: 18%

---

# Gestire i profili{#managing-profiles}



## Struttura destinatari {#recipient-tree}

Per accedere alle funzionalità avanzate di gestione dei destinatari, devi modificare la struttura di Adobe Campaign. A tale scopo, fare clic sul pulsante **[!UICONTROL Explorer]** nella barra degli strumenti.

Per impostazione predefinita, i destinatari sono memorizzati nel nodo **[!UICONTROL Profiles and targets]** della struttura Adobe Campaign. Dallo stesso nodo, puoi creare una o più cartelle e sottocartelle per archiviare i profili dei destinatari.

Ogni nodo coincide con una cartella. I dati di ciascuna cartella devono essere considerati partizionati l’uno dall’altro. Ciò significa che la gestione dei duplicati sarà più difficile per più cartelle di destinatari.

>[!NOTE]
>
> * Per visualizzare l&#39;elenco di tutti i destinatari nel database, è necessario creare una visualizzazione. Ulteriori informazioni sono disponibili nella [documentazione di Campaign v8 (console)](https://experienceleague.adobe.com/it/docs/campaign/campaign-v8/config/configuration/folders-and-views){target=_blank}.
>
> * Per ulteriori informazioni su come gestire i profili, consulta la [documentazione di Campaign v8 (console)](https://experienceleague.adobe.com/it/docs/campaign/campaign-v8/config/configuration/folders-and-views){target=_blank}.


<!--
## Move recipients {#moving-recipients}

You can select one or more recipients, drag them from the recipient list, and drop them in the desired folder. A warning message asks you to confirm this action.

## Copy a recipient {#copying-a-recipient}

You can copy a recipient in the same folder by right-clicking the desired recipient and selecting **[!UICONTROL Copy]**.

## Delete recipients {#deleting-recipients}

To delete recipients, move them to a specific folder and then purge the content of this folder. It is **strongly recommended not to use** the **[!UICONTROL Delete]** option in this case.

To purge a folder, use the **[!UICONTROL Actions > Purge folder]** menu, accessed by right-clicking the desired folder.

![](assets/s_ncs_user_purge_folder.png)

Click **[!UICONTROL Start]** to launch the operation. The middle section of the window displays the progress status, as shown below:

![](assets/s_ncs_user_purge_folder_start.png)
-->