---
product: campaign
title: Regole di controllo
description: Regole di controllo
audience: campaign
content-type: reference
topic-tags: campaign-optimization
exl-id: 5a5f26f6-38da-4488-aadb-81fcb5359331
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 1%

---

# Regole di controllo{#control-rules}

![](../../assets/v7-only.svg)

## Regole di analisi e di controllo dell&#39;arbitrato {#analysis-and-arbitration-control-rules}

Le regole di controllo ti consentono di garantire la validità e la qualità dei messaggi prima della consegna: visualizzazione dei caratteri, dimensioni dell’SMS, formato dell’indirizzo, ecc.

Una serie di regole predefinite ti consente di eseguire i consueti controlli. Questi controlli (in grassetto nell’interfaccia) sono:

* **[!UICONTROL Object approval]** (e-mail): controlla che l&#39;oggetto e l&#39;indirizzo del mittente non contengano caratteri speciali che possono causare problemi ad alcuni agenti di posta elettronica.
* **[!UICONTROL URL label approval]** (e-mail): controlla che ogni URL di tracciamento abbia un’etichetta.
* **[!UICONTROL URL approval]** (e-mail): controlla gli URL di tracciamento (presenza del carattere &quot;&amp;&quot;).
* **[!UICONTROL Message size approval]** (mobile): controlla le dimensioni dei messaggi SMS.
* **[!UICONTROL Validity period check]** (e-mail): controlla che il periodo di validità della consegna sia sufficientemente lungo da consentire l’invio di tutti i messaggi.
* **[!UICONTROL Proof size check]** (tutti i canali): genera un messaggio di errore se la popolazione target della bozza supera i 100 destinatari.
* **[!UICONTROL Wave scheduling check]** (e-mail): controlla che l’ultima serie di consegne abbia inizio prima della fine del periodo di validità, se la consegna è suddivisa in più ondate.
* **[!UICONTROL Unsubscription link approval]** (e-mail): verifica la presenza di almeno un URL di annullamento dell’abbonamento (opt-out) in ciascun contenuto (HTML e testo).

## Creazione di una regola di controllo {#creating-a-control-rule}

È possibile creare nuove regole di controllo in base alle proprie esigenze. A questo scopo, crea una regola di tipologia **[!UICONTROL Control]** e immetti la formula di controllo in SQL nella scheda **[!UICONTROL Code]** .

**Esempio:**

Nell’esempio seguente, creeremo una regola per impedire l’invio di un’offerta SMS a più di 100 destinatari. Questa regola sarà collegata a una tipologia di campagna, quindi alle consegne SMS per le quali è disponibile l’offerta interessata.

Applica i seguenti passaggi:

1. Crea una regola di tipologia **[!UICONTROL Control]**. Selezionare un livello di avviso **[!UICONTROL Warning]**.

   ![](assets/campaign_opt_create_control_01.png)

1. Nella scheda **[!UICONTROL Code]** , immetti lo script per applicare la soglia desiderata, come illustrato di seguito:

   ![](assets/campaign_opt_create_control_02.png)

   Questo script attiva un avviso se il target di consegna supera i 100 contatti:

   ```
   if( delivery.FCP == false && delivery.properties.toDeliver > 100 ) { logWarning("Significant number of SMS to deliver (" + delivery.properties.toDeliver + "). Please make sure the target is correct.") return false; } return true
   ```

1. Collega questa regola a una tipologia di campagna e fai riferimento alla tipologia nella consegna SMS interessata.

   ![](assets/campaign_opt_create_control_03.png)

1. Durante l’analisi della consegna, la regola viene applicata e viene creato un avviso, se applicabile.

   ![](assets/campaign_opt_create_control_04.png)

   Tuttavia, la consegna sarà ancora pronta per l’invio.

   Se aumenti il livello di avviso, la consegna non verrà avviata.

   ![](assets/campaign_opt_create_control_05.png)

   Al termine dell’analisi, il pulsante **[!UICONTROL Confirm delivery]** non sarà disponibile.

   ![](assets/campaign_opt_create_control_06.png)