---
product: campaign
title: Inviare e-mail su cellulari giapponesi con Adobe Campaign Classic
description: Scopri come configurare, progettare e inviare e-mail che verranno lette su un dispositivo mobile giapponese
badge-v7: label="v7" type="Informative" tooltip="Applicabile a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Email, Email Design
role: User
exl-id: 44634227-2340-49c4-b330-740c739ea551
source-git-commit: d2f5f2a662c022e258fb3cc56c8502c4f4cb2849
workflow-type: tm+mt
source-wordcount: '736'
ht-degree: 0%

---

# Inviare e-mail su cellulari giapponesi {#sending-emails-on-japanese-mobiles}

## Formati e-mail per dispositivi mobili giapponesi {#email-formats-for-japanese-mobiles}

Adobe Campaign gestisce tre formati giapponesi specifici per l’e-mail su dispositivi mobili: **Deco-mail** (DoCoMo mobiles), **Decore Mail** (Softbank mobiles) e **Decoration Mail** (KDDI AU dispositivi mobili). Questi formati impongono particolari vincoli di codifica, struttura e dimensione. Ulteriori informazioni su limitazioni e raccomandazioni in [questa sezione](#limitations-and-recommendations).

Per consentire al destinatario di ricevere correttamente i messaggi in uno di questi formati, si consiglia di selezionare **[!UICONTROL Deco-mail (DoCoMo)]**, **[!UICONTROL Decore Mail (Softbank)]** o **[!UICONTROL Decoration Mail (KDDI AU)]** nel profilo corrispondente:

![](assets/deco-mail_03.png)

Tuttavia, se si lascia il **[!UICONTROL Email format]** opzione come **[!UICONTROL Unknown]**, **[!UICONTROL HTML]** o **[!UICONTROL Text]**, Adobe Campaign rileverà automaticamente (durante l’invio dell’e-mail) il formato giapponese da utilizzare per visualizzare correttamente il messaggio.

Questo sistema di rilevamento automatico si basa sull&#39;elenco di domini predefiniti **[!UICONTROL Management of Email Formats]** set di regole di posta elettronica. Per ulteriori informazioni sulla gestione dei formati e-mail, consulta [questa pagina](../../installation/using/email-deliverability.md#managing-email-formats).

## Limitazioni e raccomandazioni {#limitations-and-recommendations}

Per l’invio di e-mail che verranno lette su un dispositivo mobile gestito da un provider giapponese (Softbank, DoCoMo, KDDI AU) si applicano alcuni vincoli.

Pertanto, devi:

* Usa solo immagini in formato JPEG o GIF
* Creare una consegna con sezioni di testo e HTML che siano strettamente inferiori a 10.000 byte (per KDDI AU e DoCoMo)
* Utilizza immagini con una dimensione totale (prima della codifica) inferiore a 100 KB
* Non utilizzare più di 20 immagini per messaggio
* Utilizza un formato HTML di dimensioni ridotte (per ogni operatore è disponibile un numero limitato di tag)

>[!NOTE]
>
>Le limitazioni specifiche di ciascun operatore devono essere tenute in considerazione durante la creazione del messaggio. Consulta la relativa documentazione del prodotto.


## Verificare il contenuto dell’e-mail {#testing-the-email-content}

### Anteprima del messaggio {#previewing-the-message}

Adobe Campaign consente di verificare che il formato del messaggio sia adattato per essere inviato a un cellulare giapponese.

Dopo aver definito il contenuto e inserito l’oggetto dell’e-mail, puoi controllare la visualizzazione e la formattazione al momento della creazione del messaggio.

In **[!UICONTROL Preview]** della finestra di modifica del contenuto, facendo clic su **[!UICONTROL More... > Deco-mail diagnostic]** consente di:

* Verifica che i tag di contenuto HTML siano conformi alle restrizioni del formato giapponese
* Verifica che il numero di immagini nel messaggio non superi il limite imposto dal formato (20 immagini)
* Verifica la dimensione totale del messaggio (inferiore a 100 KB)

  ![](assets/deco-mail_06.png)

### Eseguire la regola di tipologia {#running-typology-rule}

Oltre alla diagnosi di anteprima, viene eseguito un secondo controllo quando si invia una bozza o una consegna: una regola di tipologia specifica, **[!UICONTROL Deco-mail check]**, viene avviato durante l&#39;analisi.

>[!IMPORTANT]
>
>Questa regola di tipologia viene eseguita solo se almeno uno dei destinatari è configurato per ricevere e-mail in **[!UICONTROL Deco-mail (DoCoMo)]**, **[!UICONTROL Decore Mail (Softbank)]** o **[!UICONTROL Decoration Mail (KDDI AU)]** formato.

Questa regola di tipologia ti consente di verificare che la consegna rispetti le [vincoli di formato](#limitations-and-recommendations) definiti dagli operatori giapponesi, in particolare in relazione alle dimensioni totali dell’e-mail, alle dimensioni delle sezioni HTML e testo, al numero di immagini nei messaggi e ai tag nel contenuto di HTML.

### Inviare bozze {#sending-proofs}

Puoi inviare delle bozze per verificare la consegna. Quando invii la bozza, se utilizzi indirizzi di sostituzione, inserisci gli indirizzi che corrispondono al formato e-mail del profilo utilizzato.

Ad esempio, puoi sostituire l’indirizzo di un profilo con test@softbank.ne.jp se il formato e-mail per questo profilo è stato definito in precedenza il **[!UICONTROL Decore Mail (Softbank)]**.

![](assets/deco-mail_05.png)

## Inviare messaggi {#sending-messages}

Per inviare un’e-mail a destinatari con formati e-mail giapponesi con Campaign, sono possibili due opzioni:

* Creare due consegne: una solo per i destinatari giapponesi e un’altra per gli altri destinatari. Fai riferimento a [questa sezione](#designing-a-specific-delivery-for-japanese-formats).
* Crea una singola consegna e Adobe Campaign rileverà automaticamente il formato da utilizzare. Fai riferimento a [questa sezione](#designing-a-delivery-for-all-formats).

### Progettare una consegna specifica per i formati giapponesi {#designing-a-specific-delivery-for-japanese-formats}

Puoi creare un flusso di lavoro contenente due consegne: una da leggere su un dispositivo mobile giapponese e un’altra per i destinatari con un formato e-mail standard.

A tale scopo, utilizza **[!UICONTROL Split]** attività nel flusso di lavoro e definisci i formati e-mail giapponesi (Deco-mail, Decoration Mail e Decore Mail) come condizioni di filtro.

![](assets/deco-mail_08.png)

![](assets/deco-mail_07.png)

### Progettare una consegna per tutti i formati {#designing-a-delivery-for-all-formats}

Quando Adobe Campaign gestisce dinamicamente i formati in base al dominio (profili con formati e-mail definiti come **[!UICONTROL Unknown]**, **[!UICONTROL HTML]** o **[!UICONTROL Text]** ), puoi inviare la stessa consegna a tutti i destinatari.

Il contatto del messaggio verrà visualizzato correttamente per gli utenti sui cellulari giapponesi, come per i destinatari standard.

>[!IMPORTANT]
>
>Assicurati di rispettare le funzioni speciali associate a ciascun formato e-mail giapponese (Deco-mail, Decoration Mail e Decore Mail). Per ulteriori informazioni sulle limitazioni, consulta [questa sezione](#limitations-and-recommendations).
