---
product: campaign
title: Gestire le risposte
description: Scopri come gestire le risposte ai sondaggi
feature: Surveys
exl-id: 0b5dc602-e16f-4bf1-bd8f-352e0bc78996
source-git-commit: 1f80c9967f4859f26dd2890d657f95ada6cf2087
workflow-type: tm+mt
source-wordcount: '839'
ht-degree: 1%

---

# Gestire le risposte{#managing-answers}

![](../../assets/common.svg)

## Archiviazione delle risposte raccolte {#storing-collected-answers}

Oltre alle modalità di archiviazione standard comuni a tutti i moduli Web in Adobe Campaign (campo database e variabile locale), i sondaggi consentono l’estensione dinamica del modello dati utilizzando campi archiviati.

>[!CAUTION]
>
>Questa opzione è disponibile per **Sondaggio** solo applicazioni Web di tipo. Non è disponibile per altri tipi di moduli web.

### Archiviazione in un campo archiviato {#storing-in-an-archived-field}

È facile estendere il modello dati aggiungendo nuovi spazi di archiviazione per salvare le risposte fornite nei sondaggi. A questo scopo, seleziona la **[!UICONTROL Store answers to a question]** durante la creazione del campo di input. Fai clic sul pulsante **[!UICONTROL New field...]** collegare e assegnare le relative proprietà:

![](assets/s_ncs_admin_survey_new_space.png)

Immetti l’etichetta e il nome del campo e seleziona il tipo di campo: Testo, booleano, numero intero o decimale, data, ecc.

Il tipo di campo selezionato comporta un controllo dei dati quando le risposte vengono inserite dagli utenti. Per **text** è possibile aggiungere un vincolo (case, format) o un collegamento a un&#39;enumerazione esistente per forzare la selezione.

Per aggiungere un vincolo, selezionalo dall’elenco a discesa. Esistono due tipi di vincoli:

1. Case carattere

   Le informazioni immesse possono essere memorizzate nel campo nei seguenti formati: tutte le lettere maiuscole, tutte minuscole o con maiuscolo iniziale. Questo vincolo non richiede all’utente di immettere i dati nel formato selezionato, ma il contenuto immesso nel campo verrà convertito al momento del salvataggio.

1. Formato dei dati

Se questo campo viene utilizzato in un elenco, i valori dell’enumerazione possono essere recuperati automaticamente nella tabella dei valori utilizzando **[!UICONTROL Initialize the list of values from the database]** sopra l’elenco dei valori.

Ad esempio, puoi creare un elenco a discesa in cui l’utente può selezionare la propria lingua nativa. Il campo archiviato corrispondente può essere associato al **language** enumerazione contenente un elenco di lingue:

![](assets/s_ncs_admin_survey_database_values_2b.png)

La **[!UICONTROL Edit link]** icona situata a destra del campo consente di modificare il contenuto di questa enumerazione:

![](assets/s_ncs_admin_survey_database_values_2c.png)

In **[!UICONTROL General]** della scheda del campo, **[!UICONTROL Initialize the list of values from the database]** link ti consente di inserire automaticamente l&#39;elenco delle etichette offerte.

![](assets/s_ncs_admin_survey_database_values_2.png)

**Esempio**: immagazzinare i contratti di un destinatario in un campo

Per memorizzare diversi tipi di contratti in un campo, crea un **[!UICONTROL Text]** campo di input e seleziona la **[!UICONTROL Store answers to a question]** opzione .

Fai clic sul pulsante **[!UICONTROL New field...]** collega e immetti le proprietà del campo . Seleziona la **[!UICONTROL Multiple values]** per abilitare la memorizzazione di più valori.

![](assets/s_ncs_admin_survey_storage_multi_ex1.png)

Creare campi di ingresso per gli altri contratti e archiviare i dati nello stesso campo archiviato.

![](assets/s_ncs_admin_survey_storage_multi_ex2.png)

Quando gli utenti approvano il sondaggio, le loro risposte saranno memorizzate nella **[!UICONTROL Contracts]** campo .

Nel nostro esempio, per le seguenti risposte:

![](assets/s_ncs_admin_survey_storage_multi_ex3.png)

Il profilo del convenuto conterrà i quattro contratti stipulati.

Possono essere visualizzati nella **[!UICONTROL Answers]** scheda del sondaggio visualizzando le colonne pertinenti.

![](assets/s_ncs_admin_survey_storage_multi_ex4.png)

