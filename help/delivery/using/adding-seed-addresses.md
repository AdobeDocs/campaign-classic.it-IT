---
product: campaign
title: Aggiungere indirizzi seed
description: Aggiungere indirizzi seed
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Seed Address
role: User
exl-id: ae6eb4b0-b419-4661-9d63-e758f0242a0f
TQID: https://experienceleague.adobe.com/pVYaTG48-HiK0RwJXgBbIMWa-o-R7jlEpauXNXvGi5E
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 336
ht-degree: 5%

---

# Aggiungere indirizzi seed{#adding-seed-addresses}

## Indirizzi seed in una consegna {#seed-addresses-in-a-delivery}

Per aggiungere indirizzi di seed specifici per una consegna, fai clic sul collegamento **[!UICONTROL To]**, quindi seleziona la scheda **[!UICONTROL Seed addresses]**.

![](assets/s_ncs_user_edit_del_addresses_tab.png)

Sono disponibili tre modalità di inserimento:

1. Inserimento di indirizzi seed singoli.

   A tale scopo, fare clic sul pulsante **[!UICONTROL Add]** e definire il contenuto dei campi indirizzo. Ripeti per ogni indirizzo.

1. Importazione di modelli di indirizzo e loro adattamento in base alle esigenze.

   A tale scopo, fare clic sul collegamento **[!UICONTROL Import seed templates...]** e selezionare la cartella contenente i modelli di indirizzo. Per ulteriori informazioni al riguardo, consulta [questa sezione](creating-seed-addresses.md#creating-seed-address-templates).

   Se necessario, una volta aggiunti, è possibile fare doppio clic su di essi o fare clic sul pulsante **[!UICONTROL Detail...]** per adattare il contenuto di ciascun indirizzo.

1. Creazione di una condizione per la selezione dinamica degli indirizzi di controllo da inserire.

   A tale scopo, fare clic sul collegamento **[!UICONTROL Edit the dynamic condition...]**, quindi immettere i parametri di selezione dell&#39;indirizzo di seed. Ad esempio, puoi includere tutti gli indirizzi seed contenuti in una cartella specifica o gli indirizzi seed appartenenti a un reparto specifico della tua organizzazione.

   Un esempio è presentato in questa sezione: [Caso d&#39;uso: selezionare gli indirizzi seed in base ai criteri](use-case-selecting-seed-addresses-on-criteria.md).

>[!NOTE]
>
>Questa opzione viene utilizzata quando la tabella dei destinatari utilizzata non è la tabella predefinita **nms:recipient** e si utilizza la funzionalità di rendering della casella in entrata fornita con il modulo **[!UICONTROL Deliverability]** di Adobe Campaign.
>
>Per ulteriori informazioni, consulta [Utilizzare una tabella dei destinatari esterna](using-an-external-recipient-table.md) e la documentazione sul [rendering della casella in entrata](inbox-rendering.md).

Per le consegne, puoi anche personalizzare il modo in cui gli indirizzi vengono inseriti nel file di estrazione. Per impostazione predefinita, vengono inserite nell’ordine di ordinamento del file di output, ma puoi scegliere di inserirle alla fine o all’inizio del file oppure in modo casuale tra i destinatari del target principale.

![](assets/s_ncs_user_edit_del_addresses_sort.png)

## Indirizzi seed in una campagna {#seed-addresses-in-a-campaign}

Per aggiungere indirizzi di seed a una destinazione per una campagna, selezionare l&#39;operazione e fare clic sulla scheda **[!UICONTROL Edit]**.

Fare clic sul collegamento **[!UICONTROL Advanced campaign settings...]** e quindi sulla scheda **[!UICONTROL Seed addresses]**, come illustrato di seguito:

![](assets/s_ncs_user_edit_op_addresses_tab.png)

Gli indirizzi di seed inseriti dalla campagna verranno aggiunti al target di ogni consegna nella campagna.
