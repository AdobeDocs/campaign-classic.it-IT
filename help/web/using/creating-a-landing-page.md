---
product: campaign
title: Creazione di una pagina di destinazione
description: Creazione di una pagina di destinazione
audience: web
content-type: reference
topic-tags: editing-html-content
exl-id: 71c737c2-b0d6-4ae8-a5df-28a08dff82d7
source-git-commit: 360fd1ed8970c17c0687eaca0a4c1960d6f5838c
workflow-type: tm+mt
source-wordcount: '724'
ht-degree: 3%

---

# Creazione di una pagina di destinazione{#creating-a-landing-page}

## Informazioni sulla creazione di pagine di destinazione {#about-landing-pages-creation}

Questo caso d’uso mostra l’utilizzo dell’editor digitale per creare una pagina di destinazione dalla console Adobe Campaign.

Prima di iniziare a configurare la pagina di destinazione in Adobe Campaign, assicurati di disporre di **uno o più modelli** per rappresentare le pagine HTML.

Lo scopo principale di questo caso d’uso è quello di far corrispondere i campi del modulo Pagina di destinazione con i campi interni di Adobe Campaign che utilizzano le funzioni di DCE.

## Creazione della pagina di destinazione {#creating-the-landing-page}

Per creare una nuova applicazione Web di tipo Pagina di destinazione, procedere come segue:

1. Vai alla scheda **[!UICONTROL Campaigns]** e fai clic sul collegamento **[!UICONTROL Web application]** , quindi fai clic sul pulsante **[!UICONTROL Create]** .
1. Seleziona il modello **[!UICONTROL New landing page]** e inserisci un’etichetta, quindi fai clic su **[!UICONTROL Save]**.

   ![](assets/dce_uc1_newlandingpage.png)

1. Fai clic sulla scheda **[!UICONTROL Edit]** .
1. Elimina l&#39;attività **End** .
1. Aggiungi un’attività **[!UICONTROL Page]** dopo l’attività **[!UICONTROL Storage]** .
1. Modifica l&#39;attività **Pagina 2** , quindi deseleziona l&#39;opzione **[!UICONTROL Activate outbound transitions]** nella scheda **[!UICONTROL Properties]** .

   ![](assets/dce_uc1_transition.png)

1. Salva le modifiche.

Verrà quindi visualizzata la seguente sequenza:

![](assets/dce_uc1_edition_activity.png)

>[!NOTE]
>
>Per ulteriori informazioni sulla creazione di un&#39;applicazione Web, consulta [questa sezione](creating-a-new-web-application.md).

## Passaggio 1: selezionare e caricare i modelli {#step-1---selecting-and-loading-templates}

In questa sezione verrà illustrato come **importare contenuto HTML** per ogni pagina dell&#39;applicazione Web.

Un modello deve contenere:

* un file **HTML** (obbligatorio)
* uno o più file **CSS** (facoltativo)
* una o più **immagini** (facoltativo)

Per caricare il modello sulla prima pagina, esegui i seguenti passaggi:

1. Apri la prima **[!UICONTROL Page]** attività dell&#39;applicazione Web.
1. Seleziona **[!UICONTROL From a file]** per recuperare il modello di contenuto.

   ![](assets/dce_uc1_selectmodel.png)

1. Selezionare il file HTML da utilizzare.
1. Fai clic su **Apri** per avviare l&#39;importazione.

   Durante il caricamento viene visualizzato l&#39;elenco dei file condivisi. Il sistema di importazione verifica che siano presenti tutti i file collegati all’HTML selezionato (CSS, immagini, ecc.).

   Al termine dell’importazione, fai clic sul pulsante **[!UICONTROL Close]** .

   ![](assets/dce_uc1_import.png)

   >[!CAUTION]
   >
   >È necessario attendere fino a quando non viene visualizzato il seguente messaggio prima di chiudere: **[!UICONTROL The external resources have been successfully published]** .

1. Fai clic sulla scheda **[!UICONTROL Properties]** .
1. Immetti un **etichetta** per ogni pagina (ad esempio: Pagina 1= Raccogli, Pagina 2=Grazie).

   ![](assets/dce_uc1_pagelabel.png)

Applicare questi passaggi per ogni pagina inserita nell&#39;applicazione Web.

>[!CAUTION]
>
>**Il DCE esegue il codice JavaScript per la pagina HTML caricata.** Errori JavaScript nel modello HTML che possono apparire nell&#39;interfaccia Adobe Campaign. Questi errori non sono correlati all&#39;editor. Per verificare che non ci siano errori nei file importati, si consiglia di testarli in un browser (Internet Explorer / Firefox / Chrome) prima di importare i file nel DCE.

## Passaggio 2: configurazione del contenuto {#step-2---configuring-the-content}

In questa sezione verrà regolato il contenuto importato e verranno collegati i campi del database al modulo della pagina web. L&#39;applicazione Web creata in precedenza è:

![](assets/dce_uc1_lp_enchainement.png)

### Modifica del contenuto {#modifying-content}

Cominciamo modificando i colori della pagina. Per eseguire questa operazione:

1. Apri la pagina **[!UICONTROL Collection]** .
1. Fai clic sullo sfondo.
1. Fare clic su **Colore sfondo** sul lato destro.
1. Selezionare un nuovo colore di sfondo.
1. Fare clic su **OK** per confermare la modifica.

   ![](assets/dce_uc1_changecolor.png)

1. Applicare gli stessi processi per modificare il colore del pulsante

   ![](assets/dce_uc1_finalcolor.png)

### Collegamento di campi modulo {#linking-form-fields}

Collegheremo i campi della pagina a quelli del database per salvare le informazioni fornite.

1. Selezionare un campo modulo.
1. Modifica la sezione **[!UICONTROL Field]** sul lato destro dell’editor.
1. Selezionare il campo del database che si desidera collegare al campo selezionato.

   ![](assets/dce_uc1_mapping.png)

1. Ripetere questa procedura per ogni campo della pagina.

È possibile rendere obbligatorio un campo: ad esempio, fai clic sul campo **[!UICONTROL Email]** e abilita l&#39;opzione **Obbligatorio**.

![](assets/dce_uc1_fieldmandatory.png)

### Creazione di un collegamento alla pagina successiva {#creating-a-link-to-the-next-page}

Questo passaggio è obbligatorio perché consentirà all&#39;applicazione Web di determinare la sequenza dei passaggi successivi: Salvataggio dei dati raccolti nel database e visualizzazione della pagina successiva (**Grazie** pagina).

1. Selezionare il pulsante **[!UICONTROL Send it!]** della pagina **[!UICONTROL Collection]**.
1. Fai clic sul menu a discesa **[!UICONTROL Action]** .
1. Seleziona l’azione **[!UICONTROL Next page]** .

   ![](assets/dce_uc1_actionbouton.png)

### Inserimento di un campo di personalizzazione {#inserting-a-personalization-field}

Questo passaggio ti consente di personalizzare la pagina di ringraziamento. Per eseguire questa operazione:

1. Apri la pagina **[!UICONTROL Thank you]** .
1. Posizionare il cursore in un&#39;area di testo in cui si desidera inserire il nome del destinatario.
1. Selezionare **[!UICONTROL Personalization field]** nel menu **[!UICONTROL Insert]** della barra degli strumenti.
1. Selezionare il nome.

   ![](assets/dce_uc1_persochamp.png)

Il campo di personalizzazione ha uno sfondo giallo nell’editor.

![](assets/dce_uc1_edit_champperso.png)

## Passaggio 3 - Pubblicazione del contenuto {#step-3---publishing-content}

Il contenuto viene pubblicato dal dashboard dell&#39;applicazione Web. Fai clic sul pulsante **[!UICONTROL Publish]** per eseguirlo.

![](assets/dce_uc1_pub_dashboard.png)

Durante la pubblicazione viene visualizzato un registro. Il sistema di pubblicazione analizza tutti i contenuti presenti nell&#39;applicazione Web

![](assets/dce_uc1_pub_dashboard_journal.png)

>[!NOTE]
>
>Nel registro della pubblicazione gli avvisi e gli errori vengono ordinati per attività.

Il modulo è ora disponibile: il relativo URL è accessibile nel dashboard dell’applicazione e può essere inviato ai destinatari.