Puoi anche filtrare i destinatari in base alle risposte per visualizzare solo gli utenti che ti interessano. A questo scopo, crea un flusso di lavoro di targeting e utilizza il **[!UICONTROL Survey responses]** scatola.

![](assets/s_ncs_admin_survey_read_responses_wf.png)

Crea la query in base ai profili che desideri recuperare. Nell’esempio seguente, la query ti consente di selezionare profili con almeno due contratti, incluso un contratto di tipo A.

![](assets/s_ncs_admin_survey_read_responses_edit.png)

Per ciascun modulo, le risposte fornite possono essere utilizzate in campi o etichette. Utilizza la sintassi seguente per il contenuto memorizzato in un campo archiviato:

```
<%= ctx.webAppLogRcpData.name of the archived field %
```

>[!NOTE]
>
>Per altri tipi di campi, la sintassi è dettagliata in [questa sezione](../../platform/using/about-queries-in-campaign.md).

### Impostazioni di archiviazione {#storage-settings}

È possibile archiviare le risposte ai sondaggi in formato XML. Ciò ti consente di salvare una copia non elaborata delle risposte raccolte, che può essere utile in caso di eccessiva standardizzazione dei dati in un elenco dettagliato. [Ulteriori informazioni](../../surveys/using/publish--track-and-use-collected-data.md#standardizing-data)

>[!CAUTION]
>
>L&#39;archiviazione delle risposte non elaborate influisce sullo spazio di archiviazione richiesto. Utilizza questa opzione con cautela.

Per eseguire questa operazione:

* Modificare le proprietà del sondaggio tramite il **[!UICONTROL Properties]** pulsante **[!UICONTROL Edit]** scheda .
* Fai clic sul pulsante **[!UICONTROL Advanced parameters]** e controlla il **[!UICONTROL Save a copy of raw answers]** opzione .

![](assets/s_ncs_admin_survey_xml_archive_option.png)

Per impostazione predefinita, è possibile abilitarla per tutti i sondaggi (questa opzione viene applicata quando il sondaggio viene pubblicato). A questo scopo, crea la **[!UICONTROL NmsWebApp_XmlBackup]** opzione e assegna valore **[!UICONTROL 1]** come mostrato di seguito:

![](assets/s_ncs_admin_survey_xml_global_option.png)

## Gestione dei punteggi {#score-management}

È possibile assegnare un punteggio alle opzioni offerte nelle pagine del modulo. I punteggi possono essere collegati solo a domande chiuse: casella di controllo, valore da un elenco a discesa, abbonamento, ecc.

![](assets/s_ncs_admin_survey_score_create.png)

I punteggi vengono accumulati e salvati sul lato server quando la pagina viene confermata, ad esempio quando l’utente fa clic sul **[!UICONTROL Next]** o **[!UICONTROL Finish]** pulsante .

>[!NOTE]
>
>È possibile utilizzare valori positivi o negativi, interi o non interi.

I punteggi possono essere utilizzati in test o script.

>[!CAUTION]
>
>I punteggi non possono essere utilizzati nelle condizioni di visibilità per i campi che si trovano sulla stessa pagina. Tuttavia, possono essere utilizzati nelle pagine successive.

* Per utilizzare i punteggi nei test, utilizza il **[!UICONTROL Score]** nella formula di calcolo del test, come illustrato di seguito:

   ![](assets/s_ncs_admin_survey_score_in_a_test.png)

* È possibile utilizzare il punteggio in uno script.

**Esempio**: calcola un punteggio e lo utilizza come condizione per la visualizzazione della pagina successiva:

* In un sondaggio, la pagina successiva ti consente di assegnare punteggi diversi agli utenti in base al valore selezionato nell’elenco a discesa:

   ![](assets/s_ncs_admin_survey_score_exa.png)

* Puoi combinare questo punteggio con un secondo valore, a seconda dell’opzione selezionata:

   ![](assets/s_ncs_admin_survey_score_exb.png)

* Quando l&#39;utente fa clic sul pulsante **[!UICONTROL Next]** i due valori vengono sommati.

   ![](assets/s_ncs_admin_survey_score_exe.png)

* Le condizioni possono essere applicate alla pagina da visualizzare in base al punteggio. Questa configurazione è la seguente:

   ![](assets/s_ncs_admin_survey_score_exd.png)

   ![](assets/s_ncs_admin_survey_score_exg.png)
