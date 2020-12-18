---
solution: Campaign Classic
product: campaign
title: Metodo di migrazione
description: Metodo di migrazione
audience: migration
content-type: reference
topic-tags: migration-overview
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 1%

---


# Metodo di migrazione{#migration-method}

## Modernizzazione dell&#39;ambiente {#modernizing-your-environment}

L&#39;esecuzione di una migrazione può essere un&#39;opportunità per aggiornare l&#39;ambiente (motori di database, sistemi operativi).  Adobe Campaign consiglia vivamente di aggiornare gli ambienti di produzione alle versioni più recenti.

I database e i sistemi operativi a 32 bit sono ancora supportati in v7, ma non saranno più supportati nelle versioni future di  Adobe Campaign. È consigliabile aggiornare la piattaforma a 64 bit il prima possibile.

In v6.02, la modalità &quot;multi timezone&quot; era disponibile solo per i motori di database PostSQL. Ora è disponibile indipendentemente dal tipo di motore di database utilizzato. Consigliamo vivamente di trasformare la base in una base &quot;multi-timezone&quot;. Per ulteriori informazioni, vedere la sezione [Fusi orari](../../migration/using/general-configurations.md#time-zones).

>[!IMPORTANT]
>
>Alcune versioni software supportate in  Adobe Campaign 5.11 e 6.02 non sono più supportate in  Adobe Campaign v7.
>
>Per ulteriori informazioni sulle versioni supportate da  Adobe Campaign, consultare la [matrice di compatibilità](../../rn/using/compatibility-matrix.md).

## Passaggi di migrazione chiave {#key-migration-steps}

La procedura generale per la migrazione a  Adobe Campaign v7 è descritta in dettaglio nella sezione [Prima di avviare la migrazione](../../migration/using/before-starting-migration.md).

I passaggi di implementazione per la migrazione a  Adobe Campaign v7 sono descritti dettagliatamente nella sezione [Prerequisiti per la migrazione a  Adobe Campaign 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md).

Le configurazioni richieste dipendono dalle configurazioni esistenti e dalla versione iniziale della piattaforma. Questi sono descritti nella sezione [Configurazioni generali](../../migration/using/general-configurations.md).

## Configurazioni specifiche {#specific-configurations}

Le modifiche apportate da  Adobe Campaign v7 possono anche significare che è necessario adattare alcune configurazioni specifiche sviluppate nelle versioni precedenti. Pertanto, prima della migrazione potrebbe essere necessario eseguire un audit su tutte le configurazioni: contattate  Adobe Campaign per assistenza.

Ad esempio, occorre prestare particolare attenzione alle impostazioni specifiche per applicazioni Web, alle estensioni dello schema con SQLdata o alla duplicazione dello schema out-of-the-box. Per ulteriori informazioni, consultare la sezione [Configurazione della piattaforma](../../migration/using/configuring-your-platform.md).

Allo stesso modo, per rispondere all&#39;accresciuta sicurezza all&#39;interno  Adobe Campaign, sono stati modificati alcuni meccanismi interni: dovete adattare queste configurazioni corrispondenti.
