---
product: campaign
title: Gestire le risposte
description: Scopri come gestire le risposte ai sondaggi
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Surveys
exl-id: 0b5dc602-e16f-4bf1-bd8f-352e0bc78996
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '839'
ht-degree: 1%

---

# Gestire le risposte{#managing-answers}



## Memorizza le risposte raccolte {#storing-collected-answers}

Oltre alle modalità di archiviazione standard comuni a tutti i moduli web in Adobe Campaign (campo del database e variabile locale), i sondaggi consentono l’estensione dinamica del modello dati utilizzando i campi archiviati.

>[!CAUTION]
>
>Questa opzione è disponibile per **Sondaggio** digitare Solo applicazioni Web. Non è disponibile per altri tipi di moduli Web.

### Memorizza in un campo archiviato {#storing-in-an-archived-field}

È facile estendere il modello dati aggiungendo nuovi spazi di archiviazione per salvare le risposte fornite nei sondaggi. A questo scopo, seleziona la **[!UICONTROL Store answers to a question]** durante la creazione del campo di input. Fai clic su **[!UICONTROL New field...]** e assegna le proprietà:

![](assets/s_ncs_admin_survey_new_space.png)

Immettere l&#39;etichetta e il nome del campo e selezionare il tipo di campo: Testo, Booleano, Numero intero o decimale, Data e così via.

Il tipo di campo selezionato include un controllo dei dati quando le risposte vengono immesse dagli utenti. Per **text** campi, puoi aggiungere un vincolo (maiuscole/minuscole, formato) o un collegamento a un’enumerazione esistente per forzare la selezione.

Per aggiungere un vincolo, selezionatelo dall&#39;elenco a discesa. Esistono due tipi di vincoli:

1. Maiuscole/minuscole caratteri

   Le informazioni immesse possono essere memorizzate nel campo nei seguenti formati: tutto maiuscolo, tutto minuscolo o iniziale maiuscolo. Questo vincolo non richiede all’utente di immettere i dati nel formato selezionato, ma il contenuto immesso nel campo verrà convertito al momento del salvataggio.

1. Formato dei dati

Se questo campo viene utilizzato in un elenco, i valori dell’enumerazione possono essere recuperati automaticamente nella tabella di valori utilizzando **[!UICONTROL Initialize the list of values from the database]** sopra l’elenco dei valori.

Ad esempio, puoi creare un elenco a discesa per consentire all’utente di selezionare la propria lingua nativa. Il campo archiviato corrispondente può essere associato al **lingua** enumerazione che contiene un elenco di lingue:

![](assets/s_ncs_admin_survey_database_values_2b.png)

Il **[!UICONTROL Edit link]** a destra del campo consente di modificare il contenuto di questa enumerazione:

![](assets/s_ncs_admin_survey_database_values_2c.png)

In **[!UICONTROL General]** del campo, la scheda **[!UICONTROL Initialize the list of values from the database]** consente di inserire automaticamente l’elenco delle etichette offerte.

![](assets/s_ncs_admin_survey_database_values_2.png)

**Esempio**: memorizzazione dei contratti di un destinatario in un campo

Per memorizzare diversi tipi di contratti in un campo, creare un **[!UICONTROL Text]** campo di input e selezionare **[!UICONTROL Store answers to a question]** opzione.

Fai clic su **[!UICONTROL New field...]** e immetti le proprietà del campo. Seleziona la **[!UICONTROL Multiple values]** per la memorizzazione di più valori.

![](assets/s_ncs_admin_survey_storage_multi_ex1.png)

Creare campi di immissione per gli altri contratti e archiviare i dati nello stesso campo archiviato.

![](assets/s_ncs_admin_survey_storage_multi_ex2.png)

Quando gli utenti approvano il sondaggio, le loro risposte verranno memorizzate nel **[!UICONTROL Contracts]** campo.

Nel nostro esempio, per le seguenti risposte:

![](assets/s_ncs_admin_survey_storage_multi_ex3.png)

Il profilo del rispondente conterrà i quattro contratti sottoscritti.

Possono essere visualizzate nella **[!UICONTROL Answers]** del sondaggio visualizzando le colonne pertinenti.

![](assets/s_ncs_admin_survey_storage_multi_ex4.png)

