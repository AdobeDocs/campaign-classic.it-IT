---
product: campaign
title: Invio di e-mail su dispositivi mobili giapponesi con Adobe Campaign Classic
description: Scopri come configurare, progettare e inviare e-mail che verranno lette su un cellulare giapponese
exl-id: 44634227-2340-49c4-b330-740c739ea551
source-git-commit: 1e11b7419388698f5de366cbeddf2be88ef12873
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 0%

---

# Inviare e-mail su dispositivi mobili giapponesi {#sending-emails-on-japanese-mobiles}

![](../../assets/common.svg)

## Formati e-mail per dispositivi mobili giapponesi {#email-formats-for-japanese-mobiles}

Adobe Campaign gestisce tre formati specifici giapponesi per le e-mail sui dispositivi mobili: **Deco-mail** (cellulari DoCoMo), **Decorare la posta** (cellulari Softbank) e **Decoration Mail** (KDDI AU mobiles). Questi formati impongono vincoli di codifica, struttura e dimensione particolari. Ulteriori informazioni sulle limitazioni e sui consigli in [questa sezione](#limitations-and-recommendations).

Affinché il destinatario possa ricevere correttamente i messaggi in uno di questi formati, è consigliabile selezionare **[!UICONTROL Deco-mail (DoCoMo)]**, **[!UICONTROL Decore Mail (Softbank)]** o **[!UICONTROL Decoration Mail (KDDI AU)]** nel profilo corrispondente:

![](assets/deco-mail_03.png)

Tuttavia, se si lascia il **[!UICONTROL Email format]** opzione come **[!UICONTROL Unknown]**, **[!UICONTROL HTML]** o **[!UICONTROL Text]**, Adobe Campaign rileverà automaticamente (durante l’invio dell’e-mail) il formato giapponese da utilizzare in modo che il messaggio venga visualizzato correttamente.

Questo sistema di rilevamento automatico si basa sull&#39;elenco dei domini predefiniti definiti nella **[!UICONTROL Management of Email Formats]** set di regole di posta elettronica. Per ulteriori informazioni sulla gestione dei formati e-mail, consulta [questa pagina](../../installation/using/email-deliverability.md#managing-email-formats).

## Limitazioni e raccomandazioni {#limitations-and-recommendations}

Per l’invio di e-mail che verranno lette su un cellulare gestito da un provider giapponese (Softbank, DoCoMo, KDDI AU) si applica un certo numero di vincoli.

Pertanto, devi:

* Utilizza solo immagini in formato JPEG o GIF
* Crea una consegna con sezioni di testo e HTML rigorosamente inferiori a 10.000 byte (per KDDI AU e DoCoMo)
* Utilizza immagini con dimensioni totali (prima della codifica) inferiori a 100 KB
* Non utilizzare più di 20 immagini per messaggio
* Utilizza un formato HTML di dimensioni ridotte (per ogni operatore sono disponibili un numero limitato di tag)

>[!NOTE]
>
>Durante la creazione del messaggio è necessario tenere conto delle limitazioni specifiche di ciascun operatore. Fai riferimento a:
>
>* Per DoCoMo, fai riferimento a [questa pagina](https://www.nttdocomo.co.jp/service/developer/make/content/deco_mail/index.html)
>* Per KDDI AU, fare riferimento a [questa pagina](https://www.au.com/ezfactory/tec/spec/decorations/template.html)
>* Per Softbank, fare riferimento a [questa pagina](https://www.support.softbankmobile.co.jp/partner/home_tech3/index.cfm)


## Test del contenuto dell’e-mail {#testing-the-email-content}

### Anteprima del messaggio {#previewing-the-message}

Adobe Campaign ti consente di verificare che il formato del messaggio sia adattato per essere inviato a un cellulare giapponese.

Una volta definito il contenuto e inserito l’oggetto dell’e-mail, puoi controllare la visualizzazione e la formattazione al momento della creazione del messaggio.

In **[!UICONTROL Preview]** scheda della finestra di modifica del contenuto, facendo clic su **[!UICONTROL More... > Deco-mail diagnostic]** consente di:

* Verifica che i tag di contenuto HTML siano conformi alle restrizioni del formato giapponese
* Verifica che il numero di immagini nel messaggio non superi il limite imposto dal formato (20 immagini)
* Controlla la dimensione totale del messaggio (inferiore a 100 kB)

   ![](assets/deco-mail_06.png)

### Esegui regola di tipologia {#running-typology-rule}

Oltre alla diagnosi di anteprima, viene effettuato un secondo controllo quando si invia una prova o una consegna: una regola specifica di tipologia, **[!UICONTROL Deco-mail check]**, viene avviato durante l’analisi.

>[!IMPORTANT]
>
>Questa regola di tipologia viene eseguita solo se almeno uno dei destinatari è configurato per ricevere e-mail in **[!UICONTROL Deco-mail (DoCoMo)]**, **[!UICONTROL Decore Mail (Softbank)]** o **[!UICONTROL Decoration Mail (KDDI AU)]** formato.

Questa regola di tipologia ti consente di assicurarti che la consegna rispetti la [vincoli di formato](#limitations-and-recommendations) definiti dagli operatori giapponesi, in particolare in relazione alle dimensioni totali dell’e-mail, alle dimensioni delle sezioni di HTML e testo, al numero di immagini nei messaggi e ai tag nel contenuto di HTML.

### Invia bozze {#sending-proofs}

Puoi inviare bozze per verificare la consegna. Quando invii la bozza, se utilizzi indirizzi di sostituzione, inserisci gli indirizzi che corrispondono al formato e-mail del profilo utilizzato.

Ad esempio, puoi sostituire l’indirizzo di un profilo con test@softbank.ne.jp se il formato e-mail per questo profilo è stato definito in precedenza su **[!UICONTROL Decore Mail (Softbank)]**.

![](assets/deco-mail_05.png)

## Inviare messaggi {#sending-messages}

Per inviare un’e-mail ai destinatari con formati e-mail giapponesi con Campaign, sono possibili due opzioni:

* Crea due consegne: uno solo per i destinatari giapponesi e un altro per gli altri destinatari - fai riferimento a [questa sezione](#designing-a-specific-delivery-for-japanese-formats).
* Crea una singola consegna e Adobe Campaign rileverà automaticamente il formato da utilizzare - fai riferimento a [questa sezione](#designing-a-delivery-for-all-formats).

### Progettazione di una consegna specifica per i formati giapponesi {#designing-a-specific-delivery-for-japanese-formats}

Puoi creare un flusso di lavoro contenente due consegne: da leggere su un cellulare giapponese e un altro per i destinatari con un formato e-mail standard.

Per eseguire questa operazione, utilizza la variabile **[!UICONTROL Split]** nel flusso di lavoro e definisci i formati e-mail giapponesi (Deco-mail, Decoration Mail e Decore Mail) come condizioni di filtro.

![](assets/deco-mail_08.png)

![](assets/deco-mail_07.png)

### Progettazione di una consegna per tutti i formati {#designing-a-delivery-for-all-formats}

Quando Adobe Campaign gestisce in modo dinamico i formati in base al dominio (profili con formati e-mail definiti come **[!UICONTROL Unknown]**, **[!UICONTROL HTML]** o **[!UICONTROL Text]** ), puoi inviare la stessa consegna a tutti i destinatari.

Il contatto del messaggio verrà visualizzato correttamente per gli utenti su dispositivi mobili giapponesi, proprio come per i destinatari standard.

>[!IMPORTANT]
>
>Assicurati di rispettare le funzioni speciali associate a ciascun formato e-mail giapponese (Deco-mail, Decoration Mail e Decore Mail). Per ulteriori informazioni sulle limitazioni, consulta [questa sezione](#limitations-and-recommendations).
