---
product: campaign
title: Creazione di un’istanza e accesso
description: Creazione di un’istanza e accesso
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a025026e-688e-4ec1-abc4-40ee040d2b3b
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 5%

---

# Creazione di un’istanza e accesso{#creating-an-instance-and-logging-on}



Per creare una nuova istanza e un database Adobe Campaign, attenersi alla seguente procedura:

1. Crea la connessione.
1. Accedere per creare la relativa istanza.
1. Creare e configurare il database.

>[!NOTE]
>
>Solo il **interno** L&#39;identificatore può eseguire queste operazioni. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../installation/using/configuring-campaign-server.md#internal-identifier).

Quando si avvia la console Adobe Campaign, si accede a una pagina di accesso.

Per creare una nuova istanza, effettua le seguenti operazioni:

1. Fai clic sul collegamento nell’angolo in alto a destra dei campi delle credenziali per accedere alla finestra di configurazione della connessione. Questo collegamento può essere **[!UICONTROL New...]** o un nome di istanza esistente.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Clic **[!UICONTROL Add > Connection]** e immetti l’etichetta e l’URL del server applicazioni Adobe Campaign.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Specifica una connessione al server applicazioni Adobe Campaign tramite un URL. Utilizza un DNS o un alias del computer oppure il tuo indirizzo IP.

   Ad esempio, puoi utilizzare `https://<machine>.<domain>.com` digita URL.

   >[!CAUTION]
   >
   >Per l’URL di connessione, utilizza solo i seguenti caratteri: `[a-z]`, `[A-Z]`, `[0-9]` e trattini (-) o punti interi.

1. Clic **[!UICONTROL Ok]** per confermare le impostazioni: ora puoi iniziare con il processo di creazione dell’istanza.
1. In **[!UICONTROL Connection settings]** finestra, inserire **interno** e la relativa password per connettersi al server applicazioni di Adobe Campaign. Una volta effettuata la connessione, è possibile accedere alla procedura guidata di creazione dell&#39;istanza per dichiarare una nuova istanza
1. In **[!UICONTROL Name]** , immettere il **nome istanza**. Poiché questo nome viene utilizzato per generare un file di configurazione **config-`<instance>`.xml** e viene utilizzato nei parametri della riga di comando per identificare l’istanza, assicurati di scegliere un nome breve senza caratteri speciali. Ad esempio: **eMarketing**.

   ![](assets/s_ncs_install_create_instance.png)

   Il nome dell’istanza aggiunta al nome di dominio non può superare i 40 caratteri. Questo consente di limitare le dimensioni delle intestazioni &quot;ID messaggio&quot; e impedisce che i messaggi vengano considerati come spam, in particolare da strumenti come SpamAssassin.

1. In **[!UICONTROL DNS masks]** , immettere il **elenco delle maschere DNS** a cui deve essere collegata l’istanza. Il server Adobe Campaign utilizza il nome host visualizzato nelle richieste HTTP per determinare quale istanza raggiungere.

   Il nome host è contenuto tra la stringa **https://** e il primo carattere barra **/** dell&#39;indirizzo del server.

   È possibile definire un elenco di valori separati da virgole.

   I caratteri ? e &#42; i caratteri possono essere utilizzati come caratteri jolly per sostituire uno o più caratteri (DNS, porta, ecc.). Ad esempio, **demo&#42;** value funziona con &quot;https://demo&quot; come con &quot;https://demo:8080&quot; e anche &quot;https://demo2&quot;.

   I nomi utilizzati devono essere definiti nel DNS. È inoltre possibile informare la corrispondenza tra un nome DNS e un indirizzo IP in **c:/windows/system32/drivers/etc/hosts** in Windows e in **/etc/hosts** in Linux. È quindi necessario modificare le impostazioni di connessione per utilizzare questo nome DNS per connettersi all’istanza selezionata.

   Il server deve essere identificato da questo nome, in particolare per il caricamento di immagini nelle e-mail.

   Inoltre, il server deve essere in grado di connettersi a se stesso con questo nome, e se possibile con un indirizzo di loopback - 127.0.0.1 -, in particolare per consentire l&#39;esportazione dei report in formato PDF.

1. In **[!UICONTROL Language]** , selezionare il **lingua dell’istanza**: inglese (Stati Uniti), inglese (Regno Unito), francese o giapponese.

   Le differenze tra l&#39;inglese americano e l&#39;inglese britannico sono descritte in [questa sezione](../../platform/using/adobe-campaign-workspace.md#date-and-time).

   >[!CAUTION]
   >
   >Impossibile modificare la lingua dell&#39;istanza dopo questo passaggio. Le istanze di Adobe Campaign non sono multilingue: non è possibile passare da una lingua all’altra.

1. Clic **[!UICONTROL Ok]** per confermare la dichiarazione dell’istanza. Disconnettersi e rieseguire l&#39;accesso per dichiarare il database.

   >[!NOTE]
   >
   >L’istanza può essere creata dalla riga di comando. Per ulteriori informazioni, consulta [Righe di comando](../../installation/using/command-lines.md).
