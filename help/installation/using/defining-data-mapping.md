---
product: campaign
title: Definire la mappatura dei dati esterni
description: Scopri come mappare i dati in un database esterno
feature: Installation, Instance Settings
exl-id: a7253ca7-47e5-4def-849d-3ce1c9b948fb
TQID: 'https://experienceleague.adobe.com/9mE5BjrDg-E4FDyFFL0GVAVPof0rlSSOlzyj2zk21ag'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
  - id: 7f0a1ee5-eeb8-5478-a9cd-b1896f033118
    internal-label: Instance Settings
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
    internal-label: PI
  - id: e656c701-3899-4db3-989c-de0980ddfffa
    internal-label: Installation
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 3%
---
# Definire la mappatura dei dati esterni {#defining-data-mapping}



Adobe Campaign consente di definire la mappatura sui dati in una tabella esterna.

A questo scopo, una volta creato lo schema della tabella esterna, è necessario creare una nuova mappatura di consegna per utilizzare i dati in questa tabella come destinazione di consegna.

A questo scopo, esegui i seguenti passaggi:

1. Crea una nuova mappatura di consegna e scegli la dimensione di targeting, lo schema appena creato, ad esempio.

   ![](assets/wf_new_mapping_create_fda.png)

1. Indica i campi in cui sono memorizzate le informazioni di consegna (cognome, nome, e-mail, indirizzo, ecc.).

   ![](assets/wf_new_mapping_define_join.png)

1. Specifica i parametri per l’archiviazione delle informazioni, compreso il suffisso degli schemi di estensione affinché siano facilmente identificabili.

   ![](assets/wf_new_mapping_define_names.png)

   Puoi scegliere se memorizzare le esclusioni (**excludelog**), con i messaggi (**broadlog**) o in una tabella separata.

   Puoi anche scegliere se gestire il tracciamento per questa mappatura di consegna (**trackinglog**).

1. Quindi seleziona le estensioni da prendere in considerazione. Il tipo di estensione dipende dai parametri e dalle opzioni della piattaforma (vedi il contratto di licenza).

   ![](assets/wf_new_mapping_define_extensions.png)

   Fai clic sul pulsante **[!UICONTROL Save]** per avviare la creazione della mappatura di consegna: tutte le tabelle collegate vengono create automaticamente in base ai parametri selezionati.
