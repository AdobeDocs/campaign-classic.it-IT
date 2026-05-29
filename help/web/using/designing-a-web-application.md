---
product: campaign
title: Progettare un’applicazione web
description: Progettare un’applicazione web
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Web Apps
exl-id: dcdf6afc-321e-4027-a350-fff6bbf22e71
TQID: https://experienceleague.adobe.com/8HdoOgOBgZgI3-Kxnn-I0kW5zyTSBfUtM0IoLGBvHag
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616aid: c5474392-5419-4296-9e41-f6f4ce4f6e9bid: a4671286-a59f-47e3-b97b-90627a1977d5
topic_v2: id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
subfeature_v2: id: f391046b-0cf3-4e76-bd3b-97fe06654506id: ed29abcd-b6a8-4d4b-ab8b-b7e746973281id: d7be2b01-dc9c-40f7-aace-a151707504ed
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 296
ht-degree: 4%

---

# Progettare un’applicazione web{#designing-a-web-application}



Le applicazioni Web vengono create e gestite in base allo stesso principio dei [moduli Web](about-web-forms.md).

>[!CAUTION]
>
>Utilizzare la scheda secondaria **[!UICONTROL Preview]** per verificare gli errori durante la progettazione dell&#39;applicazione Web. Il test del profilo utilizzato per visualizzare in anteprima l&#39;applicazione Web deve trovarsi in una cartella con **[!UICONTROL Access rights]** per l&#39;operatore **[!UICONTROL Web application agent]**. </br>Fino alla pubblicazione dell&#39;applicazione Web, le modifiche non vengono esposte agli utenti finali.

## Inserimento di grafici in un&#39;applicazione Web {#inserting-charts-in-a-web-application}

È possibile includere grafici nelle applicazioni Web. A tale scopo, utilizzare l&#39;elenco a discesa dei grafici nella barra delle applicazioni per selezionare il tipo di grafico da inserire.

![](assets/s_ncs_admin_webapps_bar_graph.png)

È inoltre possibile selezionare il menu **[!UICONTROL Add a chart]**.

![](assets/s_ncs_admin_webapps_graph.png)

## Inserimento di tabelle in un&#39;applicazione Web {#inserting-tables-in-a-web-application}

Per aggiungere una tabella, utilizzare l&#39;elenco a discesa delle tabelle nella barra delle applicazioni per selezionare il tipo di tabella da utilizzare.

![](assets/s_ncs_admin_webapps_bar_table.png)

Puoi anche selezionare il tipo di tabella nel menu a discesa.

![](assets/s_ncs_admin_webapps_table.png)

## Applicazioni Web di tipo Panoramica {#overview-type-web-applications}

L’interfaccia di Adobe Campaign utilizza molte applicazioni web per accedere, gestire e interagire con destinatari, consegne, campagne, scorte e così via.

Vengono visualizzati nell’interfaccia sotto forma di dashboard con una sola pagina.

Le applicazioni Web predefinite sono archiviate nel nodo **[!UICONTROL Administration > Configuration > Web applications]**.

## Modificare le applicazioni Web di tipo form {#edit-forms-type-web-applications}

Modifica di applicazioni Web per una extranet sono caratterizzate da:

* Una casella di precaricamento

  Nella maggior parte dei casi, i dati da visualizzare devono essere precaricati. Poiché gli utenti che accedono a questi moduli vengono identificati (tramite un controllo di accesso), il precaricamento non viene necessariamente crittografato.

* Una casella di salvataggio
* Aggiunta di pagine

  Mentre le applicazioni web di tipo &quot;Panoramica&quot; hanno tutte una singola pagina, i moduli di modifica possono offrire una sequenza di pagine in base a criteri specifici (test, selezioni, profilo dell’operatore connesso, ecc.).

