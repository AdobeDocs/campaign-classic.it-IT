---
solution: Campaign Classic
product: campaign
title: Configurazione del server
description: Ulteriori informazioni sulle best practice per la configurazione del server.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: 564eaedb09282c85593f638617baded0a63494a0
workflow-type: tm+mt
source-wordcount: '1206'
ht-degree: 2%

---


# Configurazione del server {#server-configuration}

## Configurazione delle aree di protezione

A partire dalla build 8977, l&#39;interfaccia utente autonoma delle aree di protezione non è più disponibile. Se non sei in hosting su AWS, rivolgiti al team di supporto Adobe per aggiungere IP all’elenco consentiti. In caso contrario, l&#39;aggiunta di IP all&#39;elenco consentiti deve essere eseguita in [Pannello di controllo Campaign](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html).

Per verificare se l&#39;istanza è ospitata su AWS, segui i passaggi descritti in [questa pagina](https://experienceleague.adobe.com/docs/control-panel/using/faq.html).

>[!NOTE]
> 
>Il Pannello di controllo Campaign è accessibile a tutti gli utenti amministratori. I passaggi per concedere all’amministratore l’accesso a un utente sono descritti in [questa sezione](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=en#discover-control-panel).
>
>Tieni presente che l’istanza deve essere ospitata su AWS e aggiornata con la build [Gold Standard](../../rn/using/gs-overview.md) più recente o con la build [GA più recente (21.1)](../../rn/using/latest-release.md). Scopri come controllare la versione in [questa sezione](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).


* Assicurati che il proxy inverso non sia consentito in subNetwork. In tal caso, il traffico **all** verrà rilevato come proveniente da questo IP locale, pertanto sarà attendibile.

* Riduci al minimo l&#39;utilizzo di sessionTokenOnly=&quot;true&quot;:

   * Avviso: Se questo attributo è impostato su true, l&#39;operatore può essere esposto a un **attacco CRSF**.
   * Inoltre, il cookie sessionToken non è impostato con un flag httpOnly, quindi alcuni codici javascript lato client possono leggerlo.
   * Tuttavia, il Centro messaggi su più celle di esecuzione richiede sessionTokenOnly: crea una nuova zona di sicurezza con sessionTokenOnly impostato su &quot;true&quot; e aggiungi **solo gli IP necessari** in questa zona.

* Quando possibile, imposta tutti allowHTTP, showErrors su false (non per localhost) e controllali.

   * allowHTTP = &quot;false&quot;: forza l’utilizzo di HTTPS da parte degli operatori
   * showErrors = &quot;false&quot;: nasconde gli errori tecnici (inclusi quelli SQL). Impedisce la visualizzazione di troppe informazioni, ma riduce la capacità dell’addetto al marketing di risolvere gli errori (senza chiedere ulteriori informazioni a un amministratore)

* Imposta allowDebug su true solo sugli IP utilizzati dagli utenti/amministratori di marketing che devono creare (in realtà anteprima) sondaggi, webApps e rapporti. Questo flag consente a questi IP di visualizzare le regole di relay e di eseguirne il debug.

* Non impostare mai allowEmptyPassword, allowUserPassword, allowSQLInjection su true. Questi attributi sono qui solo per consentire una migrazione fluida dalle versioni v5 e v6.0:

   * **** Gli operatori allowEmptyPasswordlets hanno una password vuota. In questo caso, avvisa tutti gli operatori di chiedere loro di impostare una password con una scadenza. Una volta trascorsa la scadenza, cambia questo attributo in false.

   * **** gli operatori allowUserPasswordlets inviano le loro credenziali come parametri (in modo che vengano registrate da apache/IIS/proxy). Questa funzione è stata utilizzata in passato per semplificare l’utilizzo delle API. È possibile verificare se alcune applicazioni di terze parti lo utilizzano o meno nella propria cartella di cottura (o nelle specifiche). In tal caso, devi inviare loro una notifica per modificare il modo in cui utilizzano la nostra API e rimuovere al più presto questa funzione.

   * **** allowSQLInjectionconsente all&#39;utente di eseguire iniezioni SQL utilizzando una vecchia sintassi. Non appena possibile eseguire le correzioni descritte in [questa pagina](../../migration/using/general-configurations.md) per essere in grado di impostare questo attributo su false. Puoi utilizzare /nl/jsp/ping.jsp?zone=true per controllare la configurazione dell&#39;area di sicurezza. In questa pagina viene visualizzato lo stato attivo delle misure di sicurezza (calcolate con questi flag di sicurezza) per l&#39;IP corrente.

* Cookie HttpOnly/useSecurityToken: fai riferimento al flag **sessionTokenOnly** .

* Minimizza gli IP aggiunti all’elenco consentiti: In aree di sicurezza abbiamo aggiunto i 3 intervalli per le reti private. È improbabile che utilizzerai tutti questi indirizzi IP. Quindi tieni solo quelli di cui hai bisogno.

* Aggiorna l&#39;operatore webApp/interno per essere accessibile solo in localhost.

## Protezione caricamento file

Controlla con gli utenti operativi che tipo di file caricano sul server utilizzando l&#39;interfaccia nlclient/web. Come promemoria, le esigenze aziendali possono essere:

* immagini (jpg, gif, png, ...)
* contenuto (zip, html, css, ...)
* risorse di marketing (doc, xls, pdf, psd, tiff, ...)
* allegato e-mail (doc, pdf, ...)
* ETL (txt, csv, tab, ...)
* ecc.

Aggiungi tutti in serverConf/shared/datastore/@uploadAllowlist (espressione regolare java valida). Ulteriori informazioni in [questa pagina](../../installation/using/configuring-campaign-server.md#limiting-uploadable-files).

Adobe Campaign non limita la dimensione del file. Ma è possibile farlo configurando IIS/Apache. Ulteriori informazioni in [questa sezione](../../installation/using/web-server-configuration.md).

## Relè

Fare riferimento a [questa pagina](../../installation/using/configuring-campaign-server.md#dynamic-page-security-and-relays) per ulteriori informazioni.

Per impostazione predefinita, tutte le pagine dinamiche vengono automaticamente inviate al server Tomcat locale del computer di cui viene avviato il modulo Web. Puoi scegliere di non inoltrarne alcuni. Se non utilizzi alcuni moduli di Adobe Campaign (come webapp, interazione, alcuni jsp) puoi rimuoverli dalle regole di relay.

Con questa funzione abbiamo forzato la capacità di visualizzare le risorse degli utenti finali utilizzando http (httpAllowed=&quot;true&quot;). Poiché queste pagine possono visualizzare alcuni PII (come contenuto e-mail, indirizzo), buono riscattare, offerta, è necessario forzare di nuovo HTTPS su questi percorsi.

Se utilizzi nomi host diversi (uno pubblico e uno per gli operatori), puoi anche impedire la trasmissione di alcune risorse necessarie agli operatori sul nome DNS pubblico.

## Protezione delle connessioni in uscita

L’elenco predefinito di URL che possono essere richiamati tramite codici JavaScript (flussi di lavoro, ecc.) è limitato. Per consentire un nuovo URL, l&#39;amministratore deve farvi riferimento nel file [serverConf.xml](../../installation/using/the-server-configuration-file.md).

Esistono tre modalità di protezione della connessione:

* **Blocco** : tutti gli URL che non appartengono all’elenco consentiti vengono bloccati e viene visualizzato un messaggio di errore. Questa è la modalità predefinita dopo un aggiornamento successivo.
* **Permissivo** : tutti gli URL che non appartengono all’elenco consentiti sono consentiti.
* **Avviso** : tutti gli URL non nell’elenco consentiti sono consentiti, ma l’interprete JS invia un avviso in modo che l’amministratore possa raccoglierli. Questa modalità aggiunge messaggi di avviso JST-310027.

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

I nuovi client utilizzeranno la modalità di blocco. Se desiderano consentire un nuovo URL, devono contattare il proprio amministratore per aggiungerlo all’elenco consentiti.

I clienti esistenti provenienti da una migrazione possono utilizzare la modalità di avviso per un po’ di tempo. Nel frattempo devono analizzare il traffico in uscita prima di autorizzare gli URL.

## Restrizione dei comandi (lato server)

Diversi comandi vengono inseriti in blacklist e non possono essere eseguiti utilizzando la funzione execCommand. Un utente Unix dedicato fornisce una protezione aggiuntiva per eseguire comandi esterni. Per le installazioni in hosting, questa restrizione viene applicata automaticamente. Per le installazioni on-premise, puoi impostare manualmente questa restrizione seguendo le istruzioni riportate in [questa pagina](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands). Inoltre, le attività del flusso di lavoro **[!UICONTROL Script]** e **[!UICONTROL External task]** non sono disponibili (istanze appena installate).

## Altre configurazioni

Puoi aggiungere intestazioni HTTP aggiuntive per tutte le pagine (per ulteriori informazioni, consulta [questa pagina](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands)):

* Puoi aggiungere alcune intestazioni aggiuntive come HSTS, X-FRAME-OPTIONS, CSP...
* È necessario testarli in un ambiente di test prima di applicarli in produzione.

   >[!IMPORTANT]
   >
   >È possibile interrompere Adobe Campaign aggiungendo alcune intestazioni.

Adobe Campaign consente di impostare una password semplice nell’elemento `<dbcnx .../>` . Non utilizzare questa funzione.

Per impostazione predefinita, Adobe Campaign non blocca una sessione a un IP specifico, ma la puoi attivare per evitare che la sessione venga rubata. Per farlo, nel file [serverConf.xml](../../installation/using/the-server-configuration-file.md), imposta l&#39;attributo checkIPConsistent su **true** nel nodo `<authentication>`.

Per impostazione predefinita, l’MTA di Adobe Campaign non utilizza una connessione protetta per inviare il contenuto al server SMTP. Devi abilitare questa funzione (può ridurre la velocità di consegna). A questo scopo, imposta **enableTLS** su **true** nel nodo `<smtp ...>`.

Puoi ridurre la durata di una sessione nel nodo di autenticazione (attributo sessionTimeOutSec ).
