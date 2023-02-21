---
product: campaign
title: Installazione di un server di mid-sourcing in Campaign
description: Questa sezione descrive l’installazione e la configurazione di un server di mid-sourcing in Campaign
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 3e55d7f5-2858-4390-bba9-8fb5be0c3d98
source-git-commit: f4513834cf721f6d962c7c02c6c64b2171059352
workflow-type: tm+mt
source-wordcount: '995'
ht-degree: 1%

---

# Server di mid-sourcing{#mid-sourcing-server}

![](../../assets/v7-only.svg)

Questa sezione descrive l’installazione e la configurazione di un server di mid-sourcing, nonché la distribuzione di un’istanza che consente a terze parti di inviare messaggi **mid-sourcing** modalità.

L&#39;architettura &quot;mid-sourcing&quot; viene presentata in [Distribuzione mid-sourcing](../../installation/using/mid-sourcing-deployment.md).

L&#39;installazione di un server di mid-sourcing segue lo stesso processo dell&#39;installazione di un server nel modo normale (fare riferimento alla configurazione standard). Si tratta di un’istanza indipendente con il proprio database che può essere utilizzata per eseguire le consegne. In poche parole, contiene una configurazione aggiuntiva per consentire alle istanze remote di eseguire consegne attraverso di essa in modalità mid-sourcing.

>[!CAUTION]
>
>Una volta configurato il server di mid-sourcing e il [flussi di lavoro sincronizzati](../../workflow/using/about-technical-workflows.md) aver eseguito per la prima volta, assicurati di non aggiornare il nome interno degli account esterni di mid-sourcing.

## Passaggi per l’installazione e la configurazione di un’istanza {#steps-for-installing-and-configuring-an-instance}

### Prerequisiti per l’installazione e la configurazione di un’istanza {#prerequisites-for-installing-and-configuring-an-instance}

* JDK sul server dell&#39;applicazione.
* Accesso a un server di database sul server dell&#39;applicazione.
* Firewall configurato per aprire le porte HTTP (80) o HTTPS (443) al server di mid-sourcing.

La procedura seguente descrive una configurazione che utilizza un singolo server di mid-sourcing. È inoltre possibile utilizzare più server. Allo stesso modo è anche possibile inviare determinati messaggi (ad esempio le notifiche del flusso di lavoro) da una configurazione interna.

### Installazione e configurazione del server applicazioni per la distribuzione di mid-sourcing {#installing-and-configuring-the-application-server-for-mid-sourcing-deployment}

La procedura di installazione è identica a quella dell&#39;istanza indipendente. Fai riferimento a [Installazione e configurazione (computer singolo)](../../installation/using/standalone-deployment.md#installing-and-configuring--single-machine-).

Tuttavia, è necessario applicare quanto segue:

