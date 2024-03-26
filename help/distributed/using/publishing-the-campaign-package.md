---
product: campaign
title: Pubblicare il pacchetto della campagna
description: Pubblicare il pacchetto della campagna
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
feature: Distributed Marketing
exl-id: e96add16-cbc8-43af-acff-06a95d5b7749
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 4%

---

# Pubblicare il pacchetto della campagna{#publishing-the-campaign-package}



Gli operatori di entità centrali pubblicano le campagne che desiderano offrire agli enti locali nell’ambito **[!UICONTROL list of campaign packages]**.

Prima di poter essere pubblicati nell’elenco dei pacchetti della campagna, i pacchetti della campagna devono essere approvati dall’entità centrale. A questo scopo, puoi specificare un revisore o un gruppo di revisori tramite **[!UICONTROL Approval parameters]** nel pacchetto della campagna.

## Assegnazione di un revisore {#assigning-a-reviewer}

Per selezionare il revisore, fare clic su **[!UICONTROL Approval parameters]** collega dal pacchetto campaign e scegli il revisore pertinente dall’elenco a discesa.

![](assets/s_advuser_mkg_dist_define_valid.png)

È quindi possibile avviare il processo di approvazione facendo clic su **[!UICONTROL Submit for approval]**.

![](assets/s_advuser_mkg_dist_valid_process.png)

Viene quindi inviato un messaggio di notifica al revisore per confermare la disponibilità di questo pacchetto della campagna. Il messaggio contiene un collegamento per accettare o rifiutare l’approvazione tramite accesso web.

![](assets/s_advuser_mkg_dist_valid_process1.png)

>[!NOTE]
>
>A livello di entità organizzativa, è inoltre possibile specificare revisori per approvare gli ordini. Per ulteriori informazioni, consulta [Entità organizzative](about-distributed-marketing.md#organizational-entities).

## Aggiunta di altri revisori {#adding-other-reviewers}

Puoi aggiungere altri revisori da **[!UICONTROL Edit...]** , presente nel pacchetto della campagna **[!UICONTROL Approval parameters...]** scheda.

![](assets/s_advuser_mkg_dist_select_op_valid.png)

## Periodi di approvazione {#approval-periods}

Per impostazione predefinita, ai revisori vengono concessi tre giorni dalla data di invio per elaborare l’approvazione.

All’interno della finestra di modifica dei revisori, puoi anche impostare i promemoria per l’invio di uno o più messaggi se un pacchetto della campagna non è stato approvato. A questo scopo, fai clic su **[!UICONTROL Add reminder]** , quindi il **[!UICONTROL Add]** pulsante.

I promemoria possono essere inviati in una determinata data e/o **x** giorni dopo la data di invio. Il tipo di promemoria può essere configurato nella prima colonna della tabella dei promemoria. Nell’esempio seguente, i revisori riceveranno un messaggio di promemoria in data 29/01/2014, ovvero due giorni prima della data selezionata nell’ **[!UICONTROL Date]** e un secondo promemoria un giorno prima della fine del periodo di approvazione, ossia due giorni dopo la data di presentazione per l’approvazione.

![](assets/s_advuser_mkg_dist_reminder_planning.png)

Una volta definito e inviato il pacchetto per l’approvazione, la pianificazione di esecuzione viene visualizzata in **[!UICONTROL Audit]** scheda. Mostra la scadenza dell’elaborazione calcolata in base alla configurazione precedente, nonché le date di tutti i promemoria configurati.

## Approvazione tramite la console Adobe Campaign {#approving-via-the-adobe-campaign-console}

Se non è stato specificato un revisore o se nessuno degli operatori notificati ha approvato il pacchetto, il **[!UICONTROL Approve the package]** consente di passare direttamente all’approvazione dal pacchetto della campagna **[!UICONTROL Dashboard]** o dalla panoramica dei pacchetti.

![](assets/s_advuser_mkg_dist_valid_button.png)

Dopo l’approvazione, la campagna viene pubblicata, aggiunta all’elenco e, non appena viene raggiunta la data di disponibilità, le entità locali possono utilizzarla. Se durante la creazione della campagna sono state specificate le entità locali, viene inviato un messaggio agli operatori nel gruppo di notifica per comunicare loro che la campagna è disponibile. Se in precedenza non è stata specificata alcuna entità, la campagna è disponibile per tutte le entità locali per impostazione predefinita. Per ulteriori informazioni, consulta [Entità organizzative](about-distributed-marketing.md#organizational-entities).
