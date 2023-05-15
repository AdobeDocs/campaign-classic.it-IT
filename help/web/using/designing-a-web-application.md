---
product: campaign
title: Progettare un’applicazione web
description: Progettare un’applicazione web
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Web Apps
exl-id: dcdf6afc-321e-4027-a350-fff6bbf22e71
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 4%

---

# Progettare un’applicazione web{#designing-a-web-application}



Le applicazioni web vengono create e gestite in base allo stesso principio [moduli web](about-web-forms.md).

>[!CAUTION]
>
>Utilizza la **[!UICONTROL Preview]** sottoscheda per verificare gli errori durante la progettazione di applicazioni web. Tieni presente che il test del profilo utilizzato per visualizzare l’anteprima dell’applicazione web deve trovarsi in una cartella con **[!UICONTROL Access rights]** per **[!UICONTROL Web application agent]** operatore. </br>Fino alla pubblicazione dell&#39;applicazione Web, le modifiche non vengono esposte agli utenti finali.

## Inserimento di grafici in un’applicazione Web {#inserting-charts-in-a-web-application}

È possibile includere grafici nelle applicazioni Web. A questo scopo, utilizzare l’elenco a discesa dei grafici nella barra delle attività per selezionare il tipo di grafico da inserire.

![](assets/s_ncs_admin_webapps_bar_graph.png)

Puoi anche selezionare la **[!UICONTROL Add a chart]** menu.

![](assets/s_ncs_admin_webapps_graph.png)

## Inserimento di tabelle in un&#39;applicazione Web {#inserting-tables-in-a-web-application}

Per aggiungere una tabella, utilizzare l’elenco a discesa delle tabelle nella barra delle attività per selezionare il tipo di tabella da utilizzare.

![](assets/s_ncs_admin_webapps_bar_table.png)

È inoltre possibile selezionare il tipo di tabella nel menu a discesa.

![](assets/s_ncs_admin_webapps_table.png)

## Applicazioni web di tipo Panoramica {#overview-type-web-applications}

L’interfaccia di Adobe Campaign utilizza molte applicazioni web per accedere, gestire e interagire con destinatari, consegne, campagne, stock, ecc.

Vengono visualizzate nell’interfaccia sotto forma di dashboard con una sola pagina.

Le applicazioni web predefinite sono memorizzate nella **[!UICONTROL Administration > Configuration > Web applications]** nodo.

## Modifica di applicazioni Web di tipo modulo {#edit-forms-type-web-applications}

Le applicazioni Web di modifica per un extranet sono caratterizzate da:

* Una casella di precaricamento

   Nella maggior parte dei casi, i dati da visualizzare devono essere precaricati. Poiché gli utenti che accedono a questi moduli sono identificati (tramite un controllo di accesso), il precaricamento non è necessariamente crittografato.

* Una casella di salvataggio
* Aggiunta di pagine

   Mentre le applicazioni Web di tipo &quot;Panoramica&quot; dispongono tutte di una singola pagina, i moduli di modifica possono offrire una sequenza di pagine in base a criteri specifici (test, selezioni, profilo dell’operatore connesso, ecc.).

