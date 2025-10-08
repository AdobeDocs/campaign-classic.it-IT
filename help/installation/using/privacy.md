---
product: campaign
title: Personalizzazione e privacy
description: Scopri le best practice sulla sicurezza per la privacy e la personalizzazione
feature: Installation, Privacy, Privacy Tools, URL Personalization
exl-id: 0a3473bf-0528-486d-a799-8db86fece522
source-git-commit: 192505e1c4d387de55ca18b578b837d237cc0607
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 2%

---

# Personalizzazione e privacy {#privacy}

## URL PERSONALIZATION {#url-personalization}

Quando aggiungi collegamenti personalizzati al contenuto, evita sempre di includere alcuna personalizzazione nella parte nome host dell’URL per evitare potenziali lacune di sicurezza. I seguenti esempi non devono mai essere utilizzati in tutti gli attributi URL &lt;`a href="">` o `<img src="">`:

* `<%= url >`
* `https://<%= url >`
* `https://<%= domain >/path`
* `https://<%= sub-domain >.domain.tld/path`
* `https://sub.domain<%= main domain %>/path`

### Consiglio

Per convalidare e assicurarsi di non utilizzare quanto sopra, eseguire una query sulla tabella degli URL di tracciamento tramite [Editor query generico di Campaign](../../platform/using/about-queries-in-campaign.md) oppure creare un flusso di lavoro con criteri di filtro nell&#39;attività [query](../../workflow/using/query.md).

Esempio:

1. Crea un flusso di lavoro e aggiungi un&#39;attività **Query**. [Ulteriori informazioni](../../workflow/using/query.md).

1. Aprire l&#39;attività **Query** e creare un filtro per la tabella `nmsTrackingUrl` nel modo seguente:

   `source URL starts with http://<% or source URL starts with https://<%`

1. Esegui il flusso di lavoro e verifica se sono presenti risultati.

1. In tal caso, apri la transizione di output per visualizzare l’elenco degli URL.

   ![](assets/privacy-query-dynamic-url.png)


### Firma URL

Per migliorare la sicurezza, è stato introdotto un meccanismo di firma per il tracciamento dei collegamenti nelle e-mail. È disponibile a partire dalle build 19.1.4 (9032@3a9dc9c) e 20.2. Questa funzione è attivata per impostazione predefinita.

>[!NOTE]
>
>Quando si fa clic su un URL firmato non valido, viene restituito questo errore: `Requested URL '…' was not found.`

Inoltre, puoi utilizzare un miglioramento per disabilitare gli URL generati nelle build precedenti. Questa funzione è disabilitata per impostazione predefinita. Puoi contattare [l&#39;Assistenza clienti](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) per abilitare questa funzione.

Se esegui la build 19.1.4, potrebbero verificarsi problemi con le consegne di notifiche push tramite collegamenti di tracciamento o le consegne con tag di ancoraggio. In tal caso, si consiglia di disabilitare la firma URL.

In qualità di cliente ibrido, Managed Cloud Services o in hosting per Campaign, devi contattare l&#39;[Assistenza clienti](https://helpx.adobe.com/it/enterprise/using/support-for-experience-cloud.html) per disabilitare la firma URL.

Se esegui Campaign in un’architettura ibrida, prima di abilitare la firma URL, assicurati che l’istanza mid-sourcing ospitata sia stata aggiornata come segue:

* Prima l’istanza di marketing on-premise
* Quindi effettua l’aggiornamento alla stessa versione dell’istanza di marketing on-premise o a una versione leggermente superiore

In caso contrario, potrebbero verificarsi alcuni dei seguenti problemi:

* Prima che l’istanza di mid-sourcing venga aggiornata, gli URL vengono inviati senza firma tramite questa istanza.
* Dopo l’aggiornamento dell’istanza di mid-sourcing e l’abilitazione della firma URL in entrambe le istanze, gli URL inviati in precedenza senza firma vengono rifiutati. Il motivo è che una firma viene richiesta dai file di tracciamento forniti dall’istanza di marketing.

Per disabilitare gli URL generati nelle build precedenti, effettua le seguenti operazioni su tutti i server Campaign contemporaneamente:

1. Nel file di configurazione del server (`serverConf.xml`), modificare l&#39;opzione **blockRedirectForUnsignedTrackingLink** in **true**.
1. Riavviare il servizio `nlserver`.
1. Sul server `tracking`, riavviare il server `web` (apache2 su Debian, httpd su CentOS/RedHat, IIS su Windows).

Per abilitare la firma URL, effettua le seguenti operazioni su tutti i server Campaign contemporaneamente:

1. Nel file di configurazione del server (`serverConf.xml`), modifica l&#39;opzione **signEmailLinks** in **true**.
1. Riavviare il servizio **nlserver**.
1. Sul server `tracking`, riavviare il server `web` (apache2 su Debian, httpd su CentOS/RedHat, IIS su Windows).

## Limitazione dei dati

È necessario assicurarsi che le password crittografate non siano accessibili da un utente autenticato con privilegi limitati. A questo scopo, limita l’accesso solo ai campi della password o all’intera entità (è necessaria una build >= 8770).

Questa restrizione ti consente di rimuovere i campi delle password, ma di consentire all’account esterno di essere accessibile dall’interfaccia per tutti gli utenti. [Ulteriori informazioni](../../configuration/using/restricting-pii-view.md).

A tale scopo, segui i passaggi indicati di seguito:

1. Selezionare la cartella **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data schemas]** di Esplora campagne.

