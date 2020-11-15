---
title: Accesso a un database esterno
seo-title: Accesso a un database esterno
description: Accesso a un database esterno
seo-description: null
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
translation-type: tm+mt
source-git-commit: 9bbde65aea6735e30e95e75c2b6ae5445d4a2bdd
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 1%

---


# Definizione della mappatura dei dati {#defining-data-mapping}

 Adobe Campaign consente di definire la mappatura dei dati in una tabella esterna.

A tal fine, una volta creato lo schema della tabella esterna, è necessario creare una nuova mappatura di consegna per utilizzare i dati in questa tabella come destinazione di consegna.

A questo scopo, eseguire i seguenti passaggi:

1. Create una nuova mappatura di consegna e scegliete la dimensione di targeting, lo schema appena creato, ad esempio.

   ![](assets/wf_new_mapping_create_fda.png)

1. Indicate i campi in cui sono memorizzate le informazioni di consegna (cognome, nome, e-mail, indirizzo, ecc.).

   ![](assets/wf_new_mapping_define_join.png)

1. Specificate i parametri per l’archiviazione delle informazioni, compreso il suffisso degli schemi di estensione per facilitarne l’identificazione.

   ![](assets/wf_new_mapping_define_names.png)

   Puoi scegliere se memorizzare le esclusioni (**escluso**), con i messaggi (**broadcast**) o in una tabella separata.

   Puoi anche scegliere se gestire il tracciamento per questa mappatura di consegna (**trackinglog**).

1. Selezionare quindi le estensioni da prendere in considerazione. Il tipo di estensione dipende dai parametri e dalle opzioni della piattaforma (visualizzate il contratto di licenza).

   ![](assets/wf_new_mapping_define_extensions.png)

   Fate clic sul **[!UICONTROL Save]** pulsante per avviare la creazione della mappatura della consegna: tutte le tabelle collegate vengono create automaticamente in base ai parametri selezionati.
