---
product: campaign
title: Informazioni sui modelli
description: Informazioni sui modelli
audience: delivery
content-type: reference
topic-tags: using-delivery-templates
exl-id: d943898c-06fe-451d-aa28-8a95665f4112
source-git-commit: a129f49d4f045433899fd7fdbd057fb16d0ed36a
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 2%

---

# Informazioni sui modelli{#about-templates}

Per essere riutilizzata, è possibile salvare una configurazione di consegna in un modello di consegna. Il modello può contenere una configurazione completa o parziale della consegna.

Il modello di consegna può essere eseguito manualmente, come descritto in questo capitolo, o in base a un evento (avviato in un determinato momento, all&#39;arrivo di un file su un server, ecc.). I modelli di consegna possono essere configurati tramite il nodo **[!UICONTROL Resources > Templates > Delivery templates]** nella struttura.

![](assets/s_user_template_list.png)

Esistono due tipi di modelli:

1. Modelli di consegna nativi per Adobe Campaign

   I modelli nativi NON DEVONO essere eliminati dal sistema. Includono una configurazione minima per ogni canale di consegna. Tuttavia, l’amministratore può limitare determinate funzioni o offrire valori predefiniti agli utenti (tracciamento dell’attivazione, indirizzi e-mail del mittente, ecc.). Gli scenari nativi vengono visualizzati in grassetto nell’elenco dei modelli. Devono essere duplicati per modificarli.

1. Modelli di consegna predefiniti

   L’amministratore di Adobe Campaign può creare nuovi modelli di consegna. Possono essere riutilizzati dagli operatori (quelli con diritti di accesso adeguati) o automaticamente dai processi server. Ad esempio, puoi configurare un modello di consegna e-mail e, quando l’utente crea una consegna utilizzando questo modello, deve semplicemente immettere il testo o il contenuto HTML e quindi consegnarlo; le altre scelte sono già state definite dall’amministratore.

>[!NOTE]
>
>I modelli disponibili dipendono dai diritti di accesso, dalla configurazione dell’istanza e dal contesto. Ad esempio, quando crei un servizio di informazioni, puoi collegare un modello di consegna per i messaggi di conferma: potrai quindi accedere solo ai modelli la cui mappatura di destinazione è la mappatura della sottoscrizione. Per ulteriori informazioni, consulta [Selezionare una mappatura target](selecting-a-target-mapping.md) e [Informazioni su servizi e abbonamenti](about-services-and-subscriptions.md).
