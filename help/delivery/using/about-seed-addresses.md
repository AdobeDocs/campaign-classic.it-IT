---
title: Informazioni sugli indirizzi seed
seo-title: Informazioni sugli indirizzi seed
description: Informazioni sugli indirizzi seed
seo-description: null
page-status-flag: never-activated
uuid: 80ab5abc-3ae0-484d-88c0-be039aac360d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
discoiquuid: b49acfd0-b601-4694-88e3-cc0a169cb866
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d96912e39956f2f7b0b0af29dc765d0b9775a020
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 2%

---


# Informazioni sugli indirizzi seed{#about-seed-addresses}

Gli indirizzi dei semi vengono utilizzati per i destinatari a cui non corrispondono ai criteri di destinazione definiti. In questo modo, i destinatari che non rientrano nell&#39;ambito di distribuzione possono ricevere la consegna, come farebbe qualsiasi altro destinatario.

Una delle ragioni principali per utilizzarli è **la protezione** della mailing list. L&#39;inserimento di indirizzi iniziali nella mailing list consente di notare se viene utilizzato da un terzo, in quanto gli indirizzi iniziali che contiene riceveranno le consegne inviate alla mailing list.

Inoltre, gli indirizzi iniziali consentono di **visualizzare in anteprima e verificare la personalizzazione e il rendering** delle consegne prima del loro invio, inviando loro le prove (vedere [Uso degli indirizzi iniziali come prova](../../delivery/using/steps-defining-the-target-population.md#using-seed-addresses-as-proof)).

La funzione degli indirizzi di base presenta i seguenti vantaggi:

* Sostituzione casuale dei campi con dati provenienti dai profili dei destinatari: questo consente di immettere solo l&#39;indirizzo e-mail, ad esempio nella sezione dell&#39;indirizzo e di consentire a Campaign di compilare automaticamente gli altri campi del profilo (consultate Caso di [utilizzo: configurazione della sostituzione](../../delivery/using/use-case--configuring-the-field-substitution.md)del campo).
* Quando si utilizza un flusso di lavoro con funzionalità di gestione dati, i dati aggiuntivi elaborati nelle consegne possono essere immessi a livello di indirizzo seed per imporre i valori: in questo modo si verifica una sostituzione casuale del valore.
* Gli indirizzi dei semi vengono automaticamente esclusi dai rapporti sulle seguenti statistiche di consegna: **[!UICONTROL Clicks]**, **[!UICONTROL Opens]**, **[!UICONTROL Unsubscriptions]**.

Gli indirizzi dei semi vengono aggiunti alla destinazione delle consegne importando o creando direttamente nella consegna o nella campagna.

>[!NOTE]
>
>Gli indirizzi dei semi non appartengono alla tabella dei destinatari, ma vengono creati in una tabella separata. Se si estende la tabella dei destinatari con nuovi dati, è necessario estendere la tabella degli indirizzi iniziali insieme agli stessi dati. In caso contrario, i campi estesi non saranno presi in considerazione per gli indirizzi iniziali.
>
>Un esempio di come estendere la tabella degli indirizzi di base è presentato in questa sezione: [Caso di utilizzo: selezione degli indirizzi di base sui criteri](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md)

Per le consegne per corrispondenza diretta, gli indirizzi iniziali vengono aggiunti durante l&#39;estrazione e mescolati nel documento di output.

>[!IMPORTANT]
>
>Per le consegne per corrispondenza diretta, il formato del file di estrazione deve rispettare i seguenti limiti:
>
>* Non deve utilizzare l&#39;opzione **[!UICONTROL Handle groupings (GROUP BY+HAVING)]**.
>* Se le raccolte di elementi vengono estratte, questi campi avranno un valore vuoto per gli indirizzi iniziali, a meno che l&#39; **[!UICONTROL Single row (expert user)]** opzione non sia selezionata. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../platform/using/exporting-data.md#step-7---data-formatting).
>


