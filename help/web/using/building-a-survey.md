---
product: campaign
title: Progettazione di un sondaggio
description: Progettazione di un sondaggio
audience: web
content-type: reference
topic-tags: online-surveys
exl-id: 8d83dfd5-70ec-4656-965b-f6b5e6f9eec1
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '796'
ht-degree: 1%

---

# Progettazione di un sondaggio{#building-a-survey}

## Creazione di un nuovo sondaggio {#creating-a-new-survey}

Questo capitolo descrive la progettazione di un modulo di tipo **Survey** utilizzando Adobe Campaign, nonché le opzioni e le configurazioni disponibili. Adobe Campaign consente di rendere questo sondaggio disponibile agli utenti e raccogliere e archiviare le risposte nel database.

I moduli web sono accessibili tramite il nodo **[!UICONTROL Resources > Online > Web applications]** della struttura. Per creare un sondaggio, fai clic sul pulsante **[!UICONTROL New]** sopra l’elenco delle applicazioni oppure fai clic con il pulsante destro del mouse sull’elenco e scegli **[!UICONTROL New]**.

Seleziona il modello di sondaggio (**[!UICONTROL newSurvey]** per impostazione predefinita).

![](assets/s_ncs_admin_survey_select_template.png)

Le pagine del modulo vengono create utilizzando un editor speciale che consente di definire e configurare (testo) campi di input, campi di selezione (elenchi, caselle di controllo, ecc.) ed elementi statici (immagini, contenuto HTML, ecc.). Possono essere raccolti in &quot;contenitori&quot; e disposti in base ai requisiti (vedi [Aggiunta di domande](#adding-questions)).

>[!NOTE]
>
>Per ulteriori informazioni su come definire il contenuto e creare layout di schermo per un modulo web, vedere [questa sezione](../../web/using/about-web-forms.md).

## Aggiunta di campi {#adding-fields}

I campi di un modulo consentono agli utenti di immettere informazioni e selezionare opzioni. Per ogni pagina del modulo, vengono create tramite il primo pulsante nella barra degli strumenti utilizzando il menu **[!UICONTROL Add using the wizard]** .

![](assets/s_ncs_admin_survey_add_field_menu.png)

>[!NOTE]
>
>È inoltre possibile utilizzare un clic con il pulsante destro del mouse e inserire una zona di input. Per impostazione predefinita, la zona viene inserita alla fine della struttura selezionata. Utilizzare le frecce nella barra degli strumenti per spostarle.

### Tipi di campi {#types-of-fields}

Quando aggiungi un campo a un sondaggio, devi selezionarne il tipo. Sono disponibili le seguenti opzioni:

1. **[!UICONTROL Answer a question]**: questa opzione consente di dichiarare un nuovo campo (noto come &quot;campo archiviato&quot;) per memorizzare le risposte. In questo caso, tutti i valori raccolti vengono salvati, anche quando un partecipante compila il modulo più di una volta. Questa modalità di archiviazione è disponibile solo in **Sondaggi**. Fare riferimento a [Memorizzazione delle risposte raccolte](../../web/using/managing-answers.md#storing-collected-answers).
1. **[!UICONTROL Edit a recipient]**: questa opzione consente di selezionare un campo nel database. In questo caso, le risposte utente verranno memorizzate in questo campo. Per ciascun partecipante, viene mantenuto solo l’ultimo valore salvato e aggiunto ai dati del profilo.
1. **[!UICONTROL Add a variable]**: questa opzione consente di creare una configurazione in modo che le informazioni non vengano memorizzate nel database. Le variabili locali possono essere dichiarate a monte. Puoi anche aggiungerli direttamente durante la creazione del campo.
1. **[!UICONTROL Import an existing question]**: questa opzione ti consente di importare le domande esistenti create in altri sondaggi.

   >[!NOTE]
   >
   >Le modalità di archiviazione e le importazioni dei campi sono descritte in [Memorizzazione delle risposte raccolte](../../web/using/managing-answers.md#storing-collected-answers).

La natura del campo da aggiungere (elenco a discesa, campo di testo, caselle di controllo, ecc.) si adatta alla modalità di archiviazione selezionata. Puoi modificarlo utilizzando il campo **[!UICONTROL Type]** della scheda **[!UICONTROL General]** , ma accertati di mantenere la coerenza con il tipo di dati.

![](assets/s_ncs_admin_survey_change_type.png)

I vari tipi di campi disponibili sono descritti in [questa sezione](../../web/using/about-web-forms.md).

## Elementi specifici del sondaggio {#survey-specific-elements}

I sondaggi online utilizzano le funzionalità delle applicazioni web. Di seguito sono descritte le funzioni specifiche collegate ai campi del sondaggio.

### Scelta multipla {#multiple-choice}

Per i controlli di tipo **[!UICONTROL Multiple choice]**, è possibile definire un numero minimo e massimo di selezioni. Ad esempio, questa opzione consente di forzare la selezione ad almeno i valori **2** e al massimo i valori **4** dalle opzioni disponibili:

![](assets/s_ncs_admin_survey_multichoice_ex1.png)

Se il numero di selezioni è troppo grande o troppo piccolo, viene visualizzato il messaggio appropriato.

![](assets/s_ncs_admin_survey_multichoice_ex2.png)

>[!NOTE]
>
>In questo caso, le opzioni vengono selezionate utilizzando le caselle di controllo. Quando è possibile utilizzare una sola opzione, vengono utilizzati i pulsanti di scelta.

La configurazione corrispondente è la seguente:

![](assets/s_ncs_admin_survey_multichoice_ex3.png)

Inoltre, il percorso di archiviazione per questo campo di input deve essere di tipo **[!UICONTROL Multiple values]** **campo archiviato**:

![](assets/s_ncs_admin_survey_multiple_values_field.png)

>[!CAUTION]
>
>* Questa funzionalità è disponibile solo per i moduli di tipo **Survey**.
>* Questa opzione non è compatibile con la visualizzazione casuale delle domande. Per ulteriori informazioni, consulta [Aggiunta di domande](#adding-questions).


### Aggiunta di domande {#adding-questions}

Esistono due tipi di contenitori: standard e domanda. I contenitori standard vengono utilizzati per configurare il layout di pagina e la visualizzazione condizionale in una pagina. Sono descritti in [questa sezione](../../web/using/about-web-forms.md).

Utilizza un contenitore **Domanda** per aggiungere una domanda alla pagina e per inserire le possibili risposte sotto nella gerarchia. Le risposte degli utenti alle domande inserite in questo tipo di contenitore possono essere analizzate nei rapporti.

>[!CAUTION]
>
>Non inserire mai un contenitore **Domanda** sotto un altro contenitore **Domanda** nella gerarchia.

![](assets/s_ncs_admin_question_label.png)

L’etichetta della domanda viene inserita nel campo dell’etichetta. In questo caso, verrà applicato lo stile del foglio di stile del modulo. Seleziona l’opzione **[!UICONTROL Enter the title in HTML format]** per personalizzarla. In questo modo potrai accedere all’editor HTML.

>[!NOTE]
>
>Per ulteriori informazioni sull’utilizzo dell’editor HTML, consulta [questa sezione](../../web/using/about-web-forms.md) .

Ad esempio:

![](assets/s_ncs_admin_survey_containers_qu_arbo.png)

Nell’esempio precedente, il rendering sarà il seguente:

![](assets/s_ncs_admin_survey_containers_qu_ex.png)

>[!NOTE]
>
>Ogni domanda ha un contenitore di tipo **Domanda**.

Puoi abilitare il disegno casuale delle domande da parte di Adobe Campaign. È quindi possibile specificare il numero di domande da visualizzare nella pagina, nel campo situato nella parte inferiore della finestra di configurazione.

![](assets/s_ncs_admin_survey_containers_qu_display.png)

Il rendering sarà simile al seguente:

![](assets/s_ncs_admin_survey_containers_qu_display_rendering.png)

Quando la pagina viene aggiornata, le domande visualizzate non sono le stesse.

>[!CAUTION]
>
>Quando visualizzi una domanda in modo casuale (**[!UICONTROL Display randomly]** opzione selezionata nella pagina), fai attenzione a non utilizzare più domande di scelta per le quali una o più selezioni sono obbligatorie.
