---
product: campaign
title: Gestione dei profili
description: Gestione dei profili
feature: Profiles
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
audience: platform
content-type: reference
topic-tags: profile-management
exl-id: e1d0556a-6f30-4863-9025-eb9c1b8b53d3
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 3%

---

# Gestire i profili{#managing-profiles}



## Struttura destinatari {#recipient-tree}

Per accedere alle funzionalità avanzate di gestione dei destinatari, devi modificare la struttura di Adobe Campaign. A questo scopo, fai clic su **[!UICONTROL Explorer]** nella barra degli strumenti.

Per impostazione predefinita, i destinatari sono memorizzati in **[!UICONTROL Profiles and targets]** della struttura Adobe Campaign. Dallo stesso nodo, puoi creare una o più cartelle e sottocartelle per archiviare i profili dei destinatari.

Ogni nodo coincide con una cartella. I dati di ciascuna cartella devono essere considerati partizionati l’uno dall’altro. Ciò significa che la gestione dei duplicati sarà più difficile per più cartelle di destinatari.

>[!NOTE]
>
>Per visualizzare l&#39;elenco di tutti i destinatari nel database, è necessario creare una visualizzazione. Ulteriori informazioni in [Cartelle e visualizzazioni](../../platform/using/access-management-folders.md).

## Sposta destinatari {#moving-recipients}

Puoi selezionare uno o più destinatari, trascinarli dall’elenco dei destinatari e rilasciarli nella cartella desiderata. Un messaggio di avviso richiede di confermare questa azione.

## Copiare un destinatario {#copying-a-recipient}

È possibile copiare un destinatario nella stessa cartella facendo clic con il pulsante destro del mouse sul destinatario desiderato e selezionando **[!UICONTROL Copy]**.

## Elimina destinatari {#deleting-recipients}

Per eliminare i destinatari, spostali in una cartella specifica e quindi elimina il contenuto di questa cartella. È **si consiglia vivamente di non utilizzare** il **[!UICONTROL Delete]** in questo caso.

Per eliminare una cartella, utilizza **[!UICONTROL Actions > Purge folder]** , accessibile facendo clic con il pulsante destro del mouse sulla cartella desiderata.

![](assets/s_ncs_user_purge_folder.png)

Clic **[!UICONTROL Start]** per avviare l&#39;operazione. Nella sezione centrale della finestra viene visualizzato lo stato di avanzamento, come illustrato di seguito:

![](assets/s_ncs_user_purge_folder_start.png)
