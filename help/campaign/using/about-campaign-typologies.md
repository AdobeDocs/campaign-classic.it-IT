---
solution: Campaign Classic
product: campaign
title: Informazioni sulle tipologie di campagne
description: Informazioni sulle tipologie di campagne
audience: campaign
content-type: reference
topic-tags: campaign-optimization
translation-type: tm+mt
source-git-commit: 20dcdd91d71158bc373db68c3f61f6808b240bd2
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 13%

---


# Informazioni sulle tipologie di campagne{#about-campaign-typologies}

Ottimizzazione campagna è il modulo Adobe Campaign  che consente di controllare, filtrare e monitorare l&#39;invio di consegne. Per evitare conflitti tra campagne, Adobe Campaign può sottoporre a test diverse combinazioni applicando regole di vincolo specifiche. Questo garantisce che i messaggi inviati soddisfino le esigenze e le aspettative dei clienti e le politiche di comunicazione aziendali.

![](assets/do-not-localize/how-to-video.png) [Scopri questa funzione nel video](#typologies-video)

>[!NOTE]
>
>A seconda dell&#39;offerta, è possibile includere l&#39;ottimizzazione per le campagne o un componente aggiuntivo. Controlla il contratto di licenza.

## Regole di tipologia {#typology-rules}

Con  Adobe Campaign è possibile progettare e applicare quattro tipi di regole di tipologia:

* **Filteringrule** che consentono di escludere parte della destinazione in base ai criteri. Per ulteriori informazioni, vedere [Regole di filtro](../../campaign/using/filtering-rules.md).
* **** Pressione che permette di controllare la fatica del marketing. Per ulteriori informazioni, fare riferimento a [Regole di pressione](../../campaign/using/pressure-rules.md).
* **Regole di** capacità che consentono di limitare i carichi per garantire condizioni di elaborazione ottimali. Per ulteriori informazioni, fare riferimento a [Capacità di controllo](../../campaign/using/consistency-rules.md#controlling-capacity).
* **** Controlla le regole che ti consentono di verificare la validità dei messaggi prima che vengano inviati. Per ulteriori informazioni, fare riferimento a [Regole di controllo](../../campaign/using/control-rules.md).

Una volta create, le regole di tipologia sono raggruppate nelle tipologie di campagna a cui viene fatto riferimento nelle consegne. Vedere [Applicazione di tipologie](#applying-typologies).

## Tipologie {#typologies}

Una tipologia di campagna può contenere diverse [regole di tipologia](#typology-rules), ma una consegna può fare riferimento a una sola tipologia.

La scheda **[!UICONTROL Rules]** consente di aggiungere, eliminare o visualizzare le regole di tipologia da applicare.

![](assets/campaign_opt_rules_tab.png)

## Applicazione delle tipologie {#applying-typologies}

I passaggi per creare e applicare una tipologia alle consegne sono elencati di seguito:

1. Creare regole di tipologia.

   Le regole di tipologia si trovano nel nodo **[!UICONTROL Administration > Campaign management > Typology management > Typology rules]**.

   Diverse regole disponibili in Campaign sono descritte nelle seguenti sezioni: [regole di pressione di vendita](../../campaign/using/pressure-rules.md), [regole di capacità](../../campaign/using/consistency-rules.md#controlling-capacity), [regole di controllo](../../campaign/using/control-rules.md) e [regole di filtro](../../campaign/using/filtering-rules.md).

1. Create una tipologia e fate riferimento alle regole create al suo interno.

   Le tipologie sono accessibili tramite il nodo **[!UICONTROL Administration > Campaign Management > Typology management]** > **[!UICONTROL Typologies]**.

1. Configurate la distribuzione in modo da utilizzare la tipologia creata. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../campaign/using/applying-rules.md#applying-a-typology-to-a-delivery).
1. Test e controllo del comportamento mediante simulazioni di campagne. Per ulteriori informazioni sulle simulazioni delle campagne, consultare [questa sezione](../../campaign/using/campaign-simulations.md).

Durante la preparazione della consegna, i destinatari sono esclusi quando il criterio è soddisfatto. Per monitorare le esclusioni, puoi controllare i registri. I casi di utilizzo di esempio sulle regole di tipo pressione sono disponibili in [questa pagina](../../campaign/using/pressure-rules.md#use-cases-on-pressure-rules).

## Video tutorial {#typologies-video}

### Come impostare la gestione dell&#39;affaticamento utilizzando le regole di tipologia

Questo video spiega come implementare la gestione della fatica in Adobe Campaign Classic sfruttando le regole della tipologia.

>[!VIDEO](https://video.tv.adobe.com/v/25090?quality=12)

### Come impostare la gestione della fatica utilizzando filtri predefiniti

La gestione della fatica controlla la frequenza e la quantità di messaggi per evitare un eccesso di richieste da parte dei destinatari. Se nell’istanza della campagna non è presente il modulo di ottimizzazione della campagna, potete configurare un filtro predefinito che filtrerà la popolazione di destinazione in base al numero di messaggi ricevuti.
Questo video spiega come implementare la gestione della fatica in Adobe Campaign Classic utilizzando i filtri.

>[!VIDEO](https://video.tv.adobe.com/v/25091?quality=12)

Ulteriori video dimostrativi sui Campaign Classic sono disponibili [qui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=it).

**Argomento correlato**

* [Applica regole aziendali automatiche alle consegne su qualsiasi canale](https://helpx.adobe.com/campaign/kb/simplifying-campaign-management-acc.html#Applyautomaticbusinessrulestodeliveriesonanychannel)

* [Informazioni sulle tipologie di campagne](../../campaign/using/pressure-rules.md)

* [Gestione della stanchezza di marketing con le regole di pressione](https://docs.adobe.com/content/help/en/campaign-classic/using/orchestrating-campaigns/campaign-optimization/pressure-rules.html)