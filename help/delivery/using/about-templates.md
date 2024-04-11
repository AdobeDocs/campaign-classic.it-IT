---
product: campaign
title: Informazioni sui modelli
description: Introduzione ai modelli di consegna
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Delivery Templates
role: User
exl-id: d943898c-06fe-451d-aa28-8a95665f4112
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 1%

---

# Informazioni sui modelli{#about-templates}

Una configurazione di consegna può essere salvata in un modello di consegna per essere riutilizzata. Il modello può contenere una configurazione completa o parziale della consegna.

Il modello di consegna può essere eseguito manualmente, come descritto in questo capitolo, o in base a un evento (avviato a un orario impostato, all’arrivo di un file su un server, ecc.). I modelli di consegna possono essere configurati tramite **[!UICONTROL Resources > Templates > Delivery templates]** nella struttura.

![](assets/s_user_template_list.png)

Esistono due tipi di modello:

1. Modelli di consegna nativi di Adobe Campaign

   I modelli nativi NON DEVONO essere eliminati dal sistema. Includono una configurazione minima per ciascun canale di consegna. L’amministratore può, tuttavia, limitare determinate funzioni o offrire valori predefiniti agli utenti (attivazione del tracciamento, indirizzi e-mail del mittente, ecc.). Gli scenari nativi vengono visualizzati in grassetto nell’elenco dei modelli. Devono essere duplicati per poterli modificare.

1. Modelli di consegna predefiniti

   L’amministratore Adobe Campaign può creare nuovi modelli di consegna. Possono essere riutilizzati dagli operatori (che dispongono di diritti di accesso adeguati) o automaticamente dai processi server. Ad esempio, puoi configurare un modello di consegna e-mail e, quando gli utenti creano una consegna utilizzando questo modello, devono semplicemente inserire il testo o il contenuto HTML e quindi consegnarlo; le altre scelte sono già state definite dall’amministratore.

>[!NOTE]
>
>I modelli disponibili dipendono dai diritti di accesso, dalla configurazione dell’istanza e dal contesto. Ad esempio, quando crei un servizio di informazioni, puoi collegare un modello di consegna per i messaggi di conferma: puoi quindi accedere solo ai modelli il cui mapping di destinazione è il mapping di abbonamento. Per ulteriori informazioni, consulta [Seleziona una mappatura di destinazione](selecting-a-target-mapping.md) e [Servizi e abbonamenti](about-services-and-subscriptions.md).
