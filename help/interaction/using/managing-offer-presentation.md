---
solution: Campaign Classic
product: campaign
title: Gestione della presentazione delle offerte
description: Gestione della presentazione delle offerte
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '996'
ht-degree: 0%

---


# Gestione della presentazione delle offerte{#managing-offer-presentation}

## Panoramica delle regole di presentazione {#presentation-rules-overview}

L&#39;interazione consente di controllare il flusso delle proposte di offerta utilizzando le regole di presentazione. Queste regole, specifiche dell&#39;interazione, sono regole di tipologia. Consentono di escludere le offerte in base alla cronologia delle proposte già presentate a un destinatario. Sono citati nell&#39;ambiente

## Creazione e riferimento a una regola di presentazione delle offerte {#creating-and-referencing-an-offer-presentation-rule}

1. Andate al nodo **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Typology management]** > **[!UICONTROL Typology rules]**.
1. Create una regola di tipologia e scegliete il tipo **[!UICONTROL Offer presentation]**.

   ![](assets/offer_typology_001.png)

1. Specificate il canale a cui applicare la regola.

   ![](assets/offer_typology_002.png)

1. Configurare i criteri di applicazione della regola. Per ulteriori informazioni, fare riferimento a [Impostazioni regola presentazione](#presentation-rule-settings).
1. Andate al nodo **[!UICONTROL Administration]** > **[!UICONTROL Campaign execution]** > **[!UICONTROL Typology management]** > **[!UICONTROL Typologies]** e create una tipologia che raggrupperà tutte le regole di tipo **[!UICONTROL Offer presentation]**.

   ![](assets/offer_typology_003.png)

1. Una volta creata la tipologia, posizionate il cursore sulle regole di tipologia e raggruppatele nella tipologia appena creata.

   ![](assets/offer_typology_004.png)

1. Nell’ambiente delle offerte, fate riferimento alla tipologia utilizzando l’elenco a discesa.

   ![](assets/offer_typology_005.png)

## Impostazioni della regola di presentazione {#presentation-rule-settings}

### Criteri di applicazione {#application-criteria-}

I criteri di applicazione disponibili nella scheda **[!UICONTROL General]** consentono di specificare le offerte a cui si applicherà la regola di presentazione. A tal fine, è necessario creare una query e scegliere le offerte interessate, come descritto di seguito.

1. Nella regola di tipologia, fai clic sul collegamento **[!UICONTROL Edit the rule application conditions...]** per creare la query.

   ![](assets/offer_typology_006.png)

1. Nella finestra della query potete applicare un filtro alle offerte alle quali desiderate applicare una regola di tipologia.

   Ad esempio, potete selezionare una categoria di offerte.

   ![](assets/offer_typology_008.png)

### Dimensioni dell&#39;offerta {#offer-dimensions}

Nella scheda **[!UICONTROL Offer presentation]**, è necessario specificare le stesse dimensioni per la regola di presentazione di quelle configurate nell&#39;ambiente.

La **[!UICONTROL Targeting dimension]** coincide con la tabella dei destinatari (per impostazione predefinita: nms:destinatari) che riceveranno le proposte di offerta. La **[!UICONTROL Storage dimension]** coincide con la tabella che contiene la cronologia delle proposizioni collegata alla dimensione di targeting (per impostazione predefinita:nms:propositionRcp).

![](assets/offer_typology_009.png)

>[!NOTE]
>
>È inoltre possibile utilizzare tabelle non standard. Se desiderate utilizzare una dimensione di targeting specifica, dovrete creare tabelle e un ambiente dedicato utilizzando la mappatura di destinazione. Per ulteriori informazioni, vedere [Creazione di un ambiente di offerta](../../interaction/using/live-design-environments.md#creating-an-offer-environment).

### Periodo {#period}

Si tratta di un periodo scorrevole che inizia alla data della presentazione dell&#39;offerta. Definisce un termine per la validità delle proposte di offerta. La regola non si applica alle proposte di offerta fatte oltre tale periodo.

Il periodo inizia **n** giorni prima della data di offerta e termina **n** giorni dopo, dove **n** corrisponde al numero immesso nel campo **[!UICONTROL Period considered]**:

* Per gli spazi in entrata, la data di proposta è la data di presentazione dell&#39;offerta.
* Per gli spazi in uscita, la data di proposta è la data di contatto di consegna (ad esempio la data di consegna immessa in un flusso di lavoro di targeting).

Usate le frecce per cambiare il numero di giorni o immettere direttamente un punto (&quot;2d 6h&quot;, ad esempio).

![](assets/offer_typology_010.png)

### Numero di proposizioni {#number-of-propositions}

È possibile stabilire il numero massimo di proposte che possono essere fatte prima che le offerte in questione siano escluse.

Utilizzate le frecce per cambiare il numero di proposte di offerta.

![](assets/offer_typology_011.png)

## Definizione di proposte e destinatari {#defining-propositions-and-recipients}

La sezione **[!UICONTROL Propositions to count]** consente di specificare sia i destinatari che le proposte che porteranno all&#39;esclusione delle offerte definite nella scheda **[!UICONTROL General]** se appaiono un certo numero di volte nella cronologia delle proposte.

### Filtrare le proposizioni {#filtering-propositions}

Potete selezionare criteri di filtraggio per escludere le proposizioni in base al canale, alle offerte interessate o allo stato delle proposte assegnate in precedenza.

![](assets/offer_typology_014.png)

Tali criteri rappresentano le applicazioni più frequenti delle regole di presentazione. Per utilizzare altri criteri, potete creare una query utilizzando il collegamento **[!UICONTROL Limit propositions...]**. Per ulteriori informazioni, consultare la sezione [Creazione di una query sulle proposizioni](#creating-a-query-on-propositions).

* **Filtrare sul canale**

   **[!UICONTROL On the same channel only]** : consente di escludere le proposte di offerta sul canale specificato nella  **[!UICONTROL General]** scheda.

   Ad esempio, il canale specificato per la regola nella scheda **[!UICONTROL General]** è email. Se le offerte a cui si applica la regola finora sono state offerte solo sul canale Web, il motore di interazione può presentare le offerte in una consegna tramite e-mail. Tuttavia, una volta che le offerte sono state presentate via e-mail, il motore di interazione sceglierà un canale diverso per presentare le offerte.

   >[!NOTE]
   >
   >Stiamo parlando del canale e non dello spazio. Se la regola deve escludere un&#39;offerta sul canale Web, l&#39;offerta destinata a essere presentata su un sito Web in due spazi (ad esempio in un banner e nel corpo della pagina) non verrà visualizzata sul sito se è già stata presentata in precedenza.
   >
   >Per un flusso di lavoro che include la presentazione delle offerte, le regole vengono prese in considerazione correttamente solo se configurate su **[!UICONTROL All channels]**.

* **Filtrare l&#39;offerta**

   Questo filtro consente di limitare le proposte di offerta da conteggiare a specifici set di offerte.

   **[!UICONTROL All offers]** : valore predefinito. Alle offerte non viene applicato alcun filtro.

   **[!UICONTROL Offer being presented]** : l&#39;offerta specificata nella  **[!UICONTROL General]** scheda è esclusa se è già stata presentata.

   **[!UICONTROL Offers from the same category]** : un&#39;offerta è esclusa se è già stata presentata un&#39;offerta della stessa categoria.

   **[!UICONTROL The offers which the rule applies to]** : quando più offerte sono definite nella  **[!UICONTROL General]** scheda, ogni proposta di offerta di questo set di offerte viene presa in considerazione e termina nell&#39;esclusione di tutte le offerte se viene raggiunta la soglia di offerta.

   Ad esempio, le offerte 2, 3 e 5 sono definite nella scheda **[!UICONTROL General]**. Il numero massimo di proposte è impostato su 2. Se le offerte 2 e 5 sono presentate una volta, il numero di proposte contate sarà 2. Di conseguenza, l&#39;offerta 3 non sarà mai presentata.

* **Filtrare lo stato dell&#39;offerta**

   Questo filtro consente di scegliere gli stati più frequenti per tenere conto delle proposte nella cronologia delle proposte.

   **[!UICONTROL Regardless of the proposition status]** : valore predefinito. Nessun filtro applicato allo stato della proposta.

   **[!UICONTROL Accepted or rejected propositions]** : consente di escludere le offerte presentate in precedenza che sono state accettate o rifiutate.

   **[!UICONTROL Accepted propositions]** : consente di escludere le offerte presentate in precedenza che sono state accettate.

   **[!UICONTROL Rejected propositions]** : consente di escludere le offerte presentate in precedenza che sono state rifiutate.

### Definizione dei destinatari {#defining-recipients}

Per specificare i destinatari, fare clic sul collegamento **[!UICONTROL Edit the query from the targeting dimension...]** e selezionare i destinatari interessati dalla regola.

![](assets/offer_typology_012.png)

### Creazione di una query sulle proposizioni {#creating-a-query-on-propositions}

Per specificare le proposizioni da conteggiare tramite una query, fare clic sul collegamento **[!UICONTROL Limit propositions...]** e specificare i criteri da prendere in considerazione.

Nell&#39;esempio seguente, le proposte da conteggiare dopo due presentazioni sono quelle della categoria **Offerte speciali**, per lo spazio **Call center**, con un peso inferiore a **20**.

![](assets/offer_typology_013.png)

