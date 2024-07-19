---
product: campaign
title: Inviare un’e-mail di compleanno
description: Scopri come inviare un’e-mail di compleanno con un flusso di lavoro
feature: Workflows
exl-id: 38006cca-e945-4b9d-8e2d-ed537b8541d9
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '878'
ht-degree: 2%

---

# Inviare un’e-mail di compleanno{#sending-a-birthday-email}



## Introduzione {#introduction}

Questo caso d’uso illustra come pianificare l’invio di un’e-mail ricorrente a un elenco di destinatari il giorno del loro compleanno.

Per impostare questo caso d’uso, abbiamo creato il seguente flusso di lavoro di targeting:

![](assets/birthday-workflow_usecase_1.png)

Questo flusso di lavoro (eseguito quotidianamente) seleziona tutti i destinatari il cui compleanno cade nella data corrente.

![](assets/do-not-localize/how-to-video.png) Questo caso d&#39;uso si trova anche sotto forma di video. Per ulteriori informazioni, consulta il video [Creazione di un flusso di lavoro](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/automating-with-workflows/creating-a-workflow.html).

A tale scopo, creare una campagna e fare clic sulla scheda **[!UICONTROL Targeting and workflows]**. Per ulteriori informazioni, consulta la sezione [Creazione della destinazione principale in un flusso di lavoro](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow).

Quindi segui questi passaggi:

## Pianificazione dell’invio {#configuring-the-scheduler}

1. Innanzitutto, aggiungi un **modulo di pianificazione** per attivare l&#39;invio della consegna ogni giorno. Nell’esempio seguente, la consegna viene creata ogni giorno alle 6.

   ![](assets/recur_delivery2.png)


## Identificazione dei destinatari del compleanno {#identifying-recipients-whose-birthday-it-is}

Dopo aver configurato l&#39;attività **[!UICONTROL Scheduler]** in modo che il flusso di lavoro venga avviato ogni giorno, identificare tutti i destinatari la cui data di nascita è uguale alla data corrente.

A questo scopo, esegui i seguenti passaggi:

1. Trascinare e rilasciare un&#39;attività **[!UICONTROL Query]** nel flusso di lavoro e fare doppio clic su di essa.
1. Fai clic sul collegamento **Modifica query** e seleziona **[!UICONTROL Filtering conditions]**.

   ![](assets/s_ncs_user_create_exp_exple00.png)

1. Fare clic sulla prima cella della colonna **[!UICONTROL Expression]** e fare clic su **[!UICONTROL Edit expression]** per aprire l&#39;editor di espressioni.

   ![](assets/s_ncs_user_create_exp_exple.png)

1. Fare clic su **[!UICONTROL Advanced selection]** per selezionare la modalità di filtro.

   ![](assets/s_ncs_user_create_exp_exple_a.png)

1. Selezionare **[!UICONTROL Edit the formula using an expression]** e fare clic su **[!UICONTROL Next]** per visualizzare l&#39;editor di espressioni.
1. Nell&#39;elenco delle funzioni fare doppio clic su **[!UICONTROL Day]**, accessibile tramite il nodo **[!UICONTROL Date]**. Questa funzione restituisce il numero che rappresenta il giorno corrispondente alla data passata come parametro.

   ![](assets/s_ncs_user_create_exp_exple01.png)

1. Nell&#39;elenco dei campi disponibili fare doppio clic su **[!UICONTROL Birth date]**. La sezione superiore dell’editor visualizza quindi la seguente formula:

   ```
   Day(@birthDate)
   ```

   Fai clic su **[!UICONTROL Finish]** per confermare.

1. Nell&#39;editor delle query selezionare **[!UICONTROL equal to]** nella prima cella della colonna **[!UICONTROL Operator]**.

   ![](assets/s_ncs_user_create_exp_exple02.png)

1. Fare clic sulla prima cella della seconda colonna (**[!UICONTROL Value]**) e quindi su **[!UICONTROL Edit expression]** per aprire l&#39;editor espressioni.
1. Nell&#39;elenco delle funzioni fare doppio clic su **[!UICONTROL Day]**, accessibile tramite il nodo **[!UICONTROL Date]**.
1. Fare doppio clic sulla funzione **[!UICONTROL GetDate]** per recuperare la data corrente.

   ![](assets/s_ncs_user_create_exp_exple04.png)

   La sezione superiore dell’editor visualizza la seguente formula:

   ```
   Day(GetDate())
   ```

   Fai clic su **[!UICONTROL Finish]** per confermare.

1. Ripetere questa procedura per recuperare il mese di nascita corrispondente al mese corrente. A tale scopo, fare clic sul pulsante **[!UICONTROL Add]** e ripetere i passaggi da 3 a 10, sostituendo **[!UICONTROL Day]** con **[!UICONTROL Month]**.

   La query completa è la seguente:

   ![](assets/s_ncs_user_create_exp_exple03.png)

Collega il risultato dell&#39;attività **[!UICONTROL Query]** a un&#39;attività **[!UICONTROL Email delivery]** per inviare un&#39;e-mail all&#39;elenco di tutti i destinatari il giorno del loro compleanno.

## Inclusione di destinatari nati il 29 febbraio (facoltativo) {#including-recipients-born-on-february-29th--optional-}

