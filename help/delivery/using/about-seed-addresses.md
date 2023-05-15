---
product: campaign
title: Informazioni sugli indirizzi seed
description: Guida introduttiva agli indirizzi di seed
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Seed Address
exl-id: 1f55eda8-c393-4f86-9118-01bcd981c6df
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 8%

---

# Informazioni sugli indirizzi seed{#about-seed-addresses}



Gli indirizzi di seed vengono utilizzati per eseguire il targeting di destinatari che non corrispondono ai criteri di target definiti. In questo modo, i destinatari che non rientrano nell’ambito di consegna possono ricevere la consegna, come farebbe qualsiasi altro destinatario di destinazione.

Una delle ragioni principali per utilizzarli è **la protezione della mailing list**. L’inserimento di indirizzi di seed nella mailing list consente di notare se viene utilizzato da terze parti, in quanto gli indirizzi di seed in essa contenuti riceveranno le consegne inviate alla mailing list.

Inoltre, gli indirizzi di seed consentono di: **visualizzare in anteprima e testare la personalizzazione e il rendering delle consegne** prima dell’invio, inviando le bozze (vedi [Usa indirizzi di seed come prova](steps-defining-the-target-population.md#using-seed-addresses-as-proof)).

![](assets/do-not-localize/how-to-video.png) [Scopri questa funzione nel video](steps-defining-the-target-population.md#seeds-and-proofs-video)

La funzione degli indirizzi di seed presenta i seguenti vantaggi:

* Sostituzione casuale di campi con dati provenienti dai profili dei destinatari: questo ti consente di inserire solo l’indirizzo e-mail, ad esempio nella sezione dell’indirizzo di seed, e di consentire a Campaign di compilare automaticamente gli altri campi del profilo (consulta [Caso di utilizzo: configurare la sostituzione del campo](use-case--configuring-the-field-substitution.md)).
* Quando utilizzi un flusso di lavoro con funzionalità di gestione dati, i dati aggiuntivi elaborati nelle consegne possono essere immessi a livello di indirizzo di seed per forzare i valori: questo elimina la sostituzione casuale di valori.
* Gli indirizzi di seed vengono automaticamente esclusi dai rapporti relativi alle seguenti statistiche di consegna: **[!UICONTROL Clicks]**, **[!UICONTROL Opens]**, **[!UICONTROL Unsubscriptions]**.

Gli indirizzi di seed vengono aggiunti al target delle consegne importando o creando direttamente nella consegna o nella campagna.

>[!NOTE]
>
>Gli indirizzi di seed non appartengono alla tabella dei destinatari, ma vengono creati in una tabella separata. Se estendi la tabella dei destinatari con nuovi dati, devi estendere anche la tabella degli indirizzi di seed con gli stessi dati. In caso contrario, i campi estesi non saranno presi in considerazione per gli indirizzi di seed.
>
>Un esempio di come estendere la tabella degli indirizzi di seed è presentato in questa sezione: [Caso di utilizzo: seleziona gli indirizzi di seed in base ai criteri](use-case--selecting-seed-addresses-on-criteria.md).

Per le consegne di direct mailing, gli indirizzi di seed vengono aggiunti durante l’estrazione e mescolati nel documento di output.

>[!IMPORTANT]
>
>Per le consegne di direct mailing, il formato del file di estrazione deve rispettare i seguenti limiti:
>
>* Non deve utilizzare l&#39;opzione **[!UICONTROL Handle groupings (GROUP BY+HAVING)]**.
>* Se le raccolte di elementi sono estratte, questi campi avranno un valore vuoto per gli indirizzi di seed, a meno che il valore **[!UICONTROL Single row (expert user)]** è selezionata. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../platform/using/executing-export-jobs.md#step-7---data-formatting).
>

