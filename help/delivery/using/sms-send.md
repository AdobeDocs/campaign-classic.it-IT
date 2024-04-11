---
product: campaign
title: Inviare, monitorare e tenere traccia degli SMS
description: Scopri come inviare, monitorare e tenere traccia degli SMS in Campaign
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: SMS
role: User
exl-id: 442672ee-5037-49b7-a06f-3a99920ce2b6
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '971'
ht-degree: 3%

---

# Inviare, monitorare e tenere traccia delle consegne SMS{#sms-properties}

## Inviare messaggi SMS {#sending-sms-messages}

Per approvare il messaggio e inviarlo ai destinatari della consegna creata, fai clic su **[!UICONTROL Send]**.

Il processo dettagliato di convalida e invio di una consegna è presentato nelle sezioni seguenti:

* [Convalidare la consegna](steps-validating-the-delivery.md)
* [Inviare la consegna](steps-sending-the-delivery.md)

## Parametri avanzati {#advanced-parameters}

Il **[!UICONTROL Properties]** consente di accedere al parametro di consegna avanzata. I parametri specifici per le consegne SMS si trovano in **[!UICONTROL SMS parameters]** sezione del **[!UICONTROL Delivery]** scheda.

Sono disponibili le seguenti opzioni:

* **Indirizzo mittente**: consente di personalizzare il nome del mittente della consegna utilizzando una stringa di caratteri alfanumerici limitata a undici caratteri. Il campo non deve essere costituito esclusivamente da cifre. È possibile definire una condizione da visualizzare, ad esempio nomi diversi in base all’indicativo di località del destinatario:

  ```
  <% if( String(recipient.mobilePhone).indexOf("+1") == 0){ %>NeoShopUS<%} else {%>NeoShopWorld<%}%>
  ```

  >[!IMPORTANT]
  >
  >Controlla la legge del tuo paese relativa alla modifica dei nomi dei mittenti. Dovresti anche verificare con l’operatore se offre questa funzionalità.

* **Modalità di trasmissione**: trasmissione di messaggi tramite SMS.
* **Priorità**: livello di importanza assegnato a un messaggio. **[!UICONTROL Normal]** priorità è selezionata per impostazione predefinita. Chiedi al tuo provider di servizi informazioni sul costo degli SMS inviati con **[!UICONTROL High]** priorità.
* **Tipo di applicazione**: scegli l’applicazione da assegnare alla consegna SMS. Il **[!UICONTROL Direct Marketing]** è selezionata per impostazione predefinita ed è la più comune.

**Parametri specifici del connettore NetSize**

![](assets/s_user_mobile_sms_adv_netsize.png)

* **Utilizzare più SMS per un singolo messaggio**: questo ti consente di inviare un messaggio lungo più di 160 caratteri tramite diversi messaggi SMS.

**Parametri specifici di un connettore SMPP**

![](assets/s_user_mobile_sms_adv_smpp.png)

* **Numero massimo di SMS per messaggio**: questa opzione ti consente di impostare il numero di SMS da utilizzare per inviare un messaggio. Se il numero è impostato su 0, puoi utilizzare un SMS per recapitare il messaggio. Se ad esempio il numero di SMS è impostato su 1 o 2 e il messaggio supera questa soglia, non verrà inviato.

## Monitorare e tenere traccia degli SMS {#monitoring-and-tracking-sms-deliveries}

Dopo aver inviato i messaggi, puoi monitorare e tenere traccia delle consegne. Per ulteriori informazioni, consulta queste sezioni:

* [Monitorare una consegna](about-delivery-monitoring.md)
* [Errori di consegna](understanding-delivery-failures.md)
* [Informazioni sul tracciamento dei messaggi](about-message-tracking.md)

## Elabora messaggi in entrata {#processing-inbound-messages}

Il **nlserver sms** Il modulo esegue query sul router SMS a intervalli regolari. Questo consente ad Adobe Campaign di tenere traccia dell’avanzamento delle consegne e di gestire le relazioni sullo stato e le richieste di annullamento dell’abbonamento dei destinatari.

* **Relazioni sullo stato**: visualizza i registri di consegna per controllare lo stato dei messaggi.

  >[!NOTE]
  >
  >Ogni SMS inviato è collegato a un account esterno che ne rappresenta la chiave primaria. In questo modo:
  >
  > * Le relazioni sullo stato da un account SMS esterno eliminato non vengono elaborate correttamente.
  > * Un account SMS può essere collegato solo a un singolo account esterno per garantire che le relazioni sullo stato siano attribuite all’account corretto

* **Annullamento iscrizione**: i destinatari che desiderano interrompere la ricezione delle consegne SMS possono restituire un messaggio contenente la parola STOP. Se il tuo provider lo consente in base ai termini del contratto, puoi recuperare i messaggi tramite il **SMS in entrata** attività del flusso di lavoro e quindi creare una query per abilitare **Non contattare più questo destinatario** per i destinatari interessati.

  Consulta la sezione [Flussi di lavoro](../../workflow/using/architecture.md) guida.

