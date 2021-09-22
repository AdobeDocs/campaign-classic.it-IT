---
product: campaign
title: Informazioni sugli indirizzi seed
description: Informazioni sugli indirizzi seed
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
exl-id: 1f55eda8-c393-4f86-9118-01bcd981c6df
source-git-commit: 1113afb573bad958ec7cc2cf008f71c8e751e8f9
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 9%

---

# Informazioni sugli indirizzi seed{#about-seed-addresses}

![](../../assets/common.svg)

Gli indirizzi di seed vengono utilizzati per eseguire il targeting di destinatari che non corrispondono ai criteri di target definiti. In questo modo, i destinatari che non rientrano nell’ambito di consegna possono ricevere la consegna, come farebbe qualsiasi altro destinatario di destinazione.

Una delle ragioni principali per utilizzarli è **la tua mailing list protection**. L’inserimento di indirizzi di seed nella mailing list consente di notare se viene utilizzato da terze parti, in quanto gli indirizzi di seed in essa contenuti riceveranno le consegne inviate alla mailing list.

Inoltre, gli indirizzi di seed ti consentono di **visualizzare in anteprima e testare la personalizzazione e il rendering delle consegne** prima dell’invio, inviandole prove (consulta [Utilizzare gli indirizzi di seed come prova](steps-defining-the-target-population.md#using-seed-addresses-as-proof)).

![](assets/do-not-localize/how-to-video.png) [Scopri questa funzione nel video](steps-defining-the-target-population.md#seeds-and-proofs-video)

La funzione degli indirizzi di seed presenta i seguenti vantaggi:

* Sostituzione casuale di campi con dati provenienti dai profili dei destinatari: questo ti consente di inserire solo l’indirizzo e-mail, ad esempio nella sezione dell’indirizzo di seed, e di consentire a Campaign di compilare automaticamente gli altri campi del profilo (consulta [Caso di utilizzo: configura la sostituzione del campo](use-case--configuring-the-field-substitution.md)).
* Quando utilizzi un flusso di lavoro con funzionalità di gestione dati, i dati aggiuntivi elaborati nelle consegne possono essere immessi a livello di indirizzo di seed per forzare i valori: questo elimina la sostituzione casuale di valori.
* Gli indirizzi di seed vengono automaticamente esclusi dai rapporti relativi alle seguenti statistiche di consegna: **[!UICONTROL Clicks]**, **[!UICONTROL Opens]**, **[!UICONTROL Unsubscriptions]**.

Gli indirizzi di seed vengono aggiunti al target delle consegne importando o creando direttamente nella consegna o nella campagna.

>[!NOTE]
>
>Gli indirizzi di seed non appartengono alla tabella dei destinatari, ma vengono creati in una tabella separata. Se estendi la tabella dei destinatari con nuovi dati, devi estendere anche la tabella degli indirizzi di seed con gli stessi dati. In caso contrario, i campi estesi non saranno presi in considerazione per gli indirizzi di seed.
>
>Un esempio di come estendere la tabella degli indirizzi di seed è presentato in questa sezione: [Caso di utilizzo: seleziona indirizzi di seed in criteri](use-case--selecting-seed-addresses-on-criteria.md).

Per le consegne di direct mailing, gli indirizzi di seed vengono aggiunti durante l’estrazione e mescolati nel documento di output.

>[!IMPORTANT]
>
>Per le consegne di direct mailing, il formato del file di estrazione deve rispettare i seguenti limiti:
>
>* Non deve utilizzare l&#39;opzione **[!UICONTROL Handle groupings (GROUP BY+HAVING)]**.
>* Se le raccolte di elementi sono estratte, questi campi avranno un valore vuoto per gli indirizzi di seed, a meno che l’opzione **[!UICONTROL Single row (expert user)]** non sia selezionata. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../platform/using/executing-export-jobs.md#step-7---data-formatting).
>

