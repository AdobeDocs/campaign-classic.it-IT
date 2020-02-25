---
title: Informazioni sul modello dati di Adobe Campaign Classic
description: Questo documento descrive le nozioni di base del modello dati di Adobe Campaign Classic.
page-status-flag: never-activated
uuid: faddde15-59a1-4d2c-8303-5b3e470a0c51
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5957b39e-c2c6-40a2-b81a-656e9ff7989c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b7fa53a0463c5752a5fe4d11262dbf7b8ad77144

---


# Informazioni sul modello dati Campaign Classic{#about-data-model}

Questa sezione descrive le nozioni di base del modello dati di Adobe Campaign Classic, per una migliore comprensione delle tabelle integrate in Campaign e della loro interazione.

Il modello di dati concettuali del database Adobe Campaign consiste in un insieme di tabelle integrate e nella relativa interazione.

Per accedere alla descrizione di ciascuna tabella, passare a **[!UICONTROL Admin > Configuration > Data schemas]**, selezionare una risorsa dall&#39;elenco e fare clic sulla **[!UICONTROL Documentation]** scheda.

![](assets/data-model_documentation-tab.png)

Per ulteriori informazioni sulla descrizione predefinita del modello dati Campaign Classic, consulta questo [documento](https://final-docs.campaign.adobe.com/doc/AC/en/technicalResources/_Datamodel_Description_of_the_main_tables.html).

La struttura fisica e logica dei dati trasferiti nell&#39;applicazione è descritta in XML. Obbedisce a una grammatica specifica di Adobe Campaign, denominata schema. Per ulteriori informazioni sugli schemi di Adobe Campaign, consulta questa [sezione](../../configuration/using/about-schema-reference.md).

## Panoramica {#data-model-overview}

Adobe Campaign si basa su un database relazionale contenente tabelle collegate tra loro.

La struttura di base del modello dati di Adobe Campaign può essere descritta come segue.

## Tabella destinatari {#recipient-table}

Il modello dati si basa su una tabella principale che per impostazione predefinita è la tabella Recipient (**NmsRecipient**). Questa tabella consente di archiviare tutti i profili di marketing.

Per ulteriori informazioni sulla tabella Destinatario, consulta questa [sezione](../../configuration/using/default-recipient-table.md).

## Tabella di consegna {#delivery-table}

Il modello dati include anche una parte dedicata alla memorizzazione di tutte le attività di marketing. Solitamente si tratta della tabella Consegna (**NmsDelivery**). Ogni record in questa tabella rappresenta un&#39;azione di consegna o un modello di consegna. Contiene tutti i parametri necessari per eseguire consegne quali target, contenuto, ecc.

## Tabelle dei registri {#log-tables}

Un&#39;altra parte del modello dati consente di memorizzare temporaneamente tutti i log associati all&#39;esecuzione delle campagne.

I registri di distribuzione sono tutti i messaggi inviati ai destinatari o ai dispositivi su tutti i canali. La tabella dei registri di consegna principale (**NmsBroadLog**) contiene i registri di consegna per tutti i destinatari.
La tabella dei registri di tracciamento principale (**NmsTrackingLog**) memorizza i registri di tracciamento per tutti i destinatari. I registri di tracciamento fanno riferimento alle reazioni dei destinatari, ad esempio aperture e clic delle e-mail. Ogni reazione corrisponde a un registro di tracciamento.
I registri di consegna e di tracciamento vengono eliminati dopo un certo periodo, specificato in Adobe Campaign e che possono essere modificati. Si raccomanda pertanto vivamente di esportare i tronchi su base regolare.

## Tabelle tecniche {#technical-tables}

Infine, parte del modello di dati è costituita da dati tecnici utilizzati per il processo applicativo, inclusi operatori e diritti utente (**NmsGroup**), cartelle (**XtkFolder**).