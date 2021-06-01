---
product: campaign
title: Privacy
description: Ulteriori informazioni sulle best practice da seguire in materia di privacy.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 0a3473bf-0528-486d-a799-8db86fece522
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '768'
ht-degree: 5%

---

# Privacy {#privacy}

## Richieste sulla privacy

 Adobe Campaign offre una serie di strumenti per aiutarti con la conformità in materia di privacy in relazione a GDPR e CCPA.

Fai riferimento a [questa pagina](../../platform/using/privacy-management.md) per informazioni generali su cosa è Privacy Management e sui passaggi di implementazione in Adobe Campaign. Troverai inoltre le best practice e una panoramica del processo utente e dei singoli utenti.

## Personalizzazione URL {#url-personalization}

Quando aggiungi collegamenti personalizzati al contenuto, evita sempre di avere alcuna personalizzazione nella parte dell’URL relativa al nome host per evitare potenziali lacune nella sicurezza. Gli esempi seguenti non devono mai essere utilizzati in tutti gli attributi URL &lt;`a href="">` o `<img src="">`:

* `<%= url >`
* `https://<%= url >`
* `https://<%= domain >/path`
* `https://<%= sub-domain >.domain.tld/path`
* `https://sub.domain<%= main domain %>/path`

### Consiglio

Per convalidare e assicurarsi di non utilizzare quanto sopra, esegui una query sulla tabella URL di tracciamento tramite [Editor query generico campagna](../../platform/using/steps-to-create-a-query.md) o crea un flusso di lavoro con criteri di filtro nell&#39; [attività query](../../workflow/using/query.md).

Esempio:

1. Crea un flusso di lavoro e aggiungi un’attività Query . Ulteriori informazioni.

1. Apri l’attività Query e crea un filtro sulla tabella nmsTrackingUrl come segue: l’URL sorgente inizia con http://&lt;% o l’URL sorgente inizia con https://&lt;%.

1. Esegui il flusso di lavoro e controlla se ci sono dei risultati.

1. In tal caso, apri la transizione di output per visualizzare l’elenco degli URL.

<img src="assets/privacy-query-dynamic-url.png">

### Meccanismo di firma

Per migliorare la sicurezza, nella build 19.1.4 (9032@3a9dc9c) è stato introdotto un nuovo meccanismo di firma per il tracciamento dei collegamenti nelle e-mail ed è disponibile nelle Build 19.1.4 (9032@3a9dc9c) e Campaign 20.2. Questa opzione è abilitata per impostazione predefinita per tutti i clienti.

>[!NOTE]
>
>Quando fai clic su un URL firmato non valido, viene restituito il seguente errore: &quot;Impossibile trovare l&#39;URL richiesto &quot;..&quot;.

Inoltre, a partire dalla versione Campaign 20.2 e [!DNL Gold Standard], i clienti in hosting e ibridi possono utilizzare un miglioramento per disabilitare gli URL generati dalle build precedenti. Questa opzione è disabilitata per impostazione predefinita. Per abilitare questa funzione, contatta l’ [Assistenza clienti](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) .

Per attivare questo nuovo meccanismo, i clienti on-premise devono seguire questi passaggi su tutti i server Campaign:

1. Nel file di configurazione del server (serverConf.xml), cambia **blockRedirectForUnsignedTrackingLink** in **true**.
1. Riavvia il servizio **nlserver** .
1. Sul server di tracciamento, riavvia il server web (apache2 su Debian, httpd su CentOS/RedHat, IIS su Windows).

I clienti in esecuzione su [!DNL Gold Standard] 19.1.4 possono riscontrare problemi con le consegne di notifiche push utilizzando un collegamento di tracciamento o con le consegne che utilizzano tag di ancoraggio. In tal caso, Adobe consiglia di disabilitare il nuovo meccanismo di firma per i collegamenti di tracciamento:

