---
solution: Campaign Classic
product: campaign
title: Installazione di un server di mid-sourcing in Campaign
description: Questa sezione descrive l'installazione e la configurazione di un server di mid-sourcing in Campaign
audience: installation
content-type: reference
topic-tags: additional-configurations
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '999'
ht-degree: 0%

---


# Server di mid-sourcing{#mid-sourcing-server}

Questa sezione descrive l&#39;installazione e la configurazione di un server di mid-sourcing, nonché la distribuzione di un&#39;istanza che consente a terze parti di inviare messaggi in modalità **mid-sourcing**.

L&#39;architettura &quot;mid-sourcing&quot; viene presentata in [distribuzione mid-sourcing](../../installation/using/mid-sourcing-deployment.md).

L&#39;installazione di un server mid-sourcing segue lo stesso processo dell&#39;installazione di un server nel modo normale (fare riferimento alla configurazione standard). Si tratta di un&#39;istanza indipendente con un proprio database che può essere utilizzata per eseguire le consegne. In poche parole, contiene una configurazione aggiuntiva per consentire alle istanze remote di eseguire le consegne attraverso di esso in modalità mid-sourcing.

>[!CAUTION]
>
>Una volta che il server di mid-sourcing è stato configurato e i [flussi di lavoro di sincronizzazione](../../workflow/using/transfer-to-mid-sourcing.md) sono stati eseguiti per la prima volta, accertatevi di non aggiornare il nome interno degli account esterni di mid-sourcing.

## Passaggi per l&#39;installazione e la configurazione di un&#39;istanza {#steps-for-installing-and-configuring-an-instance}

### Prerequisiti per l&#39;installazione e la configurazione di un&#39;istanza {#prerequisites-for-installing-and-configuring-an-instance}

* JDK sul server dell’applicazione.
* Accesso a un server di database sul server dell’applicazione.
* Firewall configurato per aprire le porte HTTP (80) o HTTPS (443) al server di mid-sourcing.

Nella procedura seguente viene descritta una configurazione che utilizza un singolo server mid-sourcing. È inoltre possibile utilizzare più server. Allo stesso modo, è anche possibile inviare alcuni messaggi (ad esempio, notifiche del flusso di lavoro) da una configurazione interna.

### Installazione e configurazione del server applicazione per la distribuzione di mid-sourcing {#installing-and-configuring-the-application-server-for-mid-sourcing-deployment}

La procedura di installazione è identica a quella dell&#39;istanza standalone. Fare riferimento a [Installazione e configurazione (computer singolo)](../../installation/using/standalone-deployment.md#installing-and-configuring--single-machine-).

Tuttavia, è necessario applicare quanto segue:

