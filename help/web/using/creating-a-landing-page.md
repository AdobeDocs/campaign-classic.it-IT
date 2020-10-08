---
title: Creazione di una pagina di destinazione
seo-title: Creazione di una pagina di destinazione
description: Creazione di una pagina di destinazione
seo-description: null
page-status-flag: never-activated
uuid: fc0e9749-f44e-4aa0-bdfa-6f44ba570bea
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: editing-html-content
discoiquuid: 5f1e5886-628f-4c9e-80c1-d82feec23e8c
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 3%

---


# Creazione di una pagina di destinazione{#creating-a-landing-page}

## Creazione di pagine di destinazione {#about-landing-pages-creation}

Questo caso d’uso mostra l’utilizzo dell’editor digitale per creare una pagina di destinazione dalla console Adobe Campaign .

Prima di iniziare a configurare la pagina di destinazione in  Adobe Campaign, accertatevi di disporre di **uno o più modelli** per rappresentare le pagine HTML.

Lo scopo principale di questo caso di utilizzo è far corrispondere i campi del modulo Pagina di destinazione ai campi interni di  Adobe Campaign utilizzando le funzioni di DCE.

## Creating the landing page {#creating-the-landing-page}

Per creare una nuova applicazione Web di tipo Pagina di destinazione, procedere come segue:

1. Vai alla **[!UICONTROL Campaigns]** scheda e fai clic sul **[!UICONTROL Web application]** collegamento, quindi fai clic sul **[!UICONTROL Create]** pulsante.
1. Selezionate il **[!UICONTROL New landing page]** modello e immettete un&#39;etichetta, quindi fate clic su **[!UICONTROL Save]**.

   ![](assets/dce_uc1_newlandingpage.png)

1. Fate clic sulla **[!UICONTROL Edit]** scheda.
1. Eliminate l&#39;attività **End** .
1. Aggiungete un&#39; **[!UICONTROL Page]** attività dopo l&#39; **[!UICONTROL Storage]** attività.
1. Modificate l&#39;attività **Pagina 2** , quindi deselezionate l&#39; **[!UICONTROL Activate outbound transitions]** opzione nella **[!UICONTROL Properties]** scheda.

   ![](assets/dce_uc1_transition.png)

1. Salvare le modifiche.

Verrà quindi visualizzata la seguente sequenza:

![](assets/dce_uc1_edition_activity.png)

>[!NOTE]
>
>Per ulteriori informazioni sulla creazione di un&#39;applicazione Web, consultare [questa sezione](../../web/using/creating-a-new-web-application.md).

## Passaggio 1 - Selezione e caricamento di modelli {#step-1---selecting-and-loading-templates}

In questa sezione verrà illustrato come **importare il contenuto** HTML per ciascuna pagina dell&#39;applicazione Web.

Un modello deve contenere:

* un file **HTML** (obbligatorio)
* uno o più file **CSS** (facoltativo)
* una o più **immagini** (facoltativo)

Per caricare il modello sulla prima pagina, effettuate le seguenti operazioni:

1. Aprire la prima **[!UICONTROL Page]** attività dell&#39;applicazione Web.
1. Selezionate **[!UICONTROL From a file]** per recuperare il modello di contenuto.

   ![](assets/dce_uc1_selectmodel.png)

1. Selezionate il file HTML da utilizzare.
1. Fate clic su **Apri** per avviare l’importazione.

   Durante il caricamento, viene visualizzato l&#39;elenco dei file condivisi. Il sistema di importazione verifica che siano presenti tutti i file collegati al codice HTML selezionato (CSS, immagini ecc.).

   Fate clic sul **[!UICONTROL Close]** pulsante al termine dell’importazione.

   ![](assets/dce_uc1_import.png)

   >[!CAUTION]
   >
   >Prima di chiudere è necessario attendere il messaggio seguente: **[!UICONTROL The external resources have been successfully published]** .

1. Fate clic sulla **[!UICONTROL Properties]** scheda.
1. Inserite un’ **etichetta** per ciascuna pagina (ad esempio: Pagina 1= Raccogli, Pagina 2=Grazie).

   ![](assets/dce_uc1_pagelabel.png)

