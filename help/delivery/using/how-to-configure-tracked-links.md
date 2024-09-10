---
product: campaign
title: Come configurare i collegamenti tracciati
description: Come configurare i collegamenti tracciati
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Monitoring
role: User, Developer
exl-id: ed88e1d6-c0d5-4a85-9f3e-be670f4bcc10
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 10%

---

# Come configurare i collegamenti tracciati{#how-to-configure-tracked-links}



Per ogni consegna, puoi tracciare la ricezione dei messaggi e l’attivazione dei collegamenti inseriti nel contenuto del messaggio. In questo modo puoi tracciare il comportamento dei destinatari in seguito alle azioni di consegna per le quali sono stati oggetto di targeting.

Il tracciamento si applica ai messaggi, ma il tracciamento web consente di monitorare il modo in cui i destinatari navigano in un sito web (pagine visitate, acquisti). La configurazione del tracciamento web è descritta in [questa sezione](../../configuration/using/about-web-tracking.md).

>[!NOTE]
>
>I collegamenti nel contenuto delle e-mail che contengono la personalizzazione devono essere tracciati con una sintassi specifica. Per ulteriori informazioni su come aggiungere nelle e-mail collegamenti che possono essere personalizzati e che supportano il tracciamento, consulta [questa sezione](tracking-personalized-links.md).

Si consiglia vivamente di includere gli URL nei delimitatori nella scheda **[!UICONTROL Text content]** prima di applicare la formula di tracciamento. I delimitatori URL immessi in questa scheda vengono utilizzati da Adobe Campaign per identificare gli URL all’interno delle stringhe di caratteri. Puoi utilizzare queste coppie di delimitatori:
* Parentesi ( )
* Parentesi [ ]
* Parentesi graffe { }

In questo esempio, l&#39;URL https://www.adobe.com è seguito da un punto e virgola. Il punto e virgola può essere interpretato dai client e-mail dei destinatari come parte dell’URL. Di conseguenza, il collegamento potrebbe essere interrotto. Per evitare questo problema, puoi racchiudere l’URL nei delimitatori in uno dei seguenti modi:
* (https://www.adobe.com)
* [https://www.adobe.com];
* {https://www.adobe.com};

Il tracciamento dei messaggi è abilitato per impostazione predefinita. Per personalizzare il tracciamento degli URL, effettua le seguenti operazioni:

1. Seleziona l’opzione **[!UICONTROL Display URLs]** nella sezione inferiore dell’assistente alla consegna, sotto il contenuto del messaggio.

   ![](assets/s_ncs_user_email_del_display_urls.png)

   Quando selezioni un URL dall’elenco degli URL tracciati, questo viene evidenziato nel contenuto della consegna, ad eccezione del collegamento nella pagina speculare e del collegamento di annullamento dell’abbonamento forniti per impostazione predefinita.

   ![](assets/s_ncs_user_email_del_show_urls.png)

1. Per ogni URL del messaggio, seleziona se attivare o meno il tracciamento.

   >[!IMPORTANT]
   >
   >Quando l’URL del collegamento viene utilizzato come etichetta, si consiglia di disattivare il tracciamento per evitare rischi di rifiuto a causa del phishing.
   >
   >Ad esempio, se l’URL www.adobe.com è inserito nel messaggio e il tracciamento è attivato, il contenuto del collegamento ipertestuale verrà modificato in https://nlt.adobe.net/r/?id=xxxxxx. Ciò significa che potrebbe essere considerato come fraudolento dai clienti dei messaggi dei destinatari.

1. Se necessario, modifica l’etichetta di tracciamento, fai doppio clic sull’etichetta e immettine una nuova.

   >[!NOTE]
   >
   >È possibile modificare le etichette degli URL tracciati e delle etichette per semplificare la lettura delle informazioni durante il tracciamento delle consegne. Due URL o due etichette con lo stesso nome verranno sommati durante il calcolo del conteggio dei clic.

1. Se necessario, modificare la modalità di tracciamento, selezionare una nuova modalità nella colonna **[!UICONTROL Tracking]** che corrisponda al collegamento di destinazione, come illustrato di seguito:

   ![](assets/s_ncs_user_select_tracking_mode.png)

   Per ogni singolo URL, puoi impostare la modalità di tracciamento su uno dei seguenti valori:

   * **[!UICONTROL Enabled]** : attiva il tracciamento su questo URL.
   * **[!UICONTROL Not tracked]** : disattiva il tracciamento su questo URL.
   * **[!UICONTROL Always enabled]** : attiva sempre il tracciamento di questo URL. Queste informazioni vengono salvate in modo che, se l’URL viene nuovamente visualizzato in un messaggio futuro, il suo tracciamento viene attivato automaticamente.
   * **[!UICONTROL Never tracked]** : non attiva mai il tracciamento di questo URL. Queste informazioni vengono salvate in modo che, se l’URL viene nuovamente visualizzato in un messaggio futuro, il suo tracciamento verrà disattivato automaticamente.
   * **[!UICONTROL Opt-out]** : considera questo URL come URL di rinuncia o di annullamento dell&#39;abbonamento.
   * **[!UICONTROL Mirror page]** : considera questo URL come un URL della pagina mirror.

1. È inoltre possibile selezionare una categoria per ogni URL tracciato nell&#39;elenco a discesa della colonna **[!UICONTROL Category]**. Queste categorie possono essere visualizzate come report, ad esempio in **[!UICONTROL URLs and click streams]** (vedi [questa sezione](../../reporting/using/reports-on-deliveries.md#urls-and-click-streams)). Le categorie sono definite in un&#39;enumerazione specifica: **[!UICONTROL urlCategory]** (vedere [Gestione delle enumerazioni](../../platform/using/managing-enumerations.md)).
