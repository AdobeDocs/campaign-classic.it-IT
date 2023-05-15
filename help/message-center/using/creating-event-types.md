---
product: campaign
title: Creare tipi di evento
description: Scopri come creare tipi di evento corrispondenti ai messaggi transazionali che desideri inviare in Adobe Campaign Classic
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 98b7c827-f31d-46a6-a28d-40a78a4b4248
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 3%

---

# Creare tipi di evento {#creating-event-types}



Per fare in modo che ogni evento possa essere modificato in un messaggio personalizzato, devi innanzitutto creare **tipi di evento**.

Quando [creazione di un modello di messaggio](../../message-center/using/creating-the-message-template.md), selezioni il tipo di evento che corrisponde al messaggio che desideri inviare.

>[!IMPORTANT]
>
>È necessario creare tipi di evento prima di poterli utilizzare nei modelli di messaggio.

Per creare tipi di evento che verranno elaborati da Adobe Campaign, segui i passaggi seguenti:

1. Accedi a **istanza di controllo**.

1. Vai a **[!UICONTROL Administration > Platform > Enumerations]** cartella dell&#39;albero.

1. Seleziona **[!UICONTROL Event type]** dall&#39;elenco.

1. Fai clic su **[!UICONTROL Add]** per creare un valore di enumerazione. Può trattarsi di una conferma dell’ordine, una modifica della password, una modifica della consegna dell’ordine, ecc.

   ![](assets/messagecenter_eventtype_enum_001.png)

   >[!IMPORTANT]
   >
   >Ogni tipo di evento deve corrispondere a un valore nel **[!UICONTROL Event type]** enumerazione.

1. Una volta creati i valori elenco dettagliati, disconnettiti e torna all’istanza per rendere effettiva la creazione.

>[!NOTE]
>
>Ulteriori informazioni sugli elenchi dettagliati in [Gestione dell’enumerazione](../../platform/using/managing-enumerations.md).


