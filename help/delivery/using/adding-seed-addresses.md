---
product: campaign
title: Aggiunta di indirizzi di seed
description: Aggiunta di indirizzi di seed
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
exl-id: ae6eb4b0-b419-4661-9d63-e758f0242a0f
source-git-commit: a129f49d4f045433899fd7fdbd057fb16d0ed36a
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 5%

---

# Aggiungere indirizzi seed{#adding-seed-addresses}

## Indirizzi di seed in una consegna {#seed-addresses-in-a-delivery}

Per aggiungere indirizzi di seed specifici per una consegna, fai clic sul collegamento **[!UICONTROL To]** , quindi seleziona la scheda **[!UICONTROL Seed addresses]** .

![](assets/s_ncs_user_edit_del_addresses_tab.png)

Esistono tre possibili modalità di inserimento:

1. Inserimento di indirizzi di seed singoli.

   A questo scopo, fai clic sul pulsante **[!UICONTROL Add]** e definisci il contenuto dei campi indirizzo. Ripeti per ogni indirizzo.

1. Importazione di modelli di indirizzi e loro adattamento in base alle tue esigenze.

   A questo scopo, fai clic sul collegamento **[!UICONTROL Import seed templates...]** e seleziona la cartella che contiene i modelli di indirizzo. Per ulteriori informazioni al riguardo, consulta [questa sezione](creating-seed-addresses.md#creating-seed-address-templates).

   Se necessario, una volta aggiunti, puoi fare doppio clic su di essi o fare clic sul pulsante **[!UICONTROL Detail...]** per adattare il contenuto di ciascun indirizzo.

1. Creazione di una condizione per selezionare dinamicamente gli indirizzi di controllo da inserire.

   A questo scopo, fai clic sul collegamento **[!UICONTROL Edit the dynamic condition...]** , quindi immetti i parametri di selezione dell’indirizzo di seed. Ad esempio, puoi includere tutti gli indirizzi di seed contenuti in una cartella specifica o gli indirizzi di seed appartenenti a un reparto specifico dell’organizzazione.

   Un esempio di ciò è illustrato in questa sezione: [Caso di utilizzo: seleziona indirizzi di seed in criteri](use-case--selecting-seed-addresses-on-criteria.md).

>[!NOTE]
>
>Questa opzione viene utilizzata quando la tabella dei destinatari utilizzata non è la tabella predefinita **nms:recipient** e si utilizza la funzionalità Rendering della casella in entrata fornita con il modulo Adobe Campaign **[!UICONTROL Deliverability]**.
>
>Per ulteriori informazioni, consulta [Utilizzare una tabella dei destinatari esterna](using-an-external-recipient-table.md) e la documentazione su [Rendering della casella in entrata](inbox-rendering.md).

Per le consegne, puoi anche personalizzare il modo in cui gli indirizzi vengono inseriti nel file di estrazione. Per impostazione predefinita, vengono inseriti nell’ordine di ordinamento del file di output, ma puoi scegliere di inserirli alla fine o all’inizio del file oppure in modo casuale tra i destinatari della destinazione principale.

![](assets/s_ncs_user_edit_del_addresses_sort.png)

## Indirizzi di seed in una campagna {#seed-addresses-in-a-campaign}

Per aggiungere indirizzi di seed a una destinazione per una campagna, seleziona l’operazione e fai clic sulla scheda **[!UICONTROL Edit]** .

Fai clic sul collegamento **[!UICONTROL Advanced campaign settings...]** e quindi sulla scheda **[!UICONTROL Seed addresses]** , come illustrato di seguito:

![](assets/s_ncs_user_edit_op_addresses_tab.png)

Gli indirizzi di seed inseriti dalla campagna verranno aggiunti al target di ogni consegna nella campagna.
