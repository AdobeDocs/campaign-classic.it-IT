---
solution: Campaign Classic
product: campaign
title: Informazioni sulle tipologie di campagne
description: Informazioni sulle tipologie di campagne
audience: campaign
content-type: reference
topic-tags: campaign-optimization
translation-type: tm+mt
source-git-commit: 87028ec81a8cae6793d45d7c840511b59cd0287c
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 13%

---


# Informazioni sulle tipologie di campagne{#about-campaign-typologies}

Ottimizzazione campagna è il modulo Adobe Campaign che ti consente di controllare, filtrare e monitorare l’invio di consegne. Per evitare conflitti tra campagne, Adobe Campaign può sottoporre a test diverse combinazioni applicando regole di vincolo specifiche. Questo garantisce che i messaggi inviati soddisfino le esigenze e le aspettative dei clienti e le politiche di comunicazione aziendali.

![](assets/do-not-localize/how-to-video.png) [Scopri questa funzione nel video](#typologies-video)

>[!NOTE]
>
>A seconda dell’offerta, è possibile includere l’ottimizzazione per Campaign o un componente aggiuntivo. Controlla il contratto di licenza.

## Regole di tipologia {#typology-rules}

Con Adobe Campaign puoi progettare e applicare quattro tipi di regole di tipologia:

* **** Filteringrules che ti consentono di escludere parte del target in base ai criteri. Per ulteriori informazioni, consulta [Regole di filtro](../../campaign/using/filtering-rules.md).
* **** Regole di pressione che consentono di controllare l’affaticamento del marketing. Per ulteriori informazioni, consulta [Regole di pressione](../../campaign/using/pressure-rules.md).
* **** Regole di capacità che consentono di limitare i carichi per garantire condizioni di elaborazione ottimali. Per ulteriori informazioni, consulta [Controllo della capacità](../../campaign/using/consistency-rules.md#controlling-capacity).
* **** Controlla le regole che ti consentono di verificare la validità dei messaggi prima che vengano inviati. Per ulteriori informazioni, consulta [Regole di controllo](../../campaign/using/control-rules.md).

Una volta create, le regole di tipologia sono raggruppate nelle tipologie di campagne a cui si fa riferimento nelle consegne. Consulta [Applicazione delle tipologie](#applying-typologies).

## Tipologie {#typologies}

Una tipologia di campagna può contenere diverse [regole di tipologia](#typology-rules), ma una consegna può fare riferimento a una sola tipologia.

La scheda **[!UICONTROL Rules]** ti consente di aggiungere, eliminare o visualizzare le regole di tipologia da applicare.

![](assets/campaign_opt_rules_tab.png)

## Applicazione delle tipologie {#applying-typologies}

I passaggi per creare e applicare una tipologia alle consegne sono elencati di seguito:

1. Creare regole di tipologia.

   Le regole di tipologia si trovano nel nodo **[!UICONTROL Administration > Campaign management > Typology management > Typology rules]** .

   Le diverse regole disponibili in Campaign sono descritte nelle sezioni seguenti: [regole di pressione di vendita](../../campaign/using/pressure-rules.md), [regole di capacità](../../campaign/using/consistency-rules.md#controlling-capacity), [regole di controllo](../../campaign/using/control-rules.md) e [regole di filtro](../../campaign/using/filtering-rules.md).

1. Crea una tipologia e fai riferimento alle regole create al suo interno.

   Le tipologie sono accessibili tramite il nodo **[!UICONTROL Administration > Campaign Management > Typology management]** > **[!UICONTROL Typologies]** .

1. Configura la consegna per utilizzare la tipologia creata. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../campaign/using/applying-rules.md#applying-a-typology-to-a-delivery).
1. Testa e controlla il comportamento attraverso le simulazioni delle campagne. Per ulteriori informazioni sulle simulazioni di campagne, consulta [questa sezione](../../campaign/using/campaign-simulations.md).

Durante la preparazione della consegna, i destinatari vengono esclusi quando il criterio è soddisfatto. Per monitorare le esclusioni, puoi controllare i registri. Esempi di casi d&#39;uso sulle regole di tipologia della pressione sono disponibili in [questa pagina](../../campaign/using/pressure-rules.md#use-cases-on-pressure-rules).

## Video tutorial {#typologies-video}

### Come impostare la gestione dell’affaticamento utilizzando le regole di tipologia

Questo video spiega come implementare la gestione dell’affaticamento in Adobe Campaign sfruttando le regole di tipologia.

>[!VIDEO](https://video.tv.adobe.com/v/25090?quality=12)

### Come impostare la gestione dell’affaticamento utilizzando filtri predefiniti

La gestione dell’affaticamento controlla la frequenza e la quantità di messaggi per evitare un’eccessiva sollecitazione dei destinatari. Se nell’istanza della campagna non è presente il modulo di ottimizzazione della campagna, puoi configurare un filtro predefinito che filtrerà la popolazione target in base al numero di messaggi ricevuti
Questo video spiega come implementare la gestione dell’affaticamento in Adobe Campaign Classic utilizzando i filtri.

>[!VIDEO](https://video.tv.adobe.com/v/25091?quality=12)

Sono disponibili ulteriori video dimostrativi su Campaign [qui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=it).

**Argomento correlato**

* [Applicare regole di business automatiche alle consegne su qualsiasi canale](https://helpx.adobe.com/campaign/kb/simplifying-campaign-management-acc.html#Applyautomaticbusinessrulestodeliveriesonanychannel)

* [Informazioni sulle tipologie di campagne](../../campaign/using/pressure-rules.md)

* [Gestione dell’affaticamento del marketing con le regole di pressione](https://docs.adobe.com/content/help/en/campaign-classic/using/orchestrating-campaigns/campaign-optimization/pressure-rules.html)