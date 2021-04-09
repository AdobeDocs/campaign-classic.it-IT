---
solution: Campaign Classic
product: campaign
title: Configurazione della sicurezza del server
description: Ulteriori informazioni sulle best practice per la configurazione del server
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: e1aff73a-54fb-444e-b183-df11c9b3df31
translation-type: tm+mt
source-git-commit: b0a1e0596e985998f1a1d02236f9359d0482624f
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 3%

---

# Impostazioni di sicurezza del server {#server-configuration}

## Protezione caricamento file

Controlla con gli utenti operativi che tipo di file caricano sul server utilizzando la console client di Campaign o l’interfaccia web. Come promemoria, le esigenze aziendali possono essere:

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
