---
product: campaign
title: Domande frequenti su Campaign Classic
description: Domande specifiche sull’architettura, la distribuzione e le funzionalità di Adobe Campaign Classic v7
feature: Overview, Troubleshooting
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
source-git-commit: 8d9bb9d2ff4450646bbf218804b8c8b4459b5a91
workflow-type: tm+mt
source-wordcount: '1345'
ht-degree: 3%

---

# Domande frequenti su Campaign Classic v7 {#campaign-classic-v7-faq}

>[!NOTE]
>
>Queste domande frequenti riguardano questioni specifiche relative all’architettura di Adobe Campaign Classic v7, ai modelli di distribuzione e alle funzioni specifiche di v7.
>
>**Per risposte complete alle domande comuni su Campaign** (flussi di lavoro, consegne, pubblico, creazione di rapporti, personalizzazione, ecc.), consulta le [**Domande frequenti complete su Campaign v8**](https://experienceleague.adobe.com/it/docs/campaign/campaign-v8/new/campaign-faq-comprehensive){target="_blank"}, che forniscono risposte dettagliate organizzate per argomento.

## Architettura e implementazione di Campaign Classic v7 {#v7-architecture}

Trova risposte su modelli di hosting, differenze di distribuzione e percorsi di migrazione per Campaign Classic v7. Queste domande si concentrano sulle scelte dell&#39;infrastruttura e sulle relative responsabilità.

+++ Quali sono i modelli di hosting disponibili in Campaign Classic v7? {#what-are-the-hosting-models-available-in-campaign-classic-v7}

Adobe Campaign Classic v7 offre tre modelli di distribuzione:

* **In hosting (Managed Services)** - Gestito completamente da Adobe sull&#39;infrastruttura Adobe
* **On-Premise** - Installato e gestito nella tua infrastruttura
* **Ibrido** - Architettura mid-sourcing con componenti cloud e on-premise

Ogni modello di distribuzione ha funzionalità e responsabilità di gestione diverse. La disponibilità di moduli, opzioni e configurazioni dipende dal tipo di distribuzione.

[Fai clic qui per ulteriori informazioni](../../installation/using/hosting-models.md) sui modelli di hosting e sulle loro differenze.

**Nota:** Campaign v8 è disponibile esclusivamente come Managed Cloud Services. [Scopri di più su Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/new/whats-new.html?lang=it){target="_blank"}.

+++

+++ Quali sono le differenze quando si lavora on-premise rispetto a un ambiente in hosting? {#what-are-the-differences-when-working-on-premise-vs-in-a-hosted-environment}

Adobe Campaign Classic v7 è dotato di una serie di moduli e opzioni. La disponibilità di questi moduli e la loro configurazione dipendono dal [tipo di distribuzione](../../installation/using/hosting-models.md) dell&#39;installazione: in hosting (Managed Services), ibrida o on-premise.

Differenze chiave:

* **On-Premise** - Controllo completo su installazione, infrastruttura e configurazione. Richiede risorse IT interne per la manutenzione, gli aggiornamenti e la sicurezza.
* **In hosting/Managed Services**: infrastruttura e manutenzione gestite da Adobe. Aggiornamenti automatici e maggiore sicurezza. Accesso diretto limitato al server.
* **Ibrido** - Combina i vantaggi di entrambi i modelli. Istanza di marketing ospitata da Adobe, esecuzione/mid-sourcing gestito separatamente.

[Fare clic qui per la matrice delle funzionalità complete](../../installation/using/capability-matrix.md).

+++

+++ Come posso effettuare la migrazione da on-premise/ibrido ad Adobe Managed Services? {#how-do-i-migrate-from-on-premise-hybrid-to-adobe-managed-services}

La migrazione ad Adobe Managed Services offre maggiore scalabilità, sicurezza e riduzione del sovraccarico IT. Spesso rappresenta un punto di partenza prima della transizione a Campaign v8.

**Punti chiave:**

* Nessuno strumento di migrazione automatizzata disponibile: è necessaria la pianificazione e l&#39;esecuzione manuale
* Supporto Adobe Professional Services altamente consigliato
* I vantaggi includono infrastruttura cloud, patch di sicurezza automatiche, supporto specialistico e percorso più semplice verso v8
* La migrazione prevede la dovuta diligenza, l’audit dell’ambiente, la pulizia dei dati, la migrazione degli ambienti di staging e il cutover di produzione

**Guida introduttiva:** Contatta il tuo rappresentante Adobe per valutare il tuo ambiente e sviluppare un piano di migrazione dettagliato con Adobe Professional Services.

Ulteriori informazioni sulla [migrazione a Managed Services](https://experienceleaguecommunities.adobe.com/t5/adobe-campaign-classic-blogs/migrate-your-adobe-campaign-v7-onprem-hybrid-environment-to/ba-p/681605?profile.language=it){target="_blank"}.

+++

+++ Devo effettuare la migrazione da Campaign Classic v7 a Campaign v8? {#should-i-migrate-to-v8}

Campaign v8 è la piattaforma strategica di Adobe, ideale per le organizzazioni che necessitano di campagne a volume elevato, interfaccia web moderna, vantaggi nativi per il cloud e supporto a lungo termine. Nei prossimi anni Campaign Classic v7 cesserà il supporto.

**Esegui la migrazione a Campaign v8 se:**

* Gestire grandi volumi di dati o problemi di prestazioni
* Desideri ridurre il sovraccarico IT e la gestione dell&#39;infrastruttura (v8 è solo Managed Cloud Services)
* Necessità di un’integrazione moderna dell’interfaccia utente e di Adobe Experience Platform
* Desiderate una tecnologia a prova di futuro con aggiornamenti automatici
* Attualmente si trovano su servizi gestiti/in hosting (percorso di migrazione più semplice)

**Considerazioni importanti:**

* Campaign v8 è disponibile esclusivamente come Managed Cloud Services (nessuna opzione on-premise/ibrida)
* Richiede la pianificazione della migrazione di personalizzazioni e integrazioni
* L’architettura FFDA migliora le prestazioni ma richiede alcuni adattamenti di flusso di lavoro e API

**Passaggi successivi:** Contatta il tuo rappresentante Adobe per valutare la fattibilità della migrazione e accedere agli strumenti di migrazione.

Ulteriori informazioni:

* [Panoramica di Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/new/whats-new.html?lang=it){target="_blank"}
* [Transizione da Campaign Classic v7 a v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/v7-to-v8.html){target="_blank"}
* [Domande frequenti complete su Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html){target="_blank"}

**Per risposte dettagliate alle domande comuni su Campaign relative a flussi di lavoro, consegne, tipi di pubblico, reporting, personalizzazione e altro ancora**, visita la [Domande frequenti complete su Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html){target="_blank"}.

+++

## Aggiornamenti della build (Campaign Classic v7) {#build-upgrades-v7}

Per le indicazioni sull&#39;aggiornamento della build e le relative domande frequenti, consulta le [Domande frequenti sull&#39;aggiornamento della build](faq-build-upgrade.md) e la [documentazione sull&#39;aggiornamento della build](../../production/using/build-upgrade.md).

## Configurazione Campaign Classic v7 {#v7-configuration}

Queste domande riguardano le attività e i criteri di configurazione comuni in Campaign Classic v7, dalle impostazioni della lingua all’irrigidimento della sicurezza. Utilizzali per convalidare le scelte di configurazione e le pratiche operative.

+++ Posso cambiare la lingua dell’interfaccia di Campaign Classic v7? {#can-i-change-language-v7}

Durante la creazione dell’istanza viene selezionata la lingua di Campaign Classic v7. **Impossibile modificarlo in seguito.**

L’interfaccia utente di Adobe Campaign v7 è disponibile in 4 lingue: inglese, francese, tedesco e giapponese. La console client e il server devono essere impostati nella stessa lingua. Ogni istanza di Campaign Classic v7 può essere eseguita in una sola lingua.

Per l’inglese, durante l’installazione di Campaign v7 puoi selezionare inglese US o inglese GB, che differiscono nei formati di data e ora.

[Per ulteriori informazioni, consulta questa sezione](../../installation/using/creating-an-instance-and-logging-on.md).

**Nota:** l&#39;interfaccia utente Web di Campaign v8 consente agli utenti di modificare la lingua dell&#39;interfaccia in modo indipendente. [Ulteriori informazioni](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/connect.html#language-pref){target="_blank"}.

+++

+++ Come si configurano le aree di protezione in Campaign Classic v7? {#how-can-i-configure-security-zones-v7}

L’interfaccia self-service Aree di sicurezza può essere utilizzata per gestire le voci nella configurazione dell’area di sicurezza VPN di una distribuzione di Adobe Campaign Classic v7. Questo è importante principalmente per le distribuzioni on-premise e ibride.

Leggi [questa sezione](../../installation/using/security-zones.md) per informazioni sulle aree di protezione in Campaign v7.

[Fare clic qui per ulteriori informazioni](https://helpx.adobe.com/it/campaign/kb/configuring-security-zones-self-service.html){target="_blank"} sull&#39;interfaccia utente autonoma delle aree di protezione.

**Nota:** i clienti Hosted/Managed Services devono contattare Adobe per configurare le aree di protezione.

+++

+++ Adobe Campaign Classic v7 può integrarsi con LDAP? {#can-campaign-classic-integrate-with-ldap}

Sì. In qualità di **cliente on-premise/ibrido**, puoi integrare Campaign Classic v7 con la tua directory LDAP per l&#39;autenticazione e la gestione centralizzate degli utenti.

Questa integrazione consente di:

* Utenti da autenticare nell&#39;elenco LDAP aziendale
* Gestione centralizzata di utenti e diritti
* Sincronizzazione automatica dei gruppi di utenti e delle autorizzazioni
* Funzionalità Single Sign-On

[Fai clic qui per scoprire come](../../installation/using/connecting-through-ldap.md) configurare l&#39;integrazione LDAP in Campaign Classic v7.

**Nota:** l&#39;integrazione LDAP è disponibile per le distribuzioni locali e ibride. I clienti in hosting utilizzano Adobe IMS per l’autenticazione.

+++

+++ Quali sono le best practice di sicurezza per le distribuzioni on-premise? {#security-best-practices-on-premise}

Le distribuzioni on-premise e ibride richiedono una configurazione di sicurezza e un irrigidimento aggiuntivi rispetto agli ambienti in hosting.

**Aree di protezione chiave:**

* Sicurezza di rete e configurazione del firewall
* Accesso e protezione del database
* Protezione avanzata del sistema operativo
* Autorizzazioni dei file e controlli di accesso
* Configurazione delle aree di protezione
* Crittografia (dati a riposo e in transito)
* Gestione degli accessi utente
* Applicazione regolare di patch di sicurezza
* Registrazione e monitoraggio dei controlli

Leggi la [lista di controllo per la configurazione della sicurezza](https://helpx.adobe.com/it/campaign/kb/acc-security.html){target="_blank"} per scoprire gli elementi chiave da verificare per la configurazione e l&#39;irrigidimento della sicurezza per le distribuzioni locali.

+++

+++ Come si cancella la cache della console client? {#how-do-i-clear-console-cache}

La cancellazione della cache della console client di Campaign risolve molti problemi comuni di visualizzazione e funzionalità. La cache memorizza i file di configurazione locali che a volte possono danneggiarsi o non essere più aggiornati.

**Quando cancellare la cache:**

* I nuovi elementi di branding non vengono visualizzati correttamente
* Errore imprevisto delle funzioni di esportazione/importazione
* Gli elementi dell’interfaccia non vengono aggiornati dopo le modifiche alla configurazione
* Problemi di prestazioni o risposta lenta della console
* Dopo l’aggiornamento a una nuova versione della console client

**Come cancellare la cache:**

1. **Cancellazione cache temporanea (provare prima):**
   * Apri la console del client Campaign.
   * Vai al menu **[!UICONTROL File]**
   * Seleziona **[!UICONTROL Clear the local cache...]**
   * Conferma l’azione quando richiesto
   * Riavvia la console client

2. **Cancellazione della Hard Cache (se la cancellazione temporanea non risolve il problema):**
   * Esegui prima la cancellazione della Soft Cache
   * Esci e chiudi completamente la console client
   * Accedi a:
      * Windows 7/10: `C:\Users\<Username>\AppData\Roaming\Neolane\NL_5\`
      * Windows XP: `C:\Documents and Settings\<Username>\Application Data\Neolane\NL_5\`
   * Elimina tutti i file XML denominati `nlclient-config-<alphanumerical value>.xml` e le cartelle associate
   * **Importante:** Non eliminare il file `nlclient_cnx.xml`
   * Riavvia console client

Ulteriori informazioni sono disponibili nella [documentazione della console client di Campaign](../../platform/using/launching-adobe-campaign.md).

+++

+++ Dove possono gestire le impostazioni delle istanze i clienti in hosting? {#where-to-manage-instance-settings}

Il [Pannello di controllo Campaign](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=it){target="_blank"} consente agli amministratori di prodotto per Adobe Campaign di gestire le impostazioni e tenere traccia dell&#39;utilizzo per ogni istanza. L’interfaccia intuitiva consente di monitorare le risorse chiave ed eseguire attività amministrative come aggiornamenti del inserisco nell&#39;elenco Consentiti di IP, monitoraggio dell’archiviazione SFTP, gestione delle chiavi e altro ancora.

**Vantaggi chiave:**

* Apporta rapidamente le modifiche alle impostazioni senza rivolgerti all’Assistenza clienti.
* Configurare le impostazioni in base alle diverse esigenze aziendali in momenti diversi.
* Migliora la sicurezza controllando le impostazioni di accesso in base alle necessità.

+++

## Ottenimento della Guida {#getting-help}

Trova la documentazione chiave, le domande frequenti e i canali di supporto per Campaign Classic v7, inclusi i collegamenti ai forum della community e il supporto di Adobe.

+++ Dove posso trovare la documentazione di Campaign Classic v7? {#where-to-find-more-info-v7}

**Documentazione e risorse:**

* [Documentazione di Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/campaign-classic-home.html?lang=it){target="_blank"} - Documentazione completa
* [Note sulla versione di Campaign Classic v7](../../rn/using/latest-release.md) - Informazioni sull&#39;ultima versione
* [Matrice di compatibilità di Campaign Classic](../../rn/using/compatibility-matrix.md) - Sistemi e versioni supportati
* [Esercitazioni Campaign Classic](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=it){target="_blank"} - Esercitazioni video

**Per le domande comuni su Campaign:**

Consulta le [**Domande frequenti complete su Campaign v8**](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html){target="_blank"}, che forniscono risposte dettagliate su:

* Guida introduttiva a Campaign
* Profili e tipi di pubblico
* Progettazione e consegna dei messaggi
* Flussi di lavoro e automazione
* Reporting e analisi
* Impostazioni e configurazione di Campaign
* Risorse per sviluppatori
* Privacy e conformità

+++

+++ Come posso ottenere il supporto della community o di Adobe per Campaign Classic v7? {#where-to-get-support-v7}

**Community e supporto:**

* [Forum della community di Campaign](https://experienceleaguecommunities.adobe.com/t5/adobe-campaign-classic/ct-p/adobe-campaign-classic-community?profile.language=it){target="_blank"}
* [Supporto Adobe](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){target="_blank"}

+++
