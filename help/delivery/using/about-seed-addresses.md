---
product: campaign
title: Informazioni sugli indirizzi seed
description: Introduzione agli indirizzi di seed
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Seed Address
role: User
exl-id: 1f55eda8-c393-4f86-9118-01bcd981c6df
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 8%

---

# Informazioni sugli indirizzi seed{#about-seed-addresses}

Gli indirizzi di seed vengono utilizzati per eseguire il targeting di destinatari che non corrispondono ai criteri di target definiti. In questo modo, i destinatari che non rientrano nell’ambito di consegna possono ricevere la consegna, come farebbe qualsiasi altro destinatario.

Una delle ragioni principali per utilizzarli è **protezione della mailing list**. L’inserimento di indirizzi di seed nella mailing list ti consente di notare se è utilizzato da una terza parte, in quanto gli indirizzi di seed in esso contenuti riceveranno le consegne inviate alla mailing list.

Inoltre, gli indirizzi di seed consentono di: **anteprima e test della personalizzazione e del rendering delle consegne** prima del loro invio, inviando loro le bozze (vedi [Utilizza indirizzi seed come bozza](steps-defining-the-target-population.md#using-seed-addresses-as-proof)).

![](assets/do-not-localize/how-to-video.png) [Guarda il video su questa funzione](steps-defining-the-target-population.md#seeds-and-proofs-video)

La funzione Indirizzi seed offre i seguenti vantaggi:

* Sostituzione casuale di campi con dati ottenuti dai profili dei destinatari: ciò ti consente di inserire solo l’indirizzo e-mail, ad esempio nella sezione dell’indirizzo di seed, e di consentire a Campaign di compilare automaticamente gli altri campi del profilo (consulta [Caso d’uso: configurare la sostituzione del campo](use-case-configuring-the-field-substitution.md)).
* Quando si utilizza un flusso di lavoro con funzionalità di gestione dati, i dati aggiuntivi elaborati nelle consegne possono essere inseriti a livello di indirizzo di seed per forzare i valori: in questo modo si evita la sostituzione casuale dei valori.
* Gli indirizzi di seed vengono automaticamente esclusi dai rapporti sulle seguenti statistiche di consegna: **[!UICONTROL Clicks]**, **[!UICONTROL Opens]**, **[!UICONTROL Unsubscriptions]**.

Gli indirizzi di seed vengono aggiunti al target delle consegne importando o creando direttamente nella consegna o nella campagna.

>[!NOTE]
>
>Gli indirizzi seed non appartengono alla tabella dei destinatari, ma vengono creati in una tabella separata. Se estendi la tabella dei destinatari con nuovi dati, devi estendere anche la tabella degli indirizzi di seed con gli stessi dati. In caso contrario, i campi estesi non verranno presi in considerazione per gli indirizzi seed.
>
>Un esempio di come estendere la tabella degli indirizzi di seed è presentato in questa sezione: [Caso d’uso: selezionare gli indirizzi seed in base ai criteri](use-case-selecting-seed-addresses-on-criteria.md).

Per le consegne di direct mailing, gli indirizzi di seed vengono aggiunti durante l’estrazione e mescolati nel documento di output.

>[!IMPORTANT]
>
>Per le consegne di direct mailing, il formato del file di estrazione deve rispettare le seguenti limitazioni:
>
>* Non deve utilizzare l’opzione **[!UICONTROL Handle groupings (GROUP BY+HAVING)]**.
>* Se le raccolte di elementi vengono estratte, questi campi avranno un valore vuoto per gli indirizzi di seed, a meno che **[!UICONTROL Single row (expert user)]** è selezionata. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../platform/using/executing-export-jobs.md#step-7---data-formatting).
>
