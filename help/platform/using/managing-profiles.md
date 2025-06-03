---
product: campaign
title: Gestione dei profili
description: Gestione dei profili
feature: Profiles
audience: platform
content-type: reference
topic-tags: profile-management
exl-id: e1d0556a-6f30-4863-9025-eb9c1b8b53d3
source-git-commit: 42cec0e9bede94a2995a5ad442822512bda14f2b
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 2%

---

# Gestire i profili{#managing-profiles}



## Struttura destinatari {#recipient-tree}

Per accedere alle funzionalità avanzate di gestione dei destinatari, devi modificare la struttura di Adobe Campaign. A tale scopo, fare clic sul pulsante **[!UICONTROL Explorer]** nella barra degli strumenti.

Per impostazione predefinita, i destinatari sono memorizzati nel nodo **[!UICONTROL Profiles and targets]** della struttura Adobe Campaign. Dallo stesso nodo, puoi creare una o più cartelle e sottocartelle per archiviare i profili dei destinatari.

Ogni nodo coincide con una cartella. I dati di ciascuna cartella devono essere considerati partizionati l’uno dall’altro. Ciò significa che la gestione dei duplicati sarà più difficile per più cartelle di destinatari.

>[!NOTE]
>
> * Per visualizzare l&#39;elenco di tutti i destinatari nel database, è necessario creare una visualizzazione. Ulteriori informazioni in [Cartelle e visualizzazioni](../../platform/using/access-management-folders.md).
> * Per ulteriori informazioni su come gestire i profili, consulta la [documentazione di Campaign v8](https://experienceleague.adobe.com/it/docs/campaign/campaign-v8/config/configuration/folders-and-views){target=_blank}.


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