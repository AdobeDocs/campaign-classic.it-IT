---
product: campaign
title: Personalizzazione e privacy
description: Scopri le best practice sulla sicurezza per la privacy e la personalizzazione
feature: Installation, Privacy, Privacy Tools, URL Personalization
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
exl-id: 0a3473bf-0528-486d-a799-8db86fece522
source-git-commit: a2106e55617209f28da42c50008d16188563b2da
workflow-type: tm+mt
source-wordcount: '812'
ht-degree: 3%

---

# Personalizzazione e privacy {#privacy}

## Personalizzazione URL {#url-personalization}

Quando aggiungi collegamenti personalizzati al contenuto, evita sempre di includere alcuna personalizzazione nella parte nome host dell’URL per evitare potenziali lacune di sicurezza. Gli esempi seguenti non devono mai essere utilizzati in tutti gli attributi URL &lt;`a href="">` o `<img src="">`:

* `<%= url >`
* `https://<%= url >`
* `https://<%= domain >/path`
* `https://<%= sub-domain >.domain.tld/path`
* `https://sub.domain<%= main domain %>/path`

### Consiglio

Per convalidare la tabella URL di tracciamento e assicurarti di non utilizzarla, esegui una query tramite [Editor query generico di Campaign](../../platform/using/steps-to-create-a-query.md) oppure crea un flusso di lavoro con i criteri del filtro in [attività query](../../workflow/using/query.md).

Esempio:

1. Creare un flusso di lavoro e aggiungere una **Query** attività. [Ulteriori informazioni](../../workflow/using/query.md).

1. Apri **Query** e crea un filtro per `nmsTrackingUrl` tabella come segue:

   `source URL starts with http://<% or source URL starts with https://<%`

1. Esegui il flusso di lavoro e verifica se sono presenti risultati.

1. In tal caso, apri la transizione di output per visualizzare l’elenco degli URL.

   ![](assets/privacy-query-dynamic-url.png)


### Firma URL

Per migliorare la sicurezza, è stato introdotto un meccanismo di firma per il tracciamento dei collegamenti nelle e-mail. È disponibile a partire dalle build 19.1.4 (9032@3a9dc9c) e 20.2. Questa funzione è attivata per impostazione predefinita.

>[!NOTE]
>
>Quando si fa clic su un URL firmato non valido, viene restituito questo errore: `Requested URL '…' was not found.`

Inoltre, puoi utilizzare un miglioramento per disabilitare gli URL generati nelle build precedenti. Questa funzione è disabilitata per impostazione predefinita. Puoi contattare [Assistenza clienti](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) per attivare questa funzione.

Se esegui la build 19.1.4, potrebbero verificarsi problemi con le consegne di notifiche push tramite collegamenti di tracciamento o le consegne con tag di ancoraggio. In tal caso, si consiglia di disabilitare la firma URL.

