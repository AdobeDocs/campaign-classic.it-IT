---
solution: Campaign Classic
product: campaign
title: Modifica di un profilo
description: Modifica di un profilo
audience: platform
content-type: reference
topic-tags: profile-management
translation-type: tm+mt
source-git-commit: 6d5dbc16ed6c6e5a2e62ceb522e2ccd64b142825
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 5%

---


# Modifica di un profilo{#editing-a-profile}

Per visualizzare le informazioni relative a un profilo, fai clic sul suo nome nell’elenco dei profili.

I dettagli del profilo vengono visualizzati in una nuova scheda.

![](assets/s_user_recipient_edit.png)

I dati relativi ai profili sono raggruppati in schede.

Le schede e il relativo contenuto dipendono dalla configurazione e dai pacchetti installati.

>[!CAUTION]
>
>Lo schema XML e il modulo che riguarda i campi nella tabella dei profili sono accessibili tramite il nodo **[!UICONTROL Administration > Configuration > Data schemas]** della struttura di Adobe Campaign . Solo gli utenti esperti possono apportare modifiche a tali schemi.
>
>Per ulteriori informazioni, fare riferimento a [questa pagina](../../configuration/using/about-schema-edition.md).

## Scheda Generale {#general-tab}

Questa schermata contiene tutti i dati generali sul profilo selezionato. In particolare, contiene il cognome, il nome, l&#39;indirizzo e-mail, il formato di ricezione e-mail, ecc. Si presenta così:

![](assets/s_ncs_user_profile_general_tab.png)

>[!NOTE]
>
>Quando l&#39;opzione **[!UICONTROL No longer contact (by any channel)]** è selezionata, ciò significa che il profilo è elenco Bloccati, ovvero il profilo ha espresso il desiderio di non essere contattato (ad esempio, facendo clic su un collegamento di annullamento dell&#39;iscrizione in una newsletter). Non saranno più indirizzati da invii su canali (e-mail, posta diretta, ecc.). Per ulteriori informazioni, consulta [questa pagina](../../delivery/using/understanding-quarantine-management.md).

## Scheda Informazioni di contatto {#contact-information-tab}

Questa schermata contiene l&#39;indirizzo di posta diretta del profilo selezionato. Si presenta così:

![](assets/s_ncs_user_profile_details_tab.png)

Questa schermata mostra l&#39;indice di qualità dell&#39;indirizzo e quanti errori contiene l&#39;indirizzo. Queste informazioni vengono utilizzate direttamente dal gestore della posta in base al numero di errori riscontrati durante le consegne precedenti e non possono essere modificate manualmente.

## Altra scheda {#other-tab}

Questa schermata contiene campi definiti dall’utente che possono essere personalizzati in base ai requisiti. È inoltre possibile modificare i nomi dei campi e definirne il formato, tramite **[!UICONTROL Field properties...]**, come illustrato di seguito:

![](assets/s_ncs_user_profile_others_tab.png)

>[!NOTE]
>
>Per ulteriori informazioni sulle proprietà dei campi e sull&#39;aggiunta di campi, fare riferimento a [questa pagina](../../configuration/using/new-field-wizard.md).

## Scheda Elenchi {#lists-tab}

In questa schermata vengono visualizzati i gruppi a cui appartiene il profilo selezionato. Fare clic su **[!UICONTROL Add]** per iscriversi a un elenco. Fare clic su **[!UICONTROL Detail]** per visualizzare la descrizione e l&#39;elenco dei profili nell&#39;elenco selezionato.

![](assets/s_ncs_user_profile_groups_tab_details.png)

Per ulteriori informazioni, vedere [Creazione e gestione di elenchi](../../platform/using/creating-and-managing-lists.md).

## Scheda Iscrizioni {#subscriptions-tab}

Questa schermata contiene i servizi di informazione a cui il profilo ha effettuato la sottoscrizione.

![](assets/s_ncs_user_profile_subscript_tab_details.png)

Il pulsante **[!UICONTROL Detail]** visualizza le proprietà della sottoscrizione selezionata. Il pulsante **[!UICONTROL Add]** viene utilizzato per aggiungere manualmente una nuova iscrizione.

Per ulteriori informazioni, consulta [questa pagina](../../delivery/using/managing-subscriptions.md).

## Scheda Consegne {#deliveries-tab}

In questa schermata vengono visualizzati i registri di consegna per il profilo selezionato. Puoi anche visualizzare le etichette, le date e lo stato delle azioni di consegna indirizzate al profilo tramite tutti i canali.

![](assets/s_ncs_user_profile_delivery_tab.png)

## Scheda Tracciamento {#tracking-tab}

Questa schermata consente di visualizzare i registri di tracciamento per il profilo selezionato. Queste informazioni vengono utilizzate per tenere traccia del comportamento del profilo in seguito alle consegne.

![](assets/s_ncs_user_profile_tracking_tab.png)

Questa scheda mostra il totale cumulativo di tutti gli URL tracciati nelle consegne.

L&#39;elenco è configurabile e in genere contiene: l’URL su cui si è fatto clic, la data e l’ora del clic e il documento che conteneva l’URL.

>[!NOTE]
>
>Per ulteriori informazioni sulla funzionalità di tracciamento, fare riferimento a [questa pagina](../../delivery/using/delivery-dashboard.md).

