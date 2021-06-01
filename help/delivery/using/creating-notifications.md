---
product: campaign
title: Creazione di notifiche push
description: Scopri come creare le notifiche push
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
exl-id: 13ccc5d6-4355-42ba-80dc-30a45d3b69a4
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '835'
ht-degree: 4%

---

# Creazione di notifiche{#creating-notifications}

Questa sezione descrive gli elementi specifici per la consegna delle notifiche iOS e Android. I concetti globali sulla creazione della consegna sono descritti in [questa sezione](../../delivery/using/steps-about-delivery-creation-steps.md).

Inizia creando una nuova consegna.

![](assets/nmac_delivery_1.png)

## Invio di notifiche su iOS {#sending-notifications-on-ios}

1. Seleziona il modello di consegna **[!UICONTROL Deliver on iOS]**.

   ![](assets/nmac_delivery_ios_1.png)

1. Per definire la destinazione della notifica, fai clic sul collegamento **[!UICONTROL To]** , quindi fai clic su **[!UICONTROL Add]**.

   ![](assets/nmac_delivery_ios_2.png)

   >[!NOTE]
   >
   >Il processo dettagliato durante la selezione della popolazione target di una consegna è presentato in [questa sezione](../../delivery/using/steps-defining-the-target-population.md).
   >
   >Per ulteriori informazioni sull’utilizzo dei campi di personalizzazione, consulta [Informazioni sulla personalizzazione](../../delivery/using/about-personalization.md).
   >
   >Per ulteriori informazioni sull&#39;inclusione di un elenco di seed, consulta [Informazioni sugli indirizzi di seed](../../delivery/using/about-seed-addresses.md).

1. Seleziona **[!UICONTROL Subscribers of an iOS mobile application (iPhone, iPad)]**, seleziona il servizio pertinente alla tua app mobile (in questo caso Neotrips), quindi seleziona la versione iOS dell&#39;applicazione.

   ![](assets/nmac_delivery_ios_3.png)

1. Seleziona il tipo di notifica: **[!UICONTROL Alert]**, **[!UICONTROL Badge]** o **[!UICONTROL Alert and badge]** o **[!UICONTROL Silent Push]**.

   ![](assets/nmac_delivery_ios_4.png)

   >[!NOTE]
   >
   >La modalità **Silent Push** è disponibile da iOS 7. Questo consente di inviare una notifica &quot;silenziosa&quot; a un’app mobile. L&#39;utente non viene informato dell&#39;arrivo della notifica. Viene trasferito direttamente all&#39;applicazione.

1. Nel campo **[!UICONTROL Title]** , immetti l’etichetta del titolo che desideri visualizzare nella notifica. Viene visualizzato solo nell’elenco delle notifiche disponibili dal centro notifiche. Questo campo ti consente di definire il valore del parametro **title** del payload di notifica iOS.

1. Se utilizzi il connettore HTTP/2, puoi aggiungere un sottotitolo (valore del parametro **subtitle** del payload di notifica iOS). Consulta la sezione [Configurazione dell’app mobile in Adobe Campaign](../../delivery/using/configuring-the-mobile-application.md) .

1. Quindi immetti **[!UICONTROL Message]** e **[!UICONTROL Value of the badge]** in base al tipo di notifica scelto.

   ![](assets/nmac_delivery_ios_5.png)

   >[!NOTE]
   >
   >**[!UICONTROL Badge]** le notifiche di  **[!UICONTROL Alert and badge]** tipo e ti consentono di modificare il valore del badge (il numero sopra il logo dell’app mobile). Per aggiornare il badge, è sufficiente immettere 0 come valore. Se il campo è vuoto, il valore del badge non viene modificato.

1. Fai clic sull’icona **[!UICONTROL Insert emoticon]** per inserire gli emoticon nella notifica push. Per personalizzare l’elenco delle emoticon, consulta [personalizzazione dell’elenco delle emoticon](../../delivery/using/customizing-emoticon-list.md)

1. Il **[!UICONTROL Action button]** ti consente di definire un’etichetta per il pulsante di azione visualizzato nel campo notifiche di avviso (**action_loc_key** del payload). Se l&#39;applicazione iOS gestisce stringhe localizzabili (**Localizable.strings**), immetti la chiave corrispondente in questo campo. Se l&#39;applicazione non gestisce il testo localizzabile, immettere l&#39;etichetta che si desidera visualizzare sul pulsante dell&#39;azione. Per ulteriori informazioni sulle stringhe localizzabili, consulta la [documentazione Apple](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/CreatingtheNotificationPayload.html#//apple_ref/doc/uid/TP40008194-CH10-SW1) .
1. Nel campo **[!UICONTROL Play a sound]** , seleziona il suono che deve essere riprodotto dal terminale mobile quando viene ricevuta la notifica.

   >[!NOTE]
   >
   >I suoni devono essere inclusi nell&#39;applicazione e definiti al momento della creazione del servizio. Consulta [Configurazione dell&#39;account esterno iOS](../../delivery/using/configuring-the-mobile-application.md#configuring-external-account-ios).

