---
product: campaign
title: Integrazione in un server web per Windows
description: Integrazione in un server web per Windows
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 041c4431-baae-4e64-9e9a-0daa5123bd8a
source-git-commit: f4513834cf721f6d962c7c02c6c64b2171059352
workflow-type: tm+mt
source-wordcount: '968'
ht-degree: 4%

---

# Integrazione in un server web per Windows{#integration-into-a-web-server-for-windows}

![](../../assets/v7-only.svg)

Adobe Campaign include Apache Tomcat che agisce come punto di ingresso nell’application server tramite HTTP (e SOAP).

Puoi utilizzare questo server Tomcat integrato per distribuire le richieste HTTP.

In questo caso:

* la porta di ascolto predefinita è 8080. Per modificarlo, fai riferimento a [questa sezione](../../installation/using/configure-tomcat.md).
* Le console client si connettono quindi utilizzando un URL come ```https:// `<computer>`:8080```.

Tuttavia, per motivi di sicurezza e amministrazione, si consiglia di utilizzare un server Web dedicato come punto di ingresso principale per il traffico HTTP quando il computer che esegue Adobe Campaign è esposto su Internet e si desidera aprire l&#39;accesso alla console all&#39;esterno della rete.

Un server Web consente inoltre di garantire la riservatezza dei dati con il protocollo HTTP.

Allo stesso modo, è necessario utilizzare un server Web quando si desidera utilizzare la funzionalità di tracciamento, disponibile solo come modulo di estensione del server Web.

>[!NOTE]
>
>Se non utilizzi la funzionalità di tracciamento, puoi eseguire un’installazione standard di Apache o IIS con un reindirizzamento a Campaign. Il modulo di estensione del server Web di tracciamento non è necessario.

## Configurazione del server Web IIS {#configuring-the-iis-web-server}

La procedura di configurazione per un server Web IIS è principalmente grafica. Per accedere alle risorse del server Adobe Campaign, è necessario utilizzare un sito Web (già creato o in attesa di creazione): File Java (.jsp), fogli di stile (.css, .xsl), immagini (.png), DLL ISAPI per il reindirizzamento, ecc.

Nelle sezioni seguenti viene illustrata la configurazione dettagliata in IIS 7. La configurazione per IIS8 è sostanzialmente la stessa.

Se il server Web IIS non è già installato nel computer, è possibile installarlo tramite il **[!UICONTROL Add > Remove Programs > Enable or disable Windows functionalities]** menu.

In IIS 7, oltre ai servizi standard, è necessario installare le estensioni ISAPI e i filtri ISAPI.

![](assets/s_ncs_install_iis7_isapi.png)

### Passaggi di configurazione {#configuration-steps}

Applica i seguenti passaggi di configurazione:

1. Apri IIS tramite il **[!UICONTROL Control panel > Administrative tools > Services]** menu.
1. Crea e configura il sito (Adobe Campaign, ad esempio) in base ai parametri della rete (porta di connessione TCP, host DNS, indirizzo IP).

   ![](assets/s_ncs_install_iis7_add_site.png)

   È necessario specificare almeno il nome del sito e il percorso di accesso alla directory virtuale. Poiché il percorso di accesso alla directory del sito Web non viene utilizzato, è possibile utilizzare la seguente directory.

   ```
   C:\inetpub\wwwroot
   ```

   ![](assets/s_ncs_install_iis7_parameters_step1.png)

1. A **VBS** lo script consente di configurare automaticamente le risorse utilizzate dal server Adobe Campaign nella directory virtuale appena creata. Per avviarlo, fai doppio clic sul pulsante **iis_neolane_setup.vbs** nel file `[INSTALL]\conf` cartella, dove `[INSTALL]` è il percorso per accedere alla cartella di installazione di Adobe Campaign.

   ![](assets/s_ncs_install_iis7_parameters_step2.png)

   >[!NOTE]
   >
   >In caso di installazione di un server Windows 2008/IIS7, è necessario aver effettuato l&#39;accesso come amministratore per eseguire lo script VBS o eseguire lo script come amministratore.

   Fai clic su **[!UICONTROL OK]** se il server Web viene utilizzato come server di reindirizzamento di tracciamento, in caso contrario fare clic su **[!UICONTROL Cancel]**.

   Quando più siti sono già configurati sul server Web, viene visualizzata una pagina intermedia per specificare a quale sito Web si applica l&#39;installazione: immettere il numero collegato al sito e fare clic su **[!UICONTROL OK]**.

   ![](assets/s_ncs_install_iis7_parameters_step3.png)

   Viene visualizzato un messaggio di conferma:

   ![](assets/s_ncs_install_iis7_parameters_step7.png)

