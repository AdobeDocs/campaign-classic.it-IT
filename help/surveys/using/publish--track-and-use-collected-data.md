---
product: campaign
title: Pubblicare, tracciare e utilizzare i dati raccolti
description: Scopri come pubblicare, tracciare e utilizzare i dati raccolti in un sondaggio
audience: web
content-type: reference
topic-tags: online-surveys
exl-id: 3cf3c486-6640-4d67-95cf-50d5767deb60
source-git-commit: 86963746d3de3396963d221ddbd1ef7d89733d2f
workflow-type: tm+mt
source-wordcount: '831'
ht-degree: 2%

---

# Pubblicare, tracciare e utilizzare i dati raccolti{#publish-track-and-use-collected-data}

Una volta creato, configurato e pubblicato il modulo, è possibile condividere il collegamento con il pubblico e tenere traccia delle risposte.

>[!NOTE]
>
>Il ciclo di vita di un sondaggio in Adobe Campaign e le relative modalità di pubblicazione e consegna sono simili a quelli dei moduli web: sono descritti in [questa sezione](../../web/using/about-web-forms.md).

## Dashboard dei sondaggi {#survey-dashboard}

Ogni sondaggio dispone di un proprio dashboard che consente di visualizzarne lo stato, la descrizione, l’URL pubblico e la pianificazione della disponibilità. Permette inoltre di visualizzare i rapporti disponibili. [Ulteriori informazioni](#reports-on-surveys).

L’URL pubblico del sondaggio viene visualizzato nel dashboard:

![](assets/survey_public_url.png)

## Tracciamento della risposta {#response-tracking}

Puoi tenere traccia delle risposte al sondaggio nei registri e nei rapporti.

### Registri di sondaggio {#survey-logs}

Per ogni sondaggio consegnato, puoi tenere traccia delle risposte nella scheda **[!UICONTROL Logs]** . In questa scheda viene visualizzato l’elenco degli utenti che hanno completato il sondaggio e la loro origine:

![](assets/s_ncs_admin_survey_logs.png)

Fare doppio clic su una riga per visualizzare il modulo del sondaggio come compilato dal rispondente. Puoi consultare il sondaggio completamente e accedere alle risposte complete. Questi possono essere esportati in un file esterno. Per ulteriori informazioni, consulta [Esportazione delle risposte](#exporting-answers).

L’origine è indicata nell’URL del sondaggio aggiungendo i seguenti caratteri:

```
?origin=xxx
```

durante la modifica del sondaggio, il relativo URL contiene il parametro **[!UICONTROL __uuid]** , che indica che si trova in una fase di test e non è ancora online. Quando accedi al sondaggio tramite questo URL, i record creati non vengono presi in considerazione nel tracciamento (rapporti). L&#39;origine viene forzata al valore **[!UICONTROL Adobe Campaign]**.

Per ulteriori informazioni sui parametri URL, consulta [questa pagina](../../web/using/defining-web-forms-properties.md#form-url-parameters).

### Relazioni sulle indagini {#reports-on-surveys}

La scheda dashboard ti consente di accedere ai rapporti dei sondaggi. Fai clic sul nome di un report per visualizzarlo.

![](assets/s_ncs_admin_survey_report_doc.png)

La struttura del sondaggio è visibile nel rapporto **[!UICONTROL Documentation]** .

Nella scheda **[!UICONTROL Reports]** dei sondaggi sono disponibili altri due rapporti sui sondaggi Web: **[!UICONTROL General]** e **[!UICONTROL Breakdown of responses]**.

* Generale

   Il rapporto contiene informazioni generali sul sondaggio: come cambia il numero di risposte nel tempo e la distribuzione per origine e lingua.

   Esempio di relazione generale:

   ![](assets/s_ncs_admin_survey_report_0.png)

* Scomposizione delle risposte

   Questo rapporto mostra la suddivisione delle risposte per ogni domanda. Questa suddivisione è disponibile solo per le risposte date ai campi memorizzati nei contenitori di tipo **[!UICONTROL Question]** . È valido solo per i controlli di selezione (ad esempio, nessun raggruppamento nei campi di testo).

   ![](assets/s_ncs_admin_survey_report_2.png)

## Esportazione delle risposte {#exporting-answers}

Le risposte a un sondaggio possono essere esportate in un file esterno da elaborare in un secondo momento. Ci sono due modi per farlo:

1. Esportazione dei dati dei rapporti

   Per esportare i dati del rapporto, fai clic sul pulsante **[!UICONTROL Export]** e scegli il formato di esportazione.

   Per ulteriori informazioni sull&#39;esportazione dei dati del rapporto, consulta [questa sezione](../../reporting/using/about-reports-creation-in-campaign.md).

1. Esportazione delle risposte

   Per esportare le risposte, fai clic sulla scheda **[!UICONTROL Responses]** del sondaggio e fai clic con il pulsante destro del mouse. Seleziona **[!UICONTROL Export...]**.

   ![](assets/s_ncs_admin_survey_logs_export_menu.png)

   Quindi immettere le informazioni da esportare e il file di archiviazione.

   Puoi configurare il contenuto e il formato del file di output nella procedura guidata di esportazione.

   Ciò consente di:

   * aggiungere colonne al file di output e recuperare le informazioni sul destinatario (memorizzate nel database),
   * formattare i dati esportati,
   * selezionare il formato di codifica per le informazioni nel file.

   Se il sondaggio che desideri esportare contiene diversi campi **[!UICONTROL Multi-line text]** o **[!UICONTROL HTML text]**, deve essere esportato in formato **[!UICONTROL XML]**. A questo scopo, seleziona questo formato nell’elenco a discesa del campo **[!UICONTROL Output format]** , come illustrato di seguito:

   ![](assets/s_ncs_admin_survey_logs_export_xml.png)

   Fai clic su **[!UICONTROL Start]** per eseguire l’esportazione.

   >[!NOTE]
   >
   >Le esportazioni di dati e le fasi della loro configurazione sono descritte in [questa sezione](../../platform/using/about-generic-imports-exports.md).

## Utilizzo dei dati raccolti {#using-the-collected-data}

Le informazioni raccolte tramite indagini online possono essere recuperate nel quadro di un flusso di lavoro di targeting. A questo scopo, utilizza la casella **[!UICONTROL Survey responses]** .

Nell’esempio seguente, vogliamo fare un’offerta Web appositamente per i cinque destinatari con almeno due figli e con i punteggi più alti in un sondaggio online. Le risposte a questo sondaggio sono:

![](assets/s_ncs_admin_survey_responses_wf_box_4.png)

Nel flusso di lavoro di targeting, il **[!UICONTROL Survey responses]** viene configurato come segue:

![](assets/s_ncs_admin_survey_responses_wf_box_1.png)

Inizia selezionando il sondaggio interessato, quindi i dati da estrarre nella sezione centrale della finestra. In questo caso dobbiamo estrarre almeno la colonna punteggio, poiché verrà utilizzata nella casella di divisione per recuperare i cinque punteggi più alti.

Per indicare le condizioni di filtraggio delle risposte, fai clic sul collegamento **[!UICONTROL Edit query...]** .

![](assets/s_ncs_admin_survey_responses_wf_box_2.png)

Avvia il flusso di lavoro di targeting. La query recupera 8 destinatari.

![](assets/s_ncs_admin_survey_responses_wf_box_5.png)

Fai clic con il pulsante destro del mouse sulla transizione di output della casella di raccolta per visualizzarli.

![](assets/s_ncs_admin_survey_responses_wf_box_6.png)

Quindi inserisci una casella di divisione nel flusso di lavoro per recuperare i 5 destinatari con il punteggio più alto.

Modifica la casella di suddivisione per configurarla:

* Inizia selezionando lo schema appropriato nella scheda **[!UICONTROL General]** , quindi configura il sottoinsieme:

   ![](assets/s_ncs_admin_survey_responses_wf_box_6b.png)

* Vai alla scheda **[!UICONTROL Sub-sets]** e seleziona l&#39;opzione **[!UICONTROL Limit the selected records]**, quindi fai clic sul collegamento **[!UICONTROL Edit...]** .

   ![](assets/s_ncs_admin_survey_responses_wf_box_7.png)

* Seleziona l’opzione **[!UICONTROL Keep only the first records after sorting]** e seleziona la colonna di ordinamento. Seleziona l’opzione **[!UICONTROL Descending sort]**.

   ![](assets/s_ncs_admin_survey_responses_wf_box_8.png)

* Fai clic sul pulsante **[!UICONTROL Next]** e limita il numero di record a 5.

   ![](assets/s_ncs_admin_survey_responses_wf_box_9.png)

* Fai clic su **[!UICONTROL Finish]**, quindi riavvia il flusso di lavoro per approvare il targeting.

## Standardizzazione dei dati {#standardizing-data}

È possibile impostare processi di standardizzazione in Adobe Campaign per i dati raccolti utilizzando gli alias. Ciò consente di standardizzare i dati memorizzati nel database: a tal fine, definisci gli alias negli elenchi dettagliati che contengono le informazioni pertinenti. [Ulteriori informazioni](../../platform/using/managing-enumerations.md#about-enumerations)
