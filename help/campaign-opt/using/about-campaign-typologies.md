---
product: campaign
title: Informazioni sulle tipologie di campagne
description: Informazioni sulle tipologie di campagne
feature: Typology Rules
exl-id: 6d5b8584-4aa1-4d9a-89d9-d41da75dd323
source-git-commit: 36e546a34d8c2345fefed5d459095a76c6224a38
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 21%

---

# Informazioni sulle tipologie di campagne{#about-campaign-typologies}

![](../../assets/common.svg)

Ottimizzazione campagna è il modulo Adobe Campaign che ti consente di controllare, filtrare e monitorare l’invio di consegne. Per evitare conflitti tra campagne, Adobe Campaign può sottoporre a test diverse combinazioni applicando specifiche regole di vincolo. Ciò garantisce che i messaggi inviati soddisfino le esigenze e le aspettative dei clienti, in linea con le politiche di comunicazione aziendali.

![](assets/do-not-localize/how-to-video.png) [Scopri questa funzione nel video](#typologies-video)

>[!NOTE]
>
>A seconda dell’offerta, è possibile includere l’ottimizzazione per Campaign o un componente aggiuntivo. Controlla il contratto di licenza.

## Regole di tipologia {#typology-rules}

Con Adobe Campaign puoi progettare e applicare quattro tipi di regole di tipologia:

* **Filtro** regole che ti consentono di escludere parte del target in base a criteri. Per ulteriori informazioni, consulta [Regole di filtro](filtering-rules.md).
* **Pressione** regole che ti consentono di controllare l’affaticamento del marketing. Per ulteriori informazioni, consulta [Regole di pressione](pressure-rules.md).
* **Capacità** regole che consentono di limitare i carichi per garantire condizioni di elaborazione ottimali. Per ulteriori informazioni, consulta [Capacità di controllo](consistency-rules.md#controlling-capacity).
* **Controllo** regole che ti consentono di verificare la validità dei messaggi prima che vengano inviati. Per ulteriori informazioni, consulta [Regole di controllo](control-rules.md).

Una volta create, le regole di tipologia sono raggruppate nelle tipologie di campagne a cui si fa riferimento nelle consegne. Vedi [Applicazione delle tipologie](#applying-typologies).

## Tipologie {#typologies}

Una tipologia di campagna può contenere diversi [regole di tipologia](#typology-rules), ma una consegna può fare riferimento a una sola tipologia.

La **[!UICONTROL Rules]** consente di aggiungere, eliminare o visualizzare le regole di tipologia da applicare.

![](assets/campaign_opt_rules_tab.png)

## Applicazione delle tipologie {#applying-typologies}

I passaggi per creare e applicare una tipologia alle consegne sono elencati di seguito:

1. Creare regole di tipologia.

   Le regole di tipologia si trovano nella **[!UICONTROL Administration > Campaign management > Typology management > Typology rules]** nodo.

   Le diverse regole disponibili in Campaign sono descritte nelle sezioni seguenti: [regole di pressione sulle vendite](pressure-rules.md), [regole di capacità](consistency-rules.md#controlling-capacity), [regole di controllo](control-rules.md) e [regole di filtro](filtering-rules.md).

1. Crea una tipologia e fai riferimento alle regole create al suo interno.

   Le tipologie sono accessibili tramite **[!UICONTROL Administration > Campaign Management > Typology management]** > **[!UICONTROL Typologies]** nodo.

1. Configura la consegna per utilizzare la tipologia creata. Per ulteriori informazioni al riguardo, consulta [questa sezione](applying-rules.md#applying-a-typology-to-a-delivery).
1. Testa e controlla il comportamento attraverso le simulazioni delle campagne. Per ulteriori informazioni sulle simulazioni delle campagne, consulta [questa sezione](campaign-simulations.md).

Durante la preparazione della consegna, i destinatari vengono esclusi quando il criterio è soddisfatto. Per monitorare le esclusioni, puoi controllare i registri. I casi di utilizzo di esempio sulle regole di tipologia della pressione sono disponibili in [questa pagina](pressure-rules.md#use-cases-on-pressure-rules).

## Video tutorial {#typologies-video}

### Come impostare la gestione dell’eccesso utilizzando le regole di tipologia

Questo video spiega come implementare la gestione dell’affaticamento in Adobe Campaign sfruttando le regole di tipologia.

>[!VIDEO](https://video.tv.adobe.com/v/25090?quality=12)

### Come impostare la gestione dell’affaticamento utilizzando filtri predefiniti

La gestione dell’eccesso controlla la frequenza e la quantità di messaggi per evitare un’eccessiva sollecitazione dei destinatari. Se nell&#39;istanza della campagna non è presente il modulo di ottimizzazione della campagna, è possibile configurare un filtro predefinito che filtrerà la popolazione target in base al numero di messaggi ricevuti Questo video spiega come implementare la gestione dell&#39;affaticamento in Adobe Campaign Classic utilizzando i filtri.

>[!VIDEO](https://video.tv.adobe.com/v/25091?quality=12)

Sono disponibili ulteriori video dimostrativi relativi a Campaign [qui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=it).

**Argomento correlato**

* [Applicare regole di business automatiche alle consegne su qualsiasi canale](https://helpx.adobe.com/campaign/kb/simplifying-campaign-management-acc.html#Applyautomaticbusinessrulestodeliveriesonanychannel)

* [Guida introduttiva alle tipologie e alla gestione dell’affaticamento](pressure-rules.md)

