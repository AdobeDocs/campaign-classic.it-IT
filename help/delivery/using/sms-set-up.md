---
product: campaign
title: Configurare il canale SMS Campaign
description: Scopri come configurare il canale SMS in Campaign
audience: delivery
content-type: reference
topic-tags: sending-messages-on-mobiles
exl-id: a2783a5e-6d38-41a1-b5c6-24ab489116f8
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1677'
ht-degree: 35%

---

# Configurare il canale SMS {#setting-up-sms-channel}

![](../../assets/common.svg)

Per inviare a un telefono cellulare, è necessario:

1. Un account esterno che specifica un connettore e il tipo di messaggio.

   I connettori legacy sono ora obsoleti. Le funzionalità obsolete sono ancora disponibili, ma non saranno ulteriormente migliorate né supportate. Per ulteriori informazioni, consulta [questa pagina](../../rn/using/deprecated-features.md).

1. Un modello di consegna in cui viene fatto riferimento a questo account esterno.

## Creare un account esterno SMPP {#creating-an-smpp-external-account}

Per inviare un SMS a un cellulare, devi innanzitutto creare il tuo account esterno SMPP.
Per ulteriori informazioni sul protocollo e le impostazioni SMS, consulta questa [pagina](sms-protocol.md).

Per farlo, segui la procedura indicata di seguito:

1. Nel nodo **[!UICONTROL Platform]** > **[!UICONTROL External accounts]** della struttura, fai clic sull&#39;icona **[!UICONTROL New]**.
1. Definisci il tipo di account come **Routing**, il canale come **Mobile (SMS)** e la modalità di consegna come **Consegna in blocco**.

   ![](assets/extended_smpp_create_account.png)

1. Seleziona la casella **[!UICONTROL Enabled]** .
1. Nella scheda **[!UICONTROL Mobile]** , seleziona **[!UICONTROL Extended generic SMPP]** dall’elenco a discesa **[!UICONTROL Connector]** .

   ![](assets/extended_smpp_connector.png)

   >[!CAUTION]
   >
   > A partire dalla versione 20.2, i connettori legacy sono obsoleti e non supportati. È consigliabile utilizzare il connettore **[!UICONTROL Extended generic SMPP]**. Per ulteriori informazioni sulla migrazione al connettore consigliato, consulta questa [pagina](unsupported-connector-migration.md).

1. L’opzione **[!UICONTROL Enable verbose SMPP traces in the log file]** ti consente di scaricare tutto il traffico SMPP nei file di registro. Devi abilitare questa opzione per risolvere i problemi del connettore e per confrontare il traffico rilevato dal provider.

1. Contatta il provider di servizi SMS per spiegarti come completare i diversi campi dell’account esterno dalla scheda **[!UICONTROL Connection settings]** .

   Quindi, contatta il tuo provider, a seconda di quello scelto, che ti darà il valore da inserire nel campo **[!UICONTROL SMSC implementation name]** .

   Puoi definire il numero di connessioni al provider per figlio MTA. Per impostazione predefinita, è impostato su 1.

