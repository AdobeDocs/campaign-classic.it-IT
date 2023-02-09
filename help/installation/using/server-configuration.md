---
product: campaign
title: Configurazione della sicurezza del server
description: Ulteriori informazioni sulle best practice per la configurazione del server
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: e1aff73a-54fb-444e-b183-df11c9b3df31
source-git-commit: e55fff99fd5dec8da998310dc7026c1a506abadc
workflow-type: tm+mt
source-wordcount: '624'
ht-degree: 4%

---

# Impostazioni di sicurezza del server {#server-configuration}

![](../../assets/v7-only.svg)

## Protezione caricamento file

Controlla con gli utenti operativi che tipo di file caricano sul server utilizzando la console client di Campaign o l’interfaccia web. Come promemoria, le esigenze aziendali possono essere:

* immagini (jpg, gif, png, ...)
* contenuto (zip, html, css, ...)
* risorse di marketing (doc, xls, pdf, psd, tiff, ...)
* allegato e-mail (doc, pdf, ...)
* ETL (txt, csv, tab, ...)
* ecc.

Aggiungi tutti in serverConf/shared/datastore/@uploadAllowlist (espressione regolare java valida). Per ulteriori informazioni, consulta [questa pagina](../../installation/using/file-res-management.md).

Adobe Campaign non limita la dimensione del file. Ma è possibile farlo configurando IIS/Apache. Per ulteriori informazioni, consulta [questa sezione](../../installation/using/web-server-configuration.md).

## Relè

Fai riferimento a [questa pagina](../../installation/using/configuring-campaign-server.md#dynamic-page-security-and-relays) per ulteriori informazioni.

Per impostazione predefinita, tutte le pagine dinamiche vengono automaticamente inviate al server Tomcat locale del computer di cui viene avviato il modulo Web. Puoi scegliere di non inoltrarne alcuni. Se non utilizzi alcuni moduli di Adobe Campaign (come webapp, interazione, alcuni jsp) puoi rimuoverli dalle regole di relay.

Con questa funzione abbiamo forzato la capacità di visualizzare le risorse degli utenti finali utilizzando http (httpAllowed=&quot;true&quot;). Poiché queste pagine possono visualizzare alcuni PII (come contenuto e-mail, indirizzo), buono riscattare, offerta, è necessario forzare di nuovo HTTPS su questi percorsi.

Se utilizzi nomi host diversi (uno pubblico e uno per gli operatori), puoi anche impedire la trasmissione di alcune risorse necessarie agli operatori sul nome DNS pubblico.

## Protezione delle connessioni in uscita

L’elenco predefinito di URL che possono essere richiamati tramite codici JavaScript (flussi di lavoro, ecc.) è limitato. Per consentire l’utilizzo di un nuovo URL, l’amministratore deve fare riferimento a tale URL nel [file serverConf.xml](../../installation/using/the-server-configuration-file.md).

Esistono tre modalità di protezione della connessione:

* **Blocco** : tutti gli URL che non appartengono all&#39;inserire nell&#39;elenco Consentiti vengono bloccati, con un messaggio di errore. Questa è la modalità predefinita dopo un aggiornamento successivo.
* **Permissivo** : tutti gli URL che non appartengono all’inserire nell&#39;elenco Consentiti sono consentiti.
* **Avviso** : tutti gli URL non nell’inserire nell&#39;elenco Consentiti sono consentiti, ma l’interprete JS invia un avviso in modo che l’amministratore possa raccoglierli. Questa modalità aggiunge messaggi di avviso JST-310027.

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

I nuovi client utilizzeranno la modalità di blocco. Se desiderano consentire un nuovo URL, devono contattare il proprio amministratore per aggiungerlo all’inserire nell&#39;elenco Consentiti.

I clienti esistenti provenienti da una migrazione possono utilizzare la modalità di avviso per un po’ di tempo. Nel frattempo devono analizzare il traffico in uscita prima di autorizzare gli URL.

## Restrizione dei comandi (lato server)

Diversi comandi sono inclusi nel  elenco Bloccati e non possono essere eseguiti utilizzando la funzione execCommand. Un utente Unix dedicato fornisce una protezione aggiuntiva per eseguire comandi esterni. Per le installazioni in hosting, questa restrizione viene applicata automaticamente. Per le installazioni on-premise, puoi impostare manualmente questa restrizione seguendo le istruzioni di [questa pagina](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands). Inoltre, **[!UICONTROL Script]** e **[!UICONTROL External task]** le attività del flusso di lavoro non sono disponibili (istanze appena installate).

## Altre configurazioni

Puoi aggiungere intestazioni HTTP aggiuntive per tutte le pagine (per ulteriori informazioni, consulta [questa pagina](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands)):

* Puoi aggiungere alcune intestazioni aggiuntive come HSTS, X-FRAME-OPTIONS, CSP...
* È necessario testarli in un ambiente di test prima di applicarli in produzione.

   >[!IMPORTANT]
   >
   >È possibile interrompere Adobe Campaign aggiungendo alcune intestazioni.

Adobe Campaign consente di impostare una password semplice nel `<dbcnx .../>` elemento. Non utilizzare questa funzione.

Per impostazione predefinita, Adobe Campaign non blocca una sessione a un IP specifico, ma la puoi attivare per evitare che la sessione venga rubata. Per farlo, nella [file serverConf.xml](../../installation/using/the-server-configuration-file.md), imposta l&#39;attributo checkIPConsistent su **true** in `<authentication>` nodo.

Per impostazione predefinita, l’MTA di Adobe Campaign non utilizza una connessione protetta per inviare il contenuto al server SMTP. Devi abilitare questa funzione (può ridurre la velocità di consegna). Per eseguire questa operazione, imposta **enableTLS** a **true** in `<smtp ...>` nodo.

Puoi ridurre la durata di una sessione nel nodo di autenticazione (attributo sessionTimeOutSec ).
