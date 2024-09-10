---
product: campaign
title: Creazione di un’istanza e accesso
description: Creazione di un’istanza e accesso
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a025026e-688e-4ec1-abc4-40ee040d2b3b
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '586'
ht-degree: 1%

---

# Creazione di un’istanza e accesso{#creating-an-instance-and-logging-on}



Per creare una nuova istanza e un database Adobe Campaign, attenersi alla seguente procedura:

1. Crea la connessione.
1. Effettua l&#39;accesso per creare il relativo istanza.
1. Crea e configura il database.

>[!NOTE]
>
>Solo l&#39;identificatore **interno** può eseguire queste operazioni. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../installation/using/configuring-campaign-server.md#internal-identifier).

Quando si avvia la console Adobe Campaign, viene accesso una pagina login.

Per creare una nuova istanza, seguire i passaggi riportati di seguito:

1. Fare clic sul collegare nell&#39;angolo in alto a destra dei campi delle credenziali per accesso la finestra di configurazione della connessione. Il collegamento può essere **[!UICONTROL New...]** o un nome di istanza esistente.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Fare clic su **[!UICONTROL Add > Connection]** e immettere l&#39;etichetta e l&#39;URL del server applicazioni Adobe Campaign.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Specifica una connessione al server applicazioni Adobe Campaign tramite un URL. Utilizza un DNS o un alias del computer oppure il tuo indirizzo IP.

   È possibile, ad esempio, utilizzare l&#39;URL di tipo `https://<machine>.<domain>.com`.

   >[!CAUTION]
   >
   >Per il URL di connessione, utilizzare solo i seguenti caratteri: `[a-z]`, `[A-Z]`, e `[0-9]` trattini (-) o punti.

1. Fai clic **[!UICONTROL Ok]** per confermare le impostazioni: ora puoi iniziare con il processo di creazione istanza.
1. Nella finestra, inserisci il **login interno** e il **[!UICONTROL Connection settings]** suo password per connetterti al server Adobe Campaign applicazione. Una volta connessi, accesso l&#39;assistente per la creazione del istanza dichiarare un nuovo istanza
1. **[!UICONTROL Name]** Nel campo, immettere il nome **del** istanza. Poiché questo nome viene utilizzato per generare un file **di configurazione .xml`<instance>`** e viene utilizzato nei parametri della riga di comando per identificare il istanza, assicurarsi di scegliere un nome breve senza caratteri speciali. Ad esempio: **eMarketing**.

   ![](assets/s_ncs_install_create_instance.png)

   Il nome del istanza aggiunto al nome di dominio non deve superare i 40 caratteri. Ciò consente di limitare le dimensioni delle intestazioni &quot;Invia messaggio-ID&quot; e impedisce che i messaggi vengano considerati spam, in particolare da strumenti come SpamAssassin.

1. **[!UICONTROL DNS masks]** Nei campi, inserisci l&#39;elenco **delle maschere** DNS a cui allegare il istanza. Il server Adobe Campaign utilizza il nome host visualizzato nelle richieste HTTP per determinare quale istanza raggiungere.

   Il nome host è contenuto tra la stringa **https://** e il primo carattere barra **/** dell&#39;indirizzo del server.

   È possibile definire un elenco di valori separati da virgole.

   Il? e &#42; i caratteri possono essere utilizzati come caratteri jolly per sostituire uno o più caratteri (DNS, porta, ecc.). Ad istanza, il **valore demo&#42;** funzionerà con &quot;https://demo&quot; così come con &quot;https://demo:8080&quot; e lineare &quot;https://demo2&quot;.

   I nomi utilizzati devono essere definiti nel DNS. È inoltre possibile informare la corrispondenza tra un nome DNS e un indirizzo IP nel **file c:/windows/system32/drivers/etc/hosts** in Windows e nel **file /etc/hosts** in Linux. È pertanto necessario modificare le impostazioni di connessione per utilizzare questo nome DNS per connettersi al istanza scelto.

   Il server deve essere identificato con questo nome, in particolare per il caricamento di immagini nelle e-mail.

   Inoltre, il server deve essere in grado di connettersi a se stesso con questo nome e, se possibile, con un indirizzo di loopback - 127.0.0.1 -, in particolare per consentire l&#39;esportazione dei rapporti in formato PDF.

1. Nell&#39;elenco **[!UICONTROL Language]** a discesa, seleziona la **lingua** istanza: Inglese (Stati Uniti), Inglese (Regno Unito), Francese o Giapponese.

   Le differenze tra l&#39;inglese americano e l&#39;inglese britannico sono descritte in [questa sezione](../../platform/using/adobe-campaign-workspace.md#date-and-time).

   >[!CAUTION]
   >
   >Impossibile modificare la lingua dell&#39;istanza dopo questo passaggio. Le istanze di Adobe Campaign non sono multilingue: non è possibile passare da una lingua all’altra.

1. Fare clic su **[!UICONTROL Ok]** per confermare la dichiarazione dell&#39;istanza. Disconnettersi e rieseguire l&#39;accesso per dichiarare il database.

   >[!NOTE]
   >
   >L’istanza può essere creata dalla riga di comando. Per ulteriori informazioni, fare riferimento a [Comando linee](../../installation/using/command-lines.md).