1. Creare uno schema di dati come **[!UICONTROL Extension of a schema]**.

   ![](assets/privacy-data-restriction.png)

1. Scegliere **[!UICONTROL External Account]** (extAccount).

1. Nell’ultima schermata dell’assistente, modifica il nuovo &quot;srcSchema&quot; per limitare l’accesso a tutti i campi della password:

   È possibile sostituire l&#39;elemento principale (`<element name="extAccount" ... >`) con:

   ```sql
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

   In questo modo lo schema src esteso può essere simile al seguente:

   ```sql
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

## Proteggi pagine con PI

Consigliamo vivamente ai clienti on-premise di proteggere le pagine che potrebbero contenere informazioni personali (PI) come pagine mirror, applicazioni web, ecc.

L’obiettivo di questa procedura è quello di evitare che queste pagine vengano indicizzate, evitando in tal modo un potenziale rischio per la sicurezza. Di seguito sono riportati alcuni articoli utili:

* [https://developers.google.com/search/reference/robots_txt](https://developers.google.com/search/reference/robots_txt)
* [https://developers.google.com/search/reference/robots_meta_tag](https://developers.google.com/search/reference/robots_meta_tag)

Per proteggere le pagine, effettua le seguenti operazioni:

1. Aggiungi un file `robots.txt` nella directory principale del server Web (Apache o IIS). Di seguito è riportato il contenuto del file:

   ```sql
   # Make changes for all web spiders
   User-agent:
   *Disallow: /
   ```

   Per IIS, fare riferimento a [questa pagina](https://docs.microsoft.com/en-us/iis/extensions/iis-search-engine-optimization-toolkit/managing-robotstxt-and-sitemap-files).

   Per Apache, puoi inserire il file in **/var/www/robots.txt** (Debian).

1. A volte l&#39;aggiunta di un file **robots.txt** non è sufficiente in termini di sicurezza. Ad esempio, se un altro sito Web contiene un collegamento alla pagina, potrebbe essere visualizzato in un risultato di ricerca.

   Oltre al file **robots.txt**, si consiglia di aggiungere un&#39;intestazione **X-Robots-Tag**. Puoi eseguire questa operazione in Apache o IIS e nel file di configurazione **serverConf.xml**.

   Per ulteriori informazioni, consultare [questo articolo](https://developers.google.com/search/reference/robots_meta_tag).


## Richieste di privacy

Consulta [questa pagina](../../platform/using/privacy-management.md) per informazioni generali sulla gestione della privacy e sui passaggi di implementazione in Adobe Campaign. Troverai anche best practice e una panoramica del processo utente e degli utenti tipo.