1. Nel campo **[!UICONTROL Application variables]** , immetti il valore di ciascuna variabile. Le variabili di applicazione consentono di definire il comportamento di notifica: ad esempio, puoi configurare una schermata specifica dell’applicazione da visualizzare quando l’utente attiva la notifica.

   >[!NOTE]
   >
   >Le variabili di applicazione devono essere definite nel codice dell’app mobile e immesse durante la creazione del servizio. Per ulteriori informazioni, consulta: [Configurazione di un’app mobile in Adobe Campaign](../../delivery/using/configuring-the-mobile-application.md).

1. Una volta configurata la notifica, fai clic sulla scheda **[!UICONTROL Preview]** per visualizzare l’anteprima della notifica.

   ![](assets/nmac_intro_2.png)

   >[!NOTE]
   >
   >Lo stile della notifica (banner o avviso) non è definito in Adobe Campaign. Dipende dalla configurazione selezionata dall’utente nelle impostazioni iOS. Tuttavia, Adobe Campaign ti consente di visualizzare in anteprima ogni tipo di stile di notifica. Fare clic sulla freccia in basso a destra per passare da uno stile all’altro.
   >
   >L’anteprima utilizza l’aspetto e il comportamento di iOS 10.

Per inviare una bozza e la consegna finale, utilizza lo stesso processo delle consegne e-mail.

Dopo aver inviato i messaggi, puoi monitorare e tenere traccia delle consegne. Per ulteriori informazioni, consulta queste sezioni:

* [quarantene di notifiche push](../../delivery/using/understanding-quarantine-management.md#push-notification-quarantines)
* [Monitoraggio di una consegna](../../delivery/using/about-delivery-monitoring.md)
* [Informazioni sugli errori di consegna](../../delivery/using/understanding-delivery-failures.md)

## Invio di notifiche su Android {#sending-notifications-on-android}

1. Inizia selezionando il modello di consegna **[!UICONTROL Deliver on Android (android)]** .

   ![](assets/nmac_delivery_android_1.png)

1. Per definire la destinazione della notifica, fai clic sul collegamento **[!UICONTROL To]** , quindi fai clic su **[!UICONTROL Add]**.

   ![](assets/nmac_delivery_android_2.png)

1. Seleziona **[!UICONTROL Subscribers of an Android mobile application]**, scegli il servizio pertinente alla tua app mobile (in questo caso Neotrips), quindi seleziona la versione Android dell&#39;applicazione.

   ![](assets/nmac_delivery_android_3.png)

1. Quindi inserisci il contenuto della notifica.

   ![](assets/nmac_delivery_android_4.png)

1. Fai clic sull’icona **[!UICONTROL Insert emoticon]** per inserire gli emoticon nella notifica push. Per personalizzare l’elenco delle emoticon, consulta [personalizzazione dell’elenco delle emoticon](../../delivery/using/defining-interactive-content.md)

1. Nel campo **[!UICONTROL Application variables]** , immetti il valore di ciascuna variabile. Le variabili di applicazione consentono di definire il comportamento di notifica: ad esempio, puoi configurare una schermata specifica dell’applicazione da visualizzare quando l’utente attiva la notifica.

   >[!NOTE]
   >
   >Le variabili di applicazione devono essere definite nel codice dell’app mobile e immesse durante la creazione del servizio. Per ulteriori informazioni, consulta: [Configurazione di un’app mobile in Adobe Campaign](../../delivery/using/configuring-the-mobile-application.md).

1. Una volta configurata la notifica, fai clic sulla scheda **[!UICONTROL Preview]** per visualizzare l’anteprima della notifica.

   ![](assets/nmac_intro_1.png)

Per inviare una bozza e la consegna finale, utilizza lo stesso processo delle consegne e-mail.

Il processo dettagliato di convalida e invio di una consegna è presentato nelle sezioni seguenti:

* [Convalida della consegna](../../delivery/using/steps-validating-the-delivery.md)
* [Invio della consegna](../../delivery/using/steps-sending-the-delivery.md)

Dopo aver inviato i messaggi, puoi monitorare e tenere traccia delle consegne. Per ulteriori informazioni, consulta queste sezioni:

* [quarantene di notifiche push](../../delivery/using/understanding-quarantine-management.md#push-notification-quarantines)
* [Monitoraggio di una consegna](../../delivery/using/about-delivery-monitoring.md)
* [Informazioni sugli errori di consegna](../../delivery/using/understanding-delivery-failures.md)
