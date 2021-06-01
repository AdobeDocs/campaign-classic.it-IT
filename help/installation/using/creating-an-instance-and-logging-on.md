---
product: campaign
title: Creazione di un’istanza e accesso
description: Creazione di un’istanza e accesso
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a025026e-688e-4ec1-abc4-40ee040d2b3b
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 5%

---

# Creazione di un’istanza e accesso{#creating-an-instance-and-logging-on}

Per creare una nuova istanza e un database Adobe Campaign, applica il seguente processo:

1. Crea la connessione.
1. Accedi per creare l&#39;istanza correlata.
1. Creare e configurare il database.

>[!NOTE]
>
>Solo l&#39;identificatore **internal** può eseguire queste operazioni. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../installation/using/configuring-campaign-server.md#internal-identifier).

Quando si avvia la console di Adobe Campaign, si accede a una pagina di accesso.

Per creare una nuova istanza, segui i passaggi seguenti:

1. Fai clic sul collegamento nell’angolo in alto a destra dei campi delle credenziali per accedere alla finestra di configurazione della connessione. Questo collegamento può essere **[!UICONTROL New...]** o un nome di istanza esistente.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Fai clic su **[!UICONTROL Add > Connection]** e immetti l’etichetta e l’URL del server dell’applicazione Adobe Campaign.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Specifica una connessione al server dell’applicazione Adobe Campaign tramite un URL. Utilizzare un DNS o un alias del computer o l&#39;indirizzo IP.

   Ad esempio, puoi utilizzare l&#39;URL del tipo [`https://<machine>.<domain>.com`](https://myserver.adobe.com).

   >[!CAUTION]
   >
   >Per l&#39;URL di connessione, utilizza solo i seguenti caratteri: `[a-z]`, `[A-Z]`, `[0-9]` e trattini (-) o arresti completi.

1. Fai clic su **[!UICONTROL Ok]** per confermare le impostazioni: ora puoi iniziare con il processo di creazione dell’istanza.
1. Nella finestra **[!UICONTROL Connection settings]**, immetti l&#39;accesso **internal** e la relativa password per connettersi al server dell&#39;applicazione Adobe Campaign. Una volta connessa, accedi alla procedura guidata di creazione dell&#39;istanza per dichiarare una nuova istanza
1. Nel campo **[!UICONTROL Name]** , immetti il **nome dell&#39;istanza**. Poiché questo nome viene utilizzato per generare un file di configurazione **config-`<instance>`.xml** e viene utilizzato nei parametri della riga di comando per identificare l&#39;istanza, assicurati di scegliere un nome breve senza caratteri speciali. Ad esempio: **eMarketing**.

   ![](assets/s_ncs_install_create_instance.png)

   Il nome dell&#39;istanza aggiunta al nome di dominio non deve superare i 40 caratteri. Questo ti consente di limitare le dimensioni delle intestazioni &quot;Message-ID&quot; e impedisce che i messaggi vengano considerati come spam, in particolare da strumenti come SpamAssassin.

1. Nei campi **[!UICONTROL DNS masks]** , inserisci l&#39; **elenco di maschere DNS** a cui deve essere collegata l&#39;istanza. Il server Adobe Campaign utilizza il nome host visualizzato nelle richieste HTTP per determinare quale istanza raggiungere.

   Il nome host è contenuto tra la stringa **https://** e il primo carattere barra **/** dell&#39;indirizzo del server.

   È possibile definire un elenco di valori separati da virgole.

   I caratteri ? e * possono essere utilizzati come caratteri jolly per sostituire uno o più caratteri (DNS, porta, ecc.). Ad esempio, il valore **demo*** funzionerà con &quot;https://demo&quot; come con &quot;https://demo:8080&quot; e anche con &quot;https://demo2&quot;.

   I nomi utilizzati devono essere definiti nel DNS. È inoltre possibile informare la corrispondenza tra un nome DNS e un indirizzo IP nel file **c:/windows/system32/Drivers/etc/hosts** in Windows e nel file **/etc/hosts** in Linux. È quindi necessario modificare le impostazioni di connessione per utilizzare questo nome DNS per connettersi all&#39;istanza scelta.

   Il server deve essere identificato con questo nome, in particolare per il caricamento di immagini nelle e-mail.

   Inoltre, il server deve essere in grado di connettersi a se stesso con questo nome e, se possibile, con un indirizzo di loopback - 127.0.0.1 -, in particolare per consentire l’esportazione dei rapporti in formato PDF.

1. Nell&#39;elenco a discesa **[!UICONTROL Language]** , seleziona il **linguaggio dell&#39;istanza**: Inglese (USA), inglese (Regno Unito), francese o giapponese.

   Le differenze tra inglese americano e inglese britannico sono descritte in [questa sezione](../../platform/using/adobe-campaign-workspace.md#date-and-time).

   >[!CAUTION]
   >
   >Impossibile modificare la lingua dell&#39;istanza dopo questo passaggio. Le istanze Adobe Campaign non sono multilingue: non è possibile passare da una lingua a un’altra.

1. Fai clic su **[!UICONTROL Ok]** per confermare la dichiarazione dell&#39;istanza. Disconnettiti e accedi di nuovo per dichiarare il database.

   >[!NOTE]
   >
   >L’istanza può essere creata dalla riga di comando. Per ulteriori informazioni, consulta [Righe di comando](../../installation/using/command-lines.md).
