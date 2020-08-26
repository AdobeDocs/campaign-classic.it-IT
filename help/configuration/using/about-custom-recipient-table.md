---
title: Informazioni sulla tabella dei destinatari personalizzata
seo-title: Informazioni sulla tabella dei destinatari personalizzata
description: Informazioni sulla tabella dei destinatari personalizzata
seo-description: null
page-status-flag: never-activated
uuid: 4b162da4-90d2-44ff-9f89-ff0275540359
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: c3ff8462-e47e-4637-8213-769fdeb86a57
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 6c76ce3e6da41a80d1df2adfcb17fd7c0f85b894
workflow-type: tm+mt
source-wordcount: '669'
ht-degree: 2%

---


# Informazioni sulla tabella dei destinatari personalizzata{#about-custom-recipient-table}

In questa sezione vengono descritti i principi per l&#39;utilizzo di una tabella di destinazione non standard.

Per impostazione predefinita,  Adobe Campaign offre una tabella di destinatari standard a cui sono collegati funzioni e processi out-of-the-box. La tabella dei destinatari standard include una serie di campi e tabelle predefiniti che possono essere facilmente estesi utilizzando una tabella delle estensioni.

Se questo metodo di estensione offre una buona flessibilità per estendere una tabella, non consente di ridurre il numero di campi o collegamenti in essa contenuti. L&#39;utilizzo di una tabella non standard, o &quot;tabella di destinazione esterna&quot;, consente una maggiore flessibilità, ma richiede alcune precauzioni al momento dell&#39;implementazione.

## Precisazioni {#precisions}

Questa funzionalità consente  Adobe Campaign di elaborare i dati da un database esterno: questi dati saranno utilizzati come un insieme di profili per le consegne. L&#39;implementazione di questo processo comporta diverse precisazioni che possono essere rilevanti in base alle esigenze del cliente. Ad esempio:

* Nessun flusso di aggiornamento da e per il database Adobe Campaign : i dati di questa tabella possono essere aggiornati direttamente tramite il motore di database che li ospita.
* Nessuna modifica nei processi operativi sul database esistente.
* Utilizzo di un database di profilo con una struttura non standard: possibilità di consegna a profili salvati in varie tabelle con varie strutture, utilizzando una singola istanza.
* Nessuna modifica o manutenzione necessaria per aggiornare il database Adobe Campaign .
* La tabella del destinatario standard è inutile se non sono necessari la maggior parte dei campi della tabella o se il modello del database non è centrato sui destinatari.
* Per essere efficiente, è necessaria una tabella con pochi campi se si dispone di un numero significativo di profili. La tabella dei destinatari standard contiene troppi campi per questo caso specifico.

Questa sezione descrive i punti chiave che consentono di mappare tabelle esistenti in  Adobe Campaign e la configurazione da applicare per eseguire consegne basate su qualsiasi tabella. Infine, descrive come fornire agli utenti interfacce di query pratiche quanto quelle disponibili con la tabella dei destinatari standard. Per comprendere il materiale presentato in questa sezione, è necessaria una buona conoscenza dei principi della progettazione dello schermo e dello schema.

## Recommendations e limitazioni {#recommendations-and-limitations}

L&#39;utilizzo di una tabella di destinatari esterna presenta le seguenti limitazioni:

*  Adobe Campaign non supporta più schemi destinatari, noti come schemi di targeting, collegati agli stessi schemi di trasmissione e/o di trackinglog. In caso contrario si verificheranno successivamente delle anomalie nella riconciliazione dei dati.

   L&#39;elemento grafico seguente descrive la struttura relazionale richiesta per ogni schema di destinatari personalizzato:
   ![](assets/custom_recipient_limitation.png)

   Consigliamo di:

   * Dedicare gli schemi **[!UICONTROL nms:BroadLogRcp]** e **[!UICONTROL nms:TrackingLogRcp]** gli schemi all&#39;out-of-the-box **[!UICONTROL nms:Recipientschema]**. Queste due tabelle di registro non devono essere collegate ad alcuna tabella di destinatari personalizzata aggiuntiva.
   * Definizione di schemi di log e di trackinglog personalizzati dedicati per ogni nuovo schema di destinatari personalizzato. Questa operazione può essere eseguita automaticamente durante la configurazione della mappatura di destinazione, vedete Mappatura [di](../../configuration/using/target-mapping.md)destinazione.

* Non è possibile utilizzare lo standard **[!UICONTROL Services and Subscriptions]** offerto nel prodotto.

   Ciò significa che l&#39;operazione globale descritta in [questa sezione](../../delivery/using/managing-subscriptions.md) non è applicabile.

* Il collegamento con la **[!UICONTROL visitor]** tabella non funziona.

   Pertanto, per utilizzare il **[!UICONTROL Social Marketing]** modulo è necessario configurare il passaggio di memorizzazione per fare riferimento alla tabella corretta.

   Allo stesso modo, quando si utilizzano le funzioni di riferimento, è necessario adattare il modello standard di trasferimento iniziale dei messaggi.

* Non potete aggiungere manualmente i profili in un elenco.

   Pertanto, la procedura descritta in [questa sezione](../../platform/using/creating-and-managing-lists.md) non è applicabile senza una configurazione aggiuntiva.

   >[!NOTE]
   >
   >Puoi comunque creare elenchi di destinatari utilizzando i flussi di lavoro. Per ulteriori informazioni, vedere [Creazione di un elenco di profili con un flusso di lavoro](../../configuration/using/creating-a-profile-list-with-a-workflow.md).

È inoltre consigliabile verificare i valori predefiniti utilizzati nelle diverse configurazioni pronte all&#39;uso: a seconda delle funzionalità utilizzate, devono essere effettuati diversi adattamenti.

Ad esempio:

* Alcuni rapporti standard, in particolare quelli offerti dall&#39; **interazione** e dalle applicazioni **** mobili, devono essere rielaborati. Fare riferimento alla sezione [Gestione dei rapporti](../../configuration/using/managing-reports.md) .
* Le configurazioni predefinite per determinate attività del flusso di lavoro fanno riferimento alla tabella dei destinatari standard (**[!UICONTROL nms:recipient]**): queste configurazioni devono essere modificate se utilizzate per una tabella di destinatari esterni. Fare riferimento alla sezione [Gestione dei flussi di lavoro](../../configuration/using/managing-workflows.md) .
* Il blocco **[!UICONTROL Unsubscription link]** di personalizzazione standard deve essere adattato.
* È necessario modificare la mappatura di destinazione dei modelli di consegna standard.
* I moduli V4 non sono compatibili per l&#39;uso con una tabella di destinatari esterni: è necessario utilizzare applicazioni Web.

