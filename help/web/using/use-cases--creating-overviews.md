---
solution: Campaign Classic
product: campaign
title: '"Casi di utilizzo: creazione di panoramiche"'
description: '"Casi di utilizzo: creazione di panoramiche"'
audience: web
content-type: reference
topic-tags: web-applications
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '947'
ht-degree: 1%

---


# Casi di utilizzo: creazione di panoramiche{#use-cases-creating-overviews}

Nell&#39;esempio seguente verranno create applicazioni Web di tipo panoramica per visualizzare tutte le applicazioni Web nel database. Configurate i seguenti elementi:

* un filtro nella cartella (fare riferimento a [Aggiunta di un filtro in una cartella](#adding-a-filter-on-a-folder)),
* un pulsante per la creazione di una nuova applicazione Web (fare riferimento a [Aggiunta di un pulsante per configurare una nuova applicazione Web](#adding-a-button-to-configure-a-new-web-application)),
* visualizzazione dei dettagli per ciascuna voce dell&#39;elenco (fare riferimento a [Aggiunta di dettagli a un elenco](#adding-detail-to-a-list)),
* un filtro per strumento di modifica del collegamento (fare riferimento a [Creazione di un filtro tramite un editor di collegamenti](#creating-a-filter-using-a-link-editor)),
* un collegamento di aggiornamento (fare riferimento a [Creazione di un collegamento di aggiornamento](#creating-a-refresh-link)).

![](assets/s_ncs_configuration_webapp_overview.png)

## Creazione di un&#39;applicazione Web a pagina singola {#creating-a-single-page-web-application}

1. Create una singola applicazione Web **[!UICONTROL Page]** e disattivate le transizioni in uscita e le transizioni nella pagina successiva.

   ![](assets/s_ncs_configuration_webapp_create.png)

1. Modifica del titolo della pagina.

   Questo titolo verrà visualizzato nell’intestazione della panoramica e nella panoramica dell’applicazione Web.

1. Nelle proprietà dell&#39;applicazione Web, modificare il rendering dell&#39;applicazione selezionando il modello **[!UICONTROL Single-page Web application]**.

   ![](assets/s_ncs_configuration_webapp_rendering.png)

1. Aprire l&#39;attività **[!UICONTROL Page]** dell&#39;applicazione Web e aprire un elenco (**[!UICONTROL Static element > List]**).
1. Nella scheda **[!UICONTROL Data]** dell&#39;elenco, selezionare il tipo di documento **[!UICONTROL Web applications]** e le colonne di output **[!UICONTROL Label]**, **[!UICONTROL Creation date]** e **[!UICONTROL Type of application]**.
1. Nella scheda secondaria **[!UICONTROL Filter]**, creare il filtro seguente come illustrato di seguito per visualizzare solo le applicazioni Web ed escludere i modelli dalla visualizzazione.

   ![](assets/s_ncs_configuration_webapp_filter.png)

1. Chiudete la finestra di configurazione della pagina e fate clic su **[!UICONTROL Preview]**.

   Viene visualizzato l&#39;elenco delle applicazioni Web disponibili nel database.

   ![](assets/s_ncs_configuration_webapp_preview.png)

## Aggiunta di un filtro a una cartella {#adding-a-filter-on-a-folder}

In una panoramica, potete scegliere di accedere ai dati a seconda della posizione nella struttura  Adobe Campaign. Questo è un filtro in una cartella. Per aggiungere la panoramica, effettuate le seguenti operazioni.

1. Posizionare il cursore sul nodo **[!UICONTROL Page]** dell&#39;applicazione Web e aggiungere un elemento **[!UICONTROL Select folder]** (**[!UICONTROL Advanced controls > Select folder]**).
1. Nella finestra **[!UICONTROL Storage]** visualizzata, fare clic sul collegamento **[!UICONTROL Edit variables]**.
1. Modificate l’etichetta della variabile in base alle vostre esigenze.
1. Modificate il nome della variabile con il valore **folder**.

   >[!NOTE]
   >
   >Il nome della variabile deve corrispondere al nome dell’elemento collegato alla cartella (definito nello schema), vale a dire **cartella** in questo caso. È necessario riutilizzare questo nome quando si fa riferimento alla tabella.

1. Applicate il tipo **[!UICONTROL XML]** alla variabile.

   ![](assets/s_ncs_configuration_webapp_variable_xml.png)

1. Selezionare l&#39;interazione **[!UICONTROL Refresh page]**.

   ![](assets/s_ncs_configuration_webapp_variable.png)

1. Posizionare il cursore sull&#39;elenco e nella scheda **[!UICONTROL Advanced]** fare riferimento alla variabile creata in precedenza nella scheda **[!UICONTROL Folder filter XPath]** dell&#39;elenco. Dovete usare il nome dell’elemento interessato dal collegamento della cartella, ovvero **cartella**.

   ![](assets/s_ncs_configuration_webapp_variable002.png)

   >[!NOTE]
   >
   >In questa fase, l&#39;applicazione Web non è nel relativo contesto dell&#39;applicazione, pertanto il filtro non può essere testato sulla cartella.

## Aggiunta di un pulsante per configurare una nuova applicazione Web {#adding-a-button-to-configure-a-new-web-application}

1. Posizionare il cursore sull&#39;elemento **[!UICONTROL Page]** e aggiungere un collegamento (**[!UICONTROL Static elements > Link]**).
1. Modificate l&#39;etichetta del collegamento in quanto apparirà sul pulsante nella panoramica.

   Nel nostro esempio, l&#39;etichetta è **New**.

1. Inserite il seguente URL nel campo URL: **xtk://open/?schema=nms:webApp&amp;form=nms:newWebApp**.

   >[!NOTE]
   >
   >**nms:** webAppstessa con lo schema dell&#39;applicazione Web.
   >
   >**nms:** newWebAppcoincide con la nuova procedura guidata di creazione dell&#39;applicazione Web.

1. Scegliete di visualizzare l’URL nella stessa finestra.
1. Aggiungere l&#39;icona dell&#39;applicazione Web nel campo immagine: **/nms/img/webApp.png**.

   Questa icona verrà visualizzata sul pulsante **[!UICONTROL New]**.

1. Immettere **button** nel campo **[!UICONTROL Style]**.

   Questo stile è indicato nel modello **[!UICONTROL Single-page Web application]** selezionato in precedenza.

   ![](assets/s_ncs_configuration_webapp_link.png)

## Aggiunta di dettagli a un elenco {#adding-detail-to-a-list}

Quando configurate un elenco nella panoramica, potete scegliere di visualizzare ulteriori dettagli per ogni voce dell’elenco.

1. Posizionare il cursore sull’elemento elenco creato in precedenza.
1. Nella scheda **[!UICONTROL General]**, selezionare la modalità di visualizzazione **[!UICONTROL Columns and additional detail]** nell&#39;elenco a discesa.

   ![](assets/s_ncs_configuration_webapp_detail.png)

1. Nella scheda **[!UICONTROL Data]**, aggiungere la colonna **[!UICONTROL Primary key]** , **[!UICONTROL Internal name]** e **[!UICONTROL Description]** e selezionare l&#39;opzione **[!UICONTROL Hidden field]** per ciascuna colonna.

   ![](assets/s_ncs_configuration_webapp_detail002.png)

   In questo modo, queste informazioni saranno visibili solo nei dettagli di ogni voce.

1. Nella scheda **[!UICONTROL Additional detail]** aggiungete il codice seguente:

   ```
   <div class="detailBox">
     <div class="actionBox">
       <span class="action"><img src="/xtk/img/fileEdit.png"/><a title="Open" class="linkAction" href="xtk://open/?schema=nms:webApp&form=nms:webApp&pk=
       <%=webApp.id%>">Open...</a></span>
       <% 
       if( webApp.@appType == 1 ) { //survey
       %>
       <span class="action"><img src="/xtk/img/report.png"/><a target="_blank" title="Reports" class="linkAction" href="/xtk/report.jssp?_context=selection&
         _schema=nms:webApp&_selection=<%=webApp.@id%>
         &__sessiontoken=<%=document.controller.getSessionToken()%>">Reports</a></span>
       <% 
       } 
       %>
     </div>
     <div>
       Internal name: <%= webApp.@internalName %>
     </div>
     <%
     if( webApp.desc != "" )
     {
     %>
     <div>
       Description: <%= webApp.desc %>
     </div>
     <% 
     } 
     %>
   </div>
   ```

>[!NOTE]
>
>L&#39;aggiornamento delle librerie JavaScript richiede cinque minuti. È possibile riavviare il server per evitare di attendere questo ritardo.

## Filtro e aggiornamento dell&#39;elenco {#filtering-and-updating-the-list}

In questa sezione verrà creato un filtro per visualizzare la panoramica delle applicazioni Web create da un operatore specifico. Questo filtro viene creato con un editor di collegamenti. Dopo aver selezionato un operatore, aggiornare l&#39;elenco per applicare il filtro; questo richiede la creazione di un collegamento di aggiornamento.

Questi due elementi saranno raggruppati nello stesso contenitore per essere raggruppati graficamente nella panoramica.

1. Posizionare il cursore sull&#39;elemento **[!UICONTROL Page]** e selezionare **[!UICONTROL Container > Standard]**.
1. Impostate il numero di colonne su **2**, in modo che l&#39;editor di collegamenti e il collegamento si trovino l&#39;uno accanto all&#39;altro.

   ![](assets/s_ncs_configuration_webapp_container.png)

   Per informazioni sul layout degli elementi, consultare [questa sezione](../../web/using/about-web-forms.md).

1. Applicare **dottedFilter**.

   Questo stile è indicato nel modello **[!UICONTROL Single-page Web applicatio]** n selezionato in precedenza.

   ![](assets/s_ncs_configuration_webapp_container002.png)

### Creazione di un filtro tramite un editor di collegamenti {#creating-a-filter-using-a-link-editor}

1. Posizionare il cursore sul contenitore creato durante la fase precedente e inserire un editor di collegamenti tramite il menu **[!UICONTROL Advanced controls]**.
1. Nella finestra di memorizzazione che si apre automaticamente, selezionare l&#39;opzione **[!UICONTROL Variables]**, quindi fare clic sul collegamento **[!UICONTROL Edit variables]** e creare una variabile XML per filtrare i dati.

   ![](assets/s_ncs_configuration_webapp_variable003.png)

1. Modificare l&#39;etichetta.

   Verrà visualizzato accanto al campo **[!UICONTROL Filter]** nella panoramica.

1. Scegliere la tabella Operatore come schema di applicazione.

   ![](assets/s_ncs_configuration_webapp_linkeditor.png)

1. Posizionare il cursore sull&#39;elemento elenco e creare un filtro tramite la scheda **[!UICONTROL Data > Filter]**:

   * **Espressione:chiave** esterna del collegamento &#39;Creato da&#39;
   * **Operatore:** uguale a
   * **Valore:** Variabili (variabili)
   * **Preso in considerazione se:** &#39;$(var2/@id)&#39;!=&#39;&#39;

   ![](assets/s_ncs_configuration_webapp_filter002.png)

>[!CAUTION]
>
>L&#39;utente dell&#39;applicazione Web deve essere un operatore identificato con i diritti  Adobe Campaign appropriati per accedere alle informazioni. Questo tipo di configurazione non funzionerà per le applicazioni Web anonime.

### Creazione di un collegamento di aggiornamento {#creating-a-refresh-link}

1. Posizionare il cursore sul contenitore e inserire un **[!UICONTROL Link]** tramite il menu **[!UICONTROL Static elements]**.
1. Modificare l&#39;etichetta.
1. Seleziona **[!UICONTROL Refresh data in a list]**.
1. Aggiungete l’elenco creato in precedenza.

   ![](assets/s_ncs_configuration_webapp_refreshlink.png)

1. Aggiungete l&#39;icona di aggiornamento nel campo **[!UICONTROL Image]**: **/xtk/img/refresh.png**.
1. Utilizzando le frecce di ordinamento, riorganizzare i vari elementi dell&#39;applicazione Web come mostrato di seguito.

   ![](assets/s_ncs_configuration_webapp_orderelements.png)

L&#39;applicazione Web è ora configurata. È possibile fare clic sulla scheda **[!UICONTROL Preview]** per visualizzarla in anteprima.

![](assets/s_ncs_configuration_webapp_result.png)

