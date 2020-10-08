---
title: Pubblicare, tracciare e utilizzare i dati raccolti
seo-title: Pubblicare, tracciare e utilizzare i dati raccolti
description: Pubblicare, tracciare e utilizzare i dati raccolti
seo-description: null
page-status-flag: never-activated
uuid: eac16f2c-0423-4727-a2da-3af1d6c616ec
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: online-surveys
discoiquuid: 434a4bda-0907-42a7-8a75-2db658bba046
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '844'
ht-degree: 4%

---


# Pubblicare, tracciare e utilizzare i dati raccolti{#publish-track-and-use-collected-data}

Una volta creato, configurato e pubblicato il modulo, è possibile condividere il collegamento con il pubblico e tenere traccia delle risposte.

>[!NOTE]
>
>Il ciclo di vita di un sondaggio in  Adobe Campaign e le relative modalità di pubblicazione e consegna sono simili a quelle dei moduli Web: sono descritti in [questa sezione](../../web/using/about-web-forms.md).

## Pannello di controllo {#survey-dashboard}

Ogni sondaggio dispone di una propria dashboard che consente di visualizzarne lo stato, la descrizione, l’URL pubblico e la pianificazione della disponibilità. Consente inoltre di visualizzare i rapporti disponibili. Per ulteriori informazioni, consulta [Rapporti sulle indagini](#reports-on-surveys).

L’URL pubblico del sondaggio viene visualizzato nel dashboard:

![](assets/survey_public_url.png)

## Tracciamento delle risposte {#response-tracking}

Potete tenere traccia delle risposte al sondaggio nei registri e nei rapporti.

### Registri di sondaggio {#survey-logs}

Per ciascun sondaggio distribuito, potete tenere traccia delle risposte nella **[!UICONTROL Logs]** scheda. In questa scheda viene visualizzato l’elenco degli utenti che hanno completato il sondaggio e la loro origine:

![](assets/s_ncs_admin_survey_logs.png)

Fate doppio clic su una riga per visualizzare il modulo del sondaggio compilato dal rispondente. Potete consultare il sondaggio nel dettaglio e accedere alle risposte complete. Questi possono essere esportati in un file esterno. For more on this, refer to [Exporting answers](#exporting-answers).

L’origine è indicata nell’URL del sondaggio aggiungendo i seguenti caratteri:

```
?origin=xxx
```

durante la modifica del sondaggio, il relativo URL contiene il parametro **[!UICONTROL __uuid]**, che indica che si trova in una fase di prova e non è ancora online. Quando accedete al sondaggio tramite questo URL, i record creati non vengono presi in considerazione nel tracciamento (rapporti). L&#39;origine viene forzata al valore **[!UICONTROL Adobe Campaign]**.

For more on URL parameters, refer to [this page](../../web/using/defining-web-forms-properties.md#form-url-parameters).

### Relazioni sulle indagini {#reports-on-surveys}

La scheda della dashboard consente di accedere ai rapporti dei sondaggi. Fate clic sul nome di un rapporto per visualizzarlo.

![](assets/s_ncs_admin_survey_report_doc.png)

La struttura del sondaggio è visibile nel **[!UICONTROL Documentation]** rapporto.

Altri due rapporti sui sondaggi Web sono disponibili nella **[!UICONTROL Reports]** scheda dei sondaggi: **[!UICONTROL General]** e **[!UICONTROL Breakdown of responses]**.

* Generale

   Questo rapporto contiene informazioni generali sul sondaggio: il numero di risposte cambia nel tempo e la distribuzione per origine e lingua.

   Esempio di relazione generale:

   ![](assets/s_ncs_admin_survey_report_0.png)

* Suddivisione delle risposte

   Questo rapporto mostra la suddivisione delle risposte per ogni domanda. Questa suddivisione è disponibile solo per le risposte date ai campi memorizzati in contenitori **[!UICONTROL Question]** di tipo. È valido solo per i controlli di selezione (ad esempio, nessuna suddivisione in campi di testo).

   ![](assets/s_ncs_admin_survey_report_2.png)

## Esportazione delle risposte {#exporting-answers}

Le risposte a un sondaggio possono essere esportate in un file esterno da elaborare in un secondo momento. Esistono due modi per farlo:

1. Esportazione dei dati del rapporto

   Per esportare i dati del rapporto, fate clic sul **[!UICONTROL Export]** pulsante e scegliete il formato di esportazione.

   For more on exporting report data, refer to [this section](../../reporting/using/about-reports-creation-in-campaign.md).

1. Esportazione delle risposte

   Per esportare le risposte, fate clic sulla **[!UICONTROL Responses]** scheda del sondaggio e fate clic con il pulsante destro del mouse. Seleziona **[!UICONTROL Export...]**.

   ![](assets/s_ncs_admin_survey_logs_export_menu.png)

   Quindi immettere le informazioni da esportare e il file di archiviazione.

   Potete configurare il contenuto e il formato del file di output nella procedura guidata di esportazione.

   Questo consente di:

   * aggiungere colonne al file di output e recuperare le informazioni sul destinatario (memorizzato nel database),
   * formattare i dati esportati,
   * selezionate il formato di codifica per le informazioni nel file.

   Se il sondaggio che desiderate esportare contiene diversi **[!UICONTROL Multi-line text]** campi o **[!UICONTROL HTML text]** campi, deve essere esportato in **[!UICONTROL XML]** formato. A questo scopo, selezionare questo formato nell&#39;elenco a discesa del **[!UICONTROL Output format]** campo, come mostrato di seguito:

   ![](assets/s_ncs_admin_survey_logs_export_xml.png)

   Fate clic **[!UICONTROL Start]** per eseguire l&#39;esportazione.

   >[!NOTE]
   >
   >Le esportazioni di dati e le fasi della loro configurazione sono descritte in [questa sezione](../../platform/using/generic-imports-and-exports.md).

## Utilizzo dei dati raccolti {#using-the-collected-data}

Le informazioni raccolte tramite indagini online possono essere recuperate nel quadro di un flusso di lavoro di targeting. To do this, use the **[!UICONTROL Survey responses]** box.

Nell&#39;esempio seguente, vogliamo fare un&#39;offerta Web specialmente per i cinque destinatari con almeno due bambini e con i punteggi più alti in un sondaggio online. Le risposte a questo sondaggio sono:

![](assets/s_ncs_admin_survey_responses_wf_box_4.png)

Nel flusso di lavoro di targeting, l&#39; **[!UICONTROL Survey responses]** evento sarà configurato come segue:

![](assets/s_ncs_admin_survey_responses_wf_box_1.png)

Per iniziare, selezionare il sondaggio interessato, quindi i dati da estrarre nella sezione centrale della finestra. In questo caso dobbiamo estrarre almeno la colonna punteggio, in quanto verrà utilizzata nella casella di divisione per recuperare i cinque punteggi più alti.

Indicate le condizioni di filtraggio per le risposte facendo clic sul **[!UICONTROL Edit query...]** collegamento.

![](assets/s_ncs_admin_survey_responses_wf_box_2.png)

Avviate il flusso di lavoro di targeting. La query recupera 8 destinatari.

![](assets/s_ncs_admin_survey_responses_wf_box_5.png)

Fare clic con il pulsante destro del mouse sulla transizione di output della casella della raccolta per visualizzarli.

![](assets/s_ncs_admin_survey_responses_wf_box_6.png)

Quindi inserite una casella di divisione nel flusso di lavoro per recuperare i 5 destinatari con la valutazione più alta.

Modificate la casella di divisione per configurarla:

* Per iniziare, selezionate lo schema appropriato nella **[!UICONTROL General]** scheda, quindi configurate il sottoinsieme:

   ![](assets/s_ncs_admin_survey_responses_wf_box_6b.png)

* Vai alla **[!UICONTROL Sub-sets]** scheda e seleziona l&#39; **[!UICONTROL Limit the selected records]** opzione, quindi fai clic sul **[!UICONTROL Edit...]** collegamento.

   ![](assets/s_ncs_admin_survey_responses_wf_box_7.png)

* Selezionate l’ **[!UICONTROL Keep only the first records after sorting]** opzione e selezionate la colonna di ordinamento. Seleziona l’opzione **[!UICONTROL Descending sort]**.

   ![](assets/s_ncs_admin_survey_responses_wf_box_8.png)

* Fare clic sul **[!UICONTROL Next]** pulsante e limitare il numero di record a 5.

   ![](assets/s_ncs_admin_survey_responses_wf_box_9.png)

* Fate clic su **[!UICONTROL Finish]** quindi riavviate il flusso di lavoro per approvare il targeting.

## Standardizzazione dei dati {#standardizing-data}

È possibile impostare processi di standardizzazione in  Adobe Campaign per i dati raccolti utilizzando gli alias. Questo consente di standardizzare i dati memorizzati nel database: a tal fine, definire gli alias negli elenchi dettagliati che contengono le informazioni pertinenti.

Per ulteriori informazioni, consulta [questa pagina](../../platform/using/managing-enumerations.md#about-enumerations).
