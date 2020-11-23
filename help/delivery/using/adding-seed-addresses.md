---
solution: Campaign Classic
product: campaign
title: Aggiunta di indirizzi di seed
description: Aggiunta di indirizzi di seed
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 5%

---


# Aggiunta di indirizzi di seed{#adding-seed-addresses}

## Indirizzi delle sementi in una consegna {#seed-addresses-in-a-delivery}

Per aggiungere indirizzi iniziali specifici per una consegna, fai clic sul **[!UICONTROL To]** collegamento, quindi seleziona la **[!UICONTROL Seed addresses]** scheda.

![](assets/s_ncs_user_edit_del_addresses_tab.png)

Esistono tre possibili modalità di inserimento:

1. Inserimento di indirizzi iniziali singoli.

   A questo scopo, fate clic sul **[!UICONTROL Add]** pulsante e definite il contenuto dei campi indirizzo. Ripetere la procedura per ogni indirizzo. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../message-center/using/managing-seed-addresses-in-transactional-messages.md#creating-a-seed-address).

1. Importazione di modelli di indirizzo e loro adattamento in base alle esigenze.

   A questo scopo, fate clic sul **[!UICONTROL Import seed templates...]** collegamento e selezionate la cartella che contiene i modelli di indirizzo. Per ulteriori informazioni, consultate [Creazione di modelli](../../delivery/using/creating-seed-addresses.md#creating-seed-address-templates)di indirizzi di base.

   Se necessario, una volta aggiunti, è possibile fare doppio clic su di essi o fare clic sul **[!UICONTROL Detail...]** pulsante per adattare il contenuto di ciascun indirizzo.

1. Creazione di una condizione per selezionare dinamicamente gli indirizzi di controllo da inserire.

   A questo scopo, fate clic sul **[!UICONTROL Edit the dynamic condition...]** collegamento, quindi immettete i parametri di selezione dell&#39;indirizzo e-mail. Ad esempio, potete includere tutti gli indirizzi iniziali contenuti in una cartella specifica, o gli indirizzi iniziali appartenenti a un reparto specifico della vostra organizzazione.

   Un esempio è illustrato in questa sezione: [Caso di utilizzo: selezione degli indirizzi iniziali sui criteri](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md).

>[!NOTE]
>
>Questa opzione viene utilizzata quando la tabella dei destinatari utilizzata non è la tabella **nms:destinatari** predefinita e si utilizza la funzionalità di rendering Posta in arrivo fornita con  modulo Adobe Campaign **[!UICONTROL Deliverability]** .
>
>Per ulteriori informazioni, consultare [Utilizzo di una tabella](../../delivery/using/using-an-external-recipient-table.md) di destinazione esterna e la documentazione sul rendering [](../../delivery/using/inbox-rendering.md)Inbox.

Per le consegne, potete personalizzare il modo in cui gli indirizzi vengono inseriti nel file di estrazione. Per impostazione predefinita, vengono inseriti nell&#39;ordine di ordinamento del file di output, ma è possibile scegliere di inserirli alla fine o all&#39;inizio del file, oppure in modo casuale tra i destinatari della destinazione principale.

![](assets/s_ncs_user_edit_del_addresses_sort.png)

## Indirizzi di base in una campagna {#seed-addresses-in-a-campaign}

Per aggiungere indirizzi iniziali a una destinazione per una campagna, selezionate l&#39;operazione e fate clic sulla **[!UICONTROL Edit]** scheda.

Fate clic sul **[!UICONTROL Advanced campaign settings...]** collegamento e quindi sulla **[!UICONTROL Seed addresses]** scheda, come illustrato di seguito:

![](assets/s_ncs_user_edit_op_addresses_tab.png)

Gli indirizzi iniziali inseriti dalla campagna saranno aggiunti alla destinazione di ogni consegna nella campagna.
