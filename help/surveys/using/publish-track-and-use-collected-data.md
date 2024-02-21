---
product: campaign
title: Pubblicare, tracciare e utilizzare i dati raccolti
description: Scopri come pubblicare, tracciare e utilizzare i dati raccolti in un sondaggio
badge-v7: label="v7" type="Informative" tooltip="Applicabile a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Surveys
exl-id: 3cf3c486-6640-4d67-95cf-50d5767deb60
source-git-commit: 668cee663890fafe27f86f2afd3752f7e2ab347a
workflow-type: tm+mt
source-wordcount: '846'
ht-degree: 2%

---

# Pubblicare, tracciare e utilizzare i dati raccolti{#publish-track-and-use-collected-data}



Una volta creato, configurato e pubblicato il modulo, puoi condividere il collegamento con il pubblico e tenere traccia delle risposte.

>[!NOTE]
>
>Il ciclo di vita di un sondaggio in Adobe Campaign e le sue modalità di pubblicazione e consegna sono simili a quelle dei moduli web: questi sono descritti in [questa sezione](../../web/using/about-web-forms.md).

## Dashboard sondaggio {#survey-dashboard}

Ogni sondaggio ha una propria dashboard che consente di visualizzarne lo stato, la descrizione, l’URL pubblico e la pianificazione della disponibilità. Consente inoltre di visualizzare i rapporti disponibili. [Ulteriori informazioni](#reports-on-surveys).

L’URL pubblico del sondaggio viene visualizzato sulla dashboard:

![](assets/survey_public_url.png)

## Tracciamento delle risposte {#response-tracking}

Puoi tenere traccia delle risposte al sondaggio nei registri e nei rapporti.

### Registri del sondaggio {#survey-logs}

Per ogni sondaggio consegnato, puoi tenere traccia delle risposte nel **[!UICONTROL Logs]** scheda. In questa scheda viene visualizzato l’elenco degli utenti che hanno completato il sondaggio e la loro origine:

![](assets/s_ncs_admin_survey_logs.png)

Fare doppio clic su una riga per visualizzare il modulo del sondaggio compilato dal partecipante. È possibile sfogliare l&#39;intero sondaggio e accedere alle risposte complete. Possono essere esportati in un file esterno. Per ulteriori informazioni, consulta [Esportazione delle risposte](#exporting-answers).

L’origine è indicata nell’URL del sondaggio aggiungendo i seguenti caratteri:

```
?origin=xxx
```

durante la modifica del sondaggio, il relativo URL contiene il parametro **[!UICONTROL __uuid]**, che indica che si trova in una fase di test e non è ancora online. Quando accedi al sondaggio tramite questo URL, i record creati non vengono presi in considerazione nel tracciamento (rapporti). L’origine viene forzata al valore **[!UICONTROL Adobe Campaign]**.

Per ulteriori informazioni sui parametri URL, consulta [questa pagina](../../web/using/defining-web-forms-properties.md#form-url-parameters).

### Relazioni sulle indagini {#reports-on-surveys}

La scheda della dashboard ti consente di accedere ai rapporti dei sondaggi. Fai clic sul nome di un rapporto per visualizzarlo.

![](assets/s_ncs_admin_survey_report_doc.png)

La struttura dell’indagine è visibile nella sezione **[!UICONTROL Documentation]** rapporto.

Altri due rapporti sui sondaggi Web sono disponibili nel **[!UICONTROL Reports]** scheda dei sondaggi: **[!UICONTROL General]** e **[!UICONTROL Breakdown of responses]**.

* Generale

  Questo rapporto contiene informazioni generali sul sondaggio: come cambia il numero di risposte nel tempo e la distribuzione per origine e lingua.

  Esempio di rapporto generale:

  ![](assets/s_ncs_admin_survey_report_0.png)

* Raggruppamento delle risposte

  Questo rapporto mostra il raggruppamento delle risposte per ogni domanda. Questo raggruppamento è disponibile solo per le risposte date ai campi memorizzati in **[!UICONTROL Question]** contenitori di tipi. È valida solo per i controlli di selezione (ad esempio, nessuna suddivisione nei campi di testo).

  ![](assets/s_ncs_admin_survey_report_2.png)

## Esportazione delle risposte {#exporting-answers}

Le risposte a un sondaggio possono essere esportate in un file esterno per essere elaborate in un secondo momento. Esistono due modi per farlo:

1. Esportazione dei dati del rapporto

   Per esportare i dati del rapporto, fai clic su **[!UICONTROL Export]** e scegliere il formato di esportazione.

   Per ulteriori informazioni sull’esportazione dei dati del rapporto, consulta [questa sezione](../../reporting/using/about-reports-creation-in-campaign.md).

1. Esportazione delle risposte

   Per esportare le risposte, fare clic su **[!UICONTROL Responses]** del sondaggio e fare clic con il pulsante destro del mouse. Seleziona **[!UICONTROL Export...]**.

   ![](assets/s_ncs_admin_survey_logs_export_menu.png)

   Immettere quindi le informazioni che si desidera esportare e il file di archiviazione.

   È possibile configurare il contenuto e il formato del file di output nella procedura guidata di esportazione.

   Questo consente di:

   * aggiungere colonne al file di output e recuperare le informazioni sul destinatario (memorizzate nel database),
   * formattare i dati esportati,
   * selezionare il formato di codifica per le informazioni contenute nel file.

   Se il sondaggio che desideri esportare contiene diversi **[!UICONTROL Multi-line text]** o **[!UICONTROL HTML text]** , deve essere esportato in **[!UICONTROL XML]** formato. A questo scopo, seleziona questo formato nell’elenco a discesa del **[!UICONTROL Output format]** come mostrato di seguito:

   ![](assets/s_ncs_admin_survey_logs_export_xml.png)

   Clic **[!UICONTROL Start]** per eseguire l&#39;esportazione.

   >[!NOTE]
   >
   >Le esportazioni di dati e le fasi della loro configurazione sono descritte in [questa sezione](../../platform/using/about-generic-imports-exports.md).

## Utilizzo dei dati raccolti {#using-the-collected-data}

Le informazioni raccolte tramite sondaggi online possono essere recuperate nel quadro di un flusso di lavoro di targeting. A tale scopo, utilizza **[!UICONTROL Survey responses]** casella.

Nell’esempio seguente, vogliamo fare un’offerta Web appositamente per i cinque destinatari con almeno due figli e con i punteggi più elevati in un sondaggio online. Le risposte a questo sondaggio sono le seguenti:

![](assets/s_ncs_admin_survey_responses_wf_box_4.png)

Nel flusso di lavoro di targeting, il **[!UICONTROL Survey responses]** sarà configurato come segue:

![](assets/s_ncs_admin_survey_responses_wf_box_1.png)

Inizia selezionando il sondaggio interessato, quindi i dati da estrarre nella sezione centrale della finestra. In questo caso, è necessario estrarre almeno la colonna di punteggio, in quanto verrà utilizzata nella casella di divisione per recuperare i cinque punteggi più elevati.

Indica le condizioni di filtro per le risposte facendo clic sul pulsante **[!UICONTROL Edit query...]** collegamento.

![](assets/s_ncs_admin_survey_responses_wf_box_2.png)

Avvia il flusso di lavoro di targeting. La query recupera 8 destinatari.

![](assets/s_ncs_admin_survey_responses_wf_box_5.png)

Fare clic con il pulsante destro del mouse sulla transizione di output della casella di raccolta per visualizzarle.

![](assets/s_ncs_admin_survey_responses_wf_box_6.png)

Quindi inserisci una casella di divisione nel flusso di lavoro per recuperare i 5 destinatari con il punteggio più alto.

Modifica la casella di divisione per configurarla:

* Per iniziare, seleziona lo schema adeguato nella sezione **[!UICONTROL General]** , quindi configura il sottoinsieme:

  ![](assets/s_ncs_admin_survey_responses_wf_box_6b.png)

* Vai a **[!UICONTROL Sub-sets]** e seleziona la scheda **[!UICONTROL Limit the selected records]** , quindi fare clic sul pulsante **[!UICONTROL Edit...]** collegamento.

  ![](assets/s_ncs_admin_survey_responses_wf_box_7.png)

* Seleziona la **[!UICONTROL Keep only the first records after sorting]** e selezionare la colonna di ordinamento. Seleziona l’opzione **[!UICONTROL Descending sort]**.

  ![](assets/s_ncs_admin_survey_responses_wf_box_8.png)

* Fai clic su **[!UICONTROL Next]** e limitare il numero di record a 5.

  ![](assets/s_ncs_admin_survey_responses_wf_box_9.png)

* Clic **[!UICONTROL Finish]** quindi riavvia il flusso di lavoro per approvare il targeting.

## Standardizzazione dei dati {#standardizing-data}

È possibile impostare processi di standardizzazione in Adobe Campaign per i dati raccolti utilizzando gli alias. Ciò ti consente di standardizzare i dati memorizzati nel database: a questo scopo, definisci gli alias negli elenchi dettagliati che contengono le informazioni pertinenti. [Ulteriori informazioni](../../platform/using/managing-enumerations.md#about-enumerations)
