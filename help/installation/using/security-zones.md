---
solution: Campaign Classic
product: campaign
title: Configurare le aree di protezione
description: Scopri come configurare le aree di protezione
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 67dda58f-97d1-4df5-9648-5f8a1453b814
translation-type: tm+mt
source-git-commit: 830ec0ed80fdc6e27a8cc782b0e4b79abf033450
workflow-type: tm+mt
source-wordcount: '1013'
ht-degree: 0%

---


# Definire le aree di sicurezza {#defining-security-zones}

Ogni operatore deve essere collegato a una zona per accedere a un’istanza e l’IP dell’operatore deve essere incluso negli indirizzi o nei set di indirizzi definiti nella zona di sicurezza. La configurazione dell’area di sicurezza viene eseguita nel file di configurazione del server Adobe Campaign.

Gli operatori sono collegati a una zona di sicurezza dal relativo profilo nella console, accessibile nel nodo **[!UICONTROL Administration > Access management > Operators]** . [Ulteriori informazioni](#linking-a-security-zone-to-an-operator).

>[!NOTE]
>
>Questa procedura è limitata alle distribuzioni **on-premise**.
>
>In qualità di cliente **in hosting**, se puoi accedere a [Pannello di controllo Campaign di campagne](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html), puoi utilizzare l’interfaccia self-service della zona di sicurezza. [Ulteriori informazioni](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html)
>
>Altri clienti **ibridi/in hosting** devono contattare Adobe per configurare le aree di protezione per la loro istanza.


## Creare aree di protezione {#creating-security-zones}

Una zona è definita da:

* uno o più intervalli di indirizzi IP (IPv4 e IPv6)
* un nome tecnico collegato a ciascun intervallo di indirizzi IP

Le aree di sicurezza sono interbloccate, il che significa che la definizione di una nuova zona all’interno di un’altra zona riduce il numero di operatori che possono accedervi aumentando al contempo i diritti assegnati a ciascun operatore.

Le aree devono essere definite durante la configurazione del server, nel file **serverConf.xml**. Tutti i parametri disponibili in **serverConf.xml** sono elencati in [questa sezione](../../installation/using/the-server-configuration-file.md).

Ogni zona definisce i diritti, ad esempio:

* Connessione HTTP anziché HTTPS
* Visualizzazione degli errori (errori Java, JavaScript, C++, ecc.)
* Report e anteprima webApp
* Autenticazione tramite login/password
* Modalità di connessione non sicura

>[!NOTE]
>
>**Ogni operatore deve essere collegato a una zona**. Se l’indirizzo IP dell’operatore appartiene all’intervallo definito dalla zona, l’operatore può accedere all’istanza.\
>L&#39;indirizzo IP dell&#39;operatore può essere definito in più zone. In questo caso, l’operatore riceve il **set** dei diritti disponibili per ogni zona.

Il file preconfigurato **serverConf.xml** include tre aree: **pubblico, VPN e LAN**.

>[!NOTE]
>
>**La configurazione standard è sicura**. Tuttavia, prima di eseguire la migrazione da una versione precedente di Adobe Campaign, potrebbe essere necessario ridurre temporaneamente la sicurezza per migrare e approvare le nuove regole.

Esempio di come definire una zona nel file **serverConf.xml** :

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

* **allowDebug**: consente l&#39;esecuzione di un&#39;app web in modalità &quot;debug&quot;
* **allowEmptyPassword**: autorizza una connessione a un&#39;istanza senza password
* **allowHTTP**: è possibile creare una sessione senza utilizzare il protocollo HTTPS
* **allowUserPassword**: il token di sessione può avere il seguente modulo &quot;`<login>/<password>`&quot;
* **sessionTokenOnly**: il token di sicurezza non è richiesto nell’URL di connessione
* **showErrors**: gli errori sul lato server vengono inoltrati e visualizzati

>[!IMPORTANT]
>
>In una definizione di zona, ogni attributo con il valore **true** riduce la sicurezza.

Quando utilizzi Message Center (Centro messaggi), se sono presenti più istanze di esecuzione, devi creare una zona di sicurezza aggiuntiva con l’attributo **sessionTokenOnly** definito come **true**, in cui devono essere aggiunti solo gli indirizzi IP necessari. Per ulteriori informazioni sulla configurazione delle istanze, consulta [questo documento](../../message-center/using/creating-a-shared-connection.md).

## Best practice per le aree di protezione {#best-practices-for-security-zones}

Nella definizione della zona di sicurezza **lan** è possibile aggiungere una maschera per l&#39;indirizzo IP che definisca l&#39;accesso tecnico. Questa aggiunta abiliterà l’accesso a tutte le istanze ospitate sul server.

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

È consigliabile definire intervalli di indirizzi IP direttamente nel file di configurazione dedicato all’istanza per gli operatori che accedono solo a un’istanza specifica.

Nel file **`config-<instance>.xml`**:

```
  <securityZone name="public">
   ...
    <securityZone name="vpn">
      <subNetwork id="cus1" mask="a.b.c.d/xx"/>
```

## Reti secondarie e proxy in una zona di sicurezza {#sub-networks-and-proxies-in-a-security-zone}

Il parametro **proxy** può essere utilizzato in un elemento **subNetwork** per specificare l&#39;utilizzo proxy in una zona di sicurezza.

Quando si fa riferimento a un proxy e si accede a una connessione tramite questo proxy (visibile tramite l&#39;intestazione HTTP X-Forwarded-For), la zona verificata è quella dei client del proxy e non quella del proxy.

>[!IMPORTANT]
>
>Se un proxy è configurato e è possibile ignorarlo (o se non esiste), l&#39;indirizzo IP che verrà testato sarà in grado di essere falsificato.
>
>Inoltre, i relè ora vengono generati come proxy. Puoi quindi aggiungere l’indirizzo IP 127.0.0.1 all’elenco dei proxy nella configurazione della tua zona di sicurezza.
>
>Ad esempio: &quot; `<subnetwork label="Lan 1" mask="192.168.0.0/16" name="lan1" proxy="127.0.0.1,10.100.2.135" />`&quot;.

Possono verificarsi diversi casi:

* Nella zona di sicurezza viene fatto riferimento direttamente a una sottorete e non è configurato alcun proxy: gli utenti della rete secondaria possono connettersi direttamente al server Adobe Campaign.

   ![](assets/8101_proxy1.png)

* È stato specificato un proxy per una rete secondaria nella zona di sicurezza: gli utenti di questa rete secondaria possono accedere al server Adobe Campaign tramite questo proxy.

   ![](assets/8101_proxy2.png)

* Un proxy è incluso in una sottorete della zona di sicurezza: gli utenti che hanno accesso tramite questo proxy, indipendentemente dalla loro origine, possono accedere al server Adobe Campaign.

   ![](assets/8101_proxy3.png)

Gli indirizzi IP dei proxy che possono accedere al server Adobe Campaign devono essere immessi sia nella **`<subnetwork>`** interessata che nella sottorete di primo livello **`<subnetwork name="all"/>`**. Ad esempio, qui per un proxy il cui indirizzo IP è 10.131.146.102:

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

Una volta definite le zone, ogni operatore deve essere collegato a uno di essi per poter accedere a un&#39;istanza e l&#39;indirizzo IP dell&#39;operatore deve essere incluso negli indirizzi o nell&#39;intervallo di indirizzi a cui si fa riferimento nella zona.

La configurazione tecnica delle aree viene eseguita nel file di configurazione di Campaign Server: **serverConf.xml**.

Prima di questo, è necessario iniziare configurando l&#39;enumerazione preconfigurata **[!UICONTROL Security zone]** per collegare un&#39;etichetta al nome interno della zona definita nel file **serverConf.xml** .

Questa configurazione viene eseguita in Campaign Explorer:

1. Fai clic sul nodo **[!UICONTROL Administration > Platform > Enumerations]** .
1. Selezionare l&#39;enumerazione di sistema **[!UICONTROL Security zone (securityZone)]**.

   ![](assets/enum_securityzone.png)

1. Per ogni zona di sicurezza definita nel file di configurazione del server, fai clic sul pulsante **[!UICONTROL Add]** .
1. Nel campo **[!UICONTROL Internal name]** , immetti il nome della zona definita nel file **serverConf.xml** . Corrisponde all&#39;attributo **@name** dell&#39;elemento `<securityzone>`. Immetti l’etichetta collegata al nome interno nel campo **Etichetta**.

   ![](assets/enum_addsecurityvalue.png)

1. Fai clic su OK e salva le modifiche.

Una volta definite le zone e configurata l&#39;enumerazione **[!UICONTROL Security zone]** , è necessario collegare ogni operatore a una zona di sicurezza:

1. Fai clic sul nodo **[!UICONTROL Administration > Access management > Operators]** .
1. Selezionare l&#39;operatore a cui si desidera collegare un&#39;area di sicurezza e fare clic sulla scheda **[!UICONTROL Edit]**.
1. Vai alla scheda **[!UICONTROL Access rights]** e fai clic sul collegamento **[!UICONTROL Edit access parameters...]** .

   ![](assets/zone_operator.png)

1. Seleziona una zona dall’elenco a discesa **[!UICONTROL Authorized connection zone]**

   ![](assets/zone_operator_selection.png)

1. Fai clic su **[!UICONTROL OK]** e salva le modifiche per applicare queste modifiche.
