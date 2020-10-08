---
title: Gestione delle risposte
seo-title: Gestione delle risposte
description: Gestione delle risposte
seo-description: null
page-status-flag: never-activated
uuid: 329e2f4a-c5bc-4654-bdef-71a0818fc2b7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: online-surveys
discoiquuid: affecd87-00a3-4d50-92d3-31ac6228948b
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '855'
ht-degree: 1%

---


# Gestione delle risposte{#managing-answers}

## Memorizzazione delle risposte raccolte {#storing-collected-answers}

Oltre alle modalità di memorizzazione standard comuni a tutti i moduli Web in  Adobe Campaign (campo di database e variabile locale), i sondaggi consentono l&#39;estensione dinamica del modello dati utilizzando i campi archiviati.

>[!CAUTION]
>
>Questa opzione è disponibile solo per applicazioni Web di tipo **sondaggio** . Non è disponibile per altri tipi di moduli Web.

### Memorizzazione in un campo archiviato {#storing-in-an-archived-field}

È facile estendere il modello di dati aggiungendo nuovi spazi di memorizzazione per salvare le risposte fornite nei sondaggi. A tal fine, selezionare l&#39; **[!UICONTROL Store answers to a question]** opzione al momento della creazione del campo di input. Fai clic sul **[!UICONTROL New field...]** collegamento e assegna le relative proprietà:

![](assets/s_ncs_admin_survey_new_space.png)

Immettere l&#39;etichetta e il nome del campo e selezionare il tipo di campo: Testo, Booleano, Numero intero o decimale, Data, ecc.

Il tipo di campo selezionato include un controllo dei dati quando le risposte vengono immesse dagli utenti. Per i campi di **testo** , è possibile aggiungere un vincolo (maiuscole/minuscole, formato) o un collegamento a un&#39;enumerazione esistente per forzare la selezione.

Per aggiungere un vincolo, selezionatelo dall&#39;elenco a discesa. Esistono due tipi di vincoli:

1. Carattere maiuscolo

   Le informazioni immesse possono essere memorizzate nel campo nei seguenti formati: tutte le lettere maiuscole, tutte minuscole o con la maiuscola iniziale. Questo vincolo non richiede che l&#39;utente immetta i dati nel formato selezionato, ma il contenuto immesso nel campo verrà convertito al momento del salvataggio.

1. Formato dati

Se questo campo viene utilizzato in un elenco, i valori dell&#39;enumerazione possono essere recuperati automaticamente nella tabella di valori utilizzando il **[!UICONTROL Initialize the list of values from the database]** collegamento sopra l&#39;elenco di valori.

Ad esempio, potete creare un elenco a discesa per consentire all&#39;utente di selezionare la propria lingua nativa. Il campo archiviato corrispondente può essere associato all&#39;enumerazione della **lingua** che contiene un elenco di lingue:

![](assets/s_ncs_admin_survey_database_values_2b.png)

L&#39; **[!UICONTROL Edit link]** icona a destra del campo consente di modificare il contenuto di questa enumerazione:

![](assets/s_ncs_admin_survey_database_values_2c.png)

Nella **[!UICONTROL General]** scheda del campo, il **[!UICONTROL Initialize the list of values from the database]** collegamento consente di inserire automaticamente l&#39;elenco delle etichette offerte.

![](assets/s_ncs_admin_survey_database_values_2.png)

**Esempio**: archiviazione dei contratti di un destinatario in un campo

Per memorizzare diversi tipi di contratti in un campo, creare un campo di **[!UICONTROL Text]** immissione e selezionare l&#39; **[!UICONTROL Store answers to a question]** opzione.

Fare clic sul **[!UICONTROL New field...]** collegamento e immettere le proprietà del campo. Selezionare l&#39; **[!UICONTROL Multiple values]** opzione per abilitare la memorizzazione di più valori.

![](assets/s_ncs_admin_survey_storage_multi_ex1.png)

Creare campi di immissione per gli altri contratti e archiviare i dati nello stesso campo archiviato.

![](assets/s_ncs_admin_survey_storage_multi_ex2.png)

Quando gli utenti approvano il sondaggio, le loro risposte saranno memorizzate nel **[!UICONTROL Contracts]** campo.

Nel nostro esempio, per le seguenti risposte:

![](assets/s_ncs_admin_survey_storage_multi_ex3.png)

Il profilo del convenuto conterrà i quattro contratti stipulati.

Possono essere visualizzati nella **[!UICONTROL Answers]** scheda del sondaggio visualizzando le colonne pertinenti.

![](assets/s_ncs_admin_survey_storage_multi_ex4.png)

