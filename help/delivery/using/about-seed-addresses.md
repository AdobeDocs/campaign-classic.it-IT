---
product: campaign
title: Informazioni sugli indirizzi seed
description: Introduzione agli indirizzi di seed
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Seed Address
role: User
exl-id: 1f55eda8-c393-4f86-9118-01bcd981c6df
TQID: https://experienceleague.adobe.com/ZFeQSj9pGtKzG-wBsm5Go39ja7jvZ0pVi8h3xKOYR8c
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: e0eb8757-182f-49f3-94a4-1587d16f5094
feature_v2: id: b631758a-142d-425f-b9aa-f756d85cb979id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2: id: e95a583b-fcfa-4524-8666-46a29c828119id: c8da4fdd-eb94-4751-a43c-f82733fb2d6eid: d5bbe3da-ba85-4242-817e-54f7c4b943e0id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 388
ht-degree: 8%

---

# Informazioni sugli indirizzi seed{#about-seed-addresses}

Gli indirizzi di seed vengono utilizzati per eseguire il targeting di destinatari che non corrispondono ai criteri di target definiti. In questo modo, i destinatari che non rientrano nell’ambito di consegna possono ricevere la consegna, come farebbe qualsiasi altro destinatario.

Uno dei motivi principali per utilizzarli è **la protezione della tua mailing list**. L’inserimento di indirizzi di seed nella mailing list ti consente di notare se è utilizzato da una terza parte, in quanto gli indirizzi di seed in esso contenuti riceveranno le consegne inviate alla mailing list.

Inoltre, gli indirizzi di seed ti consentono di **visualizzare in anteprima e testare la personalizzazione e il rendering delle consegne** prima del loro invio, inviando loro delle bozze (vedi [Utilizzare gli indirizzi di seed come bozza](steps-defining-the-target-population.md#using-seed-addresses-as-proof)).

![](assets/do-not-localize/how-to-video.png) [Guarda un video su questa funzione](steps-defining-the-target-population.md#seeds-and-proofs-video)

La funzione Indirizzi seed offre i seguenti vantaggi:

* Sostituzione casuale di campi con dati ottenuti dai profili dei destinatari: consente di immettere solo l&#39;indirizzo e-mail, ad esempio nella sezione dell&#39;indirizzo di seed, e di consentire a Campaign di compilare automaticamente gli altri campi del profilo (vedi [Caso d&#39;uso: configurare la sostituzione del campo](use-case-configuring-the-field-substitution.md)).
* Quando si utilizza un flusso di lavoro con funzionalità di gestione dati, i dati aggiuntivi elaborati nelle consegne possono essere inseriti a livello di indirizzo di seed per forzare i valori: in questo modo si evita la sostituzione casuale dei valori.
* Gli indirizzi di seed vengono automaticamente esclusi dai rapporti delle seguenti statistiche di consegna: **[!UICONTROL Clicks]**, **[!UICONTROL Opens]**, **[!UICONTROL Unsubscriptions]**.

Gli indirizzi di seed vengono aggiunti al target delle consegne importando o creando direttamente nella consegna o nella campagna.

>[!NOTE]
>
>Gli indirizzi seed non appartengono alla tabella dei destinatari, ma vengono creati in una tabella separata. Se estendi la tabella dei destinatari con nuovi dati, devi estendere anche la tabella degli indirizzi di seed con gli stessi dati. In caso contrario, i campi estesi non verranno presi in considerazione per gli indirizzi seed.
>
>Un esempio di come estendere la tabella degli indirizzi di seed è presentato in questa sezione: [Caso d&#39;uso: selezionare gli indirizzi di seed in base ai criteri](use-case-selecting-seed-addresses-on-criteria.md).

Per le consegne di direct mailing, gli indirizzi di seed vengono aggiunti durante l’estrazione e mescolati nel documento di output.

>[!IMPORTANT]
>
>Per le consegne di direct mailing, il formato del file di estrazione deve rispettare le seguenti limitazioni:
>
>* Non deve utilizzare l&#39;opzione **[!UICONTROL Handle groupings (GROUP BY+HAVING)]**.
>* Se vengono estratte le raccolte di elementi, questi campi avranno un valore vuoto per gli indirizzi seed, a meno che non sia selezionata l&#39;opzione **[!UICONTROL Single row (expert user)]**. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../platform/using/executing-export-jobs.md#step-7---data-formatting).
>
