---
product: campaign
title: Gestione della presentazione delle offerte
description: Gestione della presentazione delle offerte
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
exl-id: 6158ffaa-cb08-4f77-82b8-b3e5e1bf7fd7
source-git-commit: d835da6c7b55d9bf70b6b5dc58880718e12211d5
workflow-type: tm+mt
source-wordcount: '995'
ht-degree: 0%

---

# Gestione della presentazione delle offerte{#managing-offer-presentation}

![](../../assets/common.svg)

## Panoramica delle regole di presentazione {#presentation-rules-overview}

L’interazione consente di controllare il flusso delle proposte di offerta utilizzando le regole di presentazione. Queste regole, specifiche dell’interazione, sono regole di tipologia. Ti consentono di escludere le offerte in base alla cronologia delle proposte già effettuate a un destinatario. Si fa riferimento ad essi nell’ambiente

## Creazione e riferimento a una regola di presentazione dell’offerta {#creating-and-referencing-an-offer-presentation-rule}

1. Vai a **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Typology management]** > **[!UICONTROL Typology rules]** nodo.
1. Crea una regola di tipologia e scegli la **[!UICONTROL Offer presentation]** digitare.

   ![](assets/offer_typology_001.png)

1. Specifica il canale a cui applicare la regola.

   ![](assets/offer_typology_002.png)

