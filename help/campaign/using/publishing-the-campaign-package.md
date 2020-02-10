---
title: Pubblicazione del pacchetto della campagna
seo-title: Pubblicazione del pacchetto della campagna
description: Pubblicazione del pacchetto della campagna
seo-description: null
page-status-flag: never-activated
uuid: f2d35a8d-191f-4c53-8682-7ccce2a94257
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: distributed-marketing
discoiquuid: 8653d4fc-e47f-451a-95f2-c9209a252664
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d30de91002862b664249c5a704b7c0f521dd30f2

---


# Pubblicazione del pacchetto della campagna{#publishing-the-campaign-package}

Gli operatori di entità centrale pubblicano le campagne che desiderano offrire alle entità locali nel **[!UICONTROL list of campaign packages]**.

Prima di poter essere pubblicati nell&#39;elenco dei pacchetti della campagna, i pacchetti della campagna devono essere approvati dall&#39;entità centrale. A questo scopo, potete specificare un revisore o un gruppo di revisori tramite il **[!UICONTROL Approval parameters]** collegamento nel pacchetto della campagna.

## Assegnazione di un revisore {#assigning-a-reviewer}

Per selezionare il revisore, fate clic sul **[!UICONTROL Approval parameters]** collegamento nel pacchetto della campagna e scegliete il revisore appropriato dall&#39;elenco a discesa.

![](assets/s_advuser_mkg_dist_define_valid.png)

Potete quindi avviare il processo di approvazione facendo clic su **[!UICONTROL Submit for approval]**.

![](assets/s_advuser_mkg_dist_valid_process.png)

Viene quindi inviato un messaggio di notifica al revisore per confermare la disponibilità del pacchetto della campagna. Il messaggio contiene un collegamento per accettare o rifiutare l&#39;approvazione tramite accesso Web.

![](assets/s_advuser_mkg_dist_valid_process1.png)

>[!NOTE]
>
>A livello di entità organizzativa, potete anche specificare i revisori per approvare gli ordini. Per ulteriori informazioni, vedere [Entità](../../campaign/using/about-distributed-marketing.md#organizational-entities)organizzative.

## Aggiunta di altri revisori {#adding-other-reviewers}

Potete aggiungere altri revisori dal **[!UICONTROL Edit...]** collegamento, disponibile nella **[!UICONTROL Approval parameters...]** scheda del pacchetto della campagna.

![](assets/s_advuser_mkg_dist_select_op_valid.png)

## Periodi di approvazione {#approval-periods}

Per impostazione predefinita, i revisori ricevono tre giorni dalla data di invio per elaborare l’approvazione.

Nella finestra dei revisori delle modifiche, potete anche impostare i promemoria per inviare uno o più messaggi se un pacchetto di campagna non è stato approvato. A questo scopo, fare clic sul **[!UICONTROL Add reminder]** collegamento, quindi sul **[!UICONTROL Add]** pulsante.

I promemoria possono essere inviati in una data specificata e/o **x** giorni successivi alla data di invio. Il tipo di promemoria può essere configurato nella prima colonna della tabella dei promemoria. Nell&#39;esempio seguente, i revisori riceveranno un promemoria sulla data del 29/01/2014, ossia due giorni prima della data selezionata nella **[!UICONTROL Date]** colonna, e un secondo promemoria un giorno prima della fine del periodo di approvazione, ossia due giorni dopo la data di invio per l&#39;approvazione.

![](assets/s_advuser_mkg_dist_reminder_planning.png)

Una volta definito e inviato il pacchetto per l&#39;approvazione, il programma di esecuzione viene visualizzato nella **[!UICONTROL Audit]** scheda. Mostra la scadenza di elaborazione calcolata in base alla configurazione precedente, nonché le date di tutti i promemoria configurati.

## Approvazione tramite la console Adobe Campaign {#approving-via-the-adobe-campaign-console}

Se non è stato specificato alcun revisore o se nessuno degli operatori notificati ha approvato il pacchetto, il **[!UICONTROL Approve the package]** pulsante consente di passare direttamente all&#39;approvazione dal pacchetto campagna **[!UICONTROL Dashboard]** o dalla panoramica dei pacchetti.

![](assets/s_advuser_mkg_dist_valid_button.png)

Dopo l&#39;approvazione, la campagna viene pubblicata, aggiunta all&#39;elenco e, non appena viene raggiunta la data di disponibilità, le entità locali possono utilizzarla. Se durante la creazione della campagna sono state specificate delle entità locali, agli operatori del gruppo di notifiche viene inviato un messaggio per informarli che la campagna è disponibile. Se non è stata specificata alcuna entità in anticipo, per impostazione predefinita la campagna è disponibile per tutte le entità locali. Per ulteriori informazioni, vedere [Entità](../../campaign/using/about-distributed-marketing.md#organizational-entities)organizzative.