In qualità di cliente ibrido, con hosting campagna o Cloud Service gestiti, devi contattare [Assistenza clienti](https://helpx.adobe.com/it/enterprise/using/support-for-experience-cloud.html) per disabilitare la firma URL.

Se esegui Campaign in un’architettura ibrida, prima di abilitare la firma URL, assicurati che l’istanza mid-sourcing ospitata sia stata aggiornata come segue:

* Prima l’istanza di marketing on-premise
* Quindi effettua l’aggiornamento alla stessa versione dell’istanza di marketing on-premise o a una versione leggermente superiore

In caso contrario, potrebbero verificarsi alcuni dei seguenti problemi:

* Prima che l’istanza di mid-sourcing venga aggiornata, gli URL vengono inviati senza firma tramite questa istanza.
* Dopo l’aggiornamento dell’istanza di mid-sourcing e l’abilitazione della firma URL in entrambe le istanze, gli URL inviati in precedenza senza firma vengono rifiutati. Il motivo è che una firma viene richiesta dai file di tracciamento forniti dall’istanza di marketing.

Per disabilitare gli URL generati nelle build precedenti, effettua le seguenti operazioni su tutti i server Campaign contemporaneamente:

1. Nel file di configurazione del server (`serverConf.xml`), modifica il **blockRedirectForUnsignedTrackingLink** opzione per **true**.
1. Riavvia il `nlserver` servizio.
1. Il giorno `tracking` server, riavviare il `web` server (apache2 su Debian, httpd su CentOS/RedHat, IIS su Windows).

Per abilitare la firma URL, effettua le seguenti operazioni su tutti i server Campaign contemporaneamente:

1. Nel file di configurazione del server (`serverConf.xml`), modifica **signEmailLinks** opzione, per **true**.
1. Riavvia il **nlserver** servizio.
1. Il giorno `tracking` server, riavviare il `web` server (apache2 su Debian, httpd su CentOS/RedHat, IIS su Windows).

## Limitazione dei dati

È necessario assicurarsi che le password crittografate non siano accessibili da un utente autenticato con privilegi limitati. A questo scopo, limita l’accesso solo ai campi della password o all’intera entità (è necessaria una build >= 8770).

Questa restrizione ti consente di rimuovere i campi delle password, ma di consentire all’account esterno di essere accessibile dall’interfaccia per tutti gli utenti. [Ulteriori informazioni](../../configuration/using/restricting-pii-view.md).

A tale scopo, segui i passaggi indicati di seguito:

1. Accedi a **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data schemas]** cartella di Campaign explorer.

1. Creare uno schema di dati, come **[!UICONTROL Extension of a schema]**.

   ![](assets/privacy-data-restriction.png)

1. Scegli **[!UICONTROL External Account]** (extAccount).

1. Nell’ultima schermata della procedura guidata, modifica il nuovo &quot;srcSchema&quot; per limitare l’accesso a tutti i campi della password:

   È possibile sostituire l&#39;elemento principale (`<element name="extAccount" ... >`) da:

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

## Pagine Protect con PI

Consigliamo vivamente ai clienti on-premise di proteggere le pagine che potrebbero contenere informazioni personali (PI) come pagine mirror, applicazioni web, ecc.

L’obiettivo di questa procedura è quello di evitare che queste pagine vengano indicizzate, evitando in tal modo un potenziale rischio per la sicurezza. Di seguito sono riportati alcuni articoli utili:

* [https://developers.google.com/search/reference/robots_txt](https://developers.google.com/search/reference/robots_txt)
* [https://developers.google.com/search/reference/robots_meta_tag](https://developers.google.com/search/reference/robots_meta_tag)

Per proteggere le pagine, effettua le seguenti operazioni:

1. Aggiungi un `robots.txt` nella directory principale del server web (Apache o IIS). Di seguito è riportato il contenuto del file:

   ```sql
   # Make changes for all web spiders
   User-agent:
   *Disallow: /
   ```

   Per IIS, consulta [questa pagina](https://docs.microsoft.com/en-us/iis/extensions/iis-search-engine-optimization-toolkit/managing-robotstxt-and-sitemap-files).

   Per Apache, puoi inserire il file in **/var/www/robots.txt** (Debian)

1. A volte l’aggiunta di un **robots.txt** non è sufficiente in termini di sicurezza. Ad esempio, se un altro sito Web contiene un collegamento alla pagina, potrebbe essere visualizzato in un risultato di ricerca.

   Oltre al **robots.txt** , è consigliabile aggiungere un **X-Robots-Tag** intestazione. Puoi eseguire questa operazione in Apache o IIS e nella **serverConf.xml** file di configurazione.

   Per ulteriori informazioni, consulta [questo articolo](https://developers.google.com/search/reference/robots_meta_tag).


## Richieste di privacy

Fai riferimento a [questa pagina](../../platform/using/privacy-management.md) per informazioni generali sulla gestione della privacy e sui passaggi di implementazione in Adobe Campaign. Troverai anche best practice e una panoramica del processo utente e degli utenti tipo.
