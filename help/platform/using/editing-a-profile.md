---
product: campaign
title: Modifica di un profilo
description: Modifica di un profilo
feature: Profiles
audience: platform
content-type: reference
topic-tags: profile-management
exl-id: 0f3a5582-5c90-4393-bee8-d9e2f07e5982
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 4%

---

# Modificare un profilo{#editing-a-profile}



Per visualizzare le informazioni relative a un profilo, fare clic sul nome nell&#39;elenco dei profili.

I dettagli del profilo vengono visualizzati in una nuova scheda.

![](assets/s_user_recipient_edit.png)

I dati relativi ai profili sono raggruppati in schede.

Le schede e il loro contenuto dipendono dalla configurazione e dai pacchetti installati.

>[!CAUTION]
>
>Lo schema XML e il modulo relativo ai campi della tabella dei profili sono accessibili tramite **[!UICONTROL Administration > Configuration > Data schemas]** della struttura Adobe Campaign. Solo gli utenti esperti possono apportare modifiche a questi schemi.
>
>Per ulteriori informazioni, fare riferimento a [questa pagina](../../configuration/using/about-schema-edition.md).

## Scheda Generale {#general-tab}

Questa schermata contiene tutti i dati generali sul profilo selezionato. In particolare, contiene il cognome, il nome, l’indirizzo e-mail, il formato di ricezione e-mail, ecc. Ecco come si presenta:

![](assets/s_ncs_user_profile_general_tab.png)

>[!NOTE]
>
>Quando **[!UICONTROL No longer contact (by any channel)]** se è selezionata l’opzione, significa che il profilo è in fase di inserisco nell&#39;elenco Bloccati, ovvero ha espresso il desiderio di non essere contattato (ad esempio, facendo clic su un collegamento di annullamento dell’abbonamento in una newsletter). Non saranno più oggetto di consegne su alcun canale (e-mail, direct mailing, ecc.). Per ulteriori informazioni, consulta [questa pagina](../../delivery/using/understanding-quarantine-management.md).

## Scheda Informazioni di contatto {#contact-information-tab}

Questa schermata contiene l’indirizzo di direct mailing del profilo selezionato. Ecco come si presenta:

![](assets/s_ncs_user_profile_details_tab.png)

Questa schermata mostra l’indice di qualità dell’indirizzo e quanti errori contiene l’indirizzo. Queste informazioni vengono utilizzate direttamente dal gestore della posta in base al numero di errori rilevati durante le consegne precedenti e non possono essere modificate manualmente.

## Altra scheda {#other-tab}

Questa schermata contiene campi definiti dall’utente che possono essere personalizzati in base ai requisiti. Puoi anche modificare i nomi dei campi e definirne il formato tramite **[!UICONTROL Field properties...]**, come illustrato di seguito:

![](assets/s_ncs_user_profile_others_tab.png)

>[!NOTE]
>
>Per ulteriori informazioni sulle proprietà dei campi e sull’aggiunta di campi, consulta [questa pagina](../../configuration/using/new-field-wizard.md).

## Scheda Elenchi {#lists-tab}

Questa schermata visualizza i gruppi a cui appartiene il profilo selezionato. Clic **[!UICONTROL Add]** per sottoscrivere il profilo a un elenco. Clic **[!UICONTROL Detail]** per visualizzare la descrizione e l’elenco dei profili nell’elenco selezionato.

![](assets/s_ncs_user_profile_groups_tab_details.png)

Per ulteriori informazioni, consulta [Creare e gestire gli elenchi](../../platform/using/creating-and-managing-lists.md).

## Scheda Iscrizioni {#subscriptions-tab}

Questa schermata contiene i servizi di informazioni a cui il profilo si è abbonato.

![](assets/s_ncs_user_profile_subscript_tab_details.png)

Il **[!UICONTROL Detail]** visualizza le proprietà della sottoscrizione selezionata. Il **[!UICONTROL Add]** per aggiungere manualmente un nuovo abbonamento.

Per ulteriori informazioni, consulta [questa pagina](../../delivery/using/managing-subscriptions.md).

## Scheda Consegne {#deliveries-tab}

In questa schermata vengono visualizzati i registri di consegna per il profilo selezionato. Puoi anche visualizzare le etichette, le date e lo stato delle azioni di consegna indirizzate al profilo tramite tutti i canali.

![](assets/s_ncs_user_profile_delivery_tab.png)

## Scheda Tracciamento {#tracking-tab}

Questa schermata ti consente di visualizzare i registri di tracciamento per il profilo selezionato. Queste informazioni vengono utilizzate per tenere traccia del comportamento del profilo dopo le consegne.

![](assets/s_ncs_user_profile_tracking_tab.png)

Questa scheda mostra il totale cumulativo di tutti gli URL tracciati nelle consegne.

L’elenco è configurabile e in genere contiene: l’URL su cui è stato fatto clic, la data e l’ora del clic e il documento che conteneva l’URL.

>[!NOTE]
>
>Per ulteriori informazioni sulla funzionalità di tracciamento, consulta [questa pagina](../../delivery/using/delivery-dashboard.md).
