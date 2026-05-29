---
product: campaign
title: Regole di controllo
description: Scopri come utilizzare le regole di controllo in Adobe Campaign
role: User, Developer
feature: Typology Rules, Campaigns
hide: true
exl-id: 5a5f26f6-38da-4488-aadb-81fcb5359331
TQID: https://experienceleague.adobe.com/zeKJZ7Y-qtGpPtZ6tUPN42ISVU6Fh6wpOuhfcXDsyAA
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
subfeature_v2:
  - id: e5fb657f-3c0a-4fcc-9980-3589a23ab4de
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 368
ht-degree: 1%

---

# Regole di controllo{#control-rules}

## Regole di analisi e di controllo arbitrato {#analysis-and-arbitration-control-rules}

Le regole di controllo ti consentono di garantire la validità e la qualità dei messaggi prima della consegna: visualizzazione dei caratteri, dimensioni dell’SMS, formato dell’indirizzo, ecc.

Una serie di regole pronte all’uso consente di eseguire i controlli standard. Questi controlli (visualizzati in grassetto nell’interfaccia) sono:

* **[!UICONTROL Object approval]** (e-mail): verifica che l&#39;oggetto e l&#39;indirizzo del mittente non contengano caratteri speciali che potrebbero causare problemi a determinati agenti di posta.
* **[!UICONTROL URL label approval]** (e-mail): verifica che ogni URL di tracciamento presenti un&#39;etichetta.
* **[!UICONTROL URL approval]** (e-mail): verifica gli URL di tracciamento (presenza del carattere &quot;&amp;&quot;).
* **[!UICONTROL Message size approval]** (cellulare): verifica la dimensione dei messaggi SMS.
* **[!UICONTROL Validity period check]** (e-mail): verifica che il periodo di validità della consegna sia sufficientemente lungo da consentire l&#39;invio di tutti i messaggi.
* **[!UICONTROL Proof size check]** (tutti i canali): genera un messaggio di errore se la popolazione target della bozza supera i 100 destinatari.
* **[!UICONTROL Wave scheduling check]** (e-mail): verifica che l&#39;ultimo numero di consegne sia programmato per iniziare prima della fine del periodo di validità, se la consegna è suddivisa in più scaglioni.
* **[!UICONTROL Unsubscription link approval]** (e-mail): verifica la presenza di almeno un URL di annullamento dell&#39;abbonamento (rinuncia) in ogni contenuto (HTML e testo).

## Creazione di una regola di controllo {#creating-a-control-rule}

È possibile creare nuove regole di controllo in base alle tue esigenze. A tale scopo, creare una regola di tipologia **[!UICONTROL Control]** e immettere la formula di controllo in SQL nella scheda **[!UICONTROL Code]**.

**Esempio:**

Nell’esempio seguente verrà creata una regola per impedire l’invio di un’offerta SMS a più di 100 destinatari. Questa regola sarà collegata a una tipologia di campagna, quindi alle consegne di SMS per le quali è disponibile l’offerta in questione.

Applica i seguenti passaggi:

1. Creare una regola di tipologia **[!UICONTROL Control]**. Selezionare un livello di avviso **[!UICONTROL Warning]**.

   ![](assets/campaign_opt_create_control_01.png)

1. Nella scheda **[!UICONTROL Code]**, immettere lo script per applicare la soglia desiderata, come illustrato di seguito:

   ![](assets/campaign_opt_create_control_02.png)

   Questo script attiverà un avviso se il target della consegna supera i 100 contatti:

   ```
   if( delivery.FCP == false && delivery.properties.toDeliver > 100 ) { logWarning("Significant number of SMS to deliver (" + delivery.properties.toDeliver + "). Please make sure the target is correct.") return false; } return true
   ```

1. Collega questa regola a una tipologia di campagna e fai riferimento alla tipologia nell’SMS interessato.

   ![](assets/campaign_opt_create_control_03.png)

1. Durante l’analisi della consegna, la regola viene applicata e viene creato un avviso, se applicabile.

   ![](assets/campaign_opt_create_control_04.png)

   Tuttavia, la consegna sarà ancora pronta per l’invio.

   Se aumenti il livello di avviso, ciò impedirà l’avvio della consegna.

   ![](assets/campaign_opt_create_control_05.png)

   Al termine dell&#39;analisi, il pulsante **[!UICONTROL Confirm delivery]** non sarà disponibile.

   ![](assets/campaign_opt_create_control_06.png)
