---
product: campaign
title: Informazioni sulle tipologie di campagne
description: Informazioni sulle tipologie di campagne
role: User, Data Engineer
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
feature: Typology Rules, Campaigns
exl-id: 6d5b8584-4aa1-4d9a-89d9-d41da75dd323
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 17%

---

# Informazioni sulle tipologie di campagne{#about-campaign-typologies}

Ottimizzazione delle campagne è il modulo di Adobe Campaign che consente di controllare, filtrare e monitorare l’invio delle consegne. Per evitare conflitti tra campagne, Adobe Campaign può sottoporre a test diverse combinazioni applicando specifiche regole di vincolo. Ciò garantisce che i messaggi inviati soddisfino le esigenze e le aspettative dei clienti, in linea con le politiche di comunicazione aziendali.

![](assets/do-not-localize/how-to-video.png) [Guarda il video su questa funzione](#typologies-video)

>[!NOTE]
>
>A seconda dell’offerta, è possibile includere l’ottimizzazione di Campaign o un componente aggiuntivo. Controlla il contratto di licenza.

## Regole di tipologia {#typology-rules}

Con Adobe Campaign puoi progettare e applicare quattro tipi di regole di tipologia:

* **Filtraggio** regole che ti consentono di escludere parte del target in base a criteri. Per ulteriori informazioni, consulta [Regole di filtro](filtering-rules.md).
* **Pressione** regole che consentono di controllare l’eccesso di marketing. Per ulteriori informazioni, consulta [Regole di pressione](pressure-rules.md).
* **Capacità** regole che consentono di limitare i carichi per garantire condizioni di elaborazione ottimali. Per ulteriori informazioni, consulta [Capacità di controllo](consistency-rules.md#controlling-capacity).
* **Controllo** regole che ti consentono di verificare la validità dei messaggi prima che vengano inviati. Per ulteriori informazioni, consulta [Regole di controllo](control-rules.md).

Una volta create, le regole di tipologia sono raggruppate in tipologie di campagne a cui si fa riferimento nelle consegne. Consulta [Applicazione delle tipologie](#applying-typologies).

## Tipologie {#typologies}

Una tipologia di campagna può contenere diversi [regole di tipologia](#typology-rules), ma una consegna può fare riferimento solo a una tipologia.

Il **[!UICONTROL Rules]** Questa scheda ti consente di aggiungere, eliminare o visualizzare le regole di tipologia da applicare.

![](assets/campaign_opt_rules_tab.png)

## Applicazione delle tipologie {#applying-typologies}

Di seguito sono elencati i passaggi per creare e applicare una tipologia alle consegne:

1. Creare regole di tipologia.

   Le regole di tipologia si trovano in **[!UICONTROL Administration > Campaign management > Typology management > Typology rules]** nodo.

   Le diverse regole disponibili in Campaign sono descritte nelle sezioni seguenti: [regole di pressione di vendita](pressure-rules.md), [regole di capacità](consistency-rules.md#controlling-capacity), [regole di controllo](control-rules.md) e [regole di filtro](filtering-rules.md).

1. Crea una tipologia e fai riferimento alle regole create al suo interno.

   Le tipologie sono accessibili tramite **[!UICONTROL Administration > Campaign Management > Typology management]** > **[!UICONTROL Typologies]** nodo.

1. Configura la consegna in modo da utilizzare la tipologia creata. Per ulteriori informazioni al riguardo, consulta [questa sezione](applying-rules.md#applying-a-typology-to-a-delivery).
1. Puoi testare e controllare il comportamento tramite simulazioni di campagne. Per ulteriori informazioni sulle simulazioni delle campagne, consulta [questa sezione](campaign-simulations.md).

Durante la preparazione della consegna, i destinatari vengono esclusi quando viene soddisfatto il criterio. Puoi controllare i registri per monitorare le esclusioni. Casi d’uso di esempio sulle regole di tipologia della pressione sono disponibili in [questa pagina](pressure-rules.md#use-cases-on-pressure-rules).

## Video tutorial {#typologies-video}

### Come impostare la gestione dell’eccesso utilizzando le regole di tipologia

Questo video spiega come implementare la gestione dell’eccesso in Adobe Campaign sfruttando le regole di tipologia.

>[!VIDEO](https://video.tv.adobe.com/v/25090?quality=12)

### Come impostare la gestione dell’affaticamento utilizzando filtri predefiniti

La gestione dell’eccesso controlla la frequenza e la quantità di messaggi per evitare un’eccessiva sollecitazione dei destinatari. Se nell’istanza della campagna non è presente il modulo di ottimizzazione, puoi configurare un filtro predefinito che filtrerà la popolazione target in base al numero di messaggi ricevuti. Questo video spiega come implementare la gestione dell’eccesso in Adobe Campaign Classic utilizzando i filtri.

>[!VIDEO](https://video.tv.adobe.com/v/25091?quality=12)

Sono disponibili altri video dimostrativi di Campaign [qui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=it).

**Argomento correlato**

* [Introduzione alle tipologie e alla gestione dell’eccesso](pressure-rules.md)