## Schema InSMS {#insms-schema}

Lo schema InSMS contiene informazioni relative agli SMS in arrivo. Una descrizione di questi campi è disponibile tramite l&#39;attributo desc.

* **messaggio**: contenuto dell’SMS ricevuto.
* **origine**: numero di cellulare all’origine del messaggio.
* **providerId**: identificatore del messaggio restituito da SMSC (centro messaggi).
* **creato**: data in cui il messaggio in arrivo è stato inserito in Adobe Campaign.
* **extAccount**: account esterno di Adobe Campaign.

  >[!IMPORTANT]
  >
  >I campi seguenti sono specifici di NetSize.
  >
  >Se l&#39;operatore in uso non è NetSize, questi campi vengono considerati vuoti.

* **alias**: alias del messaggio in arrivo.
* **separatore**: separatore tra l’alias e il corpo del messaggio.
* **messageDate**: data del messaggio fornita dall’operatore.
* **receivalDate**: il messaggio della data dall’operatore è stato ricevuto da SMSC (centro messaggi).
* **deliveryDate**: messaggio sulla data inviato da SMSC (centro messaggi).
* **largeAccount**: codice dell’account cliente collegato agli SMS in entrata.
* **countryCode**: codice del paese dell’operatore.
* **operatorCode**: codice di rete dell’operatore.
* **linkedSmsId**: identificatore Adobe Campaign (broadlogId) collegato all’SMS in uscita, dove questo SMS è la risposta.

## Gestisci risposte automatiche (regolamento americano) {#managing-automatic-replies--american-regulation-}

Quando gli abbonati rispondono a un messaggio SMS che è stato loro inviato tramite Adobe Campaign e utilizzano una parola chiave come STOP, HELP o YES, è necessario, nel mercato statunitense, configurare i messaggi che vengono restituiti automaticamente.

Ad esempio, se i destinatari inviano la parola chiave STOP, ricevono automaticamente un messaggio di conferma che informa che l’iscrizione è stata annullata.

Il nome del mittente per questo tipo di messaggio è un codice breve utilizzato in genere per inviare consegne.

>[!IMPORTANT]
>
>La procedura dettagliata seguente è valida solo per i connettori SMPP, ad eccezione del connettore SMPP generico esteso. Per ulteriori informazioni, consulta [Creare un account esterno SMPP](sms-set-up.md#creating-an-smpp-external-account) sezione.
>
>Esso fa parte del processo di certificazione svolto dagli operatori americani per campagne di marketing negli Stati Uniti. Queste risposte ai messaggi SMS dell’abbonato contenenti la parola chiave devono essere rimandate all’abbonato immediatamente dopo aver ricevuto un messaggio da parte loro.

1. Crea questo tipo di file XML:

   ```
   <autoreply>
     <shortcode name="12345">
       <reply keyword="STOP" text="You will not receive SMS anymore" />
       <reply keyword="HELP" text="Powered by Adobe Campaign" />
     </shortcode>
     <shortcode name="43115">
       <reply keyword="STOP" text="Vous ne recevrez plus de SMS" />
       <reply keyword="HELP" text="Service rendu par Adobe Campaign" />
     </shortcode>
     <shortcode name="*">
       <reply keyword="ADOBE" text="This text is replied when you send ADOBE to any short code" />
     </shortcode>
   </autoreply>
   ```

1. Per **nome** attributo del **`<shortcode>`** , specifica il codice breve che verrà visualizzato al posto del nome del mittente del messaggio.

   In ogni **`<reply>`** , immetti il **parola chiave** con una parola chiave e **text** con il messaggio da inviare per questa parola chiave.

   >[!NOTE]
   >
   >Ogni parola chiave deve essere scritta in lettere maiuscole.

   Se desideri inviare lo stesso messaggio per più parole chiave, duplica la riga corrispondente.

   Ad esempio:

   ```
   <reply keyword="STOP" text="You will not receive SMS anymore" />
   <reply keyword="QUIT" text="You will not receive SMS anymore" />
   ```

1. Al termine, salva il file con il nome **smsAutoReply.xml**.

   In Linux, il nome del file distingue tra maiuscole e minuscole.

1. Copia il file in **conf** in Adobe Campaign, nella stessa posizione del server Web.

>[!IMPORTANT]
>
>Questi tipi di messaggi automatici non conservano una cronologia. Pertanto, non vengono visualizzati nel dashboard di consegna. [Ulteriori informazioni](delivery-dashboard.md).
>
>Tali messaggi non sono presi in considerazione nelle norme sulla pressione commerciale. [Ulteriori informazioni](../../campaign-opt/using/pressure-rules.md).
