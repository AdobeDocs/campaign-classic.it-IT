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

## Indirizzi dei semi in una consegna {#seed-addresses-in-a-delivery}

Per aggiungere indirizzi iniziali specifici per una consegna, fare clic sul collegamento **[!UICONTROL To]**, quindi selezionare la scheda **[!UICONTROL Seed addresses]**.

![](assets/s_ncs_user_edit_del_addresses_tab.png)

Esistono tre possibili modalità di inserimento:

1. Inserimento di indirizzi iniziali singoli.

   A questo scopo, fare clic sul pulsante **[!UICONTROL Add]** e definire il contenuto dei campi indirizzo. Ripetere la procedura per ogni indirizzo. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../message-center/using/managing-seed-addresses-in-transactional-messages.md#creating-a-seed-address).

1. Importazione di modelli di indirizzo e loro adattamento in base alle esigenze.

   A questo scopo, fate clic sul collegamento **[!UICONTROL Import seed templates...]** e selezionate la cartella che contiene i modelli di indirizzo. Per ulteriori informazioni, vedere [Creazione di modelli di indirizzi di base](../../delivery/using/creating-seed-addresses.md#creating-seed-address-templates).

   Se necessario, una volta aggiunti, è possibile fare doppio clic su di essi o fare clic sul pulsante **[!UICONTROL Detail...]** per adattare il contenuto di ciascun indirizzo.

1. Creazione di una condizione per selezionare dinamicamente gli indirizzi di controllo da inserire.

   A questo scopo, fate clic sul collegamento **[!UICONTROL Edit the dynamic condition...]**, quindi immettete i parametri di selezione dell&#39;indirizzo di base. Ad esempio, potete includere tutti gli indirizzi iniziali contenuti in una cartella specifica, o gli indirizzi iniziali appartenenti a un reparto specifico della vostra organizzazione.

   Un esempio è illustrato in questa sezione: [Caso di utilizzo: selezione di indirizzi iniziali su criteri](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md).

>[!NOTE]
>
>Questa opzione viene utilizzata quando la tabella del destinatario utilizzata non è la tabella predefinita **nms:Recipients** e si utilizza la funzionalità di rendering della inbox fornita con  modulo Adobe Campaign **[!UICONTROL Deliverability]**.
>
>Per ulteriori informazioni, vedere [Utilizzo di una tabella di destinazione esterna](../../delivery/using/using-an-external-recipient-table.md) e la documentazione relativa al [rendering della casella in entrata](../../delivery/using/inbox-rendering.md).

Per le consegne, potete personalizzare il modo in cui gli indirizzi vengono inseriti nel file di estrazione. Per impostazione predefinita, vengono inseriti nell&#39;ordine di ordinamento del file di output, ma è possibile scegliere di inserirli alla fine o all&#39;inizio del file, oppure in modo casuale tra i destinatari della destinazione principale.

![](assets/s_ncs_user_edit_del_addresses_sort.png)

## Indirizzi dei semi in una campagna {#seed-addresses-in-a-campaign}

Per aggiungere indirizzi iniziali a una destinazione per una campagna, selezionate l&#39;operazione e fate clic sulla scheda **[!UICONTROL Edit]**.

Fare clic sul collegamento **[!UICONTROL Advanced campaign settings...]**, quindi sulla scheda **[!UICONTROL Seed addresses]**, come illustrato di seguito:

![](assets/s_ncs_user_edit_op_addresses_tab.png)

Gli indirizzi iniziali inseriti dalla campagna saranno aggiunti alla destinazione di ogni consegna nella campagna.