Puoi anche filtrare i destinatari in base alle risposte, per visualizzare solo gli utenti che ti interessano. A questo scopo, crea un flusso di lavoro di targeting e utilizza **[!UICONTROL Survey responses]** casella.

![](assets/s_ncs_admin_survey_read_responses_wf.png)

Crea la query in base ai profili che desideri recuperare. Nell’esempio seguente, la query ti consente di selezionare profili con almeno due contratti, incluso un contratto di tipo A.

![](assets/s_ncs_admin_survey_read_responses_edit.png)

Per ogni modulo è possibile utilizzare le risposte fornite nei campi o nelle etichette. Utilizza la seguente sintassi per il contenuto archiviato in un campo archiviato:

```
<%= ctx.webAppLogRcpData.name of the archived field %
```

>[!NOTE]
>
>Per altri tipi di campi, la sintassi è descritta in [questa sezione](../../platform/using/about-queries-in-campaign.md).

### Impostazioni di archiviazione {#storage-settings}

È possibile archiviare le risposte ai sondaggi in formato XML. Questo consente di salvare una copia non elaborata delle risposte raccolte, che può essere utile in caso di standardizzazione eccessiva dei dati in un elenco dettagliato. [Ulteriori informazioni](../../surveys/using/publish--track-and-use-collected-data.md#standardizing-data)

>[!CAUTION]
>
>L&#39;archiviazione delle risposte non elaborate influisce sullo spazio di archiviazione richiesto. Utilizza questa opzione con cautela.

Per eseguire questa operazione:

* Modificare le proprietà del sondaggio tramite **[!UICONTROL Properties]** pulsante della **[!UICONTROL Edit]** scheda.
* Fai clic su **[!UICONTROL Advanced parameters]** collega e controlla **[!UICONTROL Save a copy of raw answers]** opzione.

![](assets/s_ncs_admin_survey_xml_archive_option.png)

Puoi abilitarla per impostazione predefinita per tutti i sondaggi (questa opzione viene applicata quando il sondaggio viene pubblicato). Per eseguire questa operazione, crea il **[!UICONTROL NmsWebApp_XmlBackup]** opzione e valore di assegnazione **[!UICONTROL 1]** come illustrato di seguito:

![](assets/s_ncs_admin_survey_xml_global_option.png)

## Gestione dei punteggi {#score-management}

Puoi assegnare un punteggio alle opzioni offerte nelle pagine del modulo. I punteggi possono essere collegati solo a domande chiuse: casella di controllo, valore da un elenco a discesa, abbonamento, ecc.

![](assets/s_ncs_admin_survey_score_create.png)

I punteggi vengono accumulati e salvati sul lato server quando la pagina viene confermata, ovvero quando l’utente fa clic su **[!UICONTROL Next]** o **[!UICONTROL Finish]** pulsante.

>[!NOTE]
>
>È possibile utilizzare valori positivi o negativi, interi o non interi.

I punteggi possono essere utilizzati nei test o negli script.

>[!CAUTION]
>
>I punteggi non possono essere utilizzati nelle condizioni di visibilità per i campi che si trovano sulla stessa pagina. Tuttavia, possono essere utilizzati nelle pagine successive.

* Per utilizzare i punteggi nei test, utilizza **[!UICONTROL Score]** nella formula di calcolo del test, come illustrato di seguito:

   ![](assets/s_ncs_admin_survey_score_in_a_test.png)

* Puoi utilizzare il punteggio in uno script.

**Esempio**: calcola un punteggio e utilizzalo come condizione per la visualizzazione della pagina successiva:

* In un sondaggio, la pagina successiva ti consente di assegnare punteggi diversi agli utenti a seconda del valore selezionato nell’elenco a discesa:

   ![](assets/s_ncs_admin_survey_score_exa.png)

* Puoi combinare questo punteggio con un secondo valore, a seconda dell’opzione selezionata:

   ![](assets/s_ncs_admin_survey_score_exb.png)

* Quando l’utente fa clic su **[!UICONTROL Next]** , i due valori vengono sommati.

   ![](assets/s_ncs_admin_survey_score_exe.png)

* È possibile applicare le condizioni per la visualizzazione della pagina in base al punteggio. Questa configurazione è configurata come segue:

   ![](assets/s_ncs_admin_survey_score_exd.png)

   ![](assets/s_ncs_admin_survey_score_exg.png)
