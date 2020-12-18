---
solution: Campaign Classic
product: campaign
title: Introduzione ai moduli web
description: Guida introduttiva ai moduli Web in Campaign
audience: web
content-type: reference
topic-tags: web-forms
translation-type: tm+mt
source-git-commit: e76eb171aac1f7088ff8647f99c928ec349b24fc
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 5%

---


# Introduzione ai moduli web{#about-web-forms}

 Adobe Campaign integra un modulo grafico per definire e pubblicare moduli Web per creare pagine contenenti campi di input e di selezione e che possono includere dati nel database. Consente di progettare e pubblicare pagine Web a cui gli utenti possono accedere per visualizzare o immettere informazioni.

Questo capitolo descrive la creazione e la gestione di moduli Web, come gestire campi e pagine, nonché le modalità di archiviazione e salvataggio.

>[!CAUTION]
>
>Per motivi di privacy, si consiglia di utilizzare HTTPS per tutte le risorse esterne.

## Passaggi per la creazione di un modulo Web {#steps-for-creating-a-web-form}

Questo capitolo descrive i passaggi necessari per progettare un modulo di tipo **webForm** in  Adobe Campaign, nonché le opzioni e le configurazioni disponibili.  Adobe Campaign consente di rendere questo modulo Web disponibile agli utenti e di raccogliere e archiviare le risposte nel database.

>[!CAUTION]
>
>Quando si configurano applicazioni Web e moduli Web, è necessaria una risoluzione verticale minima di 900 pixel (ad esempio: 1600x900).

I moduli Web sono accessibili dal menu Applicazioni Web della scheda **Campagne**. Nella struttura  di Adobe Campaign, sono raggruppati sotto il nodo **[!UICONTROL Resources > Online > Web Applications]**.

Per creare un modulo Web, fare clic sul pulsante **[!UICONTROL Create]** sopra l&#39;elenco delle applicazioni Web.

![](assets/webapp_create_new.png)

Selezionare il modello di modulo Web ( **[!UICONTROL newWebForm]** per impostazione predefinita).

![](assets/s_ncs_admin_survey_select_template.png)

Viene visualizzata la dashboard del modulo.

![](assets/webapp_empty_dashboard.png)

La scheda **[!UICONTROL Edit]** consente di creare il contenuto.

![](assets/webapp_edit_tab.png)

Per definire la configurazione e il contenuto del modulo Web, procedere come segue:

* Per iniziare, create le pagine e i controlli richiesti: campi di input, elenchi a discesa, contenuto HTML, ecc.

   Questo passaggio è illustrato di seguito.

* Definire la sequenza delle pagine e condizionare la visualizzazione.

   Questo passaggio è dettagliato nella sezione [Definizione della sequenza delle pagine dei moduli Web](../../web/using/defining-web-forms-page-sequencing.md).

* Se necessario, traducete il contenuto.

   Questo passaggio è dettagliato in [Traduzione di un modulo Web](../../web/using/translating-a-web-form.md).

## Informazioni sulla progettazione di moduli Web {#about-web-forms-designing}

Le pagine del modulo vengono create tramite un editor specifico che consente di definire e configurare le aree di input (testo), i campi di selezione (elenchi, caselle di controllo, ecc.) ed elementi statici (immagini, contenuti HTML, ecc.). Possono essere raggruppati in contenitori e il loro layout modificato in base alle vostre esigenze (per ulteriori informazioni, consultate [Creazione di contenitori](../../web/using/defining-web-forms-layout.md#creating-containers)).

Nelle sezioni seguenti viene illustrato come definire il contenuto e il layout delle schermate dei moduli:

* [Aggiunta di campi a un modulo web](../../web/using/adding-fields-to-a-web-form.md),
* [Inserimento di contenuto](../../web/using/static-elements-in-a-web-form.md#inserting-html-content) HTML,
* [Elementi statici in un modulo web](../../web/using/static-elements-in-a-web-form.md),
* [Definizione del layout dei moduli web](../../web/using/defining-web-forms-layout.md).

>[!NOTE]
>
>* Durante la progettazione della pagina, potete visualizzare il rendering finale nella scheda **[!UICONTROL Preview]**. Per visualizzare le modifiche, salvare prima il modulo. Eventuali errori vengono visualizzati nella scheda **[!UICONTROL Log]**.
>* Per verificare che la visualizzazione della pagina e l&#39;archiviazione delle informazioni siano effettuate nella sequenza appropriata, attivare la modalità di debug nel modulo Web. A questo scopo, andate alla sottoscheda **[!UICONTROL Preview]** e selezionate la casella **[!UICONTROL Enable debug mode]**: tutte le informazioni raccolte e gli eventuali errori di esecuzione saranno visualizzati nella parte inferiore di ogni pagina.

>



### Utilizzo delle icone nella barra degli strumenti {#using-the-icons-in-the-toolbar}

È inoltre possibile utilizzare le icone nella barra degli strumenti o fare clic con il pulsante destro del mouse per inserire una zona di input.

![](assets/s_ncs_admin_webform_add_selection.png)

In questo caso, iniziare selezionando il tipo di campo da aggiungere e la modalità di memorizzazione delle risposte.

![](assets/s_ncs_admin_webform_select_storage.png)

Fare clic su **[!UICONTROL Ok]** per approvare la selezione.

![](assets/s_ncs_admin_webform_confirm_storage.png)

