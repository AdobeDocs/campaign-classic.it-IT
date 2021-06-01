---
product: campaign
title: Progettazione di un’applicazione web
description: Progettazione di un’applicazione web
audience: web
content-type: reference
topic-tags: web-applications
exl-id: dcdf6afc-321e-4027-a350-fff6bbf22e71
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 3%

---

# Progettare un’applicazione web{#designing-a-web-application}

Le applicazioni web vengono create e gestite in base allo stesso principio dei [sondaggi online](../../web/using/about-surveys.md).

Tuttavia, le differenze funzionali sono le seguenti:

* Le applicazioni Web non utilizzano campi archiviati. I dati possono pertanto essere memorizzati solo nei campi del database o nelle variabili locali.
* Non sono presenti report incorporati nelle applicazioni Web.
* Sono disponibili campi aggiuntivi, principalmente per la creazione di tabelle e grafici.

>[!CAUTION]
>
>Si consiglia vivamente di controllare continuamente le configurazioni applicate al fine di rilevare eventuali errori nella fase iniziale del processo di costruzione dell&#39;applicazione Web. Per controllare il rendering di una modifica, salva l&#39;applicazione, quindi fai clic sulla sottoscheda **[!UICONTROL Preview]** .
>
>Fino alla pubblicazione dell&#39;applicazione Web, le modifiche non possono essere visualizzate dall&#39;utente finale.

## Inserimento di grafici in un&#39;applicazione Web {#inserting-charts-in-a-web-application}

È possibile includere grafici nelle applicazioni Web. A questo scopo, utilizzare l’elenco a discesa dei grafici nella barra delle attività per selezionare il tipo di grafico da inserire.

![](assets/s_ncs_admin_webapps_bar_graph.png)

Puoi anche selezionare il menu **[!UICONTROL Add a chart]** .

![](assets/s_ncs_admin_webapps_graph.png)

## Inserimento di tabelle in un&#39;applicazione Web {#inserting-tables-in-a-web-application}

Per aggiungere una tabella, utilizzare l’elenco a discesa delle tabelle nella barra delle attività per selezionare il tipo di tabella da utilizzare.

![](assets/s_ncs_admin_webapps_bar_table.png)

È inoltre possibile selezionare il tipo di tabella nel menu a discesa.

![](assets/s_ncs_admin_webapps_table.png)

## Applicazioni Web di tipo Panoramica {#overview-type-web-applications}

L’interfaccia di Adobe Campaign utilizza molte applicazioni web per accedere, gestire e interagire con destinatari, consegne, campagne, stock, ecc.

Vengono visualizzate nell’interfaccia sotto forma di dashboard con una sola pagina.

Le applicazioni Web predefinite sono memorizzate nel nodo **[!UICONTROL Administration > Configuration > Web applications]**.

## Modifica di applicazioni Web di tipo form {#edit-forms-type-web-applications}

Le applicazioni Web di modifica per un extranet sono caratterizzate da:

* Una casella di precaricamento

   Nella maggior parte dei casi, i dati da visualizzare devono essere precaricati. Poiché gli utenti che accedono a questi moduli sono identificati (tramite un controllo di accesso), il precaricamento non è necessariamente crittografato.

* Una casella di salvataggio
* Aggiunta di pagine

   Mentre le applicazioni Web di tipo &quot;Panoramica&quot; dispongono tutte di una singola pagina, i moduli di modifica possono offrire una sequenza di pagine in base a criteri specifici (test, selezioni, profilo dell’operatore connesso, ecc.).

Il funzionamento di questo tipo di applicazione Web è simile a **Sondaggi**, ma senza gestione della cronologia o archiviazione dei campi. Gli utenti di solito vi accedono tramite una pagina di accesso in cui devono identificarsi.
