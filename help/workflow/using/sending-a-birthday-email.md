---
solution: Campaign Classic
product: campaign
title: Invio di un’e-mail di compleanno
description: Scopri come inviare un messaggio e-mail di compleanno con un flusso di lavoro
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 20dcdd91d71158bc373db68c3f61f6808b240bd2
workflow-type: tm+mt
source-wordcount: '882'
ht-degree: 1%

---


# Invio di un’e-mail di compleanno{#sending-a-birthday-email}

## Introduzione {#introduction}

Questo caso d’uso illustra come pianificare l’invio periodico di un’e-mail a un elenco di destinatari il giorno del loro compleanno.

Per impostare questo caso di utilizzo, abbiamo creato il seguente flusso di lavoro di targeting:

![](assets/birthday-workflow_usecase_1.png)

Questo flusso di lavoro (esecuzione giornaliera) seleziona tutti i destinatari la cui data di nascita è la data corrente.

![](assets/do-not-localize/how-to-video.png) Questo caso di utilizzo si trova anche sotto forma di video. Per ulteriori informazioni, consultare il video [Creazione di un flusso di lavoro](https://docs.adobe.com/content/help/en/campaign-classic-learn/tutorials/automating-with-workflows/creating-a-workflow.html).

A questo scopo, create una campagna e fate clic sulla scheda **[!UICONTROL Targeting and workflows]**. Per ulteriori informazioni, consultare la sezione [Creazione della destinazione principale in un flusso di lavoro](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow).

Effettuate quindi le seguenti operazioni:

## Pianificazione dell&#39;invio {#configuring-the-scheduler}

1. Innanzitutto, aggiungete un **Scheduler** per attivare l&#39;invio giornaliero. Nell&#39;esempio seguente, la consegna viene creata ogni giorno alle 6 del mattino.

   ![](assets/recur_delivery2.png)


## Identificazione dei destinatari il cui compleanno è {#identifying-recipients-whose-birthday-it-is}

Dopo aver configurato l&#39;attività **[!UICONTROL Scheduler]** in modo che il flusso di lavoro inizi ogni giorno, identificate tutti i destinatari la cui data di nascita è uguale alla data corrente.

A questo scopo, eseguire i seguenti passaggi:

1. Trascina un&#39;attività **[!UICONTROL Query]** nel flusso di lavoro e fai doppio clic su di essa.
1. Fare clic sul collegamento **Modifica query** e selezionare **[!UICONTROL Filtering conditions]**.

   ![](assets/s_ncs_user_create_exp_exple00.png)

1. Fare clic sulla prima cella della colonna **[!UICONTROL Expression]** e fare clic su **[!UICONTROL Edit expression]** per aprire l&#39;editor di espressioni.

   ![](assets/s_ncs_user_create_exp_exple.png)

1. Fare clic su **[!UICONTROL Advanced selection]** per selezionare la modalità di filtro.

   ![](assets/s_ncs_user_create_exp_exple_a.png)

1. Selezionare **[!UICONTROL Edit the formula using an expression]** e fare clic su **[!UICONTROL Next]** per visualizzare l&#39;editor di espressioni.
1. Nell&#39;elenco delle funzioni, fare doppio clic su **[!UICONTROL Day]**, accessibile tramite il nodo **[!UICONTROL Date]**. Questa funzione restituisce il numero che rappresenta il giorno corrispondente alla data passata come parametro.

   ![](assets/s_ncs_user_create_exp_exple01.png)

1. Nell&#39;elenco dei campi disponibili, fare doppio clic su **[!UICONTROL Birth date]**. Nella sezione superiore dell&#39;editor viene visualizzata la seguente formula:

   ```
   Day(@birthDate)
   ```

   Fare clic su **[!UICONTROL Finish]** per confermare.

1. Nell&#39;editor di query, nella prima cella della colonna **[!UICONTROL Operator]**, selezionare **[!UICONTROL equal to]**.

   ![](assets/s_ncs_user_create_exp_exple02.png)

1. Quindi, fare clic sulla prima cella della seconda colonna (**[!UICONTROL Value]**), quindi fare clic su **[!UICONTROL Edit expression]** per aprire l&#39;editor di espressioni.
1. Nell&#39;elenco delle funzioni, fare doppio clic su **[!UICONTROL Day]**, accessibile tramite il nodo **[!UICONTROL Date]**.
1. Fare doppio clic sulla funzione **[!UICONTROL GetDate]** per recuperare la data corrente.

   ![](assets/s_ncs_user_create_exp_exple04.png)

   Nella sezione superiore dell&#39;editor viene visualizzata la seguente formula:

   ```
   Day(GetDate())
   ```

   Fare clic su **[!UICONTROL Finish]** per confermare.

1. Ripetete questa procedura per recuperare il mese di nascita corrispondente al mese corrente. A questo scopo, fare clic sul pulsante **[!UICONTROL Add]** e ripetere i passaggi da 3 a 10, sostituendo **[!UICONTROL Day]** con **[!UICONTROL Month]**.

   La query completa è la seguente:

   ![](assets/s_ncs_user_create_exp_exple03.png)

Collegate il risultato dell&#39;attività **[!UICONTROL Query]** a un&#39;attività **[!UICONTROL Email delivery]** per inviare un&#39;e-mail all&#39;elenco di tutti i destinatari alla data del loro compleanno.

## Inclusi i destinatari nati il 29 febbraio (facoltativo) {#including-recipients-born-on-february-29th--optional-}

Se si desidera includere tutti i destinatari nati il 29 febbraio, questo caso d&#39;uso illustra come pianificare l&#39;invio periodico di un&#39;e-mail a un elenco di destinatari per il loro compleanno, che si tratti o meno di un anno bisestile.

Le fasi di implementazione principali per questo caso di utilizzo sono:

* Selezione dei destinatari
* Selezione se si tratta o meno di un anno bisestile
* Selezione dei destinatari nati il 29 febbraio

Per impostare questo caso di utilizzo, abbiamo creato il seguente flusso di lavoro di targeting:



Se l&#39;anno corrente **non è un anno bisestile** e il flusso di lavoro viene eseguito il 1° marzo, è necessario selezionare tutti i destinatari che hanno avuto il loro compleanno ieri (29 febbraio) e aggiungerli all&#39;elenco dei destinatari. In ogni altro caso non è richiesta alcuna azione aggiuntiva.

### Passaggio 1: Selezione dei destinatari {#step-1--selecting-the-recipients}

Dopo aver configurato l&#39;attività **[!UICONTROL Scheduler]** in modo che il flusso di lavoro inizi ogni giorno, identificate tutti i destinatari il cui anniversario è il giorno corrente.

>[!NOTE]
>
>Se l&#39;anno corrente è un anno bisestile, tutti i beneficiari nati il 29 febbraio vengono automaticamente inclusi.

![](assets/birthday-workflow_usecase_2.png)

La selezione dei destinatari il cui compleanno corrisponde alla data corrente viene presentata nella sezione [Identificazione dei destinatari il cui compleanno è](#identifying-recipients-whose-birthday-it-is).

### Passaggio 2: Selezionare se si tratta di un anno bisestile {#step-2--select-whether-or-not-it-is-a-leap-year}

L&#39;attività **[!UICONTROL Test]** consente di verificare se si tratta di un anno bisestile e se la data corrente è il 1 marzo.

Se il test viene verificato (l&#39;anno non è un anno bisestile - non c&#39;è il 29 febbraio - e la data corrente è effettivamente il 1 marzo), la transizione **[!UICONTROL True]** è abilitata e i destinatari nati il 29 febbraio saranno aggiunti alla consegna del 1 marzo. In caso contrario, la transizione **[!UICONTROL False]** è abilitata e solo i destinatari nati alla data corrente riceveranno la consegna.

Copiate e incollate il codice seguente nella sezione **[!UICONTROL Initialization script]** della scheda **[!UICONTROL Advanced]**.

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

Aggiungere la seguente condizione nella sezione **[!UICONTROL Conditional forks]**:

```
vars.currentIsALeapYear == 0 && vars.firstOfMarch == 1
```

![](assets/birthday-workflow_usecase_4.png)

### Passaggio 3: Selezionare i destinatari nati il 29 febbraio {#step-3--select-any-recipients-born-on-february-29th}

Create un&#39;attività **[!UICONTROL Fork]** e collegate una delle transizioni in uscita a un&#39;attività **[!UICONTROL Query]**.

In questa query, selezionare tutti i destinatari la cui data di nascita è il 29 febbraio.

![](assets/birthday-workflow_usecase_5.png)

Combinate i risultati con un&#39;attività **[!UICONTROL Union]**.

Collegate i risultati dei due rami di attività **[!UICONTROL Test]** a un&#39;attività **[!UICONTROL Email delivery]** per inviare un&#39;e-mail all&#39;elenco di tutti i destinatari al loro compleanno, anche a quelli nati il 29 febbraio durante un anno non bisestile.

## Creazione di una consegna ricorrente {#creating-a-recurring-delivery-in-a-targeting-workflow}

Aggiungete un&#39;attività **consegna periodica** in base al modello di e-mail di compleanno che desiderate inviare.

>[!CAUTION]
>
>Affinché i flussi di lavoro possano essere eseguiti, è necessario avviare i flussi di lavoro tecnici relativi al processo della campagna. Per ulteriori informazioni, consultare la sezione [Elenco dei flussi di lavoro dei processi delle campagne](../../workflow/using/campaign.md).
>
>Se per la campagna sono abilitati i passaggi di approvazione, le consegne verranno inviate solo dopo che tali passaggi saranno stati confermati. Per ulteriori informazioni, consultare la sezione [Scelta dei processi da approvare](../../campaign/using/marketing-campaign-approval.md#choosing-the-processes-to-be-approved).

![](assets/birthday-workflow_usecase_1.png)