* Al passaggio **5**, devi disattivare l’ **mta** (consegna) e **inMail** Moduli (mail non recapitate). La **wfserver** Il modulo (flusso di lavoro), tuttavia, deve rimanere attivato.

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

   Per ulteriori informazioni al riguardo, consulta [questa sezione](../../installation/using/configuring-campaign-server.md#enabling-processes).

* Passaggi **6**, **9** e **10** non sono necessarie.
* Passaggi **12** e **13**, è necessario indicare la porta 8080 nell’URL di connessione (poiché la console comunica direttamente con Tomcat, non tramite il server web). L’URL diventa `http://console.campaign.net:8080`. Passaggio durante **13**, seleziona **[!UICONTROL Issue towards Mid-sourcing]** e quelli da installare.

   ![](assets/s_ncs_install_midsourcing02.png)

   >[!CAUTION]
   >
   >Il routing predefinito delle consegne tecniche viene sostituito automaticamente con il routing e-mail tramite mid-sourcing.

### Installazione e configurazione del server di mid-sourcing {#installing-and-configuring-the-mid-sourcing-server}

Dalla console del client, individua la variabile **Indirizzamento e-mail tramite mid-sourcing** account di mid-sourcing (nel **/Administration/External accounts/** cartella). Popolare **URL del server**, **account**, **password** e **URL pagina speculare** impostazioni con le informazioni fornite dal provider del server che ospita il server di mid-sourcing. Verifica la connessione.

>[!NOTE]
>
>La **mid-sourcingEmitter** crea due **Mid-sourcing** flussi di lavoro. Si tratta di un processo che viene eseguito per impostazione predefinita ogni 1 ora e 20 minuti e raccoglie informazioni di consegna sul server di mid-sourcing.

## Distribuzione di un server di mid-sourcing {#deploying-a-mid-sourcing-server}

1. Installazione del server applicazioni:

   >[!CAUTION]
   >
   >Se installi il server di mid-sourcing e desideri installare moduli Adobe Campaign aggiuntivi, ti consigliamo di utilizzare il modulo Consegna e non il modulo Campaign.

   Segui la stessa procedura utilizzata per la distribuzione standard, selezionando solo la **[!UICONTROL Mid-sourcing platform]** opzione .

   ![](assets/s_ncs_install_midsourcing01.png)

1. Configurazione per la ricezione in modalità mid-sourcing

   Imposta la password dell’account di invio: In **/Mid-sourcing/Access Management/Operator/** la cartella **mid** viene utilizzato dall&#39;istanza remota per l&#39;invio in modalità mid-sourcing. È necessario impostare una password per questo operatore e assegnarla all’amministratore dell’istanza di invio.

   La **Piattaforma di mid-sourcing** crea le cartelle predefinite per l’archiviazione delle consegne inviate e l’operatore predefinito che esegue gli invii.

## Multiplexing del server di mid-sourcing {#multiplexing-the-mid-sourcing-server}

>[!CAUTION]
>
>Il multiplexing è supportato solo per gli ambienti on-premise.

È possibile che un&#39;istanza di mid-sourcing sia condivisa da più istanze di invio. Ciascuna di queste istanze deve essere associata a un operatore nel database di mid-sourcing. Per creare un secondo account sul server di mid-sourcing:

1. Crea una cartella nel **[!UICONTROL Mid-sourcing > Deliveries]** nodo che sarà associato all&#39;account mid-sourcing predefinito (ad esempio: prod).
1. Crea una cartella nel **[!UICONTROL Mid-sourcing > Deliveries]** nodo con lo stesso nome dell&#39;account (ad esempio: accept_test).

   ![](assets/mid_recette_account.png)

1. In **[!UICONTROL Mid-sourcing > Access Management > Operators]**, crea un nuovo account.

   ![](assets/mid_recette_user_create.png)

1. In **[!UICONTROL Access rights]** , assegna a questo operatore i diritti **Invio a mid-sourcing** gruppo. Questo diritto di accesso è disponibile in **[!UICONTROL Mid-sourcing > Access Management > Operator groups]**.

   ![](assets/mid_recette_user_rights.png)

1. Seleziona la **[!UICONTROL Restrict to data in the sub-folders of]** e seleziona la cartella consegne per limitare questo operatore alla cartella consegne di mid-sourcing .

   ![](assets/mid_recette_user_restrictions.png)

1. Riavvia il modulo Web utilizzando il seguente comando: **nlserver riavvio Web**.

È necessario modificare l&#39;impostazione del server di mid-sourcing nel file serverConf.xml . La seguente riga deve essere aggiunta alla sezione &quot;Gestione delle affinità con indirizzi IP&quot;, sotto la riga esistente:

```
<IPAffinity IPMask="" localDomain="" name=""/>
```

L&#39;attributo &#39;@name&#39; deve rispettare le seguenti regole:

**&#39;marketing_account_operator_name&#39;.&#39;affinity_name&#39;.&#39;affinity_group&#39;**

&#39;marketing_account_operator_name&#39; fa riferimento al nome interno dell&#39;account di mid-sourcing dichiarato nell&#39;istanza di mid-sourcing.

&#39;affinity_name&#39; fa riferimento al nome arbitrario assegnato all&#39;affinità. Questo nome deve essere univoco. I caratteri autorizzati sono `[a-z]``[A-Z]``[0-9]`. L&#39;obiettivo è quello di dichiarare un gruppo di indirizzi IP pubblici.

&#39;affinity_group&#39; fa riferimento alla sub-affinità dichiarata nel mapping di destinazione utilizzato in ciascuna consegna. L&#39;ultima parte, compreso il simbolo &quot;.&quot; viene ignorato se non è presente alcuna sottoaffinità. I caratteri autorizzati sono `[a-z]``[A-Z]``[0-9]`.

È necessario arrestare e quindi riavviare il server per tenere conto della modifica.

## Configurazione del tracciamento su un server di mid-sourcing {#configuring-tracking-on-a-mid-sourcing-server}

**Configurazione del server di mid-sourcing**

1. Vai a &quot;operatori&quot; e seleziona l’operatore **[!UICONTROL mid]**.
1. In **[!UICONTROL Frontal servers]** immettere i parametri di connessione del server di tracciamento.

   Per creare un’istanza di tracciamento, immetti l’URL del server di tracciamento, la password dell’account interno del server di tracciamento e il nome dell’istanza, la relativa password e le maschere DNS ad essa associate.

   ![](assets/s_ncs_install_midsourcing_tracking02.png)

1. Dopo aver inserito i parametri di connessione, fai clic su **[!UICONTROL Confirm the configuration]**.
1. Se necessario, specifica il percorso in cui devono essere memorizzate le immagini contenute nelle consegne. A questo scopo, seleziona una delle modalità di pubblicazione dall’elenco a discesa.

   ![](assets/s_ncs_install_midsourcing_tracking03.png)

   Se scegli la **[!UICONTROL Tracking server(s)]** le immagini verranno copiate sul server di mid-sourcing.

**Configurazione della piattaforma cliente**

1. Passa all&#39;account di routing di mid-sourcing esterno.
1. In **[!UICONTROL Mid-Sourcing]** specificare i parametri di connessione del server di mid-sourcing.

   ![](assets/s_ncs_install_midsourcing_tracking06.png)

1. Conferma la configurazione facendo clic su **[!UICONTROL Test the connection]**.
1. Dichiara l&#39;istanza di tracciamento a cui si fa riferimento nel server di mid-sourcing:

   Fai clic sul collegamento **[!UICONTROL Use this platform as a proxy to access the tracking servers]**,

   Specifica il nome dell&#39;istanza di tracciamento e quindi conferma la connessione con il server di tracciamento.

   ![](assets/s_ncs_install_midsourcing_tracking05.png)

Se la consegna dei messaggi deve essere gestita da diversi server di mid-sourcing, selezionare l’opzione **[!UICONTROL Routing with alternating mid-sourcing accounts]** e specificare i diversi server.

![](assets/s_ncs_install_midsourcing_tracking04.png)
