---
title: Domande frequenti su Test e Send
seo-title: Convalida, invio e tracciamento dei messaggi
description: Domande frequenti su Campaign Classic
page-status-flag: never-activated
uuid: 3f719ac2-cc26-4fb0-adda-84666c8c38e1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 16dbe423-018f-4666-9901-2120a8dc609a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 994ec35e37a1c26e83a8dd2ae31f6594cadd4c45

---


# Convalida, invio e tracciamento dei messaggi {#validate-send-track}

## Test e convalida {#test-and-validate-before-sending}

Scopri come eseguire i passaggi di verifica e convalida prima di inviare messaggi in Adobe Campaign.

### Cos&#39;è l&#39;analisi di consegna? {#what-is-the-delivery-analysis-}

L&#39;analisi di consegna è la fase in cui viene calcolata la popolazione di destinazione e preparato il contenuto di consegna. Una volta completato, la consegna è pronta per l&#39;invio. Consultate i registri per verificare che tutto sia corretto.

[Fai clic qui per saperne di più](../../delivery/using/steps-validating-the-delivery.md).

### Perché dovrei creare delle prove? {#why-should-i-create-proofs-}

Adobe consiglia vivamente di creare messaggi di prova per verificare la consegna su un gruppo di approvazione prima di inviarlo alla destinazione principale. Puoi quindi convalidare il contenuto dei messaggi, i parametri di personalizzazione e di distribuzione.

[Fai clic qui per saperne di più](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof). Potete anche guardare [questo video](https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/getting-started/managing-seed-and-proofs.html).

### Come utilizzare gli indirizzi iniziali in Adobe Campaign? {#how-to-use-seed-addresses-in-adobe-campaign-}

Gli indirizzi dei semi vengono utilizzati per i destinatari a cui non corrispondono ai criteri di destinazione definiti. Questi destinatari vengono aggiunti alla destinazione: possono essere importati o creati direttamente nella consegna o nella campagna. Per le consegne per corrispondenza diretta, queste vengono aggiunte durante l&#39;estrazione e mescolate nel documento di output.

Questo offre i seguenti vantaggi:

* Sostituzione casuale di campi con dati provenienti dai profili dei destinatari: questo consente di inserire solo l&#39;indirizzo e-mail, ad esempio nella sezione dell&#39;indirizzo e-mail.
* Quando si utilizza un flusso di lavoro con funzionalità di gestione dei dati, i dati aggiuntivi elaborati nelle consegne possono essere immessi a livello di indirizzo del seme per imporre valori: in questo modo si verifica una sostituzione casuale del valore.

[Clicca qui per saperne di più sugli indirizzi](../../delivery/using/about-seed-addresses.md)iniziali.

### Come posso impostare un processo di approvazione prima di inviare i messaggi? {#how-can-i-set-up-an-approval-process-before-sending-messages-}

Per rilevare eventuali errori nella configurazione dei messaggi, Adobe consiglia vivamente di impostare un ciclo di convalida della consegna. Accertatevi che il contenuto venga approvato con la frequenza necessaria inviando prove di stampa ai destinatari del test. Una prova deve essere inviata ogni volta che viene apportata una modifica per approvare il contenuto.

[Fai clic qui per saperne di più](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### Che cos&#39;è una regola di tipologia? {#what-is-a-typology-rule-}

Per evitare conflitti tra campagne, Adobe Campaign può sottoporre a test diverse combinazioni applicando regole di vincolo specifiche. Questo garantisce che i messaggi inviati soddisfino al meglio le esigenze e le aspettative dei clienti, in linea con le politiche di comunicazione aziendali.

[Fai clic qui per saperne di più](../../campaign/using/about-campaign-typologies.md).

## Invio dei messaggi {#send-your-messages}

Scopri come inviare messaggi in diversi canali con Adobe Campaign.

### Come posso inviare le e-mail a onde? {#how-can-i-send-emails-in-waves-}

Prima di inviare una consegna a una popolazione numerosa, potete [configurare le onde](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves) per dividere i messaggi in più batch e bilanciare il carico.

### Quali sono i passaggi chiave per creare un&#39;e-mail in Campaign? {#which-are-the-key-steps-to-create-an-email-in-campaign-}

Una volta creata e convalidata la consegna, potete inviarla. Puoi decidere di inviare l&#39;e-mail alla destinazione principale immediatamente o pianificare una consegna per una data successiva. Se necessario, prima di questo, potete anche stimare la popolazione di destinazione.

[Fai clic qui per saperne di più](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### Come pianificare una consegna? {#how-to-schedule-a-delivery-}

È possibile posticipare la consegna dei messaggi per pianificare la consegna o gestire la pressione di vendita ed evitare l&#39;eccesso di richieste da parte di una popolazione.

[Fai clic qui per saperne di più](../../delivery/using/steps-sending-the-delivery.md#scheduling-the-delivery-sending).

### È possibile aggiungere un allegato alle e-mail? {#can-i-add-an-attachment-to-emails-}

Con Campaign Classic puoi aggiungere allegati personalizzati alle e-mail.

[Fare clic qui per ulteriori informazioni sugli allegati](../../delivery/using/attaching-files.md)e-mail.

## Monitora i messaggi e misurane l&#39;impatto {#track-your-messages-and-measure-their-impact}

Una volta inviati i messaggi, scopri come tracciarne e misurare il loro impatto con Adobe Campaign.

### Come posso configurare i collegamenti tracciati in una consegna e-mail? {#how-can-i-configure-tracked-links-in-an-email-delivery-}

Per ogni consegna, puoi tenere traccia della ricezione dei messaggi e dell&#39;attivazione dei collegamenti inseriti nel contenuto del messaggio. In questo modo puoi tenere traccia del comportamento dei destinatari in seguito alle azioni di consegna a cui sono stati assegnati.

Per ciascun URL del messaggio, potete scegliere se attivare o meno il tracciamento, cambiare l’etichetta del collegamento, raggruppare i collegamenti per categorie, ad esempio per scopo di reporting.

[Fai clic qui per saperne di più](../../delivery/using/about-message-tracking.md) su come tenere traccia dei messaggi in Campaign Classic.

### Dove posso accedere ai registri di consegna e tracciamento? {#where-can-i-access-delivery-and-tracking-logs-}

Scopri come tenere traccia delle consegne e comprendere il comportamento dei destinatari [da questa pagina](../../delivery/using/monitoring-a-delivery.md).

### Dove è possibile ottenere i rapporti sulla consegna? {#where-can-i-get-delivery-reports-}

Adobe Campaign viene fornito con una serie di rapporti per monitorare le consegne e tenere traccia dei messaggi.

[Fai clic qui per saperne di più sui report](../../reporting/using/reports-on-deliveries.md#delivery-reports)incorporati.

### In che modo Adobe Campaign qualifica e gestisce gli indirizzi di quarantena? {#how-does-adobe-campaign-qualify-and-manage-quarantine-addresses-}

Adobe Campaign gestisce un elenco di indirizzi in quarantena. I destinatari il cui indirizzo è stato messo in quarantena sono esclusi per impostazione predefinita durante l&#39;analisi del recapito e non verranno impostati come destinazione. Un indirizzo e-mail può essere messo in quarantena, ad esempio, quando la cassetta postale è piena o se l&#39;indirizzo non esiste.

[Fai clic qui per saperne di più sulla gestione](../../delivery/using/understanding-quarantine-management.md)della quarantena.
