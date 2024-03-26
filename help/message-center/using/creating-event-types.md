---
product: campaign
title: Creare tipi di evento
description: Scopri come creare tipi di evento che corrisponderanno ai messaggi transazionali che desideri inviare in Adobe Campaign Classic
feature: Transactional Messaging, Message Center
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 98b7c827-f31d-46a6-a28d-40a78a4b4248
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 7%

---

# Creare tipi di evento {#creating-event-types}



Per garantire che ogni evento possa essere trasformato in un messaggio personalizzato, devi innanzitutto creare **tipi di evento**.

Quando [creazione di un modello di messaggio](../../message-center/using/creating-the-message-template.md), selezioni il tipo di evento che corrisponde al messaggio che desideri inviare.

>[!IMPORTANT]
>
>È necessario creare tipi di evento prima di poterli utilizzare nei modelli di messaggio.

Per creare tipi di evento che verranno elaborati da Adobe Campaign, segui questi passaggi:

1. Accedere a **istanza di controllo**.

1. Vai a **[!UICONTROL Administration > Platform > Enumerations]** cartella della struttura.

1. Seleziona **[!UICONTROL Event type]** dall&#39;elenco.

1. Clic **[!UICONTROL Add]** per creare un valore di enumerazione. Può trattarsi di una conferma d’ordine, di una modifica della password, di una modifica della consegna dell’ordine, ecc.

   ![](assets/messagecenter_eventtype_enum_001.png)

   >[!IMPORTANT]
   >
   >Ogni tipo di evento deve corrispondere a un valore in **[!UICONTROL Event type]** enumerazione.

1. Una volta creati i valori dell’elenco dettagliati, disconnettiti e accedi di nuovo all’istanza per rendere effettiva la creazione.

>[!NOTE]
>
>Ulteriori informazioni sugli elenchi dettagliati in [Gestione enumerazioni](../../platform/using/managing-enumerations.md).


