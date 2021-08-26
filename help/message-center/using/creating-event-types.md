---
product: campaign
title: Creare tipi di evento
description: Scopri come creare tipi di evento corrispondenti ai messaggi transazionali che desideri inviare in Adobe Campaign Classic.
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 98b7c827-f31d-46a6-a28d-40a78a4b4248
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 3%

---

# Creare tipi di evento {#creating-event-types}

![](../../assets/v7-only.svg)

Per assicurarti che ogni evento possa essere modificato in un messaggio personalizzato, devi innanzitutto creare **tipi di evento**.

Quando [crei un modello di messaggio](../../message-center/using/creating-the-message-template.md), selezioni il tipo di evento che corrisponde al messaggio che desideri inviare.

>[!IMPORTANT]
>
>È necessario creare tipi di evento prima di poterli utilizzare nei modelli di messaggio.

Per creare tipi di evento che verranno elaborati da Adobe Campaign, segui i passaggi seguenti:

1. Accedi all&#39; **istanza di controllo**.

1. Vai alla cartella **[!UICONTROL Administration > Platform > Enumerations]** della struttura.

1. Seleziona **[!UICONTROL Event type]** dall’elenco.

1. Fare clic su **[!UICONTROL Add]** per creare un valore di enumerazione. Può trattarsi di una conferma dell’ordine, una modifica della password, una modifica della consegna dell’ordine, ecc.

   ![](assets/messagecenter_eventtype_enum_001.png)

   >[!IMPORTANT]
   >
   >Ogni tipo di evento deve corrispondere a un valore nell&#39;enumerazione **[!UICONTROL Event type]**.

1. Una volta creati i valori elenco dettagliati, disconnettiti e torna all’istanza per rendere effettiva la creazione.

>[!NOTE]
>
>Ulteriori informazioni sugli elenchi dettagliati in [Gestione enumerazione](../../platform/using/managing-enumerations.md).