1. Configura i criteri di applicazione della regola. Per ulteriori informazioni, consulta [Impostazioni delle regole di presentazione](#presentation-rule-settings).
1. Vai a **[!UICONTROL Administration]** > **[!UICONTROL Campaign execution]** > **[!UICONTROL Typology management]** > **[!UICONTROL Typologies]** e crea una tipologia che raggrupperà tutti **[!UICONTROL Offer presentation]** digitare le regole.

   ![](assets/offer_typology_003.png)

1. Una volta creata la tipologia, posiziona il cursore sulle regole di tipologia e raggruppatele nella tipologia appena creata.

   ![](assets/offer_typology_004.png)

1. Nell’ambiente delle offerte, fai riferimento alla tipologia utilizzando l’elenco a discesa .

   ![](assets/offer_typology_005.png)

## Impostazioni delle regole di presentazione {#presentation-rule-settings}

### Criteri di applicazione {#application-criteria-}

I criteri di applicazione disponibili nel **[!UICONTROL General]** consente di specificare le offerte a cui si applica la regola di presentazione. A questo scopo, devi creare una query e scegliere le offerte interessate, come descritto di seguito.

1. Nella regola di tipologia, fai clic sul pulsante **[!UICONTROL Edit the rule application conditions...]** per creare la query.

   ![](assets/offer_typology_006.png)

1. Nella finestra della query, puoi applicare un filtro alle offerte alle quali desideri applicare una regola di tipologia.

   Ad esempio, puoi selezionare una categoria di offerta.

   ![](assets/offer_typology_008.png)

### Dimensioni dell’offerta {#offer-dimensions}

In **[!UICONTROL Offer presentation]** È necessario specificare le stesse dimensioni per la regola di presentazione di quelle configurate nell&#39;ambiente.

La **[!UICONTROL Targeting dimension]** coincide con la tabella dei destinatari (per impostazione predefinita: nms:destinatari) che riceveranno le proposte di offerta. La **[!UICONTROL Storage dimension]** coincide con la tabella che contiene la cronologia delle proposte collegata alla dimensione di targeting (per impostazione predefinita:nms:propositionRcp).

![](assets/offer_typology_009.png)

>[!NOTE]
>
>È inoltre possibile utilizzare tabelle non standard. Se desideri utilizzare una dimensione di targeting specifica, dovrai creare tabelle e un ambiente dedicato utilizzando la mappatura di destinazione. Per ulteriori informazioni, consulta [Creazione di un ambiente di offerta](../../interaction/using/live-design-environments.md#creating-an-offer-environment).

### Punto {#period}

Si tratta di un periodo scorrevole che inizia nella data di presentazione dell’offerta. Stabilisce un termine per la validità delle proposte di offerta. La regola non si applica alle proposte di offerta effettuate oltre questo periodo.

Il periodo inizia **n** giorni precedenti la data della proposta e la data di scadenza **n** giorni successivi, dove **n** corrisponde al numero immesso nel **[!UICONTROL Period considered]** campo:

* Per gli spazi in entrata, la data di proposta è la data di presentazione dell’offerta.
* Per gli spazi in uscita, la data di proposta è la data di contatto di consegna (ad esempio la data di consegna immessa in un flusso di lavoro di targeting).

Utilizzare le frecce per modificare il numero di giorni o inserire direttamente un punto (&quot;2d 6h&quot;, ad esempio).

![](assets/offer_typology_010.png)

### Numero di proposte {#number-of-propositions}

È possibile impostare il numero più elevato di proposte che possono essere fatte prima che l&#39;offerta o le offerte in questione siano escluse.

Utilizza le frecce per modificare il numero di proposte di offerta.

![](assets/offer_typology_011.png)

## Definizione di proposte e destinatari {#defining-propositions-and-recipients}

La **[!UICONTROL Propositions to count]** La sezione ti consente di specificare sia i destinatari che le proposte che porteranno all’esclusione delle offerte definite nella **[!UICONTROL General]** se appaiono un certo numero di volte nella cronologia delle proposte.

### Proposizioni di filtro {#filtering-propositions}

Puoi selezionare i criteri di filtro per escludere le proposte in base al canale, alle offerte interessate o allo stato delle proposte precedentemente assegnate.

![](assets/offer_typology_014.png)

Tali criteri rappresentano le applicazioni più frequenti delle regole di presentazione. Per utilizzare altri criteri, puoi creare una query utilizzando la **[!UICONTROL Limit propositions...]** link. Per ulteriori informazioni, consulta la sezione [Creazione di una query sulle proposte](#creating-a-query-on-propositions) sezione .

* **Filtrare sul canale**

   **[!UICONTROL On the same channel only]** : consente di escludere le proposte di offerta dal canale specificato nella **[!UICONTROL General]** scheda .

   Ad esempio, il canale specificato per la regola nel **[!UICONTROL General]** è e-mail. Se le offerte a cui si applica la regola sono state finora offerte solo sul canale web, il motore di interazione può presentare le offerte in una consegna e-mail. Tuttavia, una volta che le offerte sono state presentate tramite e-mail, il motore di interazione sceglierà un canale diverso per presentare le offerte.

   >[!NOTE]
   >
   >Stiamo parlando del canale e non dello spazio. Se la regola deve escludere un’offerta sul canale web, l’offerta destinata a essere presentata su un sito web in due spazi (ad esempio in un banner e nel corpo della pagina) non verrà visualizzata sul sito se è già stata presentata in precedenza.
   >
   >Per un flusso di lavoro che coinvolge la presentazione dell’offerta, le regole vengono prese correttamente in considerazione solo se configurate in **[!UICONTROL All channels]**.

* **Filtrare l’offerta**

   Questo filtro consente di limitare le proposte di offerta da conteggiare a specifici set di offerte.

   **[!UICONTROL All offers]** : valore predefinito. Alle offerte non viene applicato alcun filtro.

   **[!UICONTROL Offer being presented]** : l&#39;offerta specificata nel **[!UICONTROL General]** La scheda viene esclusa se è già stata presentata.

   **[!UICONTROL Offers from the same category]** : un’offerta è esclusa se è già stata presentata un’offerta della stessa categoria.

   **[!UICONTROL The offers which the rule applies to]** : quando più offerte sono definite nella **[!UICONTROL General]** scheda , ogni proposta di offerta da questo set di offerte viene presa in considerazione e termina nell’esclusione di tutte le offerte se viene raggiunta la soglia di proposta.

   Ad esempio, le offerte 2, 3 e 5 sono definite nella **[!UICONTROL General]** scheda . Il numero massimo di proposte è impostato su 2. Se le offerte 2 e 5 vengono presentate una volta, il numero di proposte conteggiate sarà 2. Di conseguenza, l&#39;offerta 3 non verrà mai presentata.

* **Filtrare lo stato della proposta**

   Questo filtro consente di scegliere gli stati più frequenti per le proposte di offerta da prendere in considerazione nella cronologia delle proposte.

   **[!UICONTROL Regardless of the proposition status]** : valore predefinito. Nessun filtro viene applicato allo stato della proposta.

   **[!UICONTROL Accepted or rejected propositions]** : consente di escludere le offerte presentate in precedenza che sono state accettate o rifiutate.

   **[!UICONTROL Accepted propositions]** : consente di escludere le offerte presentate in precedenza che sono state accettate.

   **[!UICONTROL Rejected propositions]** : consente di escludere le offerte presentate in precedenza che sono state rifiutate.

### Definizione dei destinatari {#defining-recipients}

Per specificare i destinatari, fai clic sul pulsante **[!UICONTROL Edit the query from the targeting dimension...]** collega e seleziona i destinatari interessati dalla regola.

![](assets/offer_typology_012.png)

### Creazione di una query sulle proposte {#creating-a-query-on-propositions}

Per specificare le proposte da conteggiare tramite una query, fai clic sul pulsante **[!UICONTROL Limit propositions...]** collegare e specificare i criteri da prendere in considerazione.

Nell’esempio seguente, le proposte da conteggiare dopo due presentazioni sono quelle nella **Offerte speciali** per la categoria **Call center** spazio, con un peso inferiore **20**.

![](assets/offer_typology_013.png)
