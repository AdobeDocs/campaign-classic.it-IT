---
product: campaign
title: Informazioni sui modelli
description: Guida introduttiva ai modelli di consegna
feature: Delivery Templates
exl-id: d943898c-06fe-451d-aa28-8a95665f4112
source-git-commit: f05eefc9945c4ead89eb448b6e28c3523559e055
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 1%

---

# Informazioni sui modelli{#about-templates}

![](../../assets/common.svg)

Per essere riutilizzata, è possibile salvare una configurazione di consegna in un modello di consegna. Il modello può contenere una configurazione completa o parziale della consegna.

Il modello di consegna può essere eseguito manualmente, come descritto in questo capitolo, o in base a un evento (avviato in un determinato momento, all&#39;arrivo di un file su un server, ecc.). I modelli di consegna possono essere configurati tramite **[!UICONTROL Resources > Templates > Delivery templates]** nell&#39;albero.

![](assets/s_user_template_list.png)

Esistono due tipi di modelli:

1. Modelli di consegna nativi per Adobe Campaign

   I modelli nativi NON DEVONO essere eliminati dal sistema. Includono una configurazione minima per ogni canale di consegna. Tuttavia, l’amministratore può limitare determinate funzioni o offrire valori predefiniti agli utenti (tracciamento dell’attivazione, indirizzi e-mail del mittente, ecc.). Gli scenari nativi vengono visualizzati in grassetto nell’elenco dei modelli. Devono essere duplicati per modificarli.

1. Modelli di consegna predefiniti

   L’amministratore di Adobe Campaign può creare nuovi modelli di consegna. Possono essere riutilizzati dagli operatori (quelli con diritti di accesso adeguati) o automaticamente dai processi server. Ad esempio, puoi configurare un modello di consegna e-mail e, quando gli utenti creano una consegna utilizzando questo modello, devono semplicemente inserire il contenuto di testo o HTML e quindi consegnarlo; le altre scelte sono già state definite dall’amministratore.

>[!NOTE]
>
>I modelli disponibili dipendono dai diritti di accesso, dalla configurazione dell’istanza e dal contesto. Ad esempio, quando crei un servizio di informazioni, puoi collegare un modello di consegna per i messaggi di conferma: potrai quindi accedere solo ai modelli la cui mappatura di destinazione è la mappatura della sottoscrizione. Per ulteriori informazioni, consulta [Selezionare una mappatura target](selecting-a-target-mapping.md) e [Servizi e abbonamenti](about-services-and-subscriptions.md).
