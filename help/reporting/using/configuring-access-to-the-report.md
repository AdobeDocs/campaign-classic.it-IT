---
product: campaign
title: Configurare l’accesso al rapporto
description: Configurare l’accesso al rapporto
feature: Reporting
exl-id: 1e5ab922-481c-4dce-a05e-a58408002e24
source-git-commit: 36e546a34d8c2345fefed5d459095a76c6224a38
workflow-type: tm+mt
source-wordcount: '754'
ht-degree: 1%

---

# Configurare l’accesso al rapporto{#configuring-access-to-the-report}

![](../../assets/common.svg)

## Contesto della visualizzazione del rapporto {#report-display-context}

Definisci il contesto di visualizzazione del rapporto nella piattaforma Adobe Campaign utilizzando **[!UICONTROL Display]** scheda . L’accesso a un rapporto dipende dal tipo di selezione, dalle condizioni di visualizzazione e dalle autorizzazioni di accesso.

### Tipo di selezione {#selection-type}

L’accesso al rapporto può essere limitato a un contesto specifico o a uno spazio di offerta, ad esempio una consegna, un destinatario, una selezione di destinatari e così via. Questo accesso è configurato nella **[!UICONTROL Selection type]** della sezione **[!UICONTROL Display]** scheda .

![](assets/s_ncs_advuser_report_visibility_4.png)

* **[!UICONTROL Single selection]** : il rapporto è accessibile solo quando è selezionata una specifica entità.
* **[!UICONTROL Multiple selection]** : il rapporto è accessibile quando sono selezionate più entità.
* **[!UICONTROL Global]** : il rapporto è accessibile tramite l’elenco dei rapporti disponibili nel **[!UICONTROL Reports]** scheda .

### Sequenza di visualizzazione {#display-sequence}

La **[!UICONTROL Sequence]** consente di inserire un valore numerico che specifica la sequenza di visualizzazione del rapporto nell’elenco.

Per impostazione predefinita, i rapporti vengono visualizzati in base alla rilevanza: il valore inserito in questo campo ti consente di ordinare i rapporti dal valore più alto al minore (valore più basso) pertinente.

Puoi selezionare la scala da utilizzare in base alle tue esigenze: Da 1 a 10, da 0 a 100, da -10 a 10, ecc.

### Condizioni di visualizzazione {#display-conditions}

È inoltre possibile condizionare la visualizzazione del rapporto tramite una query.

![](assets/s_ncs_advuser_report_visibility_5.png)

Nell’esempio seguente, il rapporto viene visualizzato se il canale della campagna principale è e-mail.

![](assets/s_ncs_advuser_report_visibility_6.png)

Ciò significa che se il canale principale della campagna è la direct mailing, il rapporto non sarà disponibile nei rapporti della campagna.

### Autorizzazione di accesso {#access-authorization}

Il rapporto può essere condiviso con altri operatori.

Per rendere il rapporto accessibile, seleziona la **[!UICONTROL Report shared with other operators]** opzione . Se questa opzione non è selezionata, solo l’operatore che ha creato il rapporto può accedere al rapporto.

Il rapporto può anche essere condiviso con specifici operatori o gruppi di operatori aggiunti tramite la finestra delle autorizzazioni.

![](assets/s_ncs_advuser_report_visibility_8.png)

### Definire le opzioni di filtro {#defining-the-filtering-options}

La **[!UICONTROL Reports]** visualizza tutti i report disponibili nella piattaforma e per i quali l’operatore connesso dispone di un diritto di accesso.

Per impostazione predefinita, sono ordinati per rilevanza, ma puoi applicare altri tipi di filtri: alfabetico, per età, ecc.

Puoi anche filtrare la visualizzazione in base alla categoria del rapporto:

![](assets/report_ovv_select_type.png)

Per definire la categoria di un rapporto, selezionalo tramite il **[!UICONTROL Display]** , come illustrato di seguito:

![](assets/report_select_category.png)

È possibile inserire una nuova categoria qui e aggiungerla all&#39;elenco delle categorie disponibili. L&#39;enumerazione corrispondente viene aggiornata automaticamente.