Applicare questi passaggi per ogni pagina inserita nell&#39;applicazione Web.

>[!CAUTION]
>
>**DCE esegue il codice JavaScript per la pagina HTML caricata.** Errori JavaScript nel modello HTML che possono essere visualizzati nell&#39;interfaccia Adobe Campaign . Questi errori non sono correlati all&#39;editor. Per verificare che non ci siano errori nei file importati, si consiglia di testarli in un browser (Internet Explorer / Firefox / Chrome) prima di importare i file in DCE.

## Passaggio 2 - Configurazione del contenuto {#step-2---configuring-the-content}

In questa sezione, regoleremo il contenuto importato e collegheremo i campi del database al modulo della pagina Web. L&#39;applicazione Web creata in precedenza è:

![](assets/dce_uc1_lp_enchainement.png)

### Modifica dei contenuti {#modifying-content}

Cominciamo modificando i colori della pagina. Per eseguire questa operazione:

1. Aprite la **[!UICONTROL Collection]** pagina.
1. Fate clic sullo sfondo.
1. Fare clic sul colore **** Sfondo sul lato destro.
1. Selezionare un nuovo colore di sfondo.
1. Fate clic su **OK** per confermare la modifica.

   ![](assets/dce_uc1_changecolor.png)

1. Applicare gli stessi processi per modificare il colore del pulsante

   ![](assets/dce_uc1_finalcolor.png)

### Collegamento di campi modulo {#linking-form-fields}

Collegheremo i campi della pagina a quelli del database, per salvare le informazioni fornite.

1. Selezionare un campo modulo.
1. Modificate la **[!UICONTROL Field]** sezione a destra dell’editor.
1. Selezionare il campo del database che si desidera collegare al campo selezionato.

   ![](assets/dce_uc1_mapping.png)

1. Ripetete questa procedura per ciascun campo della pagina.

È possibile rendere obbligatorio un campo: ad esempio, fare clic sul **[!UICONTROL Email]** campo e attivare l&#39;opzione **Obbligatorio** .

![](assets/dce_uc1_fieldmandatory.png)

### Creazione di un collegamento alla pagina successiva {#creating-a-link-to-the-next-page}

Questo passaggio è obbligatorio perché consentirà all&#39;applicazione Web di determinare la sequenza dei passaggi successivi: Salvataggio dei dati raccolti nel database e visualizzazione della pagina successiva (pagina di **ringraziamento** ).

1. Fate clic sul **[!UICONTROL Send it!]** pulsante della **[!UICONTROL Collection]** pagina.
1. Fate clic sul menu a **[!UICONTROL Action]** discesa.
1. Selezionate l’ **[!UICONTROL Next page]** azione.

   ![](assets/dce_uc1_actionbouton.png)

### Inserimento di un campo di personalizzazione {#inserting-a-personalization-field}

Questo passaggio consente di personalizzare la pagina di ringraziamento. Per eseguire questa operazione:

1. Aprite la **[!UICONTROL Thank you]** pagina.
1. Posizionare il cursore in un&#39;area di testo in cui si desidera inserire il nome del destinatario.
1. Selezionate **[!UICONTROL Personalization field]** nel **[!UICONTROL Insert]** menu della barra degli strumenti.
1. Selezionate il nome.

   ![](assets/dce_uc1_persochamp.png)

Il campo di personalizzazione ha uno sfondo giallo nell’editor.

![](assets/dce_uc1_edit_champperso.png)

## Passaggio 3 - Pubblicazione del contenuto {#step-3---publishing-content}

Il contenuto viene pubblicato dal dashboard dell&#39;applicazione Web. Fare clic sul **[!UICONTROL Publish]** pulsante per eseguirlo.

![](assets/dce_uc1_pub_dashboard.png)

Durante la pubblicazione viene visualizzato un registro. Il sistema di pubblicazione analizza tutto il contenuto trovato nell&#39;applicazione Web

![](assets/dce_uc1_pub_dashboard_journal.png)

>[!NOTE]
>
>Nel registro delle pubblicazioni, gli avvisi e gli errori sono ordinati per attività.

Il modulo è ora disponibile: il relativo URL è accessibile nel dashboard dell’applicazione e può essere inviato ai destinatari.
