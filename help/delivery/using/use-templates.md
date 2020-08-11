---
title: Utilizzare i modelli di consegna
seo-title: Utilizzare i modelli di consegna
page-status-flag: never-activated
uuid: a540efc7-105d-4c7f-a2ee-ade4d22b3445
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
discoiquuid: 0cbc4e92-482f-4dac-a1fb-b738e7127938
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 5e6ecd636ee0b2199808c03b2fd898a194f0c1ea
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 0%

---


# Utilizzare i modelli {#use-templates}

I modelli di distribuzione consentono una maggiore efficienza fornendo scenari pronti per la maggior parte dei tipi di attività più comuni. Grazie ai modelli, gli esperti di marketing possono distribuire nuove campagne con una personalizzazione minima in tempi più brevi.

Ulteriori informazioni sui modelli di consegna in [questa sezione](../../delivery/using/creating-a-delivery-template.md).

## Guida introduttiva ai modelli di distribuzione {#gs-templates}

Un modello [di](../../delivery/using/creating-a-delivery-template.md) consegna consente di definire una volta un insieme di proprietà tecniche e funzionali in base alle esigenze e che possono essere riutilizzate per le consegne future. È quindi possibile risparmiare tempo e standardizzare le consegne quando necessario.

Quando gestite diversi marchi in  Adobe Campaign,  Adobe consiglia di avere un sottodominio per marchio. Ad esempio, una banca può avere diversi sottodomini corrispondenti a ciascuna delle sue agenzie regionali. Se una banca possiede il dominio bluebank.com, i relativi sottodomini possono essere @ny.bluebank.com, @ma.bluebank.com, @ca.bluebank.com, ecc. La possibilità di disporre di un modello di consegna per sottodominio consente di utilizzare sempre i parametri preconfigurati corretti per ogni marchio, evitando errori e risparmiando tempo.

**Suggerimento**:  Per evitare errori di configurazione in Campaign Standard, è consigliabile duplicare un modello nativo e modificarne le proprietà anziché creare un nuovo modello.

## Configurare gli indirizzi

* L&#39;indirizzo del mittente è obbligatorio per consentire l&#39;invio di un&#39;e-mail.

* Alcuni ISP (provider di servizi Internet) controllano la validità dell&#39;indirizzo del mittente prima di accettare i messaggi.

* Un indirizzo con formato non corretto potrebbe essere rifiutato dal server ricevente. Devi accertarti che sia specificato l&#39;indirizzo corretto.

* L&#39;indirizzo deve identificare esplicitamente il mittente. Il dominio deve essere di proprietà e registrato del mittente.

*  Adobe consiglia di creare account e-mail corrispondenti agli indirizzi specificati per le consegne e le risposte. Consultate l’amministratore del sistema di messaggistica.

Per configurare gli indirizzi nell&#39;interfaccia di Campaign, effettua le seguenti operazioni:

1. Nel modello [di](../../delivery/using/creating-a-delivery-template.md)consegna, fate clic sul **[!UICONTROL From]** collegamento. Nella **[!UICONTROL Email header parameters]** finestra, compila i campi seguenti:

   ![](assets/d_best_practices_email_header.png)

1. Nel **[!UICONTROL Sender address]** campo, accertatevi che il dominio indirizzo sia lo stesso del sottodominio delegato al Adobe . È possibile modificare la parte che precede &#39;@&#39; ma non l&#39;indirizzo del dominio.

1. Nel **[!UICONTROL From]** campo, utilizzare un nome facilmente identificabile dai destinatari, come il nome del marchio, per aumentare il tasso di apertura delle consegne. Per migliorare ulteriormente l&#39;esperienza del destinatario, è possibile aggiungere il nome di una persona, ad esempio &quot;Emma da Megastore&quot;.

1. Nei **[!UICONTROL Reply address text]** campi, l&#39;indirizzo del mittente viene utilizzato per impostazione predefinita per le risposte. Tuttavia,  Adobe consiglia di utilizzare un indirizzo reale esistente, come l&#39;assistenza clienti del marchio. In questo caso, se un destinatario invia una risposta, l&#39;assistenza clienti sarà in grado di gestirla.

### Impostazione di un gruppo di controllo

Una volta inviata la consegna, potete confrontare il comportamento dei destinatari esclusi con quello dei destinatari che hanno ricevuto la consegna. Potete quindi misurare l&#39;efficienza delle campagne. Ulteriori informazioni sui gruppi di controllo [in questa sezione](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).

Per impostare un gruppo di controllo, fare clic sul **[!UICONTROL To]** collegamento. Nella **[!UICONTROL Select target]** finestra, selezionare la **[!UICONTROL Control group]** scheda. Potete estrarre una parte della destinazione, ad esempio un campione casuale del 5%.

![](assets/d_best_practices_control_group.png)

## Utilizzare le tipologie per applicare filtri o regole di controllo

Una tipologia contiene le regole di controllo applicate durante la fase di analisi, prima di inviare qualsiasi messaggio.

Nella **[!UICONTROL Typology]** scheda delle proprietà del modello, modificare la tipologia predefinita in base alle esigenze.

Ad esempio, per controllare meglio il traffico in uscita, potete definire gli indirizzi IP da utilizzare definendo un&#39;affinità per sottodominio e creando una tipologia per affinità. Le affinità sono definite nel file di configurazione dell&#39;istanza. Contattate l’amministratore  Adobe Campaign.

For more on typologies, refer to [this section](../../campaign/using/about-campaign-typologies.md).