1. In **[!UICONTROL Content View]** verificare che il sito Web sia configurato correttamente con le risorse Adobe Campaign:

   ![](assets/s_ncs_install_iis7_parameters_step6.png)

   Se la struttura non viene visualizzata, riavviare IIS.

### Gestione delle autorizzazioni {#managing-rights}

È quindi necessario configurare le impostazioni di protezione per la DLL ISAPI e per le risorse nella directory di installazione di Adobe Campaign.

A questo scopo, esegui i seguenti passaggi:

1. Seleziona la **[!UICONTROL Features View]** e fai doppio clic sul pulsante **Autenticazione** link.

   ![](assets/s_ncs_install_iis7_parameters_step8.png)

1. In **Protezione directory** Assicurarsi che l&#39;accesso anonimo sia abilitato. Se necessario, fai clic sul pulsante **[!UICONTROL Edit]** per modificare le impostazioni.

   ![](assets/s_ncs_install_iis7_parameters_step9.png)

### Avvio del server Web e verifica della configurazione {#launching-the-web-server-and-testing-the-configuration}

Ora devi verificare se la configurazione è corretta.

A questo scopo, applicare la seguente procedura:

1. Riavvia il server IIS utilizzando **iisreset** riga di comando.

1. Avvia il servizio Adobe Campaign, quindi assicurati che sia in esecuzione.

1. Verifica il modulo di tracciamento inserendo il seguente URL in un browser Web:

   ```
   https://<computer>/r/test
   ```

   Il browser deve visualizzare la seguente risposta:

   ```
   <redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='myserver.mydomain.com' localHost='localhost'/>
   ```

Per verificare la presenza del modulo di reindirizzamento, eseguire la seguente riga di comando:

```
nlserver pdump
```

Deve restituire le seguenti informazioni:

```
12:00:33 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
webmdl@default (1644) - 18.2 Mo
```

È inoltre possibile verificare che la DLL ISAPI sia caricata correttamente.

A questo scopo, esegui i seguenti passaggi:

1. Modifica i filtri ISAPI per il sito Adobe Campaign facendo clic sul pulsante **[!UICONTROL Driver mapping]** icona.
1. Controlla il contenuto del filtro ISAPI:

   ![](assets/s_ncs_install_iis7_parameters_step11.png)

## Configurazioni aggiuntive {#additional-configurations}

### Modifica del limite di dimensione del file di caricamento {#changing-the-upload-file-size-limit}

Durante la configurazione del server Web IIS, viene automaticamente impostato un limite di circa 28 MB per i file che vengono caricati sul server.

Questo può avere un impatto in Adobe Campaign, in particolare se desideri caricare file che superano questo limite.

Ad esempio, se utilizzi un **Caricamento dati (file)** digita l’attività in un flusso di lavoro per importare un file da 50 MB. Un errore impedisce l’esecuzione corretta del flusso di lavoro.

In questo caso, devi aumentare questo limite:

1. Apri IIS tramite il **[!UICONTROL Start > (Control panel) > Administration tools]** menu.
1. In **Connessioni** seleziona il sito creato per l’installazione dell’Adobe, quindi fai doppio clic su **Filtro richieste** nel riquadro principale.
1. In **Azioni** riquadro, selezionare **Modificare le impostazioni delle funzioni** per poter modificare il valore nel **Dimensione massima del contenuto autorizzata (byte)** campo .

   Ad esempio, per autorizzare il caricamento di file di 50 MB, devi specificare un valore superiore a &quot;52428800&quot; byte.

>[!NOTE]
>
>Per ulteriori informazioni su questa opzione IIS, consulta la sezione &quot;Come fare per&quot; nel [documentazione ufficiale](https://www.iis.net/configreference/system.webserver/security/requestfiltering/requestlimits).

### Configurazione della visualizzazione del messaggio di errore http {#configuring-http-error-message-display}

Se utilizzi un server IIS versione 6.1, i messaggi di errore generati possono risultare di difficile lettura a causa della visualizzazione di un codice HTML indesiderato nel messaggio.

Per risolvere il problema e visualizzare correttamente l’errore, applica la seguente configurazione:

1. Apri IIS tramite il **[!UICONTROL Start > Control Panel > Administrative tools]** menu.
1. In **Connessioni** seleziona il sito creato per l’installazione di Adobe Campaign, quindi fai doppio clic su **Editor di configurazione** nel riquadro principale.
1. In **Sezione** elenco a discesa, seleziona **system.webServer** > **httpErrors**.
1. Seleziona la **PassThrough** nella **currentResponse** linea.

![](assets/ins_iis_httperrors.png)
