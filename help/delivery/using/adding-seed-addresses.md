---
product: campaign
title: Aggiungere indirizzi seed
description: Aggiungere indirizzi seed
badge-v7: label="v7" type="Informative" tooltip="Applicabile a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Seed Address
role: User
exl-id: ae6eb4b0-b419-4661-9d63-e758f0242a0f
source-git-commit: 668cee663890fafe27f86f2afd3752f7e2ab347a
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 5%

---

# Aggiungere indirizzi seed{#adding-seed-addresses}

## Indirizzi seed in una consegna {#seed-addresses-in-a-delivery}

Per aggiungere indirizzi di seed specifici per una consegna, fai clic sul pulsante **[!UICONTROL To]** , quindi seleziona la **[!UICONTROL Seed addresses]** scheda.

![](assets/s_ncs_user_edit_del_addresses_tab.png)

Sono disponibili tre modalità di inserimento:

1. Inserimento di indirizzi seed singoli.

   A questo scopo, fai clic su **[!UICONTROL Add]** e definiscono il contenuto dei campi indirizzo. Ripeti per ogni indirizzo.

1. Importazione di modelli di indirizzo e loro adattamento in base alle esigenze.

   A questo scopo, fai clic su **[!UICONTROL Import seed templates...]** e selezionare la cartella contenente i modelli di indirizzo. Per ulteriori informazioni al riguardo, consulta [questa sezione](creating-seed-addresses.md#creating-seed-address-templates).

   Se necessario, una volta aggiunti, puoi fare doppio clic su di essi o fare clic sul pulsante **[!UICONTROL Detail...]** per adattare il contenuto di ciascun indirizzo.

1. Creazione di una condizione per la selezione dinamica degli indirizzi di controllo da inserire.

   A questo scopo, fai clic su **[!UICONTROL Edit the dynamic condition...]** , quindi immettere i parametri di selezione dell&#39;indirizzo di seed. Ad esempio, puoi includere tutti gli indirizzi seed contenuti in una cartella specifica o gli indirizzi seed appartenenti a un reparto specifico della tua organizzazione.

   Un esempio è presentato in questa sezione: [Caso d’uso: selezionare gli indirizzi seed in base ai criteri](use-case-selecting-seed-addresses-on-criteria.md).

>[!NOTE]
>
>Questa opzione viene utilizzata quando la tabella dei destinatari utilizzata non è predefinita **nms:destinatario** e si sta utilizzando la funzionalità di rendering della casella in entrata fornita con Adobe Campaign **[!UICONTROL Deliverability]** modulo.
>
>Per ulteriori informazioni, consulta [Utilizzare una tabella dei destinatari esterna](using-an-external-recipient-table.md) e la documentazione su [Rendering casella in entrata](inbox-rendering.md).

Per le consegne, puoi anche personalizzare il modo in cui gli indirizzi vengono inseriti nel file di estrazione. Per impostazione predefinita, vengono inserite nell’ordine di ordinamento del file di output, ma puoi scegliere di inserirle alla fine o all’inizio del file oppure in modo casuale tra i destinatari del target principale.

![](assets/s_ncs_user_edit_del_addresses_sort.png)

## Indirizzi seed in una campagna {#seed-addresses-in-a-campaign}

Per aggiungere indirizzi di seed a una destinazione per una campagna, seleziona l’operazione e fai clic su **[!UICONTROL Edit]** scheda.

Fai clic su **[!UICONTROL Advanced campaign settings...]** e quindi il **[!UICONTROL Seed addresses]** come mostrato di seguito:

![](assets/s_ncs_user_edit_op_addresses_tab.png)

Gli indirizzi di seed inseriti dalla campagna verranno aggiunti al target di ogni consegna nella campagna.
