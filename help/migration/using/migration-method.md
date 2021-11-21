---
product: campaign
title: Metodo di migrazione
description: Metodo di migrazione
audience: migration
content-type: reference
topic-tags: migration-overview
exl-id: dd4d068b-f414-448f-8d9a-eedf44e7b6e6
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 1%

---

# Metodo di migrazione{#migration-method}

![](../../assets/v7-only.svg)

## Modernizzazione dell&#39;ambiente {#modernizing-your-environment}

L’esecuzione di una migrazione può essere un’opportunità per aggiornare l’ambiente (motori di database, sistemi operativi). Adobe Campaign consiglia vivamente di aggiornare gli ambienti di produzione alle versioni più recenti.

I database e i sistemi operativi a 32 bit sono ancora supportati in v7, ma non saranno più supportati nelle versioni future di Adobe Campaign. È consigliabile aggiornare la piattaforma a 64 bit il prima possibile.

Nella versione 6.02, la modalità &quot;multi timezone&quot; era disponibile solo per i motori di database PostgreSQL. Ora viene offerto indipendentemente dal tipo di motore di database utilizzato. Ti consigliamo vivamente di trasformare la tua base in una base &quot;multi-fuso orario&quot;. Per ulteriori informazioni, consulta la sezione [Fusi orari](../../migration/using/general-configurations.md#time-zones) sezione .

>[!IMPORTANT]
>
>Alcune versioni del software supportate in Adobe Campaign 5.11 e 6.02 non sono più supportate in Adobe Campaign v7.
>
>Per ulteriori informazioni sulle versioni supportate da Adobe Campaign, consulta la [matrice di compatibilità](../../rn/using/compatibility-matrix.md).

## Passaggi chiave per la migrazione {#key-migration-steps}

La procedura generale per la migrazione ad Adobe Campaign v7 è illustrata nella [Prima di avviare la migrazione](../../migration/using/before-starting-migration.md) sezione .

I passaggi di implementazione per la migrazione ad Adobe Campaign v7 sono descritti in dettaglio nella sezione [Prerequisiti per la migrazione ad Adobe Campaign 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md) sezione .

Le configurazioni richieste dipendono dalle configurazioni esistenti e dalla versione iniziale della piattaforma. Questi sono descritti nella [Configurazioni generali](../../migration/using/general-configurations.md) sezione .

## Configurazioni specifiche {#specific-configurations}

Le modifiche introdotte da Adobe Campaign v7 possono anche significare che è necessario adattare alcune configurazioni specifiche sviluppate nelle versioni precedenti. Pertanto, potrebbe essere necessario eseguire un controllo di tutte le configurazioni prima della migrazione: contatta Adobe Campaign per assistenza.

Ad esempio, è necessario prestare particolare attenzione alle impostazioni specifiche per le applicazioni Web, alle estensioni dello schema con SQLdata o alla duplicazione di schemi preconfigurata. Per ulteriori informazioni, consulta la [Configurazione della piattaforma](../../migration/using/configuring-your-platform.md) sezione .

Allo stesso modo, per rispondere all’aumento della sicurezza in Adobe Campaign, sono stati modificati alcuni meccanismi interni: devi adattare queste configurazioni corrispondenti.
