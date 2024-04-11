---
product: campaign
title: Integrazione in un server web per Windows
description: Integrazione in un server web per Windows
feature: Installation, Instance Settings
badge-v7-prem: label="on-premise e ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 041c4431-baae-4e64-9e9a-0daa5123bd8a
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '889'
ht-degree: 2%

---

# Integrazione in un server web per Windows{#integration-into-a-web-server-for-windows}



Adobe Campaign include Apache Tomcat che funge da punto di ingresso nel server applicazioni tramite HTTP (e SOAP).

Puoi utilizzare questo server Tomcat integrato per soddisfare le richieste HTTP.

In questo caso:

* la porta di ascolto predefinita è 8080. Per modificarlo, fare riferimento a [questa sezione](../../installation/using/configure-tomcat.md).
* Le console client si connettono quindi utilizzando un URL come ```https:// `<computer>`:8080```.

Tuttavia, per motivi di sicurezza e amministrazione, si consiglia di utilizzare un server Web dedicato come punto di ingresso principale per il traffico HTTP quando il computer che esegue Adobe Campaign è esposto su Internet e si desidera aprire l&#39;accesso alla console al di fuori della rete.

Un server web consente inoltre di garantire la riservatezza dei dati con il protocollo HTTP.

Allo stesso modo, è necessario utilizzare un server Web quando si desidera utilizzare la funzionalità di tracciamento, disponibile solo come modulo di estensione del server Web.

>[!NOTE]
>
>Se non utilizzi la funzionalità di tracciamento, puoi eseguire un’installazione standard di Apache o IIS con un reindirizzamento a Campaign. Il modulo di estensione del server Web di tracciamento non è richiesto.

## Configurazione del server Web IIS {#configuring-the-iis-web-server}

La procedura di configurazione per un server Web IIS è prevalentemente grafica. Comporta l’utilizzo di un sito web (già creato o in attesa di creazione) per accedere alle risorse del server Adobe Campaign: file Java (.jsp), fogli di stile (.css, .xsl), immagini (.png), DLL ISAPI per il reindirizzamento e così via.

Nelle sezioni seguenti viene descritta la configurazione in IIS 7. La configurazione per IIS8 è sostanzialmente la stessa.

Se il server Web IIS non è già installato nel computer, è possibile installarlo tramite **[!UICONTROL Add > Remove Programs > Enable or disable Windows functionalities]** menu.

In IIS 7, oltre ai servizi standard, devi installare le estensioni ISAPI e i filtri ISAPI.

![](assets/s_ncs_install_iis7_isapi.png)

### Passaggi di configurazione {#configuration-steps}

Applica i seguenti passaggi di configurazione:

1. Apri IIS tramite **[!UICONTROL Control panel > Administrative tools > Services]** menu.
1. Crea e configura il sito (ad esempio, Adobe Campaign) in base ai parametri della rete (porta di connessione TCP, host DNS, indirizzo IP).

   ![](assets/s_ncs_install_iis7_add_site.png)

   Specificare almeno il nome del sito e il percorso di accesso alla directory virtuale. Poiché non viene utilizzato il percorso per accedere alla directory del sito Web, è possibile utilizzare la directory seguente.

   ```
   C:\inetpub\wwwroot
   ```

   ![](assets/s_ncs_install_iis7_parameters_step1.png)

1. A **VBS** script consente di configurare automaticamente le risorse utilizzate dal server Adobe Campaign nella directory virtuale appena creata. Per avviarlo, fai doppio clic sul pulsante **iis_neolane_setup.vbs** file che si trova in `[INSTALL]\conf` cartella, dove `[INSTALL]` è il percorso per accedere alla cartella di installazione di Adobe Campaign.

   ![](assets/s_ncs_install_iis7_parameters_step2.png)

   >[!NOTE]
   >
   >In caso di installazione di Windows Server 2008/IIS7, è necessario aver effettuato l&#39;accesso come amministratore per eseguire lo script VBS o eseguire lo script come amministratore.

   Clic **[!UICONTROL OK]** se il server Web viene utilizzato come server di reindirizzamento di tracciamento, altrimenti fai clic su **[!UICONTROL Cancel]**.

   Quando nel server Web sono già configurati più siti, viene visualizzata una pagina intermedia per specificare a quale sito Web si applica l&#39;installazione: immettere il numero collegato al sito e fare clic su **[!UICONTROL OK]**.

   ![](assets/s_ncs_install_iis7_parameters_step3.png)

   Viene visualizzato un messaggio di conferma:

   ![](assets/s_ncs_install_iis7_parameters_step7.png)