1. Per impostazione predefinita, il numero di caratteri in un SMS soddisfa gli standard GSM.

   I messaggi SMS che utilizzano la codifica GSM sono limitati a 160 caratteri o 153 caratteri per SMS per messaggi inviati in più parti.

   >[!NOTE]
   >
   >Alcuni caratteri contano come due (parentesi graffe e quadre, il simbolo dell’euro, ecc.).
   >
   >L’elenco dei caratteri GSM disponibili è presentato di seguito.

   Se lo desideri, puoi autorizzare la traslitterazione di caratteri selezionando la casella corrispondente.

   ![](assets/extended_smpp_transliteration.png)

   Per ulteriori informazioni al riguardo, consulta [questa sezione](#about-character-transliteration).

1. Nella scheda **[!UICONTROL Throughput and delays]** puoi specificare il throughput massimo dei messaggi in uscita (&quot;MT&quot;, Mobile Terminated) in MT al secondo. Se inserisci &quot;0&quot; nel campo corrispondente, il throughput effettivo sarà illimitato.

   È necessario completare in secondi i valori di tutti i campi corrispondenti alle durate.

1. Nella scheda **[!UICONTROL Mapping of encodings]** puoi definire le codifiche.

   Per ulteriori informazioni al riguardo, consulta [questa sezione](#about-text-encodings).

1. Nella scheda **[!UICONTROL SMSC specificities]** , l’opzione **[!UICONTROL Send full phone number]** è disabilitata per impostazione predefinita. Non attivarla se desideri rispettare il protocollo SMPP e trasferire solo le cifre al server del provider SMS (SMSC).

   Tuttavia, dato che alcuni provider richiedono l’uso del prefisso &quot;+&quot;, ti consigliamo di verificare con il provider se è necessario abilitare questa opzione.

   La casella di controllo **[!UICONTROL Enable TLS over SMPP]** ti consente di crittografare il traffico SMPP. Per ulteriori informazioni, consulta questa [pagina](sms-protocol.md).

1. Se stai configurando un connettore **[!UICONTROL Extended generic SMPP]**, puoi impostare le risposte automatiche.

   Per ulteriori informazioni al riguardo, consulta [questa sezione](#automatic-reply).

## Traduzione di caratteri SMS {#about-character-transliteration}

La traslitterazione dei caratteri può essere impostata in un account esterno SMPP mobile delivery, nella scheda **[!UICONTROL Mobile]** .

La traslitterazione consiste nel sostituire un carattere di un SMS con un altro quando quel carattere non è preso in considerazione dallo standard GSM.

* Se la traslitterazione è **[!UICONTROL authorized]**, ogni carattere non preso in considerazione viene sostituito da un carattere GSM al momento dell’invio del messaggio. Ad esempio, la lettera &quot;ë&quot; è sostituita da &quot;e&quot;. Il messaggio viene quindi leggermente modificato, ma il limite di caratteri rimane lo stesso.
* Quando la traslitterazione è **[!UICONTROL not authorized]**, ogni messaggio che contiene caratteri non presi in considerazione viene inviato in formato binario (Unicode): tutti i caratteri vengono quindi inviati così come sono. Tuttavia, i messaggi SMS che utilizzano Unicode sono limitati a 70 caratteri (o 67 caratteri per SMS per messaggi inviati in più parti). Se viene superato il numero massimo di caratteri, vengono inviati diversi messaggi, il che potrebbe comportare costi aggiuntivi.

>[!IMPORTANT]
>
>L’inserimento di campi di personalizzazione nel contenuto del messaggio SMS può introdurre caratteri che non vengono presi in considerazione dalla codifica GSM.

Per impostazione predefinita, la traslitterazione di caratteri è disabilitata. Se desideri che tutti i caratteri nei messaggi SMS rimangano invariati, per non modificare ad esempio i nomi propri, ti consigliamo di non abilitare questa opzione.

Tuttavia, se i messaggi SMS contengono molti caratteri che generano messaggi Unicode, puoi abilitare questa opzione per limitare i costi di invio dei messaggi.

La tabella seguente presenta i caratteri presi in considerazione dallo standard GSM. Tutti i caratteri inseriti nel corpo del messaggio, diversi da quelli indicati di seguito, convertono l’intero messaggio in formato binario (Unicode) e quindi lo limitano a 70 caratteri.

**Caratteri base**

<table> 
 <tbody> 
  <tr> 
   <td> @ </td> 
   <td> <img height="21px" src="assets/delta.png" /> </td> 
   <td> SP </td> 
   <td> 0 </td> 
   <td> .4 </td> 
   <td> P </td> 
   <td> È </td> 
   <td> p </td> 
  </tr> 
  <tr> 
   <td> £ </td> 
   <td> _ </td> 
   <td> ! </td> 
   <td> 1 </td> 
   <td> A </td> 
   <td> Q </td> 
   <td> a </td> 
   <td> q </td> 
  </tr> 
  <tr> 
   <td> $ </td> 
   <td> <img height="21px" src="assets/phi.png" /> </td> 
   <td> " </td> 
   <td> 2 </td> 
   <td> B </td> 
   <td> R </td> 
   <td> b </td> 
   <td> r </td> 
  </tr> 
  <tr> 
   <td> ¥ </td> 
   <td> <img height="21px" src="assets/gamma.png" /> </td> 
   <td> # </td> 
   <td> 1 </td> 
   <td> C </td> 
   <td> S </td> 
   <td> c </td> 
   <td> s </td> 
  </tr> 
  <tr> 
   <td> è </td> 
   <td> <img height="21px" src="assets/delta.png" /> </td> 
   <td> m </td> 
   <td> 4 </td> 
   <td> D </td> 
   <td> T </td> 
   <td> d </td> 
   <td> t </td> 
  </tr> 
  <tr> 
   <td> é </td> 
   <td> <img height="21px" src="assets/omega.png" /> </td> 
   <td> % </td> 
   <td> 5 </td> 
   <td> E </td> 
   <td> U </td> 
   <td> e </td> 
   <td> u </td> 
  </tr> 
  <tr> 
   <td> ù </td> 
   <td> <img height="21px" src="assets/pi.png" /> </td> 
   <td> &amp; </td> 
   <td> 6 </td> 
   <td> F </td> 
   <td> V </td> 
   <td> f </td> 
   <td> v </td> 
  </tr> 
  <tr> 
   <td> ì </td> 
   <td> <img height="21px" src="assets/psi.png" /> </td> 
   <td> ' </td> 
   <td> 7 </td> 
   <td> G </td> 
   <td> W </td> 
   <td> g </td> 
   <td> w </td> 
  </tr> 
  <tr> 
   <td> ò </td> 
   <td> <img height="21px" src="assets/sigma.png" /> </td> 
   <td> ( </td> 
   <td> 8 </td> 
   <td> H </td> 
   <td> X </td> 
   <td> h </td> 
   <td> x </td> 
  </tr> 
  <tr> 
   <td> Ç </td> 
   <td> <img height="21px" src="assets/theta.png" /> </td> 
   <td> ) </td> 
   <td> 9 </td> 
   <td> I </td> 
   <td> Y </td> 
   <td> i </td> 
   <td> y </td> 
  </tr> 
  <tr> 
   <td> LF </td> 
   <td> <img height="21px" src="assets/xi.png" /> </td> 
   <td> * </td> 
   <td> : </td> 
   <td> J </td> 
   <td> Z </td> 
   <td> j </td> 
   <td> z </td> 
  </tr> 
  <tr> 
   <td> Ø </td> 
   <td> ESC </td> 
   <td> + </td> 
   <td> ; </td> 
   <td> K </td> 
   <td> Ä </td> 
   <td> k </td> 
   <td> ä </td> 
  </tr> 
  <tr> 
   <td> ø </td> 
   <td> Æ </td> 
   <td> , </td> 
   <td> &lt;&gt; </td> 
   <td> L </td> 
   <td> Ö </td> 
   <td> l </td> 
   <td> ö </td> 
  </tr> 
  <tr> 
   <td> CR </td> 
   <td> æ </td> 
   <td> - </td> 
   <td> = </td> 
   <td> M </td> 
   <td> Ñ </td> 
   <td> m </td> 
   <td> ñ </td> 
  </tr> 
  <tr> 
   <td> Å </td> 
   <td> ß </td> 
   <td> . </td> 
   <td> &gt; </td> 
   <td> N </td> 
   <td> Ü </td> 
   <td> n </td> 
   <td> ü </td> 
  </tr> 
  <tr> 
   <td> å </td> 
   <td> É </td> 
   <td> / </td> 
   <td> ? </td> 
   <td> O </td> 
   <td> § </td> 
   <td> o </td> 
   <td> à </td> 
  </tr> 
 </tbody> 
</table>

SP: Space

ESC: Escape

LF: Line Feed (avanzamento di riga)

CR: Carriage Return (ritorno a capo)

**Caratteri avanzati (contati due volte)**

^ { } `[ ~ ]` | €

## Codifiche di testo {#about-text-encodings}

Al momento di inviare un messaggio SMS, Adobe Campaign può utilizzare una o più codifiche di testo. Ogni codifica ha un set di caratteri specifico e determina il numero di caratteri da includere in un messaggio SMS.

Durante la configurazione di un nuovo account esterno per la consegna mobile SMPP, puoi definire il percorso **[!UICONTROL Mapping of encodings]** nella scheda **[!UICONTROL Mobile]** : il campo **[!UICONTROL data_coding]** consente ad Adobe Campaign di comunicare quale codifica viene utilizzata per SMSC.

>[!NOTE]
>
>La mappatura tra il valore **data_coding** e la codifica effettivamente utilizzata è standardizzata. Tuttavia, alcuni SMSC hanno una propria mappatura specifica: in questo caso, l&#39;amministratore di **Adobe Campaign** deve dichiarare questa mappatura. Consulta il provider per saperne di più.

Puoi dichiarare **data_codings** e forzare la codifica, se necessario: a questo scopo, specifica una singola codifica nella tabella.

* Quando non viene definita alcuna mappatura delle codifiche, il connettore assume un comportamento generico:

   * Prova a utilizzare la codifica GSM a cui assegna il valore **data_coding = 0**.
   * Se non è possibile usare la codifica GSM, utilizza la codifica **UCS2** assegnandole il valore **data_coding = 8**.

* Quando definisci le codifiche desiderate e i valori dei campi **[!UICONTROL data_coding]** collegati, Adobe Campaign tenterà di utilizzare la prima codifica nell’elenco, quindi la seguente, se la prima codifica risulta impossibile.

>[!IMPORTANT]
>
>L’ordine di dichiarazione è importante: ti consigliamo di inserire l’elenco in ordine crescente **di costo** per favorire le codifiche che ti consentono di contenere il maggior numero possibile di caratteri in ogni messaggio SMS.
>
>Dichiara solo le codifiche che desideri utilizzare. Se alcune delle codifiche fornite dal SMSC non devono corrispondere al tuo scopo d&#39;uso, non dichiararle nell&#39;elenco.

## Risposta automatica {#automatic-reply}

Quando si imposta un connettore SMPP generico esteso, è possibile configurare le risposte automatiche.

Quando un utente con sottoscrizione risponde a un messaggio SMS inviato tramite Adobe Campaign e il relativo messaggio contiene una parola chiave come &quot;STOP&quot;, puoi configurare i messaggi che vengono automaticamente ritrasmessi nella sezione **[!UICONTROL Automatic reply sent to the MO]** .

>[!NOTE]
>
>Le parole chiave non sono sensibili all’uso di maiuscole e minuscole.

Per ogni parola chiave, specifica un codice breve, che è un numero generalmente utilizzato per inviare consegne e fungerà da nome mittente, quindi inserisci il messaggio che verrà inviato al sottoscrittore.

Puoi anche collegare un’azione alla risposta automatica: **[!UICONTROL Send to quarantine]** o **[!UICONTROL Remove from quarantine]**. Ad esempio, se un destinatario invia la parola chiave &quot;STOP&quot;, riceverà automaticamente una conferma dell’annullamento dell’abbonamento e verrà messo in quarantena.

![](assets/extended_smpp_reply.png)

Se colleghi l’azione **[!UICONTROL Remove from quarantine]** a una risposta automatica, i destinatari che inviano la parola chiave corrispondente vengono automaticamente rimossi dalla quarantena.

I destinatari sono elencati nella tabella **[!UICONTROL Non deliverables and addresses]** disponibile dal menu **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** .

* Per inviare la stessa risposta indipendentemente dal codice breve, lasciare vuota la colonna **[!UICONTROL Short code]**.
* Per inviare la stessa risposta indipendentemente dalla parola chiave, lasciare vuota la colonna **[!UICONTROL Keyword]**.
* Per eseguire un’azione senza inviare una risposta, lascia vuota la colonna **[!UICONTROL Response]** . Ad esempio, questo consente di rimuovere dalla quarantena un utente che risponde con un messaggio diverso da &quot;STOP&quot;.

Se si dispone di più account esterni utilizzando il connettore SMPP generico esteso con lo stesso account provider, potrebbe verificarsi il seguente problema: quando invii una risposta a un codice breve, potrebbe essere ricevuta su una qualsiasi delle tue connessioni account esterne. Di conseguenza, la risposta automatica inviata non poteva essere il messaggio previsto.
Per evitare questo problema, applica una delle soluzioni seguenti, a seconda del provider in uso:

* Crea un account provider per ogni account esterno.
* Utilizza il campo **[!UICONTROL System type]** della scheda **[!UICONTROL Mobile]** > **[!UICONTROL Connection settings]** per distinguere ogni codice breve. Chiedi al tuo provider un valore diverso per ogni account.

   ![](assets/extended_smpp_system-type.png)

I passaggi per la configurazione di un account esterno utilizzando il connettore SMPP generico esteso sono descritti in dettaglio nella sezione [Creare un account esterno SMPP](#creating-an-smpp-external-account) .

## Modificare il modello di consegna {#changing-the-delivery-template}

Adobe Campaign fornisce un modello per la consegna a dispositivi mobili. Questo modello è disponibile nel nodo **[!UICONTROL Resources > Templates > Delivery templates]** . Per ulteriori informazioni, consulta la sezione [Informazioni sui modelli](about-templates.md) .

Per inviare tramite canale SMS, devi creare un modello in cui viene fatto riferimento al connettore del canale.

Per mantenere il modello di consegna nativo, ti consigliamo di duplicarlo e configurarlo.

Nell’esempio seguente, creiamo un modello per inviare messaggi tramite l’account SMPP abilitato in precedenza. Per eseguire questa operazione:

1. Passa al nodo **[!UICONTROL Delivery templates]** .
1. Fai clic con il pulsante destro del mouse sul modello **[!UICONTROL Send to mobiles]** e seleziona **[!UICONTROL Duplicate]**.

   ![](assets/s_user_mobile_template_change_01.png)

1. Modifica l’etichetta del modello, ad esempio **Inviato a dispositivi mobili (SMPP)**.

   ![](assets/s_user_mobile_template_change_02.png)

1. Fai clic su **[!UICONTROL Properties]**.
1. Nella scheda **[!UICONTROL General]** , seleziona una modalità di indirizzamento corrispondente all’account esterno creato nei passaggi precedenti.

   ![](assets/s_user_mobile_template_change_03.png)

1. Fai clic su **[!UICONTROL Save]** per creare il modello.

   ![](assets/s_user_mobile_template_list.png)

Ora disponi di un account esterno e di un modello di consegna che ti consente di inviare tramite SMS.
