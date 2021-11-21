---
product: campaign
title: Modifica di un profilo
description: Modifica di un profilo
audience: platform
content-type: reference
topic-tags: profile-management
exl-id: 0f3a5582-5c90-4393-bee8-d9e2f07e5982
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 5%

---

# Modificare un profilo{#editing-a-profile}

![](../../assets/common.svg)

Per visualizzare le informazioni relative a un profilo, fai clic sul relativo nome nell’elenco dei profili.

I dettagli del profilo vengono visualizzati in una nuova scheda.

![](assets/s_user_recipient_edit.png)

I dati relativi ai profili sono raggruppati in schede.

Le schede e il relativo contenuto dipendono dalla configurazione e dai pacchetti installati.

>[!CAUTION]
>
>Lo schema XML e il modulo che riguarda i campi della tabella dei profili sono accessibili tramite il **[!UICONTROL Administration > Configuration > Data schemas]** nodo della struttura Adobe Campaign. Solo gli utenti esperti possono apportare modifiche a tali schemi.
>
>Per ulteriori informazioni, consulta [questa pagina](../../configuration/using/about-schema-edition.md).

## Scheda Generale {#general-tab}

Questa schermata contiene tutti i dati generali sul profilo selezionato. In particolare, contiene il cognome, il nome, l’indirizzo e-mail, il formato di ricezione e-mail, ecc. Si presenta così:

![](assets/s_ncs_user_profile_general_tab.png)

>[!NOTE]
>
>Quando il **[!UICONTROL No longer contact (by any channel)]** è selezionata l’opzione , il che significa che il profilo è in elenco Bloccati, ovvero il profilo ha espresso il desiderio di non essere contattato (ad esempio, facendo clic su un collegamento di annullamento dell’abbonamento in una newsletter). Non saranno più oggetto di targeting per consegne su alcun canale (e-mail, direct mailing, ecc.). Per ulteriori informazioni, consulta [questa pagina](../../delivery/using/understanding-quarantine-management.md).

## Scheda Informazioni contatto {#contact-information-tab}

Questa schermata contiene l’indirizzo direct mailing del profilo selezionato. Si presenta così:

![](assets/s_ncs_user_profile_details_tab.png)

Questa schermata mostra l&#39;indice di qualità dell&#39;indirizzo, nonché quanti errori contiene l&#39;indirizzo. Queste informazioni vengono utilizzate direttamente dal gestore della posta in base al numero di errori riscontrati durante le consegne precedenti e non possono essere modificate manualmente.

## Scheda Altro {#other-tab}

Questa schermata contiene campi definiti dall’utente che possono essere personalizzati in base ai requisiti. È inoltre possibile modificare i nomi dei campi e definirne il formato tramite **[!UICONTROL Field properties...]**, come illustrato di seguito:

![](assets/s_ncs_user_profile_others_tab.png)

>[!NOTE]
>
>Per ulteriori informazioni sulle proprietà dei campi e sull’aggiunta di campi, consulta [questa pagina](../../configuration/using/new-field-wizard.md).

## Scheda Elenchi {#lists-tab}

In questa schermata vengono visualizzati i gruppi a cui appartiene il profilo selezionato. Fai clic su **[!UICONTROL Add]** per sottoscrivere il profilo a un elenco. Fai clic su **[!UICONTROL Detail]** per visualizzare la descrizione e l’elenco dei profili nell’elenco selezionato.

![](assets/s_ncs_user_profile_groups_tab_details.png)

Per ulteriori informazioni, consulta [Creare e gestire elenchi](../../platform/using/creating-and-managing-lists.md).

## Scheda Abbonamenti {#subscriptions-tab}

Questa schermata contiene i servizi di informazioni a cui il profilo si è iscritto.

![](assets/s_ncs_user_profile_subscript_tab_details.png)

La **[!UICONTROL Detail]** visualizza le proprietà della sottoscrizione selezionata. La **[!UICONTROL Add]** viene utilizzato per aggiungere manualmente una nuova sottoscrizione.

Per ulteriori informazioni, consulta [questa pagina](../../delivery/using/managing-subscriptions.md).

## Scheda Consegne {#deliveries-tab}

In questa schermata vengono visualizzati i registri di consegna per il profilo selezionato. Puoi anche visualizzare le etichette, le date e lo stato delle azioni di consegna indirizzate al profilo tramite tutti i canali.

![](assets/s_ncs_user_profile_delivery_tab.png)

## Scheda Tracking {#tracking-tab}

Questa schermata ti consente di visualizzare i registri di tracciamento per il profilo selezionato. Queste informazioni vengono utilizzate per tenere traccia del comportamento del profilo dopo le consegne.

![](assets/s_ncs_user_profile_tracking_tab.png)

Questa scheda mostra il totale cumulativo di tutti gli URL tracciati nelle consegne.

L’elenco è configurabile e in genere contiene: l’URL che ha fatto clic, la data e l’ora del clic e il documento che conteneva l’URL.

>[!NOTE]
>
>Per ulteriori informazioni sulla funzionalità di tracciamento, consulta [questa pagina](../../delivery/using/delivery-dashboard.md).
