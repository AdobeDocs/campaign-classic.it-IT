---
title: Configurazione dell’accesso al report
seo-title: Configurazione dell’accesso al report
description: Configurazione dell’accesso al report
seo-description: null
page-status-flag: never-activated
uuid: d32d9805-f84f-457f-b37b-a8278642336a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: dd50ca25-8fa2-48fa-84cc-a63e476701a0
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '760'
ht-degree: 2%

---


# Configurazione dell’accesso al report{#configuring-access-to-the-report}

## Contesto di visualizzazione del report {#report-display-context}

Definite il contesto di visualizzazione del rapporto nella piattaforma Adobe Campaign  utilizzando la **[!UICONTROL Display]** scheda. L&#39;accesso a un rapporto dipende dal tipo di selezione, dalle condizioni di visualizzazione e dalle autorizzazioni di accesso.

### Tipo di selezione {#selection-type}

L&#39;accesso al rapporto può essere limitato a un contesto specifico o a uno spazio di offerta, ad esempio una consegna, un destinatario, una selezione di destinatari e così via. Questo accesso è configurato nella **[!UICONTROL Selection type]** sezione della **[!UICONTROL Display]** scheda.

![](assets/s_ncs_advuser_report_visibility_4.png)

* **[!UICONTROL Single selection]** : il rapporto è accessibile solo quando è selezionata una specifica entità.
* **[!UICONTROL Multiple selection]** : l&#39;accesso al report viene eseguito quando si selezionano più entità.
* **[!UICONTROL Global]** : il rapporto è accessibile tramite l&#39;elenco dei report disponibili nell&#39;universo Reports.

### Sequenza di visualizzazione {#display-sequence}

Il **[!UICONTROL Sequence]** campo consente di immettere un valore numerico che specifica la sequenza di visualizzazione del rapporto nell&#39;elenco.

Per impostazione predefinita, i rapporti sono visualizzati per rilevanza: il valore immesso in questo campo consente di ordinare i rapporti dal valore massimo (massimo) al minimo (minimo) pertinente.

Potete selezionare la scala da usare in base alle vostre esigenze: Da 1 a 10, da 0 a 100, da -10 a 10, ecc.

### Condizioni di visualizzazione {#display-conditions}

È inoltre possibile condizionare la visualizzazione del rapporto tramite una query.

![](assets/s_ncs_advuser_report_visibility_5.png)

Nell&#39;esempio seguente, il rapporto viene visualizzato se il canale principale della campagna è e-mail.

![](assets/s_ncs_advuser_report_visibility_6.png)

Ciò significa che se il canale principale della campagna è la posta diretta, il report non sarà disponibile nei report della campagna.

### Autorizzazione di accesso {#access-authorization}

Il rapporto può essere condiviso con altri operatori.

Per rendere il rapporto accessibile, selezionare l&#39; **[!UICONTROL Report shared with other operators]** opzione. Se questa opzione non è selezionata, solo l&#39;operatore che ha creato il rapporto può accedere al rapporto.

Il rapporto può essere condiviso anche con determinati operatori o gruppi di operatori aggiunti tramite la finestra delle autorizzazioni.

![](assets/s_ncs_advuser_report_visibility_8.png)

### Definizione delle opzioni di filtro {#defining-the-filtering-options}

L&#39; **[!UICONTROL Reports]** universo visualizza tutti i report disponibili nella piattaforma e per i quali l&#39;operatore connesso ha un diritto di accesso.

Per impostazione predefinita, sono ordinati in base alla rilevanza, ma è possibile applicare altri tipi di filtri: alfabetico, per età, ecc.

Potete anche filtrare la visualizzazione in base alla categoria del rapporto:

![](assets/report_ovv_select_type.png)

Per definire la categoria di un rapporto, selezionatelo tramite la **[!UICONTROL Display]** scheda, come illustrato di seguito:

![](assets/report_select_category.png)

È possibile inserire una nuova categoria qui e aggiungerla all&#39;elenco delle categorie disponibili. L&#39;enumerazione corrispondente viene aggiornata automaticamente.

## Creazione di un collegamento a un rapporto {#creating-a-link-to-a-report-}

