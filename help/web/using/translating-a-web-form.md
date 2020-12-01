---
solution: Campaign Classic
product: campaign
title: Traduzione di un modulo web
description: Traduzione di un modulo web
audience: web
content-type: reference
topic-tags: web-forms
translation-type: tm+mt
source-git-commit: 21219f4a85a0caec4531acda33ab8bba5c7605d6
workflow-type: tm+mt
source-wordcount: '1565'
ht-degree: 1%

---


# Traduzione di un modulo web{#translating-a-web-form}

È possibile localizzare un&#39;applicazione Web in diverse lingue.

È possibile eseguire le traduzioni direttamente nella  console Adobe Campaign (fare riferimento a [Gestione delle traduzioni nell&#39;editor](#managing-translations-in-the-editor)) oppure esportare e importare le stringhe per esternalizzare la traduzione (fare riferimento a [Esternalizzazione della traduzione](#externalizing-translation)).

L&#39;elenco delle lingue di traduzione disponibili per impostazione predefinita è dettagliato nella sezione [Modifica della lingua](#changing-forms-display-language)di visualizzazione dei moduli.

L&#39;applicazione Web è progettata in una lingua di modifica: questa è la lingua di riferimento utilizzata per immettere etichette e altro contenuto da tradurre.

La lingua predefinita è la lingua in cui verrà visualizzata l&#39;applicazione Web se non viene aggiunta alcuna impostazione di lingua al relativo URL di accesso.

>[!NOTE]
>
>Per impostazione predefinita, la lingua di modifica e la lingua predefinita sono uguali alla lingua della console.

## Scelta delle lingue {#choosing-languages}

Per definire una o più lingue di traduzione, fare clic sul **[!UICONTROL Properties]** pulsante dell&#39;applicazione Web, quindi sulla **[!UICONTROL Localization]** scheda. Fare clic sul **[!UICONTROL Add]** pulsante per definire una nuova lingua di traduzione per l&#39;applicazione Web.

>[!NOTE]
>
>Questa finestra consente inoltre di modificare la lingua predefinita e la lingua di modifica.

![](assets/s_ncs_admin_survey_add_lang.png)

Quando si aggiungono lingue di traduzione per un&#39;applicazione Web (o quando la lingua predefinita e la lingua di modifica sono diverse), nella **[!UICONTROL Translation]** scheda viene aggiunta una **[!UICONTROL Edit]** sottoscheda per gestire le traduzioni.

 Adobe Campaign include uno strumento per tradurre e gestire le traduzioni multilingue. Questo editor consente di visualizzare le stringhe per tradurre o approvare, immettere le traduzioni direttamente nell&#39;interfaccia o importare/esportare le stringhe dei caratteri per esternalizzare le traduzioni.

## Gestione delle traduzioni nell&#39;editor {#managing-translations-in-the-editor}

### Raccolta di stringhe {#collecting-strings}

La **[!UICONTROL Translations]** scheda consente di immettere le traduzioni per le stringhe di caratteri che compongono l&#39;applicazione Web.

La prima volta che si apre questa scheda non conterrà alcun dato. Fare clic sul **[!UICONTROL Collect the strings to translate]** collegamento per aggiornare le stringhe nell&#39;applicazione Web.

 Adobe Campaign raccoglie le etichette di campi e stringhe definiti nelle **[!UICONTROL Texts]** schede di tutti gli elementi statici: Blocchi HTML, Javascript, ecc. Gli elementi statici sono descritti in dettaglio in Elementi [statici di un modulo](../../web/using/static-elements-in-a-web-form.md)Web.

![](assets/s_ncs_admin_survey_trad_tab.png)

>[!CAUTION]
>
>Questo processo può richiedere alcuni minuti a seconda del volume di dati da elaborare.
> 
>Se viene visualizzato un avviso che indica la mancanza di alcune traduzioni nel dizionario di sistema, fare riferimento a [Traduzione delle stringhe](#translating-the-system-strings)di sistema.

Ogni volta che una stringa viene tradotta, la sua traduzione viene aggiunta al dizionario di traduzione.

Quando il processo di raccolta rileva che esiste già una conversione, questa viene visualizzata nella **[!UICONTROL Text]** colonna della stringa. Lo stato della stringa viene ruotato in **[!UICONTROL Translated]**.

Per le stringhe di caratteri che non sono mai state tradotte, il **[!UICONTROL Text]** campo è vuoto e lo stato è **[!UICONTROL To translate]**.

### Filtrare le stringhe {#filtering-strings}

Per impostazione predefinita, viene visualizzata ogni lingua di traduzione dell&#39;applicazione Web. Esistono due filtri predefiniti: lingua e stato. Fare clic sul **[!UICONTROL Filters]** pulsante, quindi fare clic **[!UICONTROL By language or status]** per visualizzare le caselle corrispondenti. Potete anche creare un filtro avanzato. Per ulteriori informazioni, consulta [questa pagina](../../platform/using/creating-filters.md#creating-an-advanced-filter).

![](assets/s_ncs_admin_survey_trad_tab_en.png)

Passate alla casella a **[!UICONTROL Language]** discesa per selezionare la lingua di traduzione.

Per visualizzare solo le stringhe non convertite, selezionare **[!UICONTROL To translate]** nella casella a **[!UICONTROL Status]** discesa. È inoltre possibile visualizzare solo le stringhe tradotte o approvate.

### Traduzione di stringhe {#translating-strings}

1. Per tradurre una parola, fare doppio clic sulla sua riga nell&#39;elenco delle stringhe.

   ![](assets/s_ncs_admin_survey_trad_tab_add_term.png)

   La stringa di origine viene visualizzata nella sezione superiore della finestra.

1. Immettete la traduzione nella sezione inferiore. Per approvarlo, selezionare l&#39; **[!UICONTROL Translation approved]** opzione.

   >[!NOTE]
   >
   >L&#39;approvazione della traduzione è facoltativa e non bloccherà il processo.

   Le traduzioni non approvate vengono visualizzate come **[!UICONTROL Translated]**. Le traduzioni approvate vengono visualizzate come **[!UICONTROL Approved]**.

## Esternalizzazione della traduzione {#externalizing-translation}

È possibile esportare e importare stringhe di caratteri per tradurle con uno strumento diverso da  Adobe Campaign.

>[!CAUTION]
>
>Dopo aver esportato le stringhe, non eseguire alcuna traduzione utilizzando lo strumento integrato. Ciò comporterebbe un conflitto quando si reimportano le traduzioni e queste andranno perse.

### Esportazione di file {#exporting-files}

1. Selezionare le applicazioni Web di cui si desidera esportare le stringhe, fare clic con il pulsante destro del mouse, quindi selezionare **[!UICONTROL Actions > Export strings for translation...]**

   ![](assets/s_ncs_admin_survey_trad_export.png)

1. Selezionare un **[!UICONTROL Export strategy]** :

   * **[!UICONTROL One file per language]**: l&#39;esportazione genererà un file per lingua di traduzione. Ogni file sarà comune a tutte le applicazioni Web selezionate.
   * **[!UICONTROL One file per Web application]**: l&#39;esportazione genererà un file per l&#39;applicazione Web selezionata. Ogni file conterrà tutte le lingue di traduzione.

      >[!NOTE]
      >
      >Questo tipo di esportazione non è disponibile per le esportazioni XLIFF.

   * **[!UICONTROL One file per language and per Web application]**: l&#39;esportazione genererà diversi file. Ogni file conterrà una lingua di traduzione per applicazione Web.
   * **[!UICONTROL One file for all]**: l&#39;esportazione genererà un singolo file multilingue per tutte le applicazioni Web. Conterrà tutte le lingue di traduzione per tutte le applicazioni Web selezionate.

      >[!NOTE]
      >
      >Questo tipo di esportazione non è disponibile per le esportazioni XLIFF.

1. Quindi scegliete il **[!UICONTROL Target folder]** punto in cui registrare i file.
1. Selezionare il formato di file ( **[!UICONTROL CSV]** o **[!UICONTROL XLIFF]** ) e fare clic su **[!UICONTROL Start]**.

![](assets/s_ncs_admin_survey_trad_export_start.png)

>[!NOTE]
>
>I nomi dei file di esportazione vengono generati automaticamente. Se eseguite più volte la stessa esportazione, i file esistenti verranno sostituiti dai nuovi. Se dovete conservare i file precedenti, modificate il file **[!UICONTROL Target folder]** , quindi fate **[!UICONTROL Start]** di nuovo clic per eseguire l&#39;esportazione.

Quando esportate i file in formato **** CSV, ogni lingua viene collegata a uno stato e a uno stato di approvazione. L&#39; **approvazione?** column consente di approvare una traduzione. Questa colonna può contenere i valori **Sì** o **No**. Per quanto riguarda l&#39;editor integrato (consultate [Gestione delle traduzioni nell&#39;editor](#managing-translations-in-the-editor)), approvare le traduzioni è facoltativo e non blocca il processo.

### Importazione di file {#importing-files}

Una volta completata la traduzione esterna, potete importare i file convertiti.

1. Vai all&#39;elenco delle applicazioni Web, fai clic con il pulsante destro del mouse, quindi seleziona **[!UICONTROL Actions > Import translated strings...]**

   >[!NOTE]
   >
   >Non è necessario selezionare le applicazioni Web interessate dalla traduzione. Posizionare il cursore in un punto qualsiasi dell&#39;elenco delle applicazioni Web.

   ![](assets/s_ncs_admin_survey_trad_import.png)

1. Selezionate il file da importare, quindi fate clic su **[!UICONTROL Upload]**.

   ![](assets/s_ncs_admin_survey_trad_import_start.png)

>[!NOTE]
>
>Le traduzioni esterne hanno sempre la priorità sulle traduzioni interne. In caso di conflitti, la traduzione interna sarà sovrascritta con la traduzione esterna.

## Modifica della lingua di visualizzazione dei moduli {#changing-forms-display-language}

I moduli Web vengono visualizzati nella lingua predefinita specificata nella **[!UICONTROL Localization]** scheda delle proprietà dell&#39;applicazione Web. Per modificare le lingue, è necessario aggiungere i seguenti caratteri alla fine dell&#39;URL (dove **xx** è il simbolo della lingua):

```
?lang=xx
```

se la lingua è il primo o l’unico parametro dell’URL. Ad esempio: **https://myserver/webApp/APP34?lang=en**

```
&lang=xx
```

se esistono altri parametri prima della lingua nell’URL. Ad esempio: **https://myserver/webApp/APP34?status=1&amp;lang=en**

Le lingue e i dizionari di traduzione disponibili per impostazione predefinita sono elencati di seguito.

**Dizionario** di sistema predefinito: alcune lingue includono un dizionario predefinito che contiene la traduzione delle stringhe di sistema. Per ulteriori informazioni, vedere [Traduzione delle stringhe](#translating-the-system-strings)di sistema.

**Gestione** calendario: le pagine di un&#39;applicazione Web possono includere un calendario per l&#39;immissione delle date. Per impostazione predefinita, questo calendario è disponibile in diverse lingue (traduzione di giorni, formato data).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Lingua (simboli)</strong><br /> </td> 
   <td> <strong>Dizionario di sistema predefinito</strong><br /> </td> 
   <td> <strong>Gestione calendario</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Tedesco (de)<br /> </td> 
   <td> yes<br /> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> Inglese (en)<br /> </td> 
   <td> yes<br /> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> Inglese (Stati Uniti) (en_US)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Inglese (Regno Unito) (en_GB)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Arabo (ar)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Cinese (zh)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Coreano (ko)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Danese (da)<br /> </td> 
   <td> yes<br /> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> Spagnolo (es)<br /> </td> 
   <td> yes<br /> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> Estone (et)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Finlandese (fi)<br /> </td> 
   <td> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> Francese (fr)<br /> </td> 
   <td> yes<br /> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> Francese (Belgio) (fr_BE)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Francese (Francia) (fr_FR)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Greco (el)<br /> </td> 
   <td> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> Ebraico (he)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Ungherese (hu)<br /> </td> 
   <td> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> Indonesiano (id)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Irlandese (ga)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Italiano (it)<br /> </td> 
   <td> yes<br /> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> Italiano (Italia) (it_IT)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Italiano (Svizzera) (it_CH)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Giapponese (ja)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Lettone (lv)<br /> </td> 
   <td> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> Lituano (lt)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Maltese (mt)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Olandese (nl)<br /> </td> 
   <td> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> Olandese (Belgio) (nl_BE)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Olandese (Olanda) (nl_NL)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Norvegese (Norvegia) (no_NO)<br /> </td> 
   <td> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> Polacco (pl)<br /> </td> 
   <td> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> Portoghese (pt)<br /> </td> 
   <td> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> Portoghese (Brasile) (pt_BR)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Portoghese (Portogallo) (pt_PT)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Russo (ru)<br /> </td> 
   <td> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> Slovene (sl)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Slovacco (sk)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Svedese (sv)<br /> </td> 
   <td> yes<br /> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> Svedese (Finlandia) (sv_FI)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Svedese (Svezia) (sv_SE)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Ceco (cs)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Thai (th)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Vietnamita (vi)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Waloon (wa)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Per aggiungere lingue diverse da quelle offerte per impostazione predefinita, fare riferimento a [Aggiunta di una lingua di traduzione](#adding-a-translation-language)

## Esempio: visualizzazione di un&#39;applicazione Web in più lingue {#example--displaying-a-web-application-in-several-languages}

Il seguente modulo Web è disponibile in quattro lingue: Inglese, francese, tedesco e spagnolo. Le stringhe di caratteri sono state tutte tradotte tramite la **[!UICONTROL Translation]** scheda del modulo Web. Poiché la lingua predefinita è l’inglese, quando il sondaggio viene pubblicato, usate l’URL standard per visualizzarlo in inglese.

![](assets/s_ncs_admin_survey_trad_sample_fr.png)

Aggiungete **?lang=fr** alla fine dell’URL per visualizzarlo in francese:

>[!NOTE]
>
>L&#39;elenco dei simboli per ciascuna lingua è dettagliato nella sezione [Modifica della lingua](#changing-forms-display-language)di visualizzazione dei moduli.

![](assets/s_ncs_admin_survey_trad_sample_en.png)

È possibile aggiungere **?lang=es** o **?lang=de** per visualizzarlo in spagnolo o tedesco.

>[!NOTE]
>
>Se per questa applicazione Web sono già utilizzati altri parametri, aggiungere **&amp;lang=**.\
>Ad esempio: **https://myserver/webApp/APP34?status=1&amp;lang=en**

## Configurazione avanzata della traduzione {#advanced-translation-configuration}

>[!CAUTION]
>
>Questa sezione è destinata solo agli utenti esperti.

### Traduzione delle stringhe di sistema {#translating-the-system-strings}

Le stringhe di sistema sono stringhe di caratteri predefinite utilizzate da tutte le applicazioni Web. Ad esempio: **[!UICONTROL Next]** , **[!UICONTROL Previous]**, **[!UICONTROL Approve]** pulsanti, **[!UICONTROL Loading]** messaggi ecc. Per impostazione predefinita, alcune lingue contengono un dizionario con traduzioni per queste stringhe. L&#39;elenco delle lingue è dettagliato nella sezione [Modifica della lingua](#changing-forms-display-language)di visualizzazione dei moduli.

Se si traduce l&#39;applicazione Web in una lingua per la quale il dizionario di sistema non è tradotto, verrà visualizzato un messaggio di avviso per segnalare la mancanza di alcune traduzioni.

![](assets/s_ncs_admin_survey_trad_error.png)

Per aggiungere una lingua, procedere come segue:

1. Passate alla struttura  Adobe Campaign e fate clic su **[!UICONTROL Administration > Configuration > Global dictionary > System dictionary]** .
1. Nella sezione superiore della finestra, selezionare la stringa di sistema da tradurre, quindi fare clic **[!UICONTROL Add]** nella sezione inferiore.

   ![](assets/s_ncs_admin_survey_trad_system_translation.png)

1. Selezionate la lingua di traduzione e immettete una traduzione per la stringa. È possibile approvare la traduzione selezionando l&#39; **[!UICONTROL Translation approved]** opzione.

   ![](assets/s_ncs_admin_survey_trad_system_translation2.png)

   >[!NOTE]
   >
   >L&#39;approvazione della traduzione è facoltativa e non bloccherà il processo.

>[!CAUTION]
>
>Non eliminare le stringhe di sistema pronte all&#39;uso.

### Aggiunta di una lingua di traduzione {#adding-a-translation-language}

Per tradurre le applicazioni Web in lingue diverse da quelle predefinite (fare riferimento a [Modifica della lingua](#changing-forms-display-language)di visualizzazione dei moduli), sarà necessario aggiungere una nuova lingua di traduzione.

1. Fare clic sul **[!UICONTROL Administration > Platform > Enumerations]** nodo della struttura di Adobe Campaign  e selezionarlo **[!UICONTROL Languages available for translation]** dall&#39;elenco. L&#39;elenco delle traduzioni disponibili viene visualizzato nella sezione inferiore della finestra.

   ![](assets/s_ncs_admin_survey_trad_new_itemized_list_1.png)

1. Fate clic sul **[!UICONTROL Add]** pulsante, quindi immettete il **[!UICONTROL Internal name]**, **[!UICONTROL Label]** e l’identificatore dell’immagine (flag). Per aggiungere una nuova immagine, contattate l’amministratore.

   ![](assets/s_ncs_admin_survey_trad_new_itemized_list_2.png)

