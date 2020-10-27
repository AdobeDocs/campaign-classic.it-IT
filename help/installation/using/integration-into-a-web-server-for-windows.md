---
title: Integrazione in un server web per Windows
seo-title: Integrazione in un server web per Windows
description: Integrazione in un server web per Windows
seo-description: null
page-status-flag: never-activated
uuid: a5042221-44fe-46a6-9322-288b108396e2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
discoiquuid: a4f2ae0e-e631-4ab6-934e-8298e4ce6f2c
translation-type: tm+mt
source-git-commit: d509dc584cd4ae17c6dda85c09fceee8c6162dba
workflow-type: tm+mt
source-wordcount: '968'
ht-degree: 3%

---


# Integrazione in un server web per Windows{#integration-into-a-web-server-for-windows}

 Adobe Campaign include Apache Tomcat che funge da punto di ingresso nel server dell’applicazione tramite HTTP (e SOAP).

Potete utilizzare questo server Tomcat integrato per soddisfare le richieste HTTP.

In questo caso:

* la porta di ascolto predefinita è 8080. Per modificarlo, fare riferimento a [Configurazione di Tomcat](../../installation/using/configuring-campaign-server.md#configuring-tomcat).
* Le console client si connettono quindi utilizzando un URL quale [https:// `<computer>`:8080](https://machine:8080).

Tuttavia, per motivi di sicurezza e amministrazione, si consiglia di utilizzare un server Web dedicato come punto di ingresso principale per il traffico HTTP quando il computer che esegue  Adobe Campaign è esposto su Internet e si desidera aprire l&#39;accesso alla console all&#39;esterno della rete.

Un server Web consente inoltre di garantire la riservatezza dei dati con il protocollo HTTP.

Analogamente, è necessario utilizzare un server Web quando si desidera utilizzare la funzionalità di tracciamento, disponibile solo come modulo di estensione del server Web.

>[!NOTE]
>
>Se non utilizzate la funzionalità di tracciamento, potete eseguire un&#39;installazione standard di Apache o IIS con un reindirizzamento a Campaign. Il modulo di estensione del server Web di tracciamento non è richiesto.

## Configurazione del server Web IIS {#configuring-the-iis-web-server}

La procedura di configurazione per un server Web IIS è principalmente grafica. Si tratta di utilizzare un sito Web (già creato o in attesa di creazione) per accedere alle risorse del server Adobe Campaign : File Java (.jsp), fogli di stile (.css, .xsl), immagini (.png), DLL ISAPI per il reindirizzamento, ecc.

Nelle seguenti sezioni viene descritta la configurazione dei dettagli in IIS 7. La configurazione per IIS8 è sostanzialmente la stessa.

Se il server Web IIS non è già installato sul computer, è possibile installarlo tramite il **[!UICONTROL Add > Remove Programs > Enable or disable Windows functionalities]** menu.

In IIS 7, oltre ai servizi standard, è necessario installare le estensioni ISAPI e i filtri ISAPI.

![](assets/s_ncs_install_iis7_isapi.png)

### Passaggi di configurazione {#configuration-steps}

Effettuate le seguenti operazioni di configurazione:

1. Aprire IIS tramite il **[!UICONTROL Control panel > Administrative tools > Services]** menu.
1. Create e configurate il sito ( Adobe Campaign, ad esempio) in base ai parametri della rete (porta di connessione TCP, host DNS, indirizzo IP).

   ![](assets/s_ncs_install_iis7_add_site.png)

   È necessario specificare almeno il nome del sito e il percorso di accesso alla directory virtuale. Poiché il percorso di accesso alla directory del sito Web non è utilizzato, è possibile utilizzare la seguente directory.

   ```
   C:\inetpub\wwwroot
   ```

   ![](assets/s_ncs_install_iis7_parameters_step1.png)

1. Uno script **VBS** consente di configurare automaticamente le risorse utilizzate dal server Adobe Campaign  sulla directory virtuale appena creata. Per avviarlo, fate doppio clic sul file **iis_neolane_setup.vbs** che si trova nella `[INSTALL]\conf` cartella, dove `[INSTALL]` si trova il percorso di accesso alla cartella di installazione  Adobe Campaign.

   ![](assets/s_ncs_install_iis7_parameters_step2.png)

   >[!NOTE]
   >
   >Nel caso di un&#39;installazione del server Windows 2008/IIS7, è necessario aver eseguito l&#39;accesso come amministratore per eseguire lo script VBS o eseguirlo come amministratore.

   Fare clic **[!UICONTROL OK]** se il server Web viene utilizzato come server di reindirizzamento di tracciamento, altrimenti fare clic su **[!UICONTROL Cancel]**.

   Quando più siti sono già configurati sul server Web, viene visualizzata una pagina intermedia per specificare a quale sito Web si applica l&#39;installazione: inserite il numero collegato al sito e fate clic su **[!UICONTROL OK]**.

   ![](assets/s_ncs_install_iis7_parameters_step3.png)

   Deve essere visualizzato un messaggio di conferma:

   ![](assets/s_ncs_install_iis7_parameters_step7.png)

1. Nella **[!UICONTROL Content View]** scheda, verificare che il sito Web sia configurato correttamente con le risorse Adobe Campaign :

   ![](assets/s_ncs_install_iis7_parameters_step6.png)

   Se la struttura non è visualizzata, riavviare IIS.

### Gestione delle autorizzazioni {#managing-rights}

È quindi necessario configurare le impostazioni di protezione per la DLL ISAPI e per le risorse nella directory di installazione di Adobe Campaign .

A questo scopo, eseguire i seguenti passaggi:

1. Selezionate la **[!UICONTROL Features View]** scheda e fate doppio clic sul collegamento **Autenticazione** .

   ![](assets/s_ncs_install_iis7_parameters_step8.png)

1. Nella scheda Protezione **** directory del sito Web, verificare che sia attivato l&#39;accesso anonimo. Se necessario, fate clic sul **[!UICONTROL Edit]** collegamento per modificare le impostazioni.

   ![](assets/s_ncs_install_iis7_parameters_step9.png)

### Avvio del server Web e verifica della configurazione {#launching-the-web-server-and-testing-the-configuration}

È ora necessario verificare se la configurazione è corretta.

A tal fine, attenersi alla procedura seguente:

1. Riavviate il server IIS utilizzando la riga di comando **iisreset** .
1. Verificate il modulo di tracciamento inserendo il seguente URL in un browser Web:

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

Deve restituire le seguenti informazioni:

```
12:00:33 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
webmdl@default (1644) - 18.2 Mo
```

È inoltre possibile assicurarsi che la DLL ISAPI sia caricata correttamente.

A questo scopo, eseguire i seguenti passaggi:

1. Modificate i filtri ISAPI per il sito Adobe Campaign  facendo clic sull&#39; **[!UICONTROL Driver mapping]** icona.
1. Controllare il contenuto del filtro ISAPI:

   ![](assets/s_ncs_install_iis7_parameters_step11.png)

## Configurazioni aggiuntive {#additional-configurations}

### Modifica del limite di dimensione per il file di caricamento {#changing-the-upload-file-size-limit}

Quando si configura il server Web IIS, viene automaticamente impostato un limite di circa 28 MB per i file caricati nel server.

Questo potrebbe avere un impatto in  Adobe Campaign, in particolare se desiderate caricare file di dimensioni maggiori di questo limite.

Ad esempio, se si utilizza un&#39;attività di caricamento **dati (file)** in un flusso di lavoro per importare un file da 50 MB, un errore interrompe l&#39;esecuzione corretta del flusso di lavoro.

In questo caso, dovete aumentare questo limite:

1. Aprire IIS tramite il **[!UICONTROL Start > (Control panel) > Administration tools]** menu.
1. Nel riquadro **Connessioni** , selezionate il sito creato per l&#39;installazione del Adobe , quindi fate doppio clic su **Richiedi filtro** nel riquadro principale.
1. Nel riquadro **Azioni** , selezionare **Modifica impostazioni** funzione per poter modificare il valore nel campo Dimensione contenuto **massima autorizzata (byte)** .

   Ad esempio, per autorizzare il caricamento di file di 50 MB, dovete specificare un valore superiore a &quot;52428800&quot; byte.

>[!NOTE]
>
>Per ulteriori informazioni su questa opzione IIS, fare riferimento alla sezione &quot;Come fare per&quot; della documentazione [](https://www.iis.net/configreference/system.webserver/security/requestfiltering/requestlimits)ufficiale.

### Configurazione della visualizzazione del messaggio di errore HTTP {#configuring-http-error-message-display}

Se si utilizza un server IIS versione 6.1, i messaggi di errore generati potrebbero essere difficili da leggere a causa della visualizzazione nel messaggio di un codice HTML indesiderato.

Per risolvere il problema e visualizzare l&#39;errore correttamente, applicare la seguente configurazione:

1. Aprire IIS tramite il **[!UICONTROL Start > Control Panel > Administrative tools]** menu.
1. Nel riquadro **Connessioni** , selezionate il sito creato per l&#39;installazione di Adobe Campaign , quindi fate doppio clic su Editor **di** configurazione nel riquadro principale.
1. Nell&#39;elenco a discesa **Sezione** , selezionate **system.webServer** > **httpErrors**.
1. Selezionare il valore **PassThrough** nella riga **existingResponse** .

![](assets/ins_iis_httperrors.png)

