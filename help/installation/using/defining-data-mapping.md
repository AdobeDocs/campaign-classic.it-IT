---
product: campaign
title: Definire la mappatura dei dati esterni
description: Scopri come mappare i dati in un database esterno
exl-id: a7253ca7-47e5-4def-849d-3ce1c9b948fb
source-git-commit: 3af4f259b80b3e03c81ee278b470ef6ffe3fe4d0
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 3%

---

# Definire la mappatura dei dati esterni {#defining-data-mapping}

![](../../assets/v7-only.svg)

Adobe Campaign ti consente di definire la mappatura dei dati in una tabella esterna.

A questo scopo, una volta creato lo schema della tabella esterna, devi creare una nuova mappatura della consegna per utilizzare i dati presenti in questa tabella come destinazione della consegna.

A questo scopo, esegui i seguenti passaggi:

1. Crea una nuova mappatura di consegna e scegli la dimensione di targeting, lo schema appena creato, ad esempio.

   ![](assets/wf_new_mapping_create_fda.png)

1. Indica i campi in cui sono memorizzate le informazioni di consegna (cognome, nome, e-mail, indirizzo, ecc.).

   ![](assets/wf_new_mapping_define_join.png)

1. Specifica i parametri per l’archiviazione delle informazioni, compreso il suffisso degli schemi di estensione, in modo che siano facilmente identificabili.

   ![](assets/wf_new_mapping_define_names.png)

   Puoi scegliere di memorizzare le esclusioni (**excludelog**), con messaggi (**broadlog**) o in una tabella separata.

   Puoi anche scegliere di gestire il tracciamento per questa mappatura della consegna (**trackinglog**).

1. Quindi seleziona le estensioni da prendere in considerazione. Il tipo di estensione dipende dai parametri e dalle opzioni della piattaforma (visualizza il contratto di licenza).

   ![](assets/wf_new_mapping_define_extensions.png)

   Fai clic sul pulsante **[!UICONTROL Save]** pulsante per avviare la creazione della mappatura della consegna: tutte le tabelle collegate vengono create automaticamente in base ai parametri selezionati.
