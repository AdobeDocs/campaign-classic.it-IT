---
product: campaign
title: Configurare le aree di protezione
description: Scopri come configurare le aree di protezione
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
badge-v7-prem: label="on-premise e ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 67dda58f-97d1-4df5-9648-5f8a1453b814
source-git-commit: a94c361c5bdd9d61ae9232224af910a78245a889
workflow-type: tm+mt
source-wordcount: '1458'
ht-degree: 1%

---

# Definire le aree di sicurezza (on-premise){#defining-security-zones}



Ogni operatore deve essere collegato a una zona per accedere a un&#39;istanza e l&#39;IP dell&#39;operatore deve essere incluso negli indirizzi o nei set di indirizzi definiti nell&#39;area di sicurezza. La configurazione dell’area di sicurezza viene eseguita nel file di configurazione del server Adobe Campaign.

Gli operatori sono collegati a un’area di sicurezza dal suo profilo nella console, accessibile nella **[!UICONTROL Administration > Access management > Operators]** nodo. [Ulteriori informazioni](#linking-a-security-zone-to-an-operator).

>[!NOTE]
>
>Questa procedura è limitata a **on-premise** distribuzioni.
>
>As a **in hosting** cliente, se è possibile accedere [Pannello di controllo Campaign della campagna](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=it), è possibile utilizzare l&#39;interfaccia self-service dell&#39;area di protezione. [Ulteriori informazioni](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html?lang=it)
>
>Altro **ibrido/in hosting** i clienti devono contattare il team di supporto Adobe per aggiungere l’IP al inserisco nell&#39;elenco Consentiti di.
>

## Creare aree di protezione {#creating-security-zones}

Una zona è definita da:

* uno o più intervalli di indirizzi IP (IPv4 e IPv6)
* un nome tecnico associato a ciascun intervallo di indirizzi IP

Le aree di protezione sono interbloccate, il che significa che la definizione di una nuova zona all&#39;interno di un&#39;altra riduce il numero di operatori che possono accedere a tale zona, aumentando al contempo i diritti assegnati a ciascun operatore.

Le zone devono essere definite durante la configurazione del server, nel **serverConf.xml** file. Tutti i parametri disponibili in **serverConf.xml** sono elencati in [questa sezione](../../installation/using/the-server-configuration-file.md).

Ogni zona definisce i diritti, ad esempio:

* Connessione HTTP anziché HTTPS
* Visualizzazione degli errori (errori Java, JavaScript, C++, ecc.)
* Anteprima report e WebApp
* Autenticazione tramite login/password
* Modalità di connessione non sicura

>[!NOTE]
>
>**Ogni operatore deve essere collegato a una zona**. Se l’indirizzo IP dell’operatore appartiene all’intervallo definito dalla zona, l’operatore può accedere all’istanza.\
>L&#39;indirizzo IP dell&#39;operatore può essere definito in diverse zone. In questo caso, l’operatore riceve **set** dei diritti disponibili per ciascuna zona.

La soluzione preconfigurata **serverConf.xml** il file include tre aree: **pubblico, VPN e LAN**.

>[!NOTE]
>
>**La configurazione preconfigurata è sicura**. Tuttavia, prima di eseguire la migrazione da una versione precedente di Adobe Campaign, potrebbe essere necessario ridurre temporaneamente la sicurezza per migrare e approvare le nuove regole.

Esempio di come definire una zona nel **serverConf.xml** file:

```
<securityZone allowDebug="false" allowHTTP="false" label="Public Network" name="public">
<subNetwork label="All addresses" mask="*" name="all"/>

<securityZone allowDebug="true" allowHTTP="false" label="Private Network (VPN)"
              name="vpn" showErrors="true">

  <securityZone allowDebug="true" allowEmptyPassword="true" allowHTTP="true"
                allowUserPassword="false" label="Private Network (LAN)" name="lan"
                sessionTokenOnly="true" showErrors="true">
    <subNetwork label="Lan 1" mask="192.168.0.0/16" name="lan1"/>
    <subNetwork label="Lan 2" mask="172.16.0.0/12" name="lan2"/>
    <subNetwork label="Lan 3" mask="10.0.0.0/8" name="lan3"/>
    <subNetwork label="Localhost" mask="127.0.0.1/16" name="locahost"/>
    <subNetwork label="Lan (IPv6)" mask="fc00::/7" name="lan6"/>
    <subNetwork label="Localhost (IPv6)" mask="::1/128" name="localhost6"/>
  </securityZone>

</securityZone>
</securityZone>
```

Tutti i diritti che definiscono una zona sono i seguenti:

* **allowDebug**: consente di eseguire una webApp in modalità &quot;debug&quot;
* **allowEmptyPassword**: autorizza una connessione a un’istanza senza una password
* **allowHTTP**: è possibile creare una sessione senza utilizzare il protocollo HTTPS
* **allowUserPassword**: il token di sessione può avere il seguente modulo &quot;`<login>/<password>`&quot;
* **sessionTokenOnly**: il token di sicurezza non è richiesto nell’URL della connessione
* **showErrors**: gli errori sul lato server vengono inoltrati e visualizzati

>[!IMPORTANT]
>
>In una definizione di zona, ogni attributo con **true** il valore riduce la sicurezza.

Quando si utilizza il Centro messaggi, se sono presenti più istanze di esecuzione, è necessario creare un&#39;area di sicurezza aggiuntiva con **sessionTokenOnly** attributo definito come **true**, in cui devono essere aggiunti solo gli indirizzi IP necessari. Per ulteriori informazioni sulla configurazione delle istanze, consulta [questo documento](../../message-center/using/configuring-instances.md).

## Best practice per le aree di protezione {#best-practices-for-security-zones}

Nella definizione di **lan** è possibile aggiungere una maschera di indirizzo IP per definire l&#39;accesso tecnico. L’aggiunta consentirà l’accesso a tutte le istanze ospitate sul server.

```
<securityZone allowDebug="true" allowEmptyPassword="false" allowHTTP="true"
                    allowUserPassword="false" label="Private Network (LAN)" name="lan"
                    sessionTokenOnly="true" showErrors="true">
        <subNetwork label="Lan 1" mask="192.168.0.0/16" name="lan1"/>
        <subNetwork label="Lan 2" mask="172.16.0.0/12" name="lan2"/>
        <subNetwork label="Lan 3" mask="10.0.0.0/8" name="lan3"/>
        <subNetwork label="Localhost" mask="127.0.0.1/16" name="locahost"/>
        <subNetwork label="Lan (IPv6)" mask="fc00::/7" name="lan6"/>
        <subNetwork label="Localhost (IPv6)" mask="::1/128" name="localhost6"/>
  
        <!-- Customer internal IPs -->
        <subNetwork id="internalNetwork" mask="a.b.c.d/xx"/>

      </securityZone>
```

Per gli operatori che accedono solo a un’istanza specifica, è consigliabile definire gli intervalli di indirizzi IP direttamente nel file di configurazione dedicato all’istanza.

In **`config-<instance>.xml`** file:

```
  <securityZone name="public">
   ...
    <securityZone name="vpn">
      <subNetwork id="cus1" mask="a.b.c.d/xx"/>
```

## Sottoreti e proxy in un&#39;area di sicurezza {#sub-networks-and-proxies-in-a-security-zone}

Il **proxy** Il parametro può essere utilizzato in un **subNetwork** per specificare l&#39;utilizzo del proxy in un&#39;area di sicurezza.

Quando si fa riferimento a un proxy e una connessione entra tramite questo proxy (visibile tramite l’intestazione HTTP X-Forwarded-For ), la zona verificata è quella dei client del proxy e non quella del proxy.

>[!IMPORTANT]
>
>Se un proxy è configurato ed è possibile sostituirlo (o se non esiste), l’indirizzo IP che verrà testato potrà essere falsificato.
>
>Inoltre, ora vengono generati relè come proxy. È quindi possibile aggiungere l&#39;indirizzo IP 127.0.0.1 all&#39;elenco dei proxy nella configurazione dell&#39;area di sicurezza.
>
>Ad esempio: &quot; `<subnetwork label="Lan 1" mask="192.168.0.0/16" name="lan1" proxy="127.0.0.1,10.100.2.135" />`&quot;.

Possono verificarsi vari casi:

* Nell’area di sicurezza viene fatto riferimento direttamente a una sottorete e non è configurato alcun proxy: gli utenti della sottorete possono connettersi direttamente al server Adobe Campaign.

  ![](assets/8101_proxy1.png)

* È specificato un proxy per una sottorete nell&#39;area di sicurezza: gli utenti di questa sottorete possono accedere al server Adobe Campaign tramite questo proxy.

  ![](assets/8101_proxy2.png)

* Un proxy è incluso in una sottorete dell’area di sicurezza: gli utenti che hanno accesso tramite questo proxy, indipendentemente dalla loro origine, possono accedere al server Adobe Campaign.

  ![](assets/8101_proxy3.png)

Gli indirizzi IP dei proxy che probabilmente accederanno al server Adobe Campaign devono essere immessi in entrambi **`<subnetwork>`** interessata e la sottorete di primo livello **`<subnetwork name="all"/>`**. Ad esempio, qui per un proxy il cui indirizzo IP è 10.131.146.102:

```
<securityZone allowDebug="false" allowHTTP="false" label="Public Network" 
                      name="public">
    <subNetwork label="All addresses" mask="*" name="all"
                      proxy="10.131.146.102,127.0.0.1, ::1"/>

    <securityZone allowDebug="true" allowHTTP="false" label="Private Network (VPN)" 
                      name="vpn" showErrors="true">
        <securityZone allowDebug="true" allowEmptyPassword="false" allowHTTP="true" 
                      allowUserPassword="false" label="Private Network (LAN)" 
                      name="lan" sessionTokenOnly="true" showErrors="true">
            <subNetwork label="Lan proxy" mask="10.131.193.182" name="lan3" 
                      proxy="10.131.146.102,127.0.0.1, ::1"/>
            <subNetwork label="Lan 1" mask="192.168.0.0/16" name="lan1" 
                      proxy="127.0.0.1, ::1"/>

        </securityZone>
    </securityZone>
</securityZone>
```

## Collegare un’area di sicurezza a un operatore {#linking-a-security-zone-to-an-operator}

Una volta definite le zone, ogni operatore deve essere collegato a uno di essi per poter accedere a un’istanza e l’indirizzo IP dell’operatore deve essere incluso negli indirizzi o nell’intervallo di indirizzi a cui si fa riferimento nella zona.

La configurazione tecnica delle zone viene eseguita nel file di configurazione del server Campaign: **serverConf.xml**.

Prima di questo, devi iniziare configurando il **[!UICONTROL Security zone]** enumerazione per collegare un&#39;etichetta al nome interno della zona definita nella **serverConf.xml** file.

Questa configurazione viene eseguita in Esplora campagne:

1. Fai clic su **[!UICONTROL Administration > Platform > Enumerations]** nodo.
1. Seleziona la **[!UICONTROL Security zone (securityZone)]** enumerazione di sistema.

   ![](assets/enum_securityzone.png)

1. Per ogni area di protezione definita nel file di configurazione del server, fare clic sul pulsante **[!UICONTROL Add]** pulsante.
1. In **[!UICONTROL Internal name]** , immettere il nome della zona definita nel campo **serverConf.xml** file. Corrisponde al **@name** attributo del `<securityzone>`  elemento. Inserisci l’etichetta collegata al nome interno nel  **Etichetta** campo.

   ![](assets/enum_addsecurityvalue.png)

1. Fare clic su OK e salvare le modifiche.

Una volta definite le zone e **[!UICONTROL Security zone]** l&#39;enumerazione è configurata, è necessario collegare ogni operatore a un&#39;area di sicurezza:

1. Fai clic su **[!UICONTROL Administration > Access management > Operators]** nodo.
1. Selezionare l&#39;operatore a cui si desidera collegare un&#39;area di protezione e fare clic sul pulsante **[!UICONTROL Edit]** scheda.
1. Vai a **[!UICONTROL Access rights]** e fai clic sul pulsante **[!UICONTROL Edit access parameters...]** collegamento.

   ![](assets/zone_operator.png)

1. Seleziona una zona dalla sezione **[!UICONTROL Authorized connection zone]** elenco a discesa

   ![](assets/zone_operator_selection.png)

1. Clic **[!UICONTROL OK]** e salva le modifiche per applicarle.



## Raccomandazioni

* Verificare che il proxy inverso non sia consentito in subNetwork. In caso affermativo, **tutto** Il traffico verrà rilevato come proveniente da questo IP locale, quindi sarà attendibile.

* Riduci al minimo l’utilizzo di sessionTokenOnly=&quot;true&quot;:

   * Avvertenza: se questo attributo è impostato su true, l&#39;operatore può essere esposto a **Attacco di liquido cerebrospinale**.
   * Inoltre, il cookie sessionToken non è impostato con un flag httpOnly, quindi alcuni codici JavaScript lato client possono leggerlo.
   * Tuttavia, il Centro messaggi su più celle di esecuzione richiede sessionTokenOnly: crea una nuova area di sicurezza con sessionTokenOnly impostato su &quot;true&quot; e aggiungi **solo gli IP necessari** in questa zona.

* Quando possibile, imposta all allowHTTP, showErrors su false (non per localhost) e selezionali.

   * allowHTTP = &quot;false&quot;: forza gli operatori a utilizzare HTTPS
   * showErrors = &quot;false&quot;: nasconde gli errori tecnici (inclusi quelli SQL). Impedisce la visualizzazione di troppe informazioni, ma riduce la capacità dell’addetto marketing di risolvere gli errori (senza richiedere ulteriori informazioni a un amministratore)

* Imposta allowDebug su true solo per gli IP utilizzati dagli utenti/amministratori di marketing che devono creare (in realtà, visualizzare in anteprima) sondaggi, webApp e rapporti. Questo flag consente a questi IP di visualizzare le regole di inoltro e di eseguirne il debug.

   * Quando allowDebug è impostato su false, l’output è:

     ```
     <redir status='OK' date='...' sourceIP='...'/>
     ```

   * Quando allowDebug è impostato su true, l’output è:

     ```
     <redir status='OK' date='...' build='...' OR version='...' sha1='...' instance='...' sourceIP='...' host='...' localHost='...'/>
     ```

* Non impostare mai allowEmptyPassword, allowUserPassword, allowSQLInjection su true.

   * **allowEmptyPassword** consente agli operatori di disporre di una password vuota. In questo caso, avvisare tutti gli operatori affinché richiedano di impostare una password con una scadenza. Una volta passata questa scadenza, modifica questo attributo in false.

   * **allowUserPassword** consente agli operatori di inviare le credenziali come parametri, in modo che vengano registrati da apache/IIS/proxy. Questa funzione è stata utilizzata in passato per semplificare l’utilizzo delle API. Puoi verificare nel tuo manuale (o nelle specifiche) se alcune applicazioni di terze parti lo utilizzano. In tal caso, devi avvisarli di modificare il modo in cui utilizzano la nostra API e, non appena possibile, rimuovere questa funzione.

   * **allowSQLInjection** consente all&#39;utente di eseguire SQL injection utilizzando una sintassi precedente. Questo attributo deve essere impostato su false. È possibile utilizzare /nl/jsp/ping.jsp?zone=true per controllare la configurazione dell&#39;area di protezione. In questa pagina viene visualizzato lo stato attivo delle misure di protezione (calcolato con questi flag di protezione) per l&#39;IP corrente.

* Cookie/useSecurityToken HttpOnly: fare riferimento a **sessionTokenOnly** flag.

* Minimizzare gli IP aggiunti al elenco Consentiti di: nelle aree di sicurezza sono stati aggiunti i 3 intervalli predefiniti per le reti private. È improbabile che si utilizzino tutti questi indirizzi IP. Quindi tieni solo quelli di cui hai bisogno.

* Aggiorna l’operatore webApp/interno in modo che sia accessibile solo in localhost.
