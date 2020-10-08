---
title: Gestione dei profili
seo-title: Gestione dei profili
description: Gestione dei profili
seo-description: null
page-status-flag: never-activated
uuid: f045dd5e-e069-4293-8c44-49d71071b041
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: profile-management
discoiquuid: ef7aa3a0-249f-46eb-9300-5b97bce31c8c
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 3%

---


# Gestione dei profili{#managing-profiles}

## Struttura destinatari {#recipient-tree}

Per accedere alle funzionalità avanzate di gestione dei destinatari, è necessario modificare la struttura  Adobe Campaign. A tale scopo, fare clic sul **[!UICONTROL Explorer]** pulsante nella barra degli strumenti.

Per impostazione predefinita, i destinatari sono memorizzati nel **[!UICONTROL Profiles and targets]** nodo della struttura di Adobe Campaign . Dallo stesso nodo, puoi creare una o più cartelle e sottocartelle per memorizzare i profili dei destinatari.

Ogni nodo coincide con una cartella. I dati di ciascuna cartella devono essere considerati partizionati l&#39;uno dall&#39;altro. Ciò significa che la gestione dei duplicati sarà più complessa per più cartelle di destinatari.

>[!NOTE]
>
>Per visualizzare l&#39;elenco di tutti i destinatari nel database, è necessario creare una visualizzazione. Consultare [Cartelle e viste](../../platform/using/access-management.md#folders-and-views).

## Spostamento dei destinatari {#moving-recipients}

Puoi selezionare uno o più destinatari, trascinarli dall’elenco dei destinatari e rilasciarli nella cartella desiderata. Viene visualizzato un messaggio di avviso che richiede di confermare l’azione.

## Copia di un destinatario {#copying-a-recipient}

Per copiare un destinatario nella stessa cartella, fai clic con il pulsante destro del mouse sul destinatario desiderato e seleziona **[!UICONTROL Copy]**.

## Eliminazione dei destinatari {#deleting-recipients}

Per eliminare i destinatari, spostateli in una cartella specifica, quindi rimuovete il contenuto di questa cartella. È **vivamente consigliato non utilizzare** l&#39; **[!UICONTROL Delete]** opzione in questo caso.

Per eliminare una cartella, usate il **[!UICONTROL Actions > Purge folder]** menu a cui si accede facendo clic con il pulsante destro del mouse sulla cartella desiderata.

![](assets/s_ncs_user_purge_folder.png)

Fare clic **[!UICONTROL Start]** per avviare l&#39;operazione. Nella sezione centrale della finestra viene visualizzato lo stato di avanzamento, come illustrato di seguito:

![](assets/s_ncs_user_purge_folder_start.png)

