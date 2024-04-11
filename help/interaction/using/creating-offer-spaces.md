---
product: campaign
title: Creazione di spazi dell’offerta
description: Creazione di spazi dell’offerta
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: managing-environments
exl-id: bdda98f7-a083-4f3b-b691-c28ec79af780
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '986'
ht-degree: 0%

---

# Creazione di spazi dell’offerta{#creating-offer-spaces}



La creazione dello spazio dell’offerta può essere eseguita solo da un **amministratore tecnico** con accesso alla sottocartella spazio offerte. Gli spazi dell’offerta possono essere creati solo nell’ambiente di progettazione e vengono duplicati automaticamente nell’ambiente live durante l’approvazione dell’offerta.

Il contenuto delle offerte di catalogo è configurato negli spazi dell’offerta. Per impostazione predefinita, il contenuto può includere i campi seguenti: **[!UICONTROL Title]**, **[!UICONTROL Destination URL]**, **[!UICONTROL Image URL]**, **[!UICONTROL HTML content]** e **[!UICONTROL Text content]**. La sequenza di campi viene configurata nello spazio dell’offerta.

I parametri avanzati ti consentono di specificare una chiave di identificazione del contatto (che può essere costituita da vari elementi, ad esempio il nome e il campo e-mail contemporaneamente). Per ulteriori informazioni, consulta [Presentazione di un’offerta identificata](../../interaction/using/integration-via-javascript-client-side.md#presenting-an-identified-offer) sezione.

Il rendering HTML o XML viene creato tramite una funzione di rendering. La sequenza dei campi definiti nella funzione di rendering deve essere identica alla sequenza configurata nel contenuto.

![](assets/offer_space_create_009.png)

Per creare un nuovo spazio dell’offerta, applica il seguente processo:

1. Vai all’elenco degli spazi dell’offerta e fai clic su **[!UICONTROL New]**.

   ![](assets/offer_space_create_001.png)

1. Seleziona il canale da utilizzare e cambia l’etichetta dello spazio dell’offerta.

   ![](assets/offer_space_create_002.png)

1. Controlla la **[!UICONTROL Enable unitary mode]** casella se si verifica una delle seguenti situazioni:

   * Si sta utilizzando l’interazione con il Centro messaggi
   * Stai utilizzando la modalità unitaria dell’interazione (interazioni in entrata)

1. Vai a **[!UICONTROL Content field]** e fai clic su **[!UICONTROL Add]**.

   ![](assets/offer_space_create_003.png)

1. Vai a **[!UICONTROL Content]** e selezionare i campi nell&#39;ordine seguente: **[!UICONTROL Title]**, quindi **[!UICONTROL Image URL]**, quindi **[!UICONTROL HTML content]**, quindi **[!UICONTROL Destination URL]**.

   ![](assets/offer_space_create_004.png)

1. Controlla la **[!UICONTROL Required]** per rendere obbligatorio ogni campo.

   >[!NOTE]
   >
   >Questa configurazione viene utilizzata nell’anteprima e rende non validi gli spazi dell’offerta durante la pubblicazione se uno degli elementi obbligatori risulta mancante nell’offerta in questione. Tuttavia, se un’offerta è già live in uno spazio dell’offerta, questi criteri non vengono presi in considerazione.

   ![](assets/offer_space_create_005.png)

1. Clic **[!UICONTROL Edit functions]** per creare una funzione di rendering.

   Queste funzioni vengono utilizzate per generare rappresentazioni di offerta in uno spazio dell’offerta. Esistono diversi formati possibili: HTML o testo per le interazioni in uscita e XML per le interazioni in entrata.

   ![](assets/offer_space_create_006.png)

1. Vai a **[!UICONTROL HTML rendering]** e seleziona **[!UICONTROL Overload the HTML rendering function]**.
1. Inserire la funzione di rendering.

   ![](assets/offer_space_create_007.png)

Se necessario, è possibile sovraccaricare le funzioni di rendering XML per le interazioni in entrata. È inoltre possibile sovraccaricare le funzioni di HTML e di rendering del testo per le interazioni in uscita. Per ulteriori informazioni, consulta [Informazioni sui canali in entrata](../../interaction/using/about-inbound-channels.md).

## Stati delle proposte di offerta {#offer-proposition-statuses}

Una proposta di offerta può avere diversi stati a seconda delle interazioni con la popolazione target. L’interazione viene fornita con un insieme di valori che possono essere applicati alla proposta di offerta durante il suo ciclo di vita. Tuttavia, dovrai configurare la piattaforma in modo che lo stato cambi quando la proposta di offerta viene creata e accettata.

>[!NOTE]
>
>Lo stato della proposta di offerta non viene aggiornato immediatamente. Viene eseguito dal flusso di lavoro di tracciamento che viene attivato ogni ora.

### Elenco di stato {#status-list}

L’interazione viene fornita con i seguenti valori che possono essere utilizzati per qualificare lo stato di una proposta di offerta:

* **[!UICONTROL Accepted]**.
* **[!UICONTROL Scheduled]**.
* **[!UICONTROL Generated]**.
* **[!UICONTROL Interested]**.
* **[!UICONTROL Presented]**.
* **[!UICONTROL Rejected]**.

Questi valori non vengono applicati per impostazione predefinita: devono essere configurati.

>[!NOTE]
>
>Lo stato di una proposta di offerta verrà automaticamente modificato in &quot;Presentata&quot; se l’offerta è collegata a una consegna con lo stato &quot;Inviata&quot;.

### Configurazione dello stato al momento della creazione della proposta {#configuring-the-status-when-the-proposition-is-created}

Quando una proposta di offerta viene creata dal motore di interazione, il suo stato viene modificato, sia che si tratti di un’interazione in entrata che in uscita. La scelta tra questi due valori dipende dal modo in cui gli spazi dell’offerta sono stati configurati nel **[!UICONTROL Design]** ambiente

Per ogni spazio, puoi configurare lo stato che desideri applicare al momento della creazione di una proposta, in base alle informazioni che desideri visualizzare nei rapporti delle offerte.

A questo scopo, utilizza il seguente processo:

1. Vai a **[!UICONTROL Storage]** dello spazio desiderato.
1. Seleziona lo stato da applicare alla proposta al momento della sua creazione.

   ![](assets/offer_update_status_001.png)

### Configurazione dello stato quando la proposta viene accettata {#configuring-the-status-when-the-proposition-is-accepted}

Una volta accettata una proposta di offerta, puoi utilizzare uno dei valori forniti per impostazione predefinita per configurare il nuovo stato della proposta. L’aggiornamento è effettivo quando un destinatario fa clic su un collegamento nell’offerta, che richiama il motore di interazione.

A questo scopo, utilizza il seguente processo:

1. Vai a **[!UICONTROL Storage]** dello spazio desiderato.
1. Seleziona lo stato da applicare alla proposta quando viene accettata.

   ![](assets/offer_update_status_002.png)

**Interazione in entrata**

Il **[!UICONTROL Storage]** consente di definire gli stati per **proposto** e **accettato** solo proposte di offerta. Per l’interazione in entrata, lo stato delle proposte di offerta deve essere specificato direttamente nell’URL per la chiamata al motore di offerta, anziché tramite l’interfaccia. In questo modo, potrai specificare lo stato da applicare in altri casi, ad esempio se una proposta di offerta viene rifiutata.

```
<BASE_URL>?a=UpdateStatus&p=<PRIMARY_KEY_OF_THE_PROPOSITION>&st=<NEW_STATUS_OF_THE_PROPOSITION>&r=<REDIRECT_URL>
```

Ad esempio, la proposta (identificatore) **40004**) che corrisponde al **Assicurazione sulla casa** offerta visualizzata sul **Neobank** Il sito contiene il seguente URL:

```
<BASE_URL>?a=UpdateStatus&p=<40004>&st=<3>&r=<"http://www.neobank.com/insurance/subscribe.html">
```

Non appena un visitatore fa clic sull’offerta, e quindi sull’URL, **[!UICONTROL Accepted]** stato (valore) **3**) viene applicata alla proposta e il visitatore viene reindirizzato a una nuova pagina della **Neobank** per stipulare il contratto di assicurazione.

>[!NOTE]
>
>Se desideri specificare un altro stato nell’URL (ad esempio se una proposta di offerta viene rifiutata), utilizza il valore corrispondente allo stato desiderato. Esempio: **[!UICONTROL Rejected]** = &quot;5&quot; **[!UICONTROL Presented]** = &quot;1&quot; ecc.
>
>Gli stati e i relativi valori possono essere recuperati in **[!UICONTROL Offer propositions (nms)]** schema dati. Per ulteriori informazioni, consulta [questa pagina](../../configuration/using/data-schemas.md).

**Interazione in uscita**

In caso di interazione in uscita, puoi applicare automaticamente **[!UICONTROL Interested]** lo stato di una proposta di offerta quando la consegna contiene un collegamento. Aggiungi semplicemente il **_urlType=&quot;11&quot;** valore per il collegamento:

```
<a _urlType="11" href="<DEST_URL>">Link inserted into the delivery</a>
```

## Anteprima offerta per spazio {#offer-preview-per-space}

In questa scheda puoi visualizzare le offerte per le quali il destinatario è idoneo tramite un metodo scelto. Nell’esempio che segue, il destinatario può presentare tre proposte di offerta per posta.

![](assets/offer_space_overview_002.png)

Se un destinatario non è idoneo per nessuna offerta, ciò viene mostrato nell’anteprima.

![](assets/offer_space_overview_001.png)

L’anteprima può ignorare i contesti quando sono limitati a uno spazio. Questo si verifica quando lo schema di interazione è stato esteso per aggiungere campi a cui si fa riferimento in uno spazio utilizzando un canale in entrata (per ulteriori informazioni, consulta [Esempio di estensione](../../interaction/using/extension-example.md)).