È possibile rendere un report accessibile tramite un nodo specifico della struttura, ad esempio un elenco, un destinatario, una consegna e così via. A tal fine, create semplicemente un collegamento al rapporto interessato e specificate l&#39;entità in cui desiderate renderlo disponibile.

Ad esempio, creeremo un collegamento a un rapporto per renderlo accessibile tramite un elenco di destinatari.

1. Fate clic su **[!UICONTROL New]** e selezionate **[!UICONTROL Create a link to an existing report]** nella procedura guidata di creazione dei rapporti.

   ![](assets/s_ncs_advuser_report_wizard_link_01.png)

1. Selezionate il rapporto a cui desiderate creare un collegamento utilizzando l&#39;elenco a discesa. In questo esempio, selezioneremo il rapporto **Suddivisione per paese** .

   ![](assets/s_ncs_advuser_report_wizard_link_02.png)

1. Immettere un&#39;etichetta e selezionare lo schema. In questo esempio, selezioneremo la tabella degli elenchi destinatari.

   ![](assets/s_ncs_advuser_report_wizard_link_03.png)

   Ciò significa che il rapporto sarà accessibile tramite qualsiasi elenco di destinatari e che le statistiche riguarderanno i destinatari nell&#39;elenco selezionato.

1. Salvataggio e visualizzazione del rapporto.
1. Inserisci il tasto di collegamento. In questo caso, la chiave esterna del collegamento &quot;Cartelle&quot;.

   ![](assets/s_ncs_advuser_report_wizard_link_04.png)

1. Pubblicate il rapporto.
1. Accedi a uno degli elenchi dei destinatari e fai clic sul **[!UICONTROL Reports]** collegamento: il rapporto appena creato è accessibile.

   ![](assets/s_ncs_advuser_report_wizard_link_05.png)

## Anteprima del rapporto {#preview-of-the-report}

Prima di pubblicare il rapporto, accertatevi che sia visualizzato correttamente nella **[!UICONTROL Preview]** scheda.

![](assets/s_ncs_advuser_report_preview_01.png)

Per visualizzare l&#39;anteprima del rapporto, selezionate l&#39; **[!UICONTROL Global]** opzione o l&#39; **[!UICONTROL Selection]** .

Queste due opzioni vengono selezionate in base alle impostazioni di visualizzazione del rapporto. Se l&#39;impostazione di visualizzazione è **[!UICONTROL Global]**, è necessario selezionare l&#39;opzione di **[!UICONTROL Global]** anteprima. Se le impostazioni di visualizzazione sono **[!UICONTROL Single selection]** o **[!UICONTROL Multiple selection]**, l&#39;opzione di **[!UICONTROL Selection]** anteprima deve essere selezionata.

Per ulteriori informazioni, consulta Contesto [di visualizzazione](#report-display-context)report.

Impostazioni specifiche consentono di controllare gli errori. L&#39;impostazione **_uuid** si trova nell&#39;URL del rapporto. Potete aggiungere le impostazioni **&amp;_preview** o **&amp;_debug** .

Per ulteriori informazioni su queste impostazioni, fare riferimento alla sezione **Definizione delle proprietà** del modulo Web del capitolo [Moduli](../../web/using/about-web-forms.md) Web.

## Pubblicazione del rapporto {#publishing-the-report}

La pubblicazione del rapporto è obbligatoria per condividerli con altri operatori e visualizzarli nell&#39;elenco dei rapporti disponibili (fare anche riferimento al contesto [di visualizzazione del](#report-display-context)rapporto). Questa operazione deve essere eseguita nuovamente ogni volta che il rapporto viene modificato.

1. Aprite la procedura guidata di pubblicazione facendo clic **[!UICONTROL Publish]** sulla barra degli strumenti.

   ![](assets/s_ncs_advuser_report_publish_01.png)

1. Fate clic **[!UICONTROL Start]** per pubblicare.

   ![](assets/s_ncs_advuser_report_publish_02.png)

1. Fate clic sull&#39; **[!UICONTROL Enlarge]** icona per aprire il rapporto in un browser Web.

