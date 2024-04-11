---
product: campaign
title: Configurazione della sicurezza del server
description: Ulteriori informazioni sulle best practice per la configurazione dei server
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: e1aff73a-54fb-444e-b183-df11c9b3df31
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 4%

---

# Impostazioni di sicurezza del server {#server-configuration}

## Protezione caricamento file

Verifica con gli utenti operativi il tipo di file che caricano sul server utilizzando la console client di Campaign o l’interfaccia web. È opportuno ricordare che le esigenze aziendali possono essere:

* immagini (jpg, gif, png, ...)
* contenuto (zip, html, css, ...)
* risorse di marketing (doc, xls, pdf, psd, tiff, ...)
* allegato e-mail (documento, pdf, ...)
* ETL (TXT, CSV, TAB, ...)
* ecc.

Aggiungi tutti in serverConf/shared/datastore/@uploadAllowlist (espressione regolare Java valida). Per ulteriori informazioni, consulta [questa pagina](../../installation/using/file-res-management.md).

Adobe Campaign non limita la dimensione del file. Tuttavia, è possibile farlo configurando IIS/Apache. Per ulteriori informazioni, consulta [questa sezione](../../installation/using/web-server-configuration.md).

## Inoltro

Fare riferimento a [questa pagina](../../installation/using/configuring-campaign-server.md#dynamic-page-security-and-relays) per ulteriori informazioni.

Per impostazione predefinita, tutte le pagine dinamiche vengono inoltrate automaticamente al server Tomcat locale del computer in cui viene avviato il modulo Web. Puoi scegliere di non inoltrarne alcuni. Se non utilizzi alcuni moduli di Adobe Campaign (come webapp, interazione e alcune JSP) puoi rimuoverli dalle regole di inoltro.

Per impostazione predefinita, è stata forzata la possibilità di visualizzare le risorse dell’utente finale utilizzando http (httpAllowed=&quot;true&quot;). Poiché queste pagine possono visualizzare alcuni dati PII (come contenuto e-mail, indirizzo), riscattare il coupon e offrire, è necessario forzare nuovamente HTTPS su questi percorsi.

Se utilizzi nomi host diversi (uno pubblico e uno per gli operatori), puoi anche impedire l’inoltro di alcune risorse necessarie agli operatori sul nome DNS pubblico.

## Protezione delle connessioni in uscita

L’elenco predefinito di URL che possono essere richiamati tramite codici JavaScript (flussi di lavoro, ecc.) è limitato. Per consentire un nuovo URL, l’amministratore deve farvi riferimento nella sezione [file serverConf.xml](../../installation/using/the-server-configuration-file.md).

Sono disponibili tre modalità di protezione della connessione:

* **Blocco** : tutti gli URL che non appartengono al inserisco nell&#39;elenco Consentiti di vengono bloccati e viene visualizzato un messaggio di errore. Questa è la modalità predefinita dopo un post-aggiornamento.
* **Permissivo** : sono consentiti tutti gli URL che non appartengono al inserisco nell&#39;elenco Consentiti di.
* **Avvertenza** : sono consentiti tutti gli URL che non si trovano nel inserisco nell&#39;elenco Consentiti di, ma l’interprete JS genera un avviso che consente all’amministratore di raccoglierli. Questa modalità aggiunge messaggi di avviso JST-310027.

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

I nuovi client utilizzeranno la modalità di blocco. Se desidera consentire un nuovo URL, deve contattare il proprio amministratore per aggiungerlo al inserisco nell&#39;elenco Consentiti di.

I clienti esistenti provenienti da una migrazione possono utilizzare la modalità di avviso per un certo periodo di tempo. Nel frattempo devono analizzare il traffico in uscita prima di autorizzare gli URL.

## Restrizione dei comandi (lato server)

Nel inserisco nell&#39;elenco Bloccati di esecuzione del comando sono inclusi diversi comandi che non possono essere eseguiti utilizzando la funzione execCommand. Un utente Unix dedicato fornisce una protezione aggiuntiva per l’esecuzione di comandi esterni. Per le installazioni in hosting, questa restrizione viene applicata automaticamente. Per le installazioni on-premise, puoi impostare manualmente questa restrizione seguendo le istruzioni da [questa pagina](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands). Inoltre, **[!UICONTROL Script]** e **[!UICONTROL External task]** le attività del flusso di lavoro non sono disponibili (istanze appena installate).

## Altre configurazioni

Puoi aggiungere altre intestazioni HTTP per tutte le pagine (per ulteriori informazioni, consulta [questa pagina](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands)):

* Puoi aggiungere altre intestazioni come HSTS, X-FRAME-OPTIONS, CSP...
* È necessario testarli in un ambiente di test prima di applicarli in produzione.

  >[!IMPORTANT]
  >
  >Adobe Campaign può essere interrotto aggiungendo determinate intestazioni.

Adobe Campaign consente di impostare una password semplice nel `<dbcnx .../>` elemento. Non utilizzare questa funzione.

Per impostazione predefinita, Adobe Campaign non fissa una sessione a un IP specifico, ma puoi attivarla per impedire che la sessione venga rubata. Per eseguire questa operazione, in [file serverConf.xml](../../installation/using/the-server-configuration-file.md), impostare l&#39;attributo checkIPConsistent su **true** nel `<authentication>` nodo.

Per impostazione predefinita, l’MTA di Adobe Campaign non utilizza una connessione protetta per inviare contenuti al server SMTP. Devi abilitare questa funzione (potrebbe ridurre la velocità di consegna). Per eseguire questa operazione, impostare **enableTLS** a **true** nel `<smtp ...>` nodo.

È possibile ridurre la durata di una sessione nel nodo di autenticazione (attributo sessionTimeOutSec).
