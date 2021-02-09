---
solution: Campaign Classic
product: campaign
title: Invio di e-mail su cellulari giapponesi con Adobe Campaign Classic
description: Scopri come configurare, progettare e inviare e-mail che verranno lette su un dispositivo mobile giapponese.
audience: delivery
content-type: reference
topic-tags: sending-emails
translation-type: tm+mt
source-git-commit: fe4262a1da011cb155651c5e786f19188139cff1
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 0%

---


# Invio di e-mail su dispositivi mobili giapponesi {#sending-emails-on-japanese-mobiles}

## Formati e-mail per dispositivi mobili giapponesi {#email-formats-for-japanese-mobiles}

 Adobe Campaign gestisce tre formati specifici per le e-mail sui dispositivi mobili: **Deco-mail** (cellulari DoCoMo), **Decore Mail** (cellulari Softbank) e **Decoration Mail** (cellulari KDDI AU). Questi formati impongono particolari vincoli di codifica, struttura e dimensione. Ulteriori informazioni sulle limitazioni e sulle raccomandazioni in [questa sezione](#limitations-and-recommendations).

Affinché il destinatario possa ricevere correttamente i messaggi in uno di questi formati, è consigliabile selezionare **[!UICONTROL Deco-mail (DoCoMo)]**, **[!UICONTROL Decore Mail (Softbank)]** o **[!UICONTROL Decoration Mail (KDDI AU)]** nel profilo corrispondente:

![](assets/deco-mail_03.png)

Tuttavia, se lasciate l&#39;opzione **[!UICONTROL Email format]** come **[!UICONTROL Unknown]**, **[!UICONTROL HTML]** o **[!UICONTROL Text]**,  Adobe Campaign rileverà automaticamente (durante l&#39;invio dell&#39;e-mail) il formato giapponese da utilizzare in modo che il messaggio venga visualizzato correttamente.

Questo sistema di rilevamento automatico si basa sull&#39;elenco dei domini predefiniti definiti nel set di regole di posta **[!UICONTROL Management of Email Formats]**. Per ulteriori informazioni sulla gestione dei formati e-mail, consultare [questa pagina](../../installation/using/email-deliverability.md#managing-email-formats).

## Limitazioni e raccomandazioni {#limitations-and-recommendations}

Per l&#39;invio di e-mail che verranno lette su un cellulare gestito da un provider giapponese (Softbank, DoCoMo, KDDI AU) si applicano alcuni vincoli.

È pertanto necessario:

* Usare solo immagini in formato JPEG o GIF
* Create una distribuzione con sezioni di testo e HTML rigorosamente inferiori a 10 000 byte (per KDDI AU e DoCoMo)
* Usate immagini con una dimensione totale (prima della codifica) inferiore a 100 KB
* Non utilizzare più di 20 immagini per messaggio
* Utilizzate un formato HTML di dimensioni ridotte (per ogni operatore è disponibile un numero limitato di tag)

>[!NOTE]
>
>Durante la creazione del messaggio è necessario tenere conto delle limitazioni specifiche di ciascun operatore. Fai riferimento a:
>
>* Per DoCoMo, fare riferimento a [questa pagina](https://www.nttdocomo.co.jp/service/developer/make/content/deco_mail/index.html)
>* Per KDDI AU, fare riferimento a [questa pagina](https://www.au.com/ezfactory/tec/spec/decorations/template.html)
>* Per Softbank, fare riferimento a [questa pagina](https://www.support.softbankmobile.co.jp/partner/home_tech3/index.cfm)


## Verifica del contenuto dell&#39;e-mail {#testing-the-email-content}

### Anteprima del messaggio {#previewing-the-message}

 Adobe Campaign consente di verificare che il formato del messaggio sia adattato per essere inviato a un dispositivo mobile giapponese.

Una volta definito il contenuto e inserito l’oggetto dell’e-mail, potete controllare la visualizzazione e la formattazione al momento della creazione del messaggio.

Nella scheda **[!UICONTROL Preview]** della finestra di modifica del contenuto, facendo clic su **[!UICONTROL More... > Deco-mail diagnostic]** è possibile:

* Verificate che i tag di contenuto HTML siano conformi alle restrizioni di formato giapponesi
* Verificare che il numero di immagini nel messaggio non superi il limite imposto dal formato (20 immagini)
* Controlla la dimensione totale del messaggio (inferiore a 100 kB)

   ![](assets/deco-mail_06.png)

### Esecuzione della regola di tipologia {#running-typology-rule}

Oltre alla diagnosi di anteprima, durante l&#39;invio di una prova o una consegna viene effettuato un secondo controllo: durante l&#39;analisi viene avviata una regola di tipologia specifica, **[!UICONTROL Deco-mail check]**.

>[!IMPORTANT]
>
>Questa regola di tipologia viene eseguita solo se almeno uno dei destinatari è configurato per ricevere e-mail in formato **[!UICONTROL Deco-mail (DoCoMo)]**, **[!UICONTROL Decore Mail (Softbank)]** o **[!UICONTROL Decoration Mail (KDDI AU)]**.

Questa regola di tipologia consente di garantire che la consegna rispetti i vincoli [di formato](#limitations-and-recommendations) definiti dagli operatori giapponesi, in particolare in relazione alle dimensioni totali dell&#39;e-mail, alle dimensioni delle sezioni HTML e di testo, al numero di immagini nei messaggi e ai tag nel contenuto HTML.

### Invio di bozze {#sending-proofs}

Potete inviare prove per verificare la consegna. Quando si invia la prova, se si utilizzano gli indirizzi di sostituzione, immettere gli indirizzi che corrispondono al formato e-mail del profilo utilizzato.

Ad esempio, potete sostituire l&#39;indirizzo di un profilo con test@softbank.ne.jp se il formato e-mail per questo profilo è stato definito in anticipo su **[!UICONTROL Decore Mail (Softbank)]**.

![](assets/deco-mail_05.png)

## Invio di messaggi {#sending-messages}

Per inviare un&#39;e-mail ai destinatari con formati e-mail giapponesi con Campaign, sono possibili due opzioni:

* Create due consegne: uno solo per i destinatari giapponesi e un altro per gli altri destinatari - fare riferimento a [questa sezione](#designing-a-specific-delivery-for-japanese-formats).
* Crea una singola consegna e  Adobe Campaign rileverà automaticamente il formato da utilizzare - fare riferimento a [questa sezione](#designing-a-delivery-for-all-formats).

### Progettazione di una consegna specifica per i formati giapponesi {#designing-a-specific-delivery-for-japanese-formats}

Potete creare un flusso di lavoro contenente due consegne: uno da leggere su un dispositivo mobile giapponese e un altro per i destinatari con un formato e-mail standard.

A questo scopo, utilizzate l&#39;attività **[!UICONTROL Split]** nel flusso di lavoro e definite i formati di posta elettronica giapponesi (Deco-mail, Decoration Mail e Decore Mail) come condizioni di filtro.

![](assets/deco-mail_08.png)

![](assets/deco-mail_07.png)

### Progettazione di una distribuzione per tutti i formati {#designing-a-delivery-for-all-formats}

Quando  Adobe Campaign gestisce in modo dinamico i formati in base al dominio (profili con formati e-mail definiti come **[!UICONTROL Unknown]**, **[!UICONTROL HTML]** o **[!UICONTROL Text]** ), è possibile inviare la stessa consegna a tutti i destinatari.

Il contatto del messaggio verrà visualizzato correttamente per gli utenti su dispositivi mobili giapponesi, come per i destinatari standard.

>[!IMPORTANT]
>
>Assicuratevi di rispettare le funzioni speciali associate a ciascun formato di posta elettronica giapponese (Deco-mail, Decoration Mail e Decore Mail). Per ulteriori informazioni sulle limitazioni, consultare [questa sezione](#limitations-and-recommendations).
