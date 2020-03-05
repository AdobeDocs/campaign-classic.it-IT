---
title: Informazioni sulle tipologie delle campagne
seo-title: Informazioni sulle tipologie delle campagne
description: Informazioni sulle tipologie delle campagne
seo-description: null
page-status-flag: never-activated
uuid: ec89fb14-7e2f-4e9f-b7ab-3c2caf93a697
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: campaign-optimization
discoiquuid: 72c5151c-ce1e-425a-9aee-beefe9f21a67
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 44d8ba19f2e79d30229239312e6a5148d247fb28

---


# Informazioni sulle tipologie delle campagne{#about-campaign-typologies}

Ottimizzazione campagna è il modulo Adobe Campaign che consente di controllare, filtrare e monitorare l&#39;invio di consegne. Per evitare conflitti tra campagne, Adobe Campaign può sottoporre a test diverse combinazioni applicando regole di vincolo specifiche. Questo garantisce che i messaggi inviati soddisfino le esigenze e le aspettative dei clienti e le politiche di comunicazione aziendali.

>[!NOTE]
>
>A seconda dell&#39;offerta, è possibile includere l&#39;ottimizzazione per le campagne o un componente aggiuntivo. Controllare il contratto di licenza.

## Regole di tipologia {#typology-rules}

Con Adobe Campaign puoi progettare e applicare quattro tipi di regole di tipologia:

1. **Regole di filtro** che consentono di escludere parte del target in base ai criteri. Per ulteriori informazioni, consultate [Filtrare le regole](../../campaign/using/filtering-rules.md).
1. **Regole di pressione** che consentono di controllare la fatica del marketing. Per ulteriori informazioni, vedere Regole sulla [pressione](../../campaign/using/pressure-rules.md).
1. **Regole di capacità** che consentono di limitare i carichi per garantire condizioni di elaborazione ottimali. Per ulteriori informazioni, vedere [Controllo della capacità](../../campaign/using/consistency-rules.md#controlling-capacity).
1. **Controlla** le regole che ti consentono di verificare la validità dei messaggi prima che vengano inviati. Per ulteriori informazioni, vedere [Regole](../../campaign/using/control-rules.md)di controllo.

Una volta create, le regole di tipologia sono raggruppate nelle tipologie di campagna a cui viene fatto riferimento nelle consegne. Consultate [Applicazione delle tipologie](#applying-typologies).

## Tipologie {#typologies}

Una tipologia di campagna può contenere diverse regole [di](#typology-rules)tipologia, ma una consegna può fare riferimento a una sola tipologia.

La **[!UICONTROL Rules]** scheda consente di aggiungere, eliminare o visualizzare le regole di tipologia da applicare.

![](assets/campaign_opt_rules_tab.png)

## Applicazione delle tipologie {#applying-typologies}

I passaggi per creare e applicare una tipologia alle consegne sono elencati di seguito:

1. Creare regole di tipologia.

   Le regole di tipologia si trovano nel **[!UICONTROL Administration > Campaign management > Typology management > Typology rules]** nodo.

   Diverse regole disponibili in Campaign sono descritte nelle seguenti sezioni: regole [sulla pressione](../../campaign/using/pressure-rules.md)di vendita, regole [sulla](../../campaign/using/consistency-rules.md#controlling-capacity)capacità, regole [di](../../campaign/using/control-rules.md) controllo e regole [di](../../campaign/using/filtering-rules.md)filtraggio.

1. Create una tipologia e fate riferimento alle regole create al suo interno.

   Le tipologie sono accessibili tramite il nodo **[!UICONTROL Administration > Campaign Management > Typology management]** > **[!UICONTROL Typologies]** .

1. Configurate la distribuzione in modo da utilizzare la tipologia creata. For more on this, refer to [this section](../../campaign/using/applying-rules.md#applying-a-typology-to-a-delivery).
1. Test e controllo del comportamento mediante simulazioni di campagne. For more on campaign simulations, refer to [this section](../../campaign/using/campaign-simulations.md).

Durante la preparazione della consegna, i destinatari sono esclusi quando il criterio è soddisfatto. Potete controllare i registri per monitorare le esclusioni. Esempi di utilizzo delle regole di tipo pressione sono disponibili in [questa pagina](../../campaign/using/pressure-rules.md#use-cases-on-pressure-rules).

**Argomento correlato**

* [Applica regole aziendali automatiche alle consegne su qualsiasi canale](https://helpx.adobe.com/campaign/kb/simplifying-campaign-management-acc.html#Applyautomaticbusinessrulestodeliveriesonanychannel)