---
product: campaign
title: Creare una pagina di destinazione
description: Creare una pagina di destinazione
feature: Landing Pages
exl-id: 71c737c2-b0d6-4ae8-a5df-28a08dff82d7
source-git-commit: 4ff86349d6b8966273585bf2a1ea0d785a7e87cb
workflow-type: tm+mt
source-wordcount: '721'
ht-degree: 3%

---

# Creare una pagina di destinazione{#creating-a-landing-page}

![](../../assets/common.svg)

## Informazioni sulla creazione di pagine di destinazione {#about-landing-pages-creation}

Questo caso d’uso mostra l’utilizzo dell’editor digitale per creare una pagina di destinazione dalla console Adobe Campaign.

Prima di iniziare a configurare la pagina di destinazione in Adobe Campaign, assicurati di disporre di **uno o più modelli** per rappresentare le pagine di HTML.

Lo scopo principale di questo caso d’uso è quello di far corrispondere i campi del modulo Pagina di destinazione con i campi interni di Adobe Campaign che utilizzano le funzioni di DCE.

## Creazione della pagina di destinazione {#creating-the-landing-page}

Per creare una nuova applicazione Web di tipo Pagina di destinazione, procedere come segue:

1. Vai a **[!UICONTROL Campaigns]** e fai clic su **[!UICONTROL Web application]** fai clic sul collegamento **[!UICONTROL Create]** pulsante .
1. Seleziona la **[!UICONTROL New landing page]** e immetti un’etichetta, quindi fai clic su **[!UICONTROL Save]**.

   ![](assets/dce_uc1_newlandingpage.png)

1. Fai clic sul pulsante **[!UICONTROL Edit]** scheda .
1. Elimina **Fine** attività.
1. Aggiungi un **[!UICONTROL Page]** dopo **[!UICONTROL Storage]** attività.
1. Modifica le **Pagina 2** quindi deseleziona **[!UICONTROL Activate outbound transitions]** in **[!UICONTROL Properties]** scheda .

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

* un **HTML** file (obbligatorio)
* uno o più **CSS** file (facoltativo)
* uno o più **immagini** (facoltativo)

Per caricare il modello sulla prima pagina, esegui i seguenti passaggi:

1. Apri il primo **[!UICONTROL Page]** attività dell&#39;applicazione Web.
1. Seleziona **[!UICONTROL From a file]** per recuperare il modello di contenuto.

   ![](assets/dce_uc1_selectmodel.png)

1. Selezionare il file HTML da utilizzare.
1. Fai clic su **Apri** per avviare l’importazione.

   Durante il caricamento viene visualizzato l&#39;elenco dei file condivisi. Il sistema di importazione verifica la presenza di tutti i file collegati al HTML selezionato (CSS, immagini, ecc.).

   Fai clic sul pulsante **[!UICONTROL Close]** una volta completata l’importazione.

   ![](assets/dce_uc1_import.png)

   >[!CAUTION]
   >
   >È necessario attendere fino a quando non viene visualizzato il seguente messaggio prima di chiudere: **[!UICONTROL The external resources have been successfully published]** .

1. Fai clic sul pulsante **[!UICONTROL Properties]** scheda .
1. Inserisci un **etichetta** per ogni pagina (ad esempio: Pagina 1= Raccogli, Pagina 2=Grazie).

   ![](assets/dce_uc1_pagelabel.png)

Applicare questi passaggi per ogni pagina inserita nell&#39;applicazione Web.

>[!CAUTION]
>
>**Il DCE esegue il codice JavaScript per la pagina HTML caricata.** Errori JavaScript nel modello di HTML che possono comparire nell&#39;interfaccia Adobe Campaign. Questi errori non sono correlati all&#39;editor. Per verificare che non ci siano errori nei file importati, si consiglia di testarli in un browser Web prima di importare i file nel DCE.

## Passaggio 2: configurazione del contenuto {#step-2---configuring-the-content}

In questa sezione verrà regolato il contenuto importato e verranno collegati i campi del database al modulo della pagina web. L&#39;applicazione Web creata in precedenza è:

![](assets/dce_uc1_lp_enchainement.png)

### Modifica del contenuto {#modifying-content}

Cominciamo modificando i colori della pagina. Per eseguire questa operazione:

1. Apri **[!UICONTROL Collection]** pagina.
1. Fai clic sullo sfondo.
1. Fai clic su **Colore di sfondo** sul lato destro.
1. Selezionare un nuovo colore di sfondo.
1. Fai clic su **OK** per confermare la modifica.

   ![](assets/dce_uc1_changecolor.png)

1. Applicare gli stessi processi per modificare il colore del pulsante

   ![](assets/dce_uc1_finalcolor.png)

### Collegamento di campi modulo {#linking-form-fields}

Collegheremo i campi della pagina a quelli del database per salvare le informazioni fornite.

1. Selezionare un campo modulo.
1. Modifica le **[!UICONTROL Field]** sul lato destro dell’editor.
1. Selezionare il campo del database che si desidera collegare al campo selezionato.

   ![](assets/dce_uc1_mapping.png)

1. Ripetere questa procedura per ogni campo della pagina.

È possibile rendere obbligatorio un campo: ad esempio, fai clic su **[!UICONTROL Email]** quindi abilita **Obbligatorio** opzione .

![](assets/dce_uc1_fieldmandatory.png)

### Creazione di un collegamento alla pagina successiva {#creating-a-link-to-the-next-page}

Questo passaggio è obbligatorio perché consentirà all&#39;applicazione Web di determinare la sequenza dei passaggi successivi: Salvataggio dei dati raccolti nel database e visualizzazione della pagina successiva (**Grazie** page).

1. Seleziona la **[!UICONTROL Send it!]** pulsante **[!UICONTROL Collection]** pagina.
1. Fai clic sul pulsante **[!UICONTROL Action]** menu a discesa.
1. Seleziona la **[!UICONTROL Next page]** azione.

   ![](assets/dce_uc1_actionbouton.png)

### Inserimento di un campo di personalizzazione {#inserting-a-personalization-field}

Questo passaggio ti consente di personalizzare la pagina di ringraziamento. Per eseguire questa operazione:

1. Apri **[!UICONTROL Thank you]** pagina.
1. Posizionare il cursore in un&#39;area di testo in cui si desidera inserire il nome del destinatario.
1. Seleziona **[!UICONTROL Personalization field]** in **[!UICONTROL Insert]** del menu della barra degli strumenti.
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