Puoi anche filtrare i destinatari in base alle risposte per visualizzare solo gli utenti che ti interessano. A questo scopo, create un flusso di lavoro di targeting e utilizzate la **[!UICONTROL Survey responses]** casella.

![](assets/s_ncs_admin_survey_read_responses_wf.png)

Create la query in base ai profili che desiderate recuperare. Nell&#39;esempio seguente, la query consente di selezionare profili con almeno due contratti, incluso un contratto di tipo A.

![](assets/s_ncs_admin_survey_read_responses_edit.png)

Per ciascun modulo, le risposte fornite possono essere utilizzate in campi o etichette. Utilizzate la sintassi seguente per il contenuto memorizzato in un campo archiviato:

```
<%= ctx.webAppLogRcpData.name of the archived field %
```

>[!NOTE]
>
>Per altri tipi di campi, la sintassi è dettagliata in [questa sezione](../../platform/using/about-queries-in-campaign.md).

### Impostazioni di archiviazione {#storage-settings}

È possibile archiviare le risposte ai sondaggi in formato XML. Questo consente di salvare una copia grezza delle risposte raccolte, che può essere utile in caso di standardizzazione eccessiva dei dati in un elenco dettagliato (per ulteriori informazioni, fare riferimento a [Standardizzazione dei dati](../../web/using/publish--track-and-use-collected-data.md#standardizing-data)).

>[!CAUTION]
>
>L&#39;archiviazione delle risposte non elaborate aumenta notevolmente lo spazio di archiviazione richiesto. Utilizzate questa opzione con attenzione.

Per eseguire questa operazione:

* Modificate le proprietà del sondaggio mediante il **[!UICONTROL Properties]** pulsante della **[!UICONTROL Edit]** scheda.
* Fare clic sul **[!UICONTROL Advanced parameters]** collegamento e selezionare l&#39; **[!UICONTROL Save a copy of raw answers]** opzione.

![](assets/s_ncs_admin_survey_xml_archive_option.png)

Potete attivarla per impostazione predefinita per tutti i sondaggi (questa opzione viene applicata quando il sondaggio viene pubblicato). A tal fine, create l’ **[!UICONTROL NmsWebApp_XmlBackup]** opzione e assegnategli un valore **[!UICONTROL 1]** come illustrato di seguito:

![](assets/s_ncs_admin_survey_xml_global_option.png)

## Gestione punteggio {#score-management}

È possibile assegnare una valutazione alle opzioni offerte nelle pagine del modulo. I punteggi possono essere collegati solo a domande chiuse: casella di controllo, valore da un elenco a discesa, iscrizione ecc.

>[!CAUTION]
>
>La gestione del punteggio è disponibile solo per **i sondaggi** .

![](assets/s_ncs_admin_survey_score_create.png)

I punteggi vengono accumulati e salvati sul lato server quando la pagina viene confermata, ad esempio quando l&#39;utente fa clic sul **[!UICONTROL Next]** pulsante o **[!UICONTROL Finish]** .

>[!NOTE]
>
>È possibile utilizzare valori positivi o negativi, numeri interi o non interi.

I punteggi possono essere utilizzati in test o script.

>[!CAUTION]
>
>I punteggi non possono essere utilizzati nelle condizioni di visibilità per i campi che si trovano sulla stessa pagina. Tuttavia, possono essere utilizzati nelle pagine successive.

* Per utilizzare i punteggi nei test, utilizzare il **[!UICONTROL Score]** campo nella formula di calcolo del test, come illustrato di seguito:

   ![](assets/s_ncs_admin_survey_score_in_a_test.png)

* È possibile utilizzare la valutazione in uno script.

**Esempio**: calcolare una valutazione e utilizzarla come condizione per la visualizzazione della pagina successiva:

* In un sondaggio, la pagina successiva consente di assegnare agli utenti punteggi diversi a seconda del valore selezionato nell’elenco a discesa:

   ![](assets/s_ncs_admin_survey_score_exa.png)

* Puoi combinare la valutazione con un secondo valore, a seconda dell’opzione selezionata:

   ![](assets/s_ncs_admin_survey_score_exb.png)

* Quando l&#39;utente fa clic sul **[!UICONTROL Next]** pulsante, vengono aggiunti i due valori.

   ![](assets/s_ncs_admin_survey_score_exe.png)

* Le condizioni possono essere applicate alla pagina da visualizzare in base alla valutazione. Questa configurazione è la seguente:

   ![](assets/s_ncs_admin_survey_score_exd.png)

   ![](assets/s_ncs_admin_survey_score_exg.png)

