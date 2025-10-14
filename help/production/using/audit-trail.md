---
product: campaign
title: Audit trail
description: Scopri come monitorare l’istanza con Campaign Audit trail
feature: Audit Trail, Monitoring, Workflows
exl-id: 8508d879-fb38-4b1f-9f55-0341bb8d0c67
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 2%

---

# Audit trail{#audit-trail}

>[!INFO]
>
>Ulteriori informazioni sulla funzionalità Audit trail sono disponibili nella [documentazione di Adobe Campaign v8](https://experienceleague.adobe.com/it/docs/campaign/campaign-v8/analytics/audit-trail).

In Adobe Campaign, **[!UICONTROL Audit trail]** consente di accedere alla cronologia completa delle modifiche apportate all&#39;interno dell&#39;istanza.

**[!UICONTROL Audit trail]** acquisisce in tempo reale un elenco completo delle azioni e degli eventi che si verificano nell&#39;istanza Adobe Campaign. Include una modalità autonoma di accedere alla cronologia dei dati per poter rispondere a domande quali: cosa è successo ai flussi di lavoro e chi li ha aggiornati per ultimo o cosa hanno fatto gli utenti nell’istanza.

>[!NOTE]
>
>Adobe Campaign non controlla le modifiche apportate all’interno di diritti utente, modelli, personalizzazioni o campagne.\
>L’audit trail può essere gestito solo dagli amministratori dell’istanza.

![](assets/audit_trail_2.png)

+++ Ulteriori informazioni sulle entità disponibili in Audit Trail

* **Audit trail dello schema**: consente di esplorare le modifiche apportate agli schemi, nonché di identificare chi ha apportato tali modifiche e quando si sono verificate.

  Per informazioni dettagliate sugli schemi, consulta questa [pagina](../../configuration/using/data-schemas.md).

* **Audit trail del flusso di lavoro** tiene traccia di tutte le azioni relative ai flussi di lavoro, tra cui:

   * Inizio
   * Pausa
   * Interruzione
   * Riavvio
   * Pulizia uguale all’azione Cancella cronologia
   * Simula, che è uguale all’azione Avvia in modalità simulazione
   * Attivazione uguale all&#39;azione Esegui attività in sospeso ora
   * Interruzione incondizionata

  Per ulteriori informazioni sui flussi di lavoro, consulta questa [pagina](../../workflow/using/about-workflows.md).

  Per ulteriori informazioni su come monitorare i flussi di lavoro, consulta la [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-workflow-execution.html?lang=it){target="_blank"}.


* **Option audit trail** consente di controllare le attività e le ultime modifiche apportate alle opzioni.

  Per ulteriori informazioni sulle opzioni, consulta questa [pagina](../../installation/using/configuring-campaign-options.md).

* **Audit trail consegna** consente di controllare le attività e le ultime modifiche apportate alle consegne.

  Per ulteriori informazioni sulle consegne, consulta questa [pagina](../../delivery/using/communication-channels.md).

* **Account esterno** consente di controllare le modifiche apportate agli account esterni, utilizzate da processi tecnici quali flussi di lavoro tecnici o flussi di lavoro per campagne.

  Per ulteriori informazioni sull&#39;account esterno, fare riferimento a questa [pagina](../../installation/using/external-accounts.md).

* **Mappatura consegna** consente di monitorare le attività e le modifiche recenti apportate alle mappature di consegna.

  Per ulteriori informazioni sulla mappatura della consegna, consulta questa [pagina](../../configuration/using/target-mapping.md).

* **Applicazione Web** consente di controllare le modifiche apportate ai moduli Web in Campaign V8 utilizzati per creare pagine con campi di input e di selezione e che possono includere dati dal database.

  Per ulteriori informazioni sull&#39;applicazione Web, fare riferimento a questa [pagina](../../web/using/about-web-applications.md).

* **Offerta** ti consente di controllare le attività e le ultime modifiche apportate alle offerte.

  Per ulteriori informazioni sull&#39;offerta, consulta questa [pagina](../../interaction/using/interaction-and-offer-management.md).

* **Operatore** consente di monitorare le attività e le modifiche recenti apportate agli operatori.

  Per ulteriori informazioni sugli operatori, consulta questa [pagina](../../platform/using/access-management-operators.md).

+++
