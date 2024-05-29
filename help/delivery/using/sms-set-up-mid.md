---
product: campaign
title: Configurare il canale SMS Campaign su un’infrastruttura mid-sourcing
description: Scopri come configurare il canale SMS in Campaign su un’infrastruttura di mid-sourcing
feature: SMS
role: User, Developer, Admin
exl-id: 6987cb5e-8821-4619-b0e4-f0fad3355bfb
source-git-commit: b7339512d85a7bd0c5aae24af46739daafb1ba51
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 8%

---

# Configurare il canale SMS su un’infrastruttura mid-sourcing {#setting-up-sms-channel}

Per inviare a un telefono cellulare con server medi, è necessario:

1. Un operatore SMS creato sul server Mid utilizzato per l’account esterno SMS creato sul server Marketing.

1. Un account esterno sul server Marketing, che specifica il canale e la modalità di consegna.

1. Un account esterno sul Mid-server, che descrive il connettore e il tipo di messaggio.

1. Un modello di consegna che fa riferimento all’account esterno per semplificare il processo di invio.

>[!NOTE]
>
> Per le consegne di SMS, la tipologia deve utilizzare un’affinità SMS specifica creata in **uno** contenitore server applicazioni dedicato. [Ulteriori informazioni](../../installation/using/configure-delivery-settings.md#managing-outbound-smtp-traffic-with-affinities)

## Creare l’operatore SMS sul mid-server {#create-sms-operator}

Per avviare il processo di configurazione, devi creare un operatore SMS sul server mid-size specifico per l’account esterno.

>[!IMPORTANT]
>
>Ogni connettore SMS richiede un operatore SMS univoco.

1. In **[!UICONTROL Administration]** > **[!UICONTROL Access management]** > **[!UICONTROL Operators node]** dell&#39;albero, fare clic sul pulsante **[!UICONTROL New]** icona.

   ![](assets/sms_operator_mid_3.png)

1. Specifica dell’utente **[!UICONTROL Identification parameters]**, inclusi login, password e nome. L’accesso e la password sono necessari affinché l’operatore possa accedere ad Adobe Campaign in modo sicuro.

   Tieni presente che **[!UICONTROL Name (login)]** deve essere utilizzato in seguito per denominare l’account esterno SMPP nel mid-server.

   ![](assets/sms_operator_mid_1.png)

1. Seleziona le autorizzazioni concesse all’operatore nella sezione Diritti di accesso dell’operatore.

   Per allocare i diritti all’operatore, fai clic su **[!UICONTROL Add]** si trova sopra l’elenco dei diritti. Quindi, seleziona una **[!UICONTROL Operator group]** o **[!UICONTROL Named rights]** dall&#39;elenco gruppi disponibili.

   ![](assets/sms_operator_mid_2.png)

1. Clic **[!UICONTROL Save]** per finalizzare la creazione dell’operatore. Il profilo è ora incluso nell’elenco degli operatori esistenti.

## Creare un account esterno SMS sul server di marketing {#create-accound-mkt}

Per inviare un SMS a un telefono cellulare con server intermedi, devi innanzitutto creare l’account esterno SMS sul server di marketing.

1. In **[!UICONTROL Platform]** > **[!UICONTROL External accounts]** dell&#39;albero, fare clic sul pulsante **[!UICONTROL New]** icona.

   ![](assets/mid_external_account_2.png)

1. Digita il tuo **[!UICONTROL Label]** e **[!UICONTROL Internal name]**. In seguito verrà utilizzato il nome Internal per denominare l’account esterno SMPP nel mid-server.

1. Definisci il tipo di conto come **[!UICONTROL Routing]**, il canale come **[!UICONTROL Mobile (SMS)]** e la modalità di consegna come **[!UICONTROL Mid-sourcing]**.

   ![](assets/mid_external_account_1.png)

1. In **[!UICONTROL Mid-Sourcing]** , specifica i parametri di connessione al server di mid-sourcing.

   Inserisci i dettagli di [connettore SMS creato in precedenza](#create-sms-operator) nel **[!UICONTROL Account]** e **[!UICONTROL Password]** campi.

   ![](assets/mid_external_account_7.png)

1. Conferma la configurazione facendo clic su **[!UICONTROL Test the connection]**.

1. Fai clic su **[!UICONTROL Save]**.

## Creare un account esterno SMPP sul mid-server {#creating-smpp-mid}

>[!IMPORTANT]
>
>L’utilizzo dello stesso account e della stessa password per più account SMS esterni può causare conflitti e sovrapposizioni tra gli account. Consulta la sezione [Pagina Risoluzione dei problemi di SMS](troubleshooting-sms.md#external-account-conflict).

Dopo aver configurato correttamente l’account esterno SMS sul server Marketing, il passaggio successivo consiste nel stabilire l’account esterno SMPP sul server mid-server.

Per ulteriori informazioni sul protocollo e sulle impostazioni di SMS, consulta questa [pagina](sms-protocol.md).

A questo scopo, segui la procedura indicata di seguito:

1. In **[!UICONTROL Platform]** > **[!UICONTROL External accounts]** dell&#39;albero, fare clic sul pulsante **[!UICONTROL New]** icona.

1. Digita il tuo **[!UICONTROL Label]** e **[!UICONTROL Internal name]**.

   >[!WARNING]
   >
   >Quando si assegna un **[!UICONTROL Internal name]**, assicurati di seguire la convenzione di denominazione specificata:
   > </br>`SMS Operator Name_Internal Name of the Marketing SMS external account`

   ![](assets/mid_external_account_6.png)

1. Definisci il tipo di conto come **Indirizzamento**, il canale come **Dispositivi mobili (SMS)** e la modalità di consegna come **Consegna in blocco**.

   ![](assets/mid_external_account_3.png)

1. Controlla la **[!UICONTROL Enabled]** casella.

1. In **[!UICONTROL Mobile]** , seleziona **[!UICONTROL Extended generic SMPP]** dal **[!UICONTROL Connector]** elenco a discesa.

   ![](assets/mid_external_account_4.png)

1. Il **[!UICONTROL Enable verbose SMPP traces in the log file]** consente di scaricare tutto il traffico SMPP nei file di registro. Questa opzione deve essere abilitata solo per la risoluzione dei problemi del connettore e per il confronto con il traffico visualizzato dal provider.

1. Contatta il provider di servizi SMS che ti spiegherà come completare i diversi campi dell’account esterno dal **[!UICONTROL Connection settings]** scheda.

   Quindi, contatta il provider, a seconda di quello scelto, che ti fornirà il valore da immettere nel **[!UICONTROL SMSC implementation name]** campo.

   Puoi definire il numero di connessioni al provider per elemento secondario MTA. Per impostazione predefinita è impostato su 1.

1. Per impostazione predefinita, il numero di caratteri in un SMS soddisfa gli standard GSM.

   I messaggi SMS che utilizzano la codifica GSM sono limitati a 160 caratteri o 153 caratteri per SMS per messaggi inviati in più parti.

   >[!NOTE]
   >
   >Alcuni caratteri contano come due (parentesi graffe, parentesi quadre, il simbolo dell’euro, ecc.).
   >
   >L’elenco dei caratteri GSM disponibili è presentato in [questa sezione](sms-set-up.md#about-character-transliteration).

   Puoi anche autorizzare la traslitterazione di caratteri selezionando la casella corrispondente.

   ![](assets/mid_external_account_5.png)

1. In **[!UICONTROL Throughput and delays]** , puoi specificare la velocità effettiva massima dei messaggi in uscita (&quot;MT&quot;, Mobile Terminated) in MT al secondo. Se inserisci &quot;0&quot; nel campo corrispondente, il throughput effettivo sarà illimitato.

   È necessario completare in secondi i valori di tutti i campi corrispondenti alle durate.

1. In **[!UICONTROL Mapping of encodings]** , è possibile definire le codifiche.

   Per ulteriori informazioni al riguardo, consulta [questa sezione](sms-set-up.md#about-text-encodings).

1. In **[!UICONTROL SMSC specificities]** , la scheda **[!UICONTROL Send full phone number]** è disattivata per impostazione predefinita. Non attivarlo se desideri rispettare il protocollo SMPP e trasferire solo le cifre al server del provider SMS (SMSC).

   Tuttavia, dato che alcuni provider richiedono l’uso del prefisso &quot;+&quot;, ti consigliamo di verificare con il provider se è necessario abilitare questa opzione.

   Il **[!UICONTROL Enable TLS over SMPP]** La casella di controllo ti consente di crittografare il traffico SMPP. Per ulteriori informazioni, consulta questa [pagina](sms-protocol.md).

1. Se stai configurando un’ **[!UICONTROL Extended generic SMPP]** connettore, è possibile impostare risposte automatiche.

   Per ulteriori informazioni al riguardo, consulta [questa sezione](sms-set-up.md#automatic-reply).

## Modificare il modello di consegna {#changing-the-delivery-template}

Adobe Campaign offre un modello di consegna mobile che si trova in **[!UICONTROL Resources > Templates > Delivery templates]** nodo. Per ulteriori informazioni, consulta [Informazioni sui modelli](about-templates.md) sezione.

Per inviare messaggi tramite il canale SMS, devi creare un modello che includa un riferimento al connettore del canale.

Per mantenere il modello di consegna nativo, ti consigliamo di duplicarlo e quindi configurarlo.

Nell’esempio seguente viene generato un modello per facilitare la consegna dei messaggi tramite l’account SMPP creato in precedenza. Per eseguire questa operazione:

1. In **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Delivery templates]** della struttura, fare clic con il pulsante destro del mouse sulla **[!UICONTROL Send to mobiles]** e selezionare **[!UICONTROL Duplicate]**.

   ![](assets/delivery_template_mid_1.png)

1. Cambia l’etichetta del modello, ad esempio **Inviato a dispositivi mobili (SMPP)**.

   ![](assets/delivery_template_mid_2.png)

1. Fai clic su **[!UICONTROL Properties]**.

1. In **[!UICONTROL General]** , selezionare una modalità di instradamento che corrisponda all&#39;account esterno creato nella sezione [Creare un account esterno SMS sul server di marketing](#create-accound-mkt).

   ![](assets/delivery_template_mid_3.png)

1. Clic **[!UICONTROL Save]** per creare il modello.

   ![](assets/delivery_template_mid_4.png)

Ora disponi di un account esterno e di un modello di consegna che ti consente di effettuare la consegna tramite SMS.

## Argomenti correlati {#related-topics}

* [Traslitterazione di caratteri SMS](sms-set-up.md#about-character-transliteration)
* [Codifiche testo](sms-set-up.md#about-text-encodings)
* [Risposta automatica](sms-set-up.md#automatic-reply)
