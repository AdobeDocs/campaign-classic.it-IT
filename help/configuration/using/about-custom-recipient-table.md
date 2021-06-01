---
product: campaign
title: Informazioni sulla tabella dei destinatari personalizzata
description: Informazioni sulla tabella dei destinatari personalizzata
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
exl-id: d8cea496-b3f3-420a-bf6e-b7cbb321b30d
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 2%

---

# Utilizzare una tabella dei destinatari personalizzata{#about-custom-recipient-table}

Questa sezione descrive i principi per l’utilizzo di una tabella dei destinatari non standard.

Per impostazione predefinita, Adobe Campaign offre una tabella dei destinatari standard a cui sono collegati le funzioni e i processi predefiniti. La tabella dei destinatari standard dispone di una serie di campi e tabelle predefiniti che possono essere facilmente estesi utilizzando una tabella delle estensioni.

Se questo metodo di estensione offre una buona flessibilità per estendere una tabella, non consente di ridurre il numero di campi o collegamenti in essa contenuti. L’utilizzo di una tabella non standard, o &quot;tabella dei destinatari esterna&quot;, consente una maggiore flessibilità ma richiede alcune precauzioni durante l’implementazione.

## Precisazioni {#precisions}

Questa funzionalità consente ad Adobe Campaign di elaborare i dati da un database esterno: questi dati verranno utilizzati come un set di profili per le consegne. L&#39;implementazione di questo processo comporta diverse precisazioni che possono essere rilevanti in base alle esigenze del cliente. Ad esempio:

* Nessun flusso di aggiornamento da e verso il database Adobe Campaign: i dati di questa tabella possono essere aggiornati direttamente tramite il motore di database che li ospita.
* Nessuna modifica dei processi che operano sul database esistente.
* Utilizzo di un database di profilo con una struttura non standard: possibilità di consegnare a profili salvati in varie tabelle con diverse strutture, utilizzando un’unica istanza.
* Non è necessaria alcuna modifica o manutenzione per aggiornare il database Adobe Campaign.
* La tabella dei destinatari standard è inutile se non è necessaria la maggior parte dei campi della tabella o se il modello del database non è centrato sui destinatari.
* Per essere efficiente, è necessaria una tabella con pochi campi se disponi di un numero significativo di profili. La tabella dei destinatari standard contiene troppi campi per questo caso specifico.

Questa sezione descrive i punti chiave che ti consentono di mappare le tabelle esistenti in Adobe Campaign e la configurazione da applicare per eseguire consegne in base a qualsiasi tabella. Infine, descrive come fornire agli utenti interfacce di query pratiche quanto quelle disponibili con la tabella dei destinatari standard. Per comprendere il materiale presentato in questa sezione, è necessaria una buona conoscenza dei principi di progettazione dello schermo e dello schema.

## Recommendations e limitazioni {#recommendations-and-limitations}

L’utilizzo di una tabella dei destinatari esterna presenta le seguenti limitazioni:

* Adobe Campaign non supporta più schemi di destinatari, noti come schemi di targeting, collegati agli stessi schemi di registro di trasmissione e/o di trackinglog. In caso contrario, si potrebbero verificare successivamente anomalie nella riconciliazione dei dati.

   L’immagine seguente descrive la struttura relazionale richiesta per ogni schema di destinatari personalizzato:
   ![](assets/custom_recipient_limitation.png)

   Si consiglia di:

   * Dedicazione degli schemi **[!UICONTROL nms:BroadLogRcp]** e **[!UICONTROL nms:TrackingLogRcp]** all’impostazione predefinita **[!UICONTROL nms:Recipientschema]**. Queste due tabelle di registro non devono essere collegate a nessuna tabella dei destinatari personalizzata aggiuntiva.
   * Definizione di schemi di registro di trasmissione e di registro personalizzati dedicati per ogni nuovo schema di destinatari personalizzato. Questa operazione può essere eseguita automaticamente durante la configurazione della mappatura di destinazione, consulta [Mappatura di destinazione](../../configuration/using/target-mapping.md).

* Non è possibile utilizzare il **[!UICONTROL Services and Subscriptions]** standard offerto nel prodotto.

   Ciò significa che l&#39;operazione complessiva descritta in [questa sezione](../../delivery/using/managing-subscriptions.md) non è applicabile.

* Il collegamento con la tabella **[!UICONTROL visitor]** non funziona.

   Pertanto, per utilizzare il modulo **[!UICONTROL Social Marketing]** è necessario configurare il passaggio di archiviazione in modo che faccia riferimento alla tabella corretta.

   Analogamente, quando si utilizzano le funzioni di riferimento, è necessario adattare il modello standard di trasferimento iniziale dei messaggi.

* Non puoi aggiungere manualmente i profili in un elenco.

   Pertanto, la procedura descritta in [questa sezione](../../platform/using/creating-and-managing-lists.md) non è applicabile senza una configurazione aggiuntiva.

   >[!NOTE]
   >
   >Puoi comunque creare elenchi di destinatari utilizzando i flussi di lavoro. Per ulteriori informazioni, consulta [Creazione di un elenco di profili con un flusso di lavoro](../../configuration/using/creating-a-profile-list-with-a-workflow.md).

È inoltre consigliabile controllare i valori predefiniti utilizzati nelle diverse configurazioni predefinite: a seconda delle funzionalità utilizzate, devono essere effettuati diversi adeguamenti.

Ad esempio:

* Alcuni rapporti standard, in particolare quelli offerti da **Interaction** e da **Mobile Applications**, devono essere risviluppati. Consulta la sezione [Gestione dei report](../../configuration/using/managing-reports.md) .
* Le configurazioni predefinite per alcune attività del flusso di lavoro fanno riferimento alla tabella dei destinatari standard (**[!UICONTROL nms:recipient]**): queste configurazioni devono essere modificate se utilizzate per una tabella dei destinatari esterna. Consulta la sezione [Gestione dei flussi di lavoro](../../configuration/using/managing-workflows.md) .
* Il blocco di personalizzazione standard **[!UICONTROL Unsubscription link]** deve essere adattato.
* È necessario modificare la mappatura di destinazione dei modelli di consegna standard.
* I moduli V4 non sono compatibili per l’uso con una tabella dei destinatari esterna: è necessario utilizzare applicazioni web.
