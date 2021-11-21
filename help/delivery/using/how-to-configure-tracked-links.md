---
product: campaign
title: Come configurare i collegamenti tracciati
description: Come configurare i collegamenti tracciati
audience: delivery
content-type: reference
topic-tags: tracking-messages
exl-id: ed88e1d6-c0d5-4a85-9f3e-be670f4bcc10
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 10%

---

# Come configurare i collegamenti tracciati{#how-to-configure-tracked-links}

![](../../assets/common.svg)

Per ogni consegna, puoi tracciare la ricezione dei messaggi e l’attivazione dei collegamenti inseriti nel contenuto del messaggio. In questo modo puoi tracciare il comportamento dei destinatari in seguito alle azioni di consegna per le quali sono stati oggetto di targeting.

Il tracciamento si applica ai messaggi, ma il web tracking consente di monitorare il modo in cui i destinatari navigano in un sito web (pagine visitate, acquisti). La configurazione del tracciamento web è descritta in [questa sezione](../../configuration/using/about-web-tracking.md).

>[!NOTE]
>
>I collegamenti nel contenuto delle e-mail che contengono personalizzazioni devono essere tracciati con una sintassi specifica. Per ulteriori informazioni su come aggiungere collegamenti nelle e-mail che possono essere personalizzati e che supportano il tracciamento, consulta [questa sezione](tracking-personalized-links.md).

È consigliabile racchiudere gli URL nei delimitatori nel **[!UICONTROL Text content]** prima di applicare la formula di tracciamento. I delimitatori URL immessi in questa scheda vengono utilizzati da Adobe Campaign per identificare gli URL all’interno delle stringhe di caratteri. È possibile utilizzare queste coppie di delimitatori:
* Parentesi ( )
* Parentesi [ ]
* Bracce { }

In questo esempio, l’URL https://www.adobe.com è seguito da un punto e virgola. Il punto e virgola può essere interpretato dai client e-mail dei destinatari come parte dell’URL. Di conseguenza, il collegamento potrebbe non funzionare. Per evitare questo problema, puoi racchiudere l’URL nei delimitatori in uno dei seguenti modi:
* (https://www.adobe.com);
* [https://www.adobe.com];
* {https://www.adobe.com};

Il tracciamento dei messaggi è abilitato per impostazione predefinita. Per personalizzare il tracciamento degli URL, effettua le seguenti operazioni:

1. Seleziona la **[!UICONTROL Display URLs]** nella sezione inferiore della procedura guidata di consegna, sotto il contenuto del messaggio.

   ![](assets/s_ncs_user_email_del_display_urls.png)

   Quando selezioni un URL dall’elenco degli URL tracciati, questo viene evidenziato nel contenuto della consegna, ad eccezione del collegamento nella pagina speculare e del collegamento di annullamento all’abbonamento fornito per impostazione predefinita.

   ![](assets/s_ncs_user_email_del_show_urls.png)

1. Per ogni URL del messaggio, seleziona se attivare o meno il tracciamento.

   >[!IMPORTANT]
   >
   >Quando l’URL del collegamento viene utilizzato come etichetta, si consiglia di disattivare il tracciamento per evitare i rischi di rifiuto dovuti al phishing.
   >
   >Ad esempio, se l’URL www.adobe.com viene inserito nel messaggio e viene attivato il tracciamento, il contenuto del collegamento ipertestuale verrà modificato in https://nlt.adobe.net/r/?id=xxxxxx. Ciò significa che potrebbe essere considerato fraudolento dai client di messaggi dei destinatari.

1. Se necessario, modifica l’etichetta di tracciamento, fai doppio clic sull’etichetta e immetti una nuova.

   >[!NOTE]
   >
   >Le etichette degli URL tracciati e delle etichette possono essere modificate per semplificare la lettura delle informazioni durante il tracciamento delle consegne. Nel calcolo del numero di clic verranno aggiunti insieme due URL o due etichette con lo stesso nome.

1. Se necessario, modifica la modalità di tracciamento, seleziona una nuova modalità nel **[!UICONTROL Tracking]** che corrisponde al collegamento di destinazione, come illustrato di seguito:

   ![](assets/s_ncs_user_select_tracking_mode.png)

   Per ogni singolo URL, puoi impostare la modalità di tracciamento su uno dei seguenti valori:

   * **[!UICONTROL Enabled]** : attiva il tracciamento su questo URL.
   * **[!UICONTROL Not tracked]** : disattiva il tracciamento su questo URL.
   * **[!UICONTROL Always enabled]** : attiva sempre il tracciamento di questo URL. Queste informazioni vengono salvate in modo che la prossima volta, se l’URL viene visualizzato nuovamente in un contenuto di messaggio futuro, il relativo tracciamento venga attivato automaticamente.
   * **[!UICONTROL Never tracked]** : non attiva mai il tracciamento di questo URL. Queste informazioni vengono salvate in modo che la prossima volta, se l’URL viene visualizzato di nuovo in un messaggio futuro, il relativo tracciamento venga disattivato automaticamente.
   * **[!UICONTROL Opt-out]** : considera questo URL come un URL di rinuncia o di annullamento dell’abbonamento.
   * **[!UICONTROL Mirror page]** : considera questo URL come un URL della pagina speculare.

1. Inoltre, puoi selezionare una categoria per ogni URL tracciato nell’elenco a discesa della **[!UICONTROL Category]** colonna. Queste categorie possono visualizzare rapporti, come ad esempio in **[!UICONTROL URLs and click streams]** (vedi [questa sezione](../../reporting/using/reports-on-deliveries.md#urls-and-click-streams)). Le categorie sono definite in un’enumerazione specifica: **[!UICONTROL urlCategory]** (vedi [Gestione delle enumerazioni](../../platform/using/managing-enumerations.md)).
