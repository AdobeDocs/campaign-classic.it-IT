---
solution: Campaign Classic
product: campaign
title: Progettazione di un’applicazione web
description: Progettazione di un’applicazione web
audience: web
content-type: reference
topic-tags: web-applications
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 3%

---


# Progettazione di un’applicazione web{#designing-a-web-application}

Le applicazioni Web vengono create e gestite secondo lo stesso principio dei sondaggi [](../../web/using/about-surveys.md)online.

Tuttavia, le differenze funzionali sono le seguenti:

* Le applicazioni Web non utilizzano campi archiviati. I dati possono quindi essere memorizzati solo in campi di database o variabili locali.
* Non esistono rapporti incorporati sulle applicazioni Web.
* Sono disponibili campi aggiuntivi, principalmente per la creazione di tabelle e grafici.

>[!CAUTION]
>
>Si consiglia vivamente che le configurazioni applicate siano controllate continuamente al fine di rilevare eventuali errori in anticipo nel processo di costruzione dell&#39;applicazione Web. Per verificare il rendering di una modifica, salvate l’applicazione, quindi fate clic sulla **[!UICONTROL Preview]** sottoscheda.
>
>Fino alla pubblicazione dell&#39;applicazione Web, le modifiche non possono essere visualizzate dall&#39;utente finale.

## Inserimento di grafici in un&#39;applicazione Web {#inserting-charts-in-a-web-application}

È possibile includere grafici nelle applicazioni Web. A tale scopo, utilizzare l&#39;elenco a discesa dei grafici nella barra delle attività per selezionare il tipo di grafico da inserire.

![](assets/s_ncs_admin_webapps_bar_graph.png)

Potete anche selezionare il **[!UICONTROL Add a chart]** menu.

![](assets/s_ncs_admin_webapps_graph.png)

## Inserimento di tabelle in un&#39;applicazione Web {#inserting-tables-in-a-web-application}

Per aggiungere una tabella, utilizzare l&#39;elenco a discesa di tabelle nella barra delle attività per selezionare il tipo di tabella da utilizzare.

![](assets/s_ncs_admin_webapps_bar_table.png)

È inoltre possibile selezionare il tipo di tabella nel menu a discesa.

![](assets/s_ncs_admin_webapps_table.png)

## Applicazioni Web di tipo Panoramica {#overview-type-web-applications}

L&#39;interfaccia  Adobe Campaign utilizza molte applicazioni Web per accedere, gestire e interagire con destinatari, consegne, campagne, scorte e così via.

Vengono visualizzate nell&#39;interfaccia sotto forma di dashboard con una sola pagina.

Le applicazioni Web predefinite sono memorizzate nel **[!UICONTROL Administration > Configuration > Web applications]** nodo.

## Modifica di applicazioni Web di tipo moduli {#edit-forms-type-web-applications}

Le applicazioni Web per la modifica di un extranet sono caratterizzate da:

* Una casella di precaricamento

   Nella maggior parte dei casi, i dati da visualizzare devono essere precaricati. Poiché gli utenti che accedono a tali moduli sono identificati (tramite un controllo di accesso), il precaricamento non è necessariamente crittografato.

* Una casella di salvataggio
* Aggiunta di pagine

   Mentre le applicazioni Web di tipo &quot;Panoramica&quot; dispongono tutte di una singola pagina, i moduli di modifica possono offrire una sequenza di pagine in base a criteri specifici (test, selezioni, profilo dell&#39;operatore connesso, ecc.).

Il funzionamento di questo tipo di applicazione Web è simile a quello dei **sondaggi**, ma senza gestione della cronologia o archiviazione dei campi. Gli utenti di solito accedono tramite una pagina di login in cui devono identificarsi.