1. In **[!UICONTROL Content View]** , accertarsi che il sito Web sia configurato correttamente con le risorse Adobe Campaign:

   ![](assets/s_ncs_install_iis7_parameters_step6.png)

   Se la struttura non è visualizzata, riavviare IIS.

### Gestione dei diritti {#managing-rights}

È quindi necessario configurare le impostazioni di protezione per la DLL ISAPI e per le risorse nella directory di installazione di Adobe Campaign.

A questo scopo, esegui i seguenti passaggi:

1. Seleziona la **[!UICONTROL Features View]** e fare doppio clic sul pulsante **Autenticazione** collegamento.

   ![](assets/s_ncs_install_iis7_parameters_step8.png)

1. In **Sicurezza directory** del sito Web, verificare che l&#39;accesso anonimo sia abilitato. Se necessario, fai clic su **[!UICONTROL Edit]** per modificare le impostazioni.

   ![](assets/s_ncs_install_iis7_parameters_step9.png)

### Avvio del server web e verifica della configurazione {#launching-the-web-server-and-testing-the-configuration}

Ora devi verificare se la configurazione è corretta.

A tale scopo, attenersi alla procedura descritta di seguito.

1. Riavviare il server IIS utilizzando **iisreset** riga di comando.

1. Avvia il servizio Adobe Campaign, quindi assicurati che sia in esecuzione.

1. Verifica il modulo di tracciamento inserendo il seguente URL in un browser Web:

   ```
   https://<computer>/r/test
   ```

   Il browser deve visualizzare la seguente risposta:

   ```
   <redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='myserver.mydomain.com' localHost='localhost'/>
   ```

Per verificare la presenza del modulo di reindirizzamento, eseguire la riga di comando seguente:

```
nlserver pdump
```

Deve inoltre fornire le seguenti informazioni:

```
12:00:33 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
webmdl@default (1644) - 18.2 Mo
```

È inoltre possibile verificare che la DLL ISAPI sia caricata correttamente.

A questo scopo, esegui i seguenti passaggi:

1. Modifica i filtri ISAPI per il sito Adobe Campaign facendo clic sul pulsante **[!UICONTROL Driver mapping]** icona.
1. La sezione verifica il contenuto del filtro ISAPI:

   ![](assets/s_ncs_install_iis7_parameters_step11.png)

## Configurazioni aggiuntive {#additional-configurations}

### Modifica del limite di dimensione del file di caricamento {#changing-the-upload-file-size-limit}

Durante la configurazione del server Web IIS, viene automaticamente impostato un limite di circa 28 MB per i file impostati che vengono caricati sul server.

Questo può avere un impatto su Adobe Campaign, in particolare se desideri caricare file di dimensioni superiori a questo limite.

Ad esempio, se utilizzi un’ **Caricamento dati (file)** digita l’attività in un flusso di lavoro per importare un file da 50 MB; se si verifica un errore, il flusso di lavoro non viene eseguito correttamente.

In questo caso, devi aumentare questo limite:

1. Apri IIS tramite **[!UICONTROL Start > (Control panel) > Administration tools]** menu.
1. In **Connessioni** , selezionare il sito creato per l&#39;installazione dell&#39;Adobe, quindi fare doppio clic su **Filtro richieste** nel riquadro principale.
1. In **Azioni** riquadro, selezionare **Modifica impostazioni funzionalità** per poter modificare il valore in **Dimensione massima contenuto autorizzato (byte)** campo.

   Ad esempio, per autorizzare il caricamento di file di 50 MB, è necessario specificare un valore superiore a &quot;52428800&quot; byte.

>[!NOTE]
>
>Per ulteriori informazioni su questa opzione IIS, consulta la sezione &quot;Procedura&quot; del [documentazione ufficiale](https://www.iis.net/configreference/system.webserver/security/requestfiltering/requestlimits).