Se desideri includere tutti i destinatari nati il 29 febbraio, questo caso d’uso illustra come pianificare l’invio di un’e-mail ricorrente a un elenco di destinatari per il loro compleanno, indipendentemente dal fatto che si tratti di un anno bisestile o meno.

I passaggi principali di implementazione per questo caso d’uso sono:

* Selezione dei destinatari
* Scegliere se si tratta o meno di un anno bisestile
* Selezione dei destinatari nati il 29 febbraio

Per impostare questo caso d’uso, abbiamo creato il seguente flusso di lavoro di targeting:



Se l&#39;anno corrente **non è un anno bisestile** e il flusso di lavoro viene eseguito il 1° marzo, è necessario selezionare tutti i destinatari che avrebbero compiuto gli anni ieri (29 febbraio) e aggiungerli all&#39;elenco dei destinatari. In tutti gli altri casi non è necessaria alcuna azione aggiuntiva.

### Passaggio 1: selezione dei destinatari {#step-1--selecting-the-recipients}

Dopo aver configurato l&#39;attività **[!UICONTROL Scheduler]** in modo che il flusso di lavoro venga avviato ogni giorno, identificare tutti i destinatari il cui anniversario è il giorno corrente.

>[!NOTE]
>
>Se l&#39;anno corrente è un anno bisestile, vengono automaticamente inclusi tutti i destinatari nati il 29 febbraio.

![](assets/birthday-workflow_usecase_2.png)

La selezione dei destinatari il cui compleanno corrisponde alla data corrente viene presentata nella sezione [Identificazione dei destinatari il cui compleanno è](#identifying-recipients-whose-birthday-it-is).

### Passaggio 2: selezionare se si tratta o meno di un anno bisestile {#step-2--select-whether-or-not-it-is-a-leap-year}

L&#39;attività **[!UICONTROL Test]** ti consente di verificare se si tratta di un anno bisestile e se la data corrente è il 1° marzo.

Se il test viene verificato (l’anno non è bisestile - non c’è il 29 febbraio - e la data corrente è effettivamente il 1° marzo), la transizione **[!UICONTROL True]** è abilitata e i destinatari nati il 29 febbraio verranno aggiunti alla consegna del 1° marzo. In caso contrario, la transizione **[!UICONTROL False]** è abilitata e solo i destinatari nati nella data corrente riceveranno la consegna.

Copiare e incollare il codice seguente nella sezione **[!UICONTROL Initialization script]** della scheda **[!UICONTROL Advanced]**.

```
function isLeapYear(iYear)
{
    if(iYear/4 == Math.floor(iYear/4))
    {
        if(iYear/100 != Math.floor(iYear/100))
        {
            // Divisible by 4 only -> Leap Year
            return 1;
        }
        else
        {
            if(iYear/400 == Math.floor(iYear/400))
            {
                // Divisible by 4, 100 and 400 -> Leap year
                return 1;
            }
        }
    }
    // all others: no leap year
    return 0;
}

// Return today's date and time
var currentTime = new Date()
// returns the month (from 0 to 11)
var month = currentTime.getMonth() + 1
// returns the day of the month (from 1 to 31)
var day = currentTime.getDate()
// returns the year (four digits)
var year = currentTime.getFullYear()

// is current year a leap year?
vars.currentIsALeapYear = isLeapYear(year);

// is current date the first of march?
if(month == 3 && day == 1) {
  // today is 1st of march
vars.firstOfMarch = 1;
}
```

![](assets/birthday-workflow_usecase_3.png)

Aggiungi la seguente condizione nella sezione **[!UICONTROL Conditional forks]**:

```
vars.currentIsALeapYear == 0 && vars.firstOfMarch == 1
```

![](assets/birthday-workflow_usecase_4.png)

### Passaggio 3: selezionare i destinatari nati il 29 febbraio {#step-3--select-any-recipients-born-on-february-29th}

Creare un&#39;attività **[!UICONTROL Fork]** e collegare una delle transizioni in uscita a un&#39;attività **[!UICONTROL Query]**.

In questa query, seleziona tutti i destinatari la cui data di nascita è il 29 febbraio.

![](assets/birthday-workflow_usecase_5.png)

Combinare i risultati con un&#39;attività **[!UICONTROL Union]**.

Collega i risultati dei due rami dell&#39;attività **[!UICONTROL Test]** a un&#39;attività **[!UICONTROL Email delivery]** per inviare un&#39;e-mail all&#39;elenco di tutti i destinatari per il compleanno, anche a quelli nati il 29 febbraio durante un anno non bisestile.

## Creazione di una consegna ricorrente {#creating-a-recurring-delivery-in-a-targeting-workflow}

Aggiungi un&#39;attività **Consegna ricorrente** in base al modello di e-mail di compleanno che desideri inviare.

>[!CAUTION]
>
>Affinché i flussi di lavoro possano essere eseguiti, è necessario avviare i flussi di lavoro tecnici relativi al pacchetto Campaign. Per ulteriori informazioni, consulta la sezione [Elenco dei flussi di lavoro tecnici](about-technical-workflows.md).
>
>Se i passaggi di approvazione sono abilitati per la campagna, le consegne verranno inviate solo dopo che tali passaggi sono stati confermati. Per ulteriori informazioni, consulta la sezione [Selezione dei processi da approvare](../../campaign/using/marketing-campaign-approval.md#choosing-the-processes-to-be-approved).

![](assets/birthday-workflow_usecase_1.png)
