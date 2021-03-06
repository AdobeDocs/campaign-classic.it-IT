---
product: campaign
title: Utilizzare i modelli di consegna
description: Utilizzare i modelli di consegna
feature: Delivery Templates
exl-id: a5da3f29-5eab-428c-b7c3-d9e4243fe628
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '580'
ht-degree: 1%

---

# Utilizzare i modelli {#use-templates}

![](../../assets/common.svg)

I modelli di consegna consentono una maggiore efficienza, fornendo scenari pronti per la maggior parte dei tipi di attività comuni. Con i modelli, gli esperti di marketing possono distribuire nuove campagne con una personalizzazione minima in un lasso di tempo più breve.

Ulteriori informazioni sui modelli di consegna in [questa sezione](creating-a-delivery-template.md).

## Guida introduttiva ai modelli di consegna {#gs-templates}

A [modello di consegna](creating-a-delivery-template.md) consente di definire una volta un insieme di proprietà tecniche e funzionali adatte alle tue esigenze e che possono essere riutilizzate per consegne future. Puoi quindi risparmiare tempo e standardizzare le consegne quando necessario.

Quando gestisci diversi marchi in Adobe Campaign, Adobe consiglia di disporre di un sottodominio per marchio. Ad esempio, una banca può avere diversi sottodomini corrispondenti a ciascuna delle sue agenzie regionali. Se una banca possiede il dominio bluebank.com, i suoi sottodomini possono essere @ny.bluebank.com, @ma.bluebank.com, @ca.bluebank.com, ecc. Disporre di un modello di consegna per sottodominio consente di utilizzare sempre i parametri preconfigurati giusti per ogni marchio, evitando errori e risparmiando tempo.

**Suggerimento**: Per evitare errori di configurazione, è consigliabile duplicare un modello nativo e modificarne le proprietà anziché creare un nuovo modello.

## Configurare gli indirizzi

* L’indirizzo del mittente è obbligatorio per consentire l’invio di un’e-mail.

* Alcuni ISP (provider di servizi Internet) controllano la validità dell&#39;indirizzo del mittente prima di accettare i messaggi.

* Un indirizzo formato in modo non corretto può causare il rifiuto da parte del server ricevente. È necessario assicurarsi che venga fornito un indirizzo corretto.

* L&#39;indirizzo deve identificare esplicitamente il mittente. Il dominio deve essere di proprietà del mittente e registrato al mittente.

* Adobe consiglia di creare account e-mail corrispondenti agli indirizzi specificati per le consegne e le risposte. Rivolgiti all’amministratore del sistema di messaggistica.

Per configurare gli indirizzi nell’interfaccia di Campaign, segui i passaggi seguenti:

1. In [modello di consegna](creating-a-delivery-template.md), fai clic su **[!UICONTROL From]** link. In **[!UICONTROL Email header parameters]** , compila i campi seguenti:

   ![](assets/d_best_practices_email_header.png)

1. In **[!UICONTROL Sender address]** assicurati che il dominio dell’indirizzo sia lo stesso del sottodominio delegato ad Adobe. È possibile modificare la parte che precede &#39;@&#39; ma non l&#39;indirizzo del dominio.

1. In **[!UICONTROL From]** utilizza un nome facilmente identificabile dai destinatari, ad esempio il nome del brand, per aumentare il tasso di apertura delle consegne. Per migliorare ulteriormente l&#39;esperienza del destinatario, è possibile aggiungere il nome di una persona, ad esempio &quot;Emma da Megastore&quot;.

1. In **[!UICONTROL Reply address text]** campi , l’indirizzo del mittente viene utilizzato per impostazione predefinita per le risposte. Tuttavia, Adobe consiglia di utilizzare un indirizzo reale esistente, ad esempio l’assistenza clienti del tuo marchio. In questo caso, se un destinatario invia una risposta, l’assistenza clienti sarà in grado di gestirla.

### Imposta un gruppo di controllo

Una volta inviata la consegna, puoi confrontare il comportamento dei destinatari esclusi con quello dei destinatari che hanno ricevuto la consegna. Puoi quindi misurare l’efficienza delle campagne. Ulteriori informazioni sui gruppi di controllo [questa sezione](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).

Per impostare un gruppo di controllo, fai clic sul pulsante **[!UICONTROL To]** link. In **[!UICONTROL Select target]** seleziona la finestra **[!UICONTROL Control group]** scheda . È possibile estrarre una parte del target, ad esempio un campione casuale del 5%.

![](assets/d_best_practices_control_group.png)

## Utilizzare le tipologie per applicare filtri o regole di controllo

Una tipologia contiene le regole di controllo applicate durante la fase di analisi, prima di inviare qualsiasi messaggio.

In **[!UICONTROL Typology]** scheda delle proprietà del modello, modifica la tipologia predefinita in base alle tue esigenze.

Ad esempio, per controllare meglio il traffico in uscita, puoi definire quali indirizzi IP possono essere utilizzati definendo un’affinità per sottodominio e creando una tipologia per affinità. Le affinità sono definite nel file di configurazione dell’istanza. Contatta il tuo amministratore Adobe Campaign.

Per ulteriori informazioni sulle tipologie, consulta [questa sezione](../../campaign-opt/using/about-campaign-typologies.md).
