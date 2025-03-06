---
product: campaign
title: Informazioni sulle tipologie di campagne
description: Informazioni sulle tipologie di campagne
role: User, Data Engineer
feature: Typology Rules, Campaigns
hide: true
hidefromtoc: true
exl-id: 6d5b8584-4aa1-4d9a-89d9-d41da75dd323
source-git-commit: 4f809011a8b4cb3803c4e8151e358e5fd73634e4
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 16%

---

# Informazioni sulle tipologie di campagne{#about-campaign-typologies}

Ottimizzazione delle campagne è il modulo di Adobe Campaign che consente di controllare, filtrare e monitorare l’invio delle consegne. Per evitare conflitti tra campagne, Adobe Campaign può sottoporre a test diverse combinazioni applicando specifiche regole di vincolo. Ciò garantisce che i messaggi inviati soddisfino le esigenze e le aspettative dei clienti, in linea con le politiche di comunicazione aziendali.

![](assets/do-not-localize/how-to-video.png) [Guarda il video su questa funzione](#typologies-video)

>[!NOTE]
>
>A seconda dell’offerta, è possibile includere l’ottimizzazione di Campaign o un componente aggiuntivo. Controlla il contratto di licenza.

## Regole di tipologia {#typology-rules}

Con Adobe Campaign puoi progettare e applicare quattro tipi di regole di tipologia:

* **Regole di filtro** che ti consentono di escludere parte della destinazione in base a criteri. Per ulteriori informazioni, consulta [Regole di filtro](filtering-rules.md).
* **Regole di pressione** che consentono di controllare l&#39;eccesso di marketing. Per ulteriori informazioni, consulta [Regole di pressione](pressure-rules.md).
* **Regole di capacità** che consentono di limitare i carichi per garantire condizioni di elaborazione ottimali. Per ulteriori informazioni, consulta [Controllo della capacità](consistency-rules.md#controlling-capacity).
* **Regole di controllo** che consentono di verificare la validità dei messaggi prima che vengano inviati. Per ulteriori informazioni, consulta [Regole di controllo](control-rules.md).

Una volta create, le regole di tipologia sono raggruppate in tipologie di campagne a cui si fa riferimento nelle consegne. Vedi [Applicazione delle tipologie](#applying-typologies).

## Tipologie {#typologies}

Una tipologia di campagna può contenere diverse [regole di tipologia](#typology-rules), ma una consegna può fare riferimento a una sola tipologia.

La scheda **[!UICONTROL Rules]** consente di aggiungere, eliminare o visualizzare le regole di tipologia da applicare.

![](assets/campaign_opt_rules_tab.png)

## Applicazione delle tipologie {#applying-typologies}

Di seguito sono elencati i passaggi per creare e applicare una tipologia alle consegne:

1. Creare regole di tipologia.

   Regole di tipologia trovate nel nodo **[!UICONTROL Administration > Campaign management > Typology management > Typology rules]**.

   Nelle sezioni seguenti sono descritte le diverse regole disponibili in Campaign: [regole di pressione di vendita](pressure-rules.md), [regole di capacità](consistency-rules.md#controlling-capacity), [regole di controllo](control-rules.md) e [regole di filtro](filtering-rules.md).

1. Crea una tipologia e fai riferimento alle regole create al suo interno.

   Le tipologie sono accessibili tramite il nodo **[!UICONTROL Administration > Campaign Management > Typology management]** > **[!UICONTROL Typologies]**.

1. Configura la consegna in modo da utilizzare la tipologia creata. Per ulteriori informazioni al riguardo, consulta [questa sezione](applying-rules.md#applying-a-typology-to-a-delivery).
1. Puoi testare e controllare il comportamento tramite simulazioni di campagne. Per ulteriori informazioni sulle simulazioni delle campagne, consulta [questa sezione](campaign-simulations.md).

Durante la preparazione della consegna, i destinatari vengono esclusi quando viene soddisfatto il criterio. Puoi controllare i registri per monitorare le esclusioni. Casi d&#39;uso di esempio sulle regole di tipologia della pressione sono disponibili in [questa pagina](pressure-rules.md#use-cases-on-pressure-rules).

## Video tutorial {#typologies-video}

### Come impostare la gestione dell’eccesso utilizzando le regole di tipologia

Questo video spiega come implementare la gestione dell’eccesso in Adobe Campaign sfruttando le regole di tipologia.

>[!VIDEO](https://video.tv.adobe.com/v/25090?quality=12)

### Come impostare la gestione dell’affaticamento utilizzando filtri predefiniti

La gestione dell’eccesso controlla la frequenza e la quantità di messaggi per evitare un’eccessiva sollecitazione dei destinatari. Se nell’istanza della campagna non è presente il modulo di ottimizzazione, puoi configurare un filtro predefinito che filtrerà la popolazione target in base al numero di messaggi ricevuti
Questo video spiega come implementare la gestione dell’eccesso in Adobe Campaign Classic utilizzando i filtri.

>[!VIDEO](https://video.tv.adobe.com/v/25091?quality=12)

Ulteriori video dimostrativi di Campaign sono disponibili [qui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=it).

**Argomento correlato**

* [Introduzione alle tipologie e alla gestione dell’eccesso](pressure-rules.md)