## Creare un collegamento a un rapporto {#creating-a-link-to-a-report-}

È possibile rendere un rapporto accessibile tramite un nodo specifico della struttura, ad esempio un elenco, un destinatario, una consegna e così via. A questo scopo, crea semplicemente un collegamento al rapporto interessato e specifica l’entità in cui desideri renderlo disponibile.

Ad esempio, creeremo un collegamento a un rapporto per renderlo accessibile tramite un elenco di destinatari.

1. Fai clic su **[!UICONTROL New]** e seleziona **[!UICONTROL Create a link to an existing report]** nella procedura guidata di creazione dei rapporti.

   ![](assets/s_ncs_advuser_report_wizard_link_01.png)

1. Seleziona il rapporto a cui desideri creare un collegamento utilizzando l’elenco a discesa . In questo esempio, selezioneremo il **Disaggregazione per paese** rapporto.

   ![](assets/s_ncs_advuser_report_wizard_link_02.png)

1. Immetti un’etichetta e seleziona lo schema. In questo esempio, selezioneremo la tabella degli elenchi destinatari.

   ![](assets/s_ncs_advuser_report_wizard_link_03.png)

   Ciò significa che il rapporto sarà accessibile tramite qualsiasi elenco di destinatari e che le statistiche riguarderanno i destinatari nell’elenco selezionato.

1. Salvataggio e visualizzazione del report.
1. Immetti la chiave di collegamento. In questo caso, la chiave esterna del collegamento Cartelle.

   ![](assets/s_ncs_advuser_report_wizard_link_04.png)

1. Pubblica il rapporto.
1. Vai a uno degli elenchi dei destinatari e fai clic su **[!UICONTROL Reports]** link: il rapporto appena creato è accessibile.

   ![](assets/s_ncs_advuser_report_wizard_link_05.png)

## Anteprima del rapporto {#preview-of-the-report}

Prima di pubblicare il rapporto, accertati che sia visualizzato correttamente nel **[!UICONTROL Preview]** scheda .

![](assets/s_ncs_advuser_report_preview_01.png)

Per visualizzare l’anteprima del rapporto, seleziona la **[!UICONTROL Global]** o **[!UICONTROL Selection]** opzione .

Queste due opzioni vengono selezionate in base alle impostazioni di visualizzazione del rapporto. Se l&#39;impostazione di visualizzazione è **[!UICONTROL Global]**, è necessario selezionare il **[!UICONTROL Global]** opzione di anteprima. Se le impostazioni di visualizzazione sono **[!UICONTROL Single selection]** o **[!UICONTROL Multiple selection]**, **[!UICONTROL Selection]** l’opzione anteprima deve essere selezionata.

Per ulteriori informazioni, consulta [Contesto della visualizzazione del rapporto](#report-display-context).

Le impostazioni specifiche consentono di controllare gli errori. La **_uuid** si trova nell&#39;URL del report. Puoi aggiungere la **&amp;_preview** o **&amp;_debug** impostazioni.

Per ulteriori informazioni su queste impostazioni, consulta **Definizione delle proprietà del modulo web** della sezione [Moduli web](../../web/using/about-web-forms.md) capitolo.

## Pubblicare il rapporto {#publishing-the-report}

La pubblicazione del rapporto è obbligatoria per condividerlo con altri operatori e visualizzarlo nell’elenco dei rapporti disponibili (consulta anche [Contesto della visualizzazione del rapporto](#report-display-context)). Questa operazione deve essere eseguita nuovamente ogni volta che il rapporto viene modificato.

1. Apri la procedura guidata di pubblicazione facendo clic su **[!UICONTROL Publish]** nella barra degli strumenti.

   ![](assets/s_ncs_advuser_report_publish_01.png)

1. Fai clic su **[!UICONTROL Start]** da pubblicare.

   ![](assets/s_ncs_advuser_report_publish_02.png)

1. Fai clic sul pulsante **[!UICONTROL Enlarge]** per aprire il rapporto in un browser web.