* Al passaggio **5**, è necessario disabilitare i moduli **mta** (consegna) e **inMail** (messaggi di rimbalzo). Il modulo **wfserver** (flusso di lavoro) deve tuttavia rimanere attivato.

   ```
   <?xml version='1.0'?>
   <serverconf>  
     <shared>    
       <!-- add lang="eng" to dataStore to force English for the instance -->    
       <dataStore hosts="console.campaign.net*">      
         <mapping logical="*" physical="default"/>    
       </dataStore>  </shared>  
       <mta autoStart="false"/>  
       <wfserver autoStart="true"/>  
       <inMail autoStart="false"/>  
       <sms autoStart="false"/>  
       <listProtect autoStart="false"/>
   </serverconf>
   ```

   Per ulteriori informazioni, vedere [Attivazione dei processi](../../installation/using/campaign-server-configuration.md#enabling-processes).

* I passaggi **6**, **9** e **10** non sono necessari.
* Durante i passaggi **12** e **13**, è necessario indicare la porta 8080 nell&#39;URL della connessione (poiché la console comunica direttamente con Tomcat, non tramite il server Web). L&#39;URL diventa [http://console.campaign.net:8080](http://console.campaign.net). Durante il passaggio **13**, selezionare il pacchetto **[!UICONTROL Issue towards Mid-sourcing]** e quelli da installare.

   ![](assets/s_ncs_install_midsourcing02.png)

   >[!CAUTION]
   >
   >Il routing predefinito delle consegne tecniche viene sostituito automaticamente con il routing dell&#39;e-mail tramite il mid-sourcing.

### Installazione e configurazione del server di mid-sourcing {#installing-and-configuring-the-mid-sourcing-server}

Dalla console client, individuare il routing **E-mail utilizzando l&#39;account mid-sourcing** (nella cartella **/Administration/External accounts/**). Compilare l&#39; **URL di server**, **account**, **password** e le impostazioni **URL pagina mirror** con le informazioni fornite dal provider del server che ospita il server di mid-sourcing. Verificare la connessione.

>[!NOTE]
>
>L&#39;opzione **mid-sourcingEmitter** crea due flussi di lavoro **mid-sourcing**. Si tratta di un processo che viene eseguito per impostazione predefinita ogni 1 ora e 20 minuti e raccoglie le informazioni di consegna sul server di mid-sourcing.

## Implementazione di un server di mid-sourcing {#deploying-a-mid-sourcing-server}

1. Installazione del server applicazione:

   >[!CAUTION]
   >
   >Se installate il server di mid-sourcing e desiderate installare altri moduli  Adobe Campaign, si consiglia di utilizzare il modulo Consegna e non il modulo Campagna.

   Seguite la stessa procedura utilizzata per la distribuzione standard, selezionando solo l&#39;opzione **[!UICONTROL Mid-sourcing platform]**.

   ![](assets/s_ncs_install_midsourcing01.png)

1. Configurazione per la ricezione in modalità mid-sourcing

   Impostate la password dell&#39;account di invio: Nella cartella **/Mid-sourcing/Access Management/Operator/**, l&#39;operatore **mid** viene utilizzato dall&#39;istanza remota per l&#39;invio in modalità mid-sourcing. È necessario impostare una password per questo operatore e assegnarla all&#39;amministratore dell&#39;istanza di invio.

   L&#39;opzione **Piattaforma di origine intermedia** crea le cartelle predefinite per la memorizzazione delle consegne inviate e l&#39;operatore predefinito che esegue le invii.

## Multiplexing del server di mid-sourcing {#multiplexing-the-mid-sourcing-server}

>[!CAUTION]
>
>Il multiplexing è supportato solo per gli ambienti interni.

È possibile che un&#39;istanza mid-sourcing sia condivisa da più istanze di invio. Ciascuna di queste istanze deve essere associata a un operatore nel database mid-sourcing. Per creare un secondo account sul server di mid-sourcing:

1. Crea una cartella nel nodo **[!UICONTROL Mid-sourcing > Deliveries]** che verrà associata all&#39;account mid-sourcing predefinito (ad esempio: prod).
1. Create una cartella nel nodo **[!UICONTROL Mid-sourcing > Deliveries]** con lo stesso nome dell&#39;account (ad esempio: accept_test).

   ![](assets/mid_recette_account.png)

1. In **[!UICONTROL Mid-sourcing > Access Management > Operators]**, create un nuovo account.

   ![](assets/mid_recette_user_create.png)

1. Nella scheda **[!UICONTROL Access rights]**, assegnate a questo operatore i diritti del gruppo **Invio mid-sourcing**. Questo diritto di accesso è disponibile in **[!UICONTROL Mid-sourcing > Access Management > Operator groups]**.

   ![](assets/mid_recette_user_rights.png)

1. Selezionare l&#39;opzione **[!UICONTROL Restrict to data in the sub-folders of]** e selezionare la cartella consegne per limitare l&#39;operatore alla cartella consegne di origine intermedia.

   ![](assets/mid_recette_user_restrictions.png)

1. Riavviate il modulo Web utilizzando il comando seguente: **riavvio del server Web**.

È necessario modificare l&#39;impostazione del server di mid-sourcing nel file serverConf.xml. La seguente riga deve essere aggiunta alla sezione &quot;Gestione delle affinità con indirizzi IP&quot;, sotto la riga esistente:

```
<IPAffinity IPMask="" localDomain="" name=""/>
```

L&#39;attributo &#39;@name&#39; deve rispettare le regole seguenti:

**&#39;marketing_account_operator_name&#39;.&#39;affinity_name&#39;.&#39;affinity_group&#39;**

&#39;marketing_account_operator_name&#39; fa riferimento al nome interno dell&#39;account mid-sourcing dichiarato nell&#39;istanza mid-sourcing.

&#39;affinity_name&#39; fa riferimento al nome arbitrario assegnato all&#39;affinità. Questo nome deve essere univoco. I caratteri autorizzati sono `[a-z]``[A-Z]``[0-9]`. L&#39;obiettivo è dichiarare un gruppo di indirizzi IP pubblici.

&#39;affinity_group&#39; fa riferimento alla sub-affinità dichiarata nella mappatura di destinazione utilizzata in ciascuna consegna. L&#39;ultima parte include il simbolo &#39;.&#39; viene ignorato se non è presente alcuna sottoaffinità. I caratteri autorizzati sono `[a-z]``[A-Z]``[0-9]`.

Per poter prendere in considerazione la modifica, è necessario arrestare e riavviare il server.

## Configurazione del tracciamento su un server di mid-sourcing {#configuring-tracking-on-a-mid-sourcing-server}

**Configurazione del server di mid-sourcing**

1. Fare clic su &#39;operatori&#39; e selezionare l&#39;operatore **[!UICONTROL mid]**.
1. Nella scheda **[!UICONTROL Frontal servers]**, inserire i parametri di connessione del server di tracciamento.

   Per creare un’istanza di tracciamento, immettete l’URL del server di tracciamento, la password dell’account del server di tracciamento e il nome dell’istanza, la relativa password e le maschere DNS ad essa associate.

   ![](assets/s_ncs_install_midsourcing_tracking02.png)

1. Dopo aver immesso i parametri di connessione, fare clic su **[!UICONTROL Confirm the configuration]**.
1. Se necessario, specificate la posizione in cui memorizzare le immagini contenute nelle consegne. A questo scopo, selezionare una delle modalità di pubblicazione dall&#39;elenco a discesa.

   ![](assets/s_ncs_install_midsourcing_tracking03.png)

   Se scegliete l&#39;opzione **[!UICONTROL Tracking server(s)]**, le immagini verranno copiate sul server di mid-sourcing.

**Configurazione della piattaforma cliente**

1. Passare al conto di routing mid-sourcing esterno.
1. Nella scheda **[!UICONTROL Mid-Sourcing]**, specificare i parametri di connessione del server di origine mid-sourcing.

   ![](assets/s_ncs_install_midsourcing_tracking06.png)

1. Confermate la configurazione facendo clic su **[!UICONTROL Test the connection]**.
1. Dichiarare l’istanza di tracciamento a cui si fa riferimento nel server di mid-sourcing:

   Fare clic sul collegamento **[!UICONTROL Use this platform as a proxy to access the tracking servers]**,

   Specifica il nome dell’istanza di tracciamento e conferma la connessione con il server di tracciamento.

   ![](assets/s_ncs_install_midsourcing_tracking05.png)

Se la distribuzione dei messaggi deve essere gestita da diversi server di mid-sourcing, selezionare l&#39;opzione **[!UICONTROL Routing with alternating mid-sourcing accounts]** e specificare i diversi server.

![](assets/s_ncs_install_midsourcing_tracking04.png)

