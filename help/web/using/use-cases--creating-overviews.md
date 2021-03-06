---
product: campaign
title: '"Casi d’uso: creare panoramiche"'
description: '"Casi d’uso: creare panoramiche"'
feature: Web Apps
exl-id: a1ac3aab-dc81-4533-9207-26d5dc5e1c88
source-git-commit: b6f1556cf49492cefaf61c29a058584b0ccee16a
workflow-type: tm+mt
source-wordcount: '947'
ht-degree: 0%

---

# Casi di utilizzo: creare pagine di panoramica{#use-cases-creating-overviews}

![](../../assets/common.svg)

Nell&#39;esempio seguente verranno create applicazioni Web di tipo panoramica per visualizzare tutte le applicazioni Web nel database. Configura i seguenti elementi:

* un filtro sulla cartella (consulta [Aggiunta di un filtro a una cartella](#adding-a-filter-on-a-folder)),
* pulsante per la creazione di una nuova applicazione Web (fare riferimento a [Aggiunta di un pulsante per configurare una nuova applicazione Web](#adding-a-button-to-configure-a-new-web-application)),
* visualizzazione dettagliata di ciascuna voce dell’elenco (fare riferimento a [Aggiunta di dettagli a un elenco](#adding-detail-to-a-list)),
* un filtro per strumento di modifica dei collegamenti (consulta [Creazione di un filtro tramite un editor di collegamenti](#creating-a-filter-using-a-link-editor)),
* un collegamento di aggiornamento (fare riferimento a [Creazione di un collegamento di aggiornamento](#creating-a-refresh-link)).

![](assets/s_ncs_configuration_webapp_overview.png)

## Creazione di un&#39;applicazione Web a pagina singola {#creating-a-single-page-web-application}

1. Creare un singolo **[!UICONTROL Page]** Applicazione web e disabilita transizioni e transizioni in uscita alla pagina successiva.

   ![](assets/s_ncs_configuration_webapp_create.png)

1. Modifica del titolo della pagina.

   Questo titolo verrà visualizzato nell&#39;intestazione della panoramica e nella panoramica dell&#39;applicazione Web.

1. Nelle proprietà dell&#39;applicazione Web, modificare il rendering dell&#39;applicazione selezionando la **[!UICONTROL Single-page Web application]** modello.

   ![](assets/s_ncs_configuration_webapp_rendering.png)

1. Apri **[!UICONTROL Page]** attività dell&#39;applicazione Web e aprire un elenco (**[!UICONTROL Static element > List]**).
1. In **[!UICONTROL Data]** scheda dell’elenco, seleziona il tipo di **[!UICONTROL Web applications]** e **[!UICONTROL Label]** , **[!UICONTROL Creation date]** e **[!UICONTROL Type of application]** colonne di output.
1. In **[!UICONTROL Filter]** sottoscheda , crea il filtro seguente come mostrato di seguito per visualizzare solo le applicazioni web ed escludere i modelli dalla visualizzazione.

   ![](assets/s_ncs_configuration_webapp_filter.png)

1. Chiudi la finestra di configurazione della pagina e fai clic su **[!UICONTROL Preview]**.

   Viene visualizzato l&#39;elenco delle applicazioni Web disponibili nel database.

   ![](assets/s_ncs_configuration_webapp_preview.png)

## Aggiunta di un filtro a una cartella {#adding-a-filter-on-a-folder}

In una panoramica, puoi scegliere di accedere ai dati a seconda della posizione nella struttura di Adobe Campaign. Questo è un filtro su una cartella. Applica il seguente processo per aggiungerlo alla panoramica.

1. Posizionare il cursore sul **[!UICONTROL Page]** nodo dell&#39;applicazione Web e aggiungere un **[!UICONTROL Select folder]** elemento (**[!UICONTROL Advanced controls > Select folder]**).
1. In **[!UICONTROL Storage]** finestra che viene visualizzata, fai clic su **[!UICONTROL Edit variables]** link.
1. Modifica l’etichetta della variabile in base alle tue esigenze.
1. Modifica il nome della variabile con il **cartella** valore.

   >[!NOTE]
   >
   >Il nome della variabile deve corrispondere al nome dell’elemento collegato alla cartella (definito nello schema), ovvero **cartella** in questo caso. È necessario riutilizzare questo nome quando si fa riferimento alla tabella.

1. Applica la **[!UICONTROL XML]** digita nella variabile .

   ![](assets/s_ncs_configuration_webapp_variable_xml.png)

1. Seleziona la **[!UICONTROL Refresh page]** interazione.

   ![](assets/s_ncs_configuration_webapp_variable.png)

1. Posiziona il cursore sull’elenco e **[!UICONTROL Advanced]** , fai riferimento alla variabile creata in precedenza nel **[!UICONTROL Folder filter XPath]** scheda dell’elenco. È necessario utilizzare il nome dell’elemento interessato dal collegamento alla cartella, ovvero **cartella**.

   ![](assets/s_ncs_configuration_webapp_variable002.png)

   >[!NOTE]
   >
   >In questa fase, l&#39;applicazione Web non è nel relativo contesto applicativo, pertanto il filtro non può essere testato sulla cartella.

## Aggiunta di un pulsante per configurare una nuova applicazione Web {#adding-a-button-to-configure-a-new-web-application}

1. Posizionare il cursore sul **[!UICONTROL Page]** e aggiungi un collegamento (**[!UICONTROL Static elements > Link]**).
1. Modifica l’etichetta del collegamento in quanto verrà visualizzata sul pulsante nella panoramica.

   Nel nostro esempio, l’etichetta è **Nuovo**.

1. Inserisci il seguente URL nel campo URL: **xtk://open/?schema=nms:webApp&amp;form=nms:newWebApp**.

   >[!NOTE]
   >
   >**nms:webApp** coincide con lo schema dell&#39;applicazione Web.
   >
   >**nms:newWebApp** coincide con la nuova procedura guidata per la creazione di applicazioni Web.

1. Scegli di visualizzare l’URL nella stessa finestra.
1. Aggiungi l&#39;icona dell&#39;applicazione Web nel campo immagine: **/nms/img/webApp.png**.

   Questa icona apparirà sul **[!UICONTROL New]** pulsante .

1. Invio **pulsante** in **[!UICONTROL Style]** campo .

   Questo stile è indicato nel **[!UICONTROL Single-page Web application]** modello selezionato in precedenza.

   ![](assets/s_ncs_configuration_webapp_link.png)

## Aggiunta di dettagli a un elenco {#adding-detail-to-a-list}

Quando configuri un elenco nella panoramica, puoi scegliere di visualizzare ulteriori dettagli per ogni voce nell’elenco.

1. Posiziona il cursore sull’elemento elenco creato in precedenza.
1. In **[!UICONTROL General]** seleziona la scheda **[!UICONTROL Columns and additional detail]** modalità di visualizzazione nell’elenco a discesa.

   ![](assets/s_ncs_configuration_webapp_detail.png)

1. In **[!UICONTROL Data]** aggiungi la scheda **[!UICONTROL Primary key]** , **[!UICONTROL Internal name]** e **[!UICONTROL Description]** e seleziona la **[!UICONTROL Hidden field]** per ciascuna opzione.

   ![](assets/s_ncs_configuration_webapp_detail002.png)

   In questo modo, queste informazioni saranno visibili solo nei dettagli di ogni voce.

1. In **[!UICONTROL Additional detail]** aggiungi il seguente codice:

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
>L&#39;aggiornamento delle librerie JavaScript richiede cinque minuti sul server. È possibile riavviare il server per evitare di attendere questo ritardo.

## Filtrare e aggiornare l’elenco {#filtering-and-updating-the-list}

In questa sezione verrà creato un filtro per la visualizzazione della panoramica delle applicazioni Web create da un operatore specifico. Questo filtro viene creato con un editor di collegamenti. Dopo aver selezionato un operatore, aggiorna l’elenco per applicare il filtro; questo richiede la creazione di un collegamento di aggiornamento.

Questi due elementi verranno raggruppati nello stesso contenitore per essere raggruppati graficamente nella panoramica.

1. Posizionare il cursore sul **[!UICONTROL Page]** e seleziona **[!UICONTROL Container > Standard]**.
1. Imposta il numero di colonne su **2**, in modo che l’editor dei collegamenti e il collegamento siano uno accanto all’altro.

   ![](assets/s_ncs_configuration_webapp_container.png)

   Per informazioni sul layout degli elementi, consulta [questa sezione](about-web-forms.md).

1. Applica **dottedFilter**.

   Questo stile è indicato nel **[!UICONTROL Single-page Web application]** modello selezionato in precedenza.

   ![](assets/s_ncs_configuration_webapp_container002.png)

### Creazione di un filtro tramite un editor di collegamenti {#creating-a-filter-using-a-link-editor}

1. Posiziona il cursore sul contenitore creato durante lo stadio precedente e inserisci un editor di collegamenti tramite **[!UICONTROL Advanced controls]** menu.
1. Nella finestra di archiviazione che si apre automaticamente, selezionare la **[!UICONTROL Variables]** , quindi fai clic su **[!UICONTROL Edit variables]** collega e crea una variabile XML per filtrare i dati.

   ![](assets/s_ncs_configuration_webapp_variable003.png)

1. Modifica l’etichetta.

   Viene visualizzato accanto al **[!UICONTROL Filter]** nella panoramica.

1. Scegliere la tabella Operatore come schema di applicazione.

   ![](assets/s_ncs_configuration_webapp_linkeditor.png)

1. Posiziona il cursore sull’elemento elenco e crea un filtro tramite il **[!UICONTROL Data > Filter]** scheda:

   * **Espressione:** Chiave esterna del collegamento &quot;Creato da&quot;
   * **Operatore:** è uguale a
   * **Valore:** Variabili (variabili)
   * **Preso in considerazione se:** &#39;$(var2/@id)&#39;!=&#39;&#39;&#39;

   ![](assets/s_ncs_configuration_webapp_filter002.png)

>[!CAUTION]
>
>L&#39;utente dell&#39;applicazione Web deve essere un operatore identificato con i diritti Adobe Campaign appropriati per accedere alle informazioni. Questo tipo di configurazione non funzionerà per le applicazioni Web anonime.

### Creazione di un collegamento di aggiornamento {#creating-a-refresh-link}

1. Posizionare il cursore sul contenitore e inserire un **[!UICONTROL Link]** tramite **[!UICONTROL Static elements]** menu.
1. Modifica l’etichetta.
1. Seleziona **[!UICONTROL Refresh data in a list]**.
1. Aggiungi l’elenco creato in precedenza.

   ![](assets/s_ncs_configuration_webapp_refreshlink.png)

1. Aggiungi l’icona di aggiornamento nel **[!UICONTROL Image]** campo: **/xtk/img/refresh.png**.
1. Utilizzando le frecce di ordinamento, riorganizzare i vari elementi dell&#39;applicazione Web come mostrato di seguito.

   ![](assets/s_ncs_configuration_webapp_orderelements.png)

L&#39;applicazione Web è ora configurata. Puoi fare clic su **[!UICONTROL Preview]** scheda per visualizzarlo in anteprima.

![](assets/s_ncs_configuration_webapp_result.png)
