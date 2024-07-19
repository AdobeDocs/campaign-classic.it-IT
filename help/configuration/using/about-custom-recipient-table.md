---
product: campaign
title: Informazioni sulla tabella dei destinatari personalizzata
description: Informazioni sulla tabella dei destinatari personalizzata
feature: Configuration, Custom Resources
role: User, Data Engineer, Developer
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
exl-id: d8cea496-b3f3-420a-bf6e-b7cbb321b30d
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 2%

---

# Utilizzare una tabella dei destinatari personalizzata{#about-custom-recipient-table}

Questa sezione descrive i principi per l’utilizzo di una tabella dei destinatari personalizzata (o esterna).

Per impostazione predefinita, Adobe Campaign offre una tabella dei destinatari incorporata alla quale sono collegati le funzioni e i processi predefiniti. La tabella dei destinatari incorporata dispone di una serie di campi e tabelle predefiniti che possono essere facilmente estesi utilizzando una tabella delle estensioni.

Se questo metodo di estensione offre una buona flessibilità per estendere una tabella, non consente di ridurre il numero di campi o collegamenti presenti. L’utilizzo di una tabella non standard, o &quot;tabella dei destinatari esterna&quot;, offre una maggiore flessibilità ma richiede alcune precauzioni durante l’implementazione.

Questa funzionalità consente ad Adobe Campaign di elaborare i dati da un database esterno: i dati verranno utilizzati come set di profili per le consegne. L’implementazione di questo processo richiede diverse precisazioni che possono essere rilevanti in base alle esigenze del cliente. Ad esempio:

* Nessun flusso di aggiornamento da e verso il database di Adobe Campaign: i dati di questa tabella possono essere aggiornati direttamente tramite il motore di database che li ospita.
* Nessuna modifica nei processi che operano sul database esistente.
* Utilizzo di un database di profili con una struttura non standard: possibilità di distribuire ai profili salvati in varie tabelle con varie strutture, utilizzando una singola istanza.
* Non sono necessarie modifiche o manutenzione per aggiornare il database di Adobe Campaign.
* La tabella dei destinatari incorporata è inutile se non è necessaria la maggior parte dei campi della tabella o se il modello di database non è centrato sui destinatari.
* Per essere efficiente, se disponi di un numero significativo di profili è necessaria una tabella con pochi campi. La tabella dei destinatari incorporata contiene troppi campi per questo caso specifico.

Questa sezione descrive i punti chiave che ti consentono di mappare le tabelle esistenti in Adobe Campaign e la configurazione da applicare per eseguire consegne basate su qualsiasi tabella. Infine, descrive come fornire agli utenti interfacce di query pratiche come quelle disponibili con la tabella dei destinatari incorporata. Per comprendere il materiale presentato in questa sezione, è necessaria una buona conoscenza dei principi di progettazione dello schermo e dello schema.

## Recommendations e limitazioni {#recommendations-and-limitations}

L’utilizzo di una tabella dei destinatari personalizzata presenta le seguenti limitazioni:

* Adobe Campaign non supporta più schemi di destinatari, noti come schemi di targeting, collegati agli stessi schemi broadlog e/o trackinglog. In caso contrario, potrebbero verificarsi anomalie nella riconciliazione dei dati in seguito.

  L’immagine seguente descrive la struttura relazionale richiesta per ciascuno schema destinatario personalizzato:
  ![](assets/custom_recipient_limitation.png)

  Si consiglia di:

   * Dedicando gli schemi **[!UICONTROL nms:BroadLogRcp]** e **[!UICONTROL nms:TrackingLogRcp]** a **[!UICONTROL nms:Recipientschema]** predefiniti. Queste due tabelle di registro non devono essere collegate ad alcuna tabella dei destinatari personalizzata aggiuntiva.
   * Definizione di schemi broadlog e trackinglog personalizzati dedicati per ogni nuovo schema destinatario personalizzato. Questa operazione può essere eseguita automaticamente durante la configurazione del mapping di destinazione. Vedere [Mapping di destinazione](../../configuration/using/target-mapping.md).

* Impossibile utilizzare il **[!UICONTROL Services and Subscriptions]** standard offerto nel prodotto.

  Ciò significa che l&#39;operazione complessiva descritta in [questa sezione](../../delivery/using/managing-subscriptions.md) non è applicabile.

* Il collegamento con la tabella **[!UICONTROL visitor]** non funziona.

  Pertanto, per utilizzare il modulo **[!UICONTROL Social Marketing]** è necessario configurare il passaggio di archiviazione in modo che faccia riferimento alla tabella corretta.

  Analogamente, quando si utilizzano funzioni di riferimento, è necessario adattare il modello standard di trasferimento iniziale dei messaggi.

* Non è possibile aggiungere manualmente profili in un elenco.

  Pertanto, la procedura descritta in [questa sezione](../../platform/using/creating-and-managing-lists.md) non è applicabile senza una configurazione aggiuntiva.

  >[!NOTE]
  >
  >Puoi comunque creare gli elenchi dei destinatari utilizzando i flussi di lavoro. Per ulteriori informazioni, consulta [Creazione di un elenco di profili con un flusso di lavoro](../../configuration/using/creating-a-profile-list-with-a-workflow.md).

Consigliamo inoltre di controllare i valori predefiniti utilizzati nelle diverse configurazioni pronte all’uso: a seconda delle funzionalità utilizzate, è necessario effettuare diversi adeguamenti.

Ad esempio:

* Alcuni rapporti standard, in particolare quelli offerti da **Interaction** e **Mobile Applications**, devono essere risviluppati. Consulta la sezione [Gestione dei report](../../configuration/using/managing-reports.md).
* Le configurazioni predefinite per alcune attività del flusso di lavoro fanno riferimento alla tabella dei destinatari standard (**[!UICONTROL nms:recipient]**): queste configurazioni devono essere modificate quando vengono utilizzate per una tabella dei destinatari esterna. Consulta la sezione [Gestione dei flussi di lavoro](../../configuration/using/managing-workflows.md).
* È necessario adattare il blocco di personalizzazione **[!UICONTROL Unsubscription link]** standard.
* È necessario modificare la mappatura di destinazione dei modelli di consegna standard.
* I moduli V4 non sono compatibili per l’utilizzo con una tabella di destinatari esterna: è necessario utilizzare le applicazioni web.
