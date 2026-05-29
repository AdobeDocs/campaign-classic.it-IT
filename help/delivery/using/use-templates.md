---
product: campaign
title: Utilizzare i modelli di consegna
description: Utilizzare i modelli di consegna
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Delivery Templates
hide: true
exl-id: a5da3f29-5eab-428c-b7c3-d9e4243fe628
TQID: https://experienceleague.adobe.com/99urg-HfXdZVnSsbFPzG9d2RkmxkPoYGNDEojWHmux4
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616aid: b631758a-142d-425f-b9aa-f756d85cb979id: c858a28b-ea19-49b0-8d48-828717fad89c
topic_v2: id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
subfeature_v2: id: e95a583b-fcfa-4524-8666-46a29c828119id: c8da4fdd-eb94-4751-a43c-f82733fb2d6eid: d5bbe3da-ba85-4242-817e-54f7c4b943e0id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 598
ht-degree: 6%

---

# Utilizzare i modelli {#use-templates}



I modelli di consegna consentono una maggiore efficienza, fornendo scenari pronti per i tipi più comuni di attività. Con i modelli, gli esperti di marketing possono distribuire nuove campagne con una personalizzazione minima in un periodo di tempo più breve.

Ulteriori informazioni sui modelli di consegna in [questa sezione](about-templates.md).

## Introduzione ai modelli di consegna {#gs-templates}

Un [modello di consegna](about-templates.md) ti consente di definire una volta una serie di proprietà tecniche e funzionali che soddisfano le tue esigenze e che possono essere riutilizzate per le consegne future. Potrai quindi risparmiare tempo e standardizzare le consegne quando necessario.

Quando gestisci più marchi in Adobe Campaign, Adobe consiglia di avere un sottodominio per marchio. Ad esempio, una banca può avere diversi sottodomini corrispondenti a ciascuna delle sue agenzie regionali. Se una banca è proprietaria del dominio bluebank.com, i sottodomini possono essere @ny.bluebank.com, @ma.bluebank.com, @ca.bluebank.com, ecc. Disporre di un modello di consegna per sottodominio consente di utilizzare sempre i giusti parametri preconfigurati per ciascun marchio, evitando errori e risparmiando tempo.

**Suggerimento**: per evitare errori di configurazione, è consigliabile duplicare un modello nativo e modificarne le proprietà anziché crearne uno nuovo.

## Configurare gli indirizzi

* L’indirizzo del mittente è obbligatorio per consentire l’invio di un’e-mail.

* Alcuni ISP (provider di servizi Internet) verificano la validità dell’indirizzo del mittente prima di accettare i messaggi.

* Un indirizzo con formato non corretto può comportare il rifiuto da parte del server ricevente. Devi accertarti che sia stato fornito un indirizzo corretto.

* L’indirizzo deve identificare esplicitamente il mittente. Il dominio deve essere di proprietà del mittente e deve essere registrato nel mittente.

* Adobe consiglia di creare account e-mail corrispondenti agli indirizzi specificati per le consegne e le risposte. Rivolgiti all’amministratore del sistema di messaggistica.

Per configurare gli indirizzi nell’interfaccia di Campaign, effettua le seguenti operazioni:

1. Nel [modello di consegna](about-templates.md), fai clic sul collegamento **[!UICONTROL From]**. Nella finestra **[!UICONTROL Email header parameters]**, compila i campi seguenti:

   ![](assets/d_best_practices_email_header.png)

1. Nel campo **[!UICONTROL Sender address]**, assicurati che il dominio dell&#39;indirizzo sia lo stesso del sottodominio delegato ad Adobe. È possibile modificare la parte che precede &#39;@&#39; ma non l&#39;indirizzo di dominio.

1. Nel campo **[!UICONTROL From]**, utilizza un nome facilmente identificabile dai destinatari, ad esempio il nome del tuo marchio, per aumentare il tasso di apertura delle consegne. Per migliorare ulteriormente l’esperienza del destinatario, puoi aggiungere il nome di una persona, ad esempio &quot;Emma from Megastore&quot;.

1. Nei campi **[!UICONTROL Reply address text]**, l&#39;indirizzo del mittente viene utilizzato per impostazione predefinita per le risposte. Tuttavia, Adobe consiglia di utilizzare un indirizzo reale esistente, ad esempio l’assistenza clienti del tuo marchio. In questo caso, se un destinatario invia una risposta, l’assistenza clienti sarà in grado di gestirla.

### Configurare un gruppo di controllo

Una volta inviata la consegna, puoi confrontare il comportamento dei destinatari esclusi con quello dei destinatari che l’hanno ricevuta. Puoi quindi misurare l’efficienza delle campagne. Ulteriori informazioni sui gruppi di controllo [in questa sezione](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).

Per impostare un gruppo di controllo, fare clic sul collegamento **[!UICONTROL To]**. Nella finestra **[!UICONTROL Select target]**, selezionare la scheda **[!UICONTROL Control group]**. È possibile estrarre una parte della destinazione, ad esempio un campione casuale del 5%.

![](assets/d_best_practices_control_group.png)

## Utilizzare le tipologie per applicare filtri o regole di controllo

Una tipologia contiene regole di controllo applicate durante la fase di analisi, prima di inviare qualsiasi messaggio.

Nella scheda **[!UICONTROL Typology]** delle proprietà del modello, modifica la tipologia predefinita in base alle tue esigenze.

Ad esempio, per controllare meglio il traffico in uscita, puoi definire quali indirizzi IP possono essere utilizzati definendo un’affinità per sottodominio e creando una tipologia per affinità. Le affinità sono definite nel file di configurazione dell’istanza. Contatta il tuo amministratore Adobe Campaign.

Per ulteriori informazioni sulle tipologie, consulta [questa sezione](../../campaign-opt/using/about-campaign-typologies.md).
