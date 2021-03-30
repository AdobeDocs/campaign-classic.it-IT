---
solution: Campaign Classic
product: campaign
title: Gestione dei profili
description: Gestione dei profili
audience: platform
content-type: reference
topic-tags: profile-management
translation-type: tm+mt
source-git-commit: b05b8daad449aeb1f5226fdd76744776c6553b63
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 1%

---


# Gestisci profili{#managing-profiles}

## Albero dei destinatari {#recipient-tree}

Per accedere alle funzionalità avanzate di gestione dei destinatari, devi modificare la struttura ad albero di Adobe Campaign. A questo scopo, fai clic sul pulsante **[!UICONTROL Explorer]** nella barra degli strumenti.

Per impostazione predefinita, i destinatari sono memorizzati nel nodo **[!UICONTROL Profiles and targets]** della struttura di Adobe Campaign. Dallo stesso nodo, puoi creare una o più cartelle e sottocartelle per memorizzare i profili dei destinatari.

Ogni nodo coincide con una cartella. I dati di ciascuna cartella devono essere considerati partizionati l’uno dall’altro. Ciò significa che la gestione dei duplicati sarà più complessa per più cartelle di destinatari.

>[!NOTE]
>
>Per visualizzare l’elenco di tutti i destinatari nel database, è necessario creare una visualizzazione. Ulteriori informazioni in [Cartelle e visualizzazioni](../../platform/using/access-management-folders.md).

## Sposta i destinatari {#moving-recipients}

Puoi selezionare uno o più destinatari, trascinarli dall’elenco dei destinatari e rilasciarli nella cartella desiderata. Un messaggio di avviso ti chiede di confermare questa azione.

## Copia un destinatario {#copying-a-recipient}

Puoi copiare un destinatario nella stessa cartella facendo clic con il pulsante destro del mouse sul destinatario desiderato e selezionando **[!UICONTROL Copy]**.

## Elimina destinatari {#deleting-recipients}

Per eliminare i destinatari, spostali in una cartella specifica e quindi elimina il contenuto di questa cartella. In questo caso si consiglia vivamente **di non utilizzare l&#39;opzione** **[!UICONTROL Delete]**.

Per eliminare una cartella, utilizza il menu **[!UICONTROL Actions > Purge folder]**, accessibile facendo clic con il pulsante destro del mouse sulla cartella desiderata.

![](assets/s_ncs_user_purge_folder.png)

Fai clic su **[!UICONTROL Start]** per avviare l&#39;operazione. Nella sezione centrale della finestra viene visualizzato lo stato di avanzamento, come illustrato di seguito:

![](assets/s_ncs_user_purge_folder_start.png)

