---
title: Informazioni sui modelli
seo-title: Informazioni sui modelli
description: Informazioni sui modelli
seo-description: null
page-status-flag: never-activated
uuid: 13b5ad3a-aded-43b8-ae4d-c23aa7bc17bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-delivery-templates
discoiquuid: 22e289d0-c33c-4daa-a893-b292e523f30b
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 2%

---


# Informazioni sui modelli{#about-templates}

Per essere riutilizzata, è possibile salvare una configurazione di consegna in un modello di consegna. Il modello può contenere una configurazione completa o parziale della consegna.

Il modello di consegna può essere eseguito manualmente, come descritto in questo capitolo, o in base a un evento (avviato in un determinato momento, all&#39;arrivo di un file presso un server, ecc.). I modelli di consegna possono essere configurati tramite il **[!UICONTROL Resources > Templates > Delivery templates]** nodo nella struttura.

![](assets/s_user_template_list.png)

Esistono due tipi di modello:

1.  modelli di distribuzione nativa Adobe Campaign

   I modelli nativi NON DEVONO ESSERE ELIMINATI DAL SISTEMA. Includono una configurazione minima per ogni canale di consegna. Tuttavia, l&#39;amministratore può limitare determinate funzioni o offrire valori predefiniti agli utenti (tracciamento dell&#39;attivazione, indirizzi e-mail del mittente, ecc.). Gli scenari nativi vengono visualizzati in grassetto nell’elenco dei modelli. Devono essere duplicati per modificarli.

1. Modelli di consegna predefiniti

   L&#39;amministratore  Adobe Campaign può creare nuovi modelli di consegna. Possono essere riutilizzati dagli operatori (quelli con diritti di accesso adeguati) o automaticamente dai processi server. Ad esempio, potete configurare un modello per la consegna delle e-mail; quando l&#39;utente crea una consegna utilizzando questo modello, deve semplicemente immettere il testo o il contenuto HTML e quindi distribuirla; le altre scelte sono già state definite dall&#39;amministratore.

>[!NOTE]
>
>I modelli disponibili dipendono dai diritti di accesso, dalla configurazione dell’istanza e dal contesto. Ad esempio, quando create un servizio informazioni, potete collegare un modello di consegna per i messaggi di conferma: potete quindi accedere solo ai modelli la cui mappatura di destinazione è la mappatura delle sottoscrizioni. Per ulteriori informazioni, vedere [Selezione di una mappatura](../../delivery/using/selecting-a-target-mapping.md) di destinazione e [Informazioni su servizi e iscrizioni](../../delivery/using/about-services-and-subscriptions.md).
