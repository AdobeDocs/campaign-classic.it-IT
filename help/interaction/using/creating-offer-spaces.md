---
product: campaign
title: Creazione di spazi di offerta
description: Creazione di spazi di offerta
audience: interaction
content-type: reference
topic-tags: managing-environments
exl-id: bdda98f7-a083-4f3b-b691-c28ec79af780
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 1%

---

# Creazione di spazi di offerta{#creating-offer-spaces}

La creazione di spazio di offerta può essere eseguita solo da un **amministratore tecnico** con accesso alla sottocartella spazio di offerta. Gli spazi di offerta possono essere creati solo nell’ambiente di progettazione e vengono automaticamente duplicati nell’ambiente live durante l’approvazione dell’offerta.

Il contenuto delle offerte del catalogo viene configurato negli spazi delle offerte. Per impostazione predefinita, il contenuto può includere i campi seguenti: **[!UICONTROL Title]**, **[!UICONTROL Destination URL]**, **[!UICONTROL Image URL]**, **[!UICONTROL HTML content]** e **[!UICONTROL Text content]**. La sequenza di campi è configurata nello spazio di offerta.

I parametri avanzati consentono di specificare una chiave di identificazione del contatto (che può essere composta da vari elementi, ad esempio il nome e il campo e-mail contemporaneamente). Per ulteriori informazioni, consulta la sezione [Presentazione di un’offerta identificata](../../interaction/using/integration-via-javascript--client-side-.md#presenting-an-identified-offer) .

Il rendering HTML o XML viene creato tramite una funzione di rendering. La sequenza dei campi definiti nella funzione di rendering deve essere identica alla sequenza configurata nel contenuto.

![](assets/offer_space_create_009.png)

Per creare un nuovo spazio di offerta, applica il seguente processo:

1. Vai all’elenco degli spazi di offerta e fai clic su **[!UICONTROL New]**.

   ![](assets/offer_space_create_001.png)

1. Seleziona il canale da utilizzare e modifica l’etichetta dello spazio di offerta.

   ![](assets/offer_space_create_002.png)

1. Seleziona la casella **[!UICONTROL Enable unitary mode]** se si applica uno dei seguenti casi:

   * Stai utilizzando Interazione con Centro messaggi
   * Stai utilizzando la modalità unitaria di Interaction (interazioni in entrata)

1. Vai alla finestra **[!UICONTROL Content field]** e fai clic su **[!UICONTROL Add]**.

   ![](assets/offer_space_create_003.png)

1. Vai al nodo **[!UICONTROL Content]** e seleziona i campi nel seguente ordine: **[!UICONTROL Title]**, quindi **[!UICONTROL Image URL]**, **[!UICONTROL HTML content]**, quindi **[!UICONTROL Destination URL]**.

   ![](assets/offer_space_create_004.png)

1. Seleziona la casella **[!UICONTROL Required]** per rendere obbligatorio ogni campo.

   >[!NOTE]
   >
   >Questa configurazione viene utilizzata nell’anteprima e rende gli spazi di offerta non validi durante la pubblicazione se nell’offerta in questione manca uno degli elementi obbligatori. Tuttavia, se un’offerta è già attiva in uno spazio di offerta, questi criteri non vengono presi in considerazione.

   ![](assets/offer_space_create_005.png)

1. Fai clic su **[!UICONTROL Edit functions]** per creare una funzione di rendering.

   Queste funzioni vengono utilizzate per generare rappresentazioni di offerte su uno spazio di offerta. Esistono diversi formati possibili: HTML o testo per le interazioni in uscita e XML per le interazioni in entrata.

   ![](assets/offer_space_create_006.png)

1. Vai alla scheda **[!UICONTROL HTML rendering]** e seleziona **[!UICONTROL Overload the HTML rendering function]**.
1. Inserisci la funzione di rendering.

   ![](assets/offer_space_create_007.png)

Se necessario, puoi sovraccaricare le funzioni di rendering XML per le interazioni in entrata. Puoi anche sovraccaricare le funzioni di rendering HTML e testo per le interazioni in uscita. Per ulteriori informazioni, consulta [Informazioni sui canali in entrata](../../interaction/using/about-inbound-channels.md).

## Stato delle proposte di offerta {#offer-proposition-statuses}

Una proposta di offerta può avere vari stati a seconda delle interazioni con la popolazione target. L’interazione viene fornita con un set di valori che possono essere applicati alla proposta di offerta per tutto il suo ciclo di vita. Tuttavia, dovrai configurare la piattaforma in modo che lo stato cambi quando la proposta di offerta viene creata e accettata.

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

Questi valori non vengono applicati per impostazione predefinita: devono essere configurate.

>[!NOTE]
>
>Lo stato di una proposta di offerta viene automaticamente modificato in &quot;Presentato&quot; se l’offerta è collegata a una consegna con lo stato &quot;Inviato&quot;.

### Configurazione dello stato di creazione della proposta {#configuring-the-status-when-the-proposition-is-created}

Quando una proposta di offerta viene creata dal motore di interazione, il suo stato viene modificato, sia che si tratti di un’interazione in entrata che in uscita. La scelta tra questi due valori dipende dal modo in cui gli spazi di offerta sono stati configurati nell’ambiente **[!UICONTROL Design]**

Per ogni spazio, puoi configurare lo stato da applicare alla creazione di una proposta, in base alle informazioni da visualizzare nei rapporti delle offerte.

A questo scopo, utilizza il seguente processo:

1. Passa alla scheda **[!UICONTROL Storage]** dello spazio desiderato.
1. Selezionare lo stato da applicare alla proposta al momento della creazione.

   ![](assets/offer_update_status_001.png)

### Configurazione dello stato quando la proposta viene accettata {#configuring-the-status-when-the-proposition-is-accepted}

Una volta accettata la proposta di offerta, puoi utilizzare uno dei valori forniti per impostazione predefinita per configurare il nuovo stato della proposta. L’aggiornamento è efficace quando un destinatario fa clic su un collegamento nell’offerta, che richiama il motore di interazione.

A questo scopo, utilizza il seguente processo:

1. Passa alla scheda **[!UICONTROL Storage]** dello spazio desiderato.
1. Selezionare lo stato da applicare alla proposta quando viene accettata.

   ![](assets/offer_update_status_002.png)

**Interazione in entrata**

La scheda **[!UICONTROL Storage]** ti consente di definire gli stati solo per le proposte di offerta **proposte** e **accettate**. Per l’interazione in entrata, lo stato delle proposte di offerta deve essere specificato direttamente nell’URL per la chiamata al motore di offerta, anziché tramite l’interfaccia. In questo modo, potrai specificare quale stato applicare in altri casi, ad esempio se una proposta di offerta viene rifiutata.

```
<BASE_URL>?a=UpdateStatus&p=<PRIMARY_KEY_OF_THE_PROPOSITION>&st=<NEW_STATUS_OF_THE_PROPOSITION>&r=<REDIRECT_URL>
```

Ad esempio, la proposta (identificatore **40004**) che corrisponde all&#39;offerta **Home Insurance** visualizzata sul sito **Neobank** contiene il seguente URL:

```
<BASE_URL>?a=UpdateStatus&p=<40004>&st=<3>&r=<"http://www.neobank.com/insurance/subscribe.html">
```

Non appena un visitatore fa clic sull’offerta e quindi sull’URL, viene applicato lo stato **[!UICONTROL Accepted]** (valore **3**) alla proposta e il visitatore viene reindirizzato a una nuova pagina del sito **Neobank** per eliminare il contratto di assicurazione.

>[!NOTE]
>
>Se desideri specificare un altro stato nell’url (ad esempio se una proposta di offerta viene rifiutata), utilizza il valore corrispondente allo stato desiderato. Esempio: **[!UICONTROL Rejected]** = &quot;5&quot;, **[!UICONTROL Presented]** = &quot;1&quot; e così via.
>
>Gli stati e i relativi valori possono essere recuperati nello schema dati **[!UICONTROL Offer propositions (nms)]** . Per ulteriori informazioni, consulta [questa pagina](../../configuration/using/data-schemas.md).

**Interazione in uscita**

In caso di interazione in uscita, puoi applicare automaticamente lo stato **[!UICONTROL Interested]** a una proposta di offerta quando la consegna contiene un collegamento. Aggiungi semplicemente il valore **_urlType=&quot;11&quot;** al collegamento:

```
<a _urlType="11" href="<DEST_URL>">Link inserted into the delivery</a>
```

## Anteprima offerta per spazio {#offer-preview-per-space}

In questa scheda, puoi visualizzare le offerte per le quali il destinatario è idoneo tramite un metodo scelto. Nell’esempio seguente, il destinatario può ricevere tre proposte di offerta per posta.

![](assets/offer_space_overview_002.png)

Se un destinatario non è idoneo per alcuna offerta, questa viene visualizzata nell’anteprima.

![](assets/offer_space_overview_001.png)

L’anteprima può ignorare i contesti quando sono limitati a uno spazio. Questo è il caso in cui lo schema di interazione è stato esteso per aggiungere campi a cui si fa riferimento in uno spazio utilizzando un canale in entrata (per ulteriori informazioni, consulta [Esempio di estensione](../../interaction/using/extension-example.md)).