**I** clienti in hosting e ibridi devono contattare  [Customer ](https://helpx.adobe.com/it/enterprise/using/support-for-experience-cloud.html) Careto per disattivare questo meccanismo.

**I** clienti on-premise possono eseguire la scansione seguendo il passaggio seguente:

1. Nel file di configurazione del server (serverConf.xml), cambia **signEmailLinks** in **false**.
1. Riavvia il servizio **nlserver** .
1. Sul server di tracciamento, riavvia il server web (apache2 su Debian, httpd su CentOS/RedHat, IIS su Windows).

## Restrizione dei dati

Devi accertarti che le password crittografate non siano accessibili da un utente autenticato con privilegi bassi. Per fare questo, ci sono due modi principali: limita l&#39;accesso ai campi password solo o all&#39;intera entità (è necessaria una build >= 8770).

Questa limitazione consente di rimuovere i campi password, ma consente all’account esterno di essere accessibile dall’interfaccia per tutti gli utenti. Consulta [questa pagina](../../configuration/using/restricting-pii-view.md).

1. Vai in **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data schemas]**.

1. Crea un nuovo **[!UICONTROL Extension of a schema]**.

   ![](assets/privacy-data-restriction.png)

1. Scegli **[!UICONTROL External Account]** (extAccount).

1. Nell’ultima schermata della procedura guidata, puoi modificare il nuovo srcSchema per limitare l’accesso a tutti i campi password:

   Puoi sostituire l’elemento principale (`<element name="extAccount" ... >`) con:

   ```
   <element name="extAccount">
       <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
       <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
   
       <element name="s3Account">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="awsSecret"/>
       </element>
       <element name="wapPush">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
       </element>
       <element name="mms">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
       </element>
   </element>
   ```

   Il tuo srcSchema esteso può avere un aspetto simile a:

   ```
   <srcSchema _cs="External Accounts (cus)" created="2017-05-12 07:53:49.691Z" createdBy-id="0"
               desc="Definition of external accounts (Email, SMS...) used by the modules"
               entitySchema="xtk:srcSchema" extendedSchema="nms:extAccount" img="" label="External Accounts"
               labelSingular="External account" lastModified="2017-05-12 08:33:49.365Z"
               mappingType="sql" md5="E9BB0CD6A4375F500027C86EA854E101" modifiedBy-id="0"
               name="extAccount" namespace="cus" xtkschema="xtk:srcSchema">
       <createdBy _cs="Administrator (admin)"/>
       <modifiedBy _cs="Administrator (admin)"/>
       <element name="extAccount">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
   
           <element name="s3Account">
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="awsSecret"/>
           </element>
           <element name="wapPush">
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
           </element>
           <element name="mms">
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
           </element>
       </element>
   </srcSchema>    
   ```

   >[!NOTE]
   >
   >È possibile sostituire `$(loginId) = 0 or $(login) = 'admin'` con `hasNamedRight('admin')` per consentire a tutti gli utenti con diritti di amministratore di visualizzare queste password.

## Protezione delle pagine contenenti PII

Consigliamo vivamente ai clienti on-premise di proteggere le pagine che potrebbero contenere informazioni personali come pagine mirror, applicazioni web, ecc.

L&#39;obiettivo di questa procedura è evitare l&#39;indicizzazione di queste pagine, evitando così un potenziale rischio per la sicurezza. Ecco alcuni articoli utili:

* [https://developers.google.com/search/reference/robots_txt](https://developers.google.com/search/reference/robots_txt)
* [https://developers.google.com/search/reference/robots_meta_tag](https://developers.google.com/search/reference/robots_meta_tag)
* [https://www.google.com/webmasters/tools/robots-testing-tool](https://www.google.com/webmasters/tools/robots-testing-tool)

Per proteggere le pagine, effettua le seguenti operazioni:

1. Aggiungi un file robots.txt nella directory principale del server web (Apache o IIS). Ecco il contenuto del file:

   ```
   # Make changes for all web spiders
   User-agent:
   *Disallow: /
   ```

   Per IIS, fare riferimento a [questa pagina](https://docs.microsoft.com/en-us/iis/extensions/iis-search-engine-optimization-toolkit/managing-robotstxt-and-sitemap-files).

   Per Apache, puoi inserire il file in **/var/www/robots.txt** (Debian).

1. A volte l&#39;aggiunta di un file **robots.txt** non è sufficiente in termini di sicurezza. Ad esempio, se un altro sito web contiene un collegamento alla pagina, potrebbe essere visualizzato in un risultato della ricerca.

Oltre al file **robots.txt**, è consigliabile aggiungere un&#39;intestazione **X-Robots-Tag**. Puoi farlo in Apache o IIS e nel file di configurazione **serverConf.xml**.

Per ulteriori informazioni, consulta [questo articolo](https://developers.google.com/search/reference/robots_meta_tag).
