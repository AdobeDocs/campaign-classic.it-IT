---
title: Creazione di un’istanza e accesso
seo-title: Creazione di un’istanza e accesso
description: Creazione di un’istanza e accesso
seo-description: null
page-status-flag: never-activated
uuid: cb1620b3-f6e8-41dc-9142-ac0da65b6f8d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: initial-configuration
discoiquuid: c7395094-c635-45ab-8455-a050f7d16b64
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 4%

---


# Creazione di un’istanza e accesso{#creating-an-instance-and-logging-on}

Per creare una nuova istanza e  database Adobe Campaign, eseguite il seguente processo:

1. Creare la connessione.
1. Accedete per creare l’istanza correlata.
1. Creare e configurare il database.

>[!NOTE]
>
>Queste operazioni possono essere eseguite solo dall’identificatore **interno** . For more on this, refer to [Internal identifier](../../installation/using/campaign-server-configuration.md#internal-identifier).

Quando viene avviata la console di Adobe Campaign , potete accedere a una pagina di login.

Per creare una nuova istanza, effettuate le operazioni seguenti:

1. Fare clic sul collegamento nell&#39;angolo superiore destro dei campi delle credenziali per accedere alla finestra di configurazione della connessione. Questo collegamento può essere uno **[!UICONTROL New...]** o un nome di istanza esistente.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Fate clic su **[!UICONTROL Add > Connection]** e immettete l’etichetta e l’URL del server applicazione Adobe Campaign .

   ![](assets/s_ncs_install_define_connection_02.png)

1. Specificate una connessione al server  applicazione Adobe Campaign tramite un URL. Utilizzate un DNS o un alias del computer o il vostro indirizzo IP.

   Ad esempio, potete utilizzare il [`https://<machine>.<domain>.com`](https://machine) tipo URL.

   >[!CAUTION]
   >
   >Per l&#39;URL di connessione, utilizzate solo i seguenti caratteri: `[a-z]`, `[A-Z]`, `[0-9]` e trattini (-) o arresti completi.

1. Fate clic **[!UICONTROL Ok]** per confermare le impostazioni: ora potete iniziare con il processo di creazione dell&#39;istanza.
1. Nella **[!UICONTROL Connection settings]** finestra, immettete il login **interno** e la relativa password per collegarvi al server dell’applicazione Adobe Campaign . Una volta connessi, potete accedere alla procedura guidata di creazione dell&#39;istanza per dichiarare una nuova istanza
1. Nel **[!UICONTROL Name]** campo, immettete il nome **dell’** istanza. Poiché questo nome viene utilizzato per generare un file di configurazione **config-`<instance>`.xml** ed è utilizzato nei parametri della riga di comando per identificare l&#39;istanza, accertatevi di scegliere un nome breve senza caratteri speciali. Ad esempio: **eMarketing**.

   ![](assets/s_ncs_install_create_instance.png)

   Il nome dell’istanza aggiunta al nome del dominio non deve superare i 40 caratteri. Questo consente di limitare la dimensione delle intestazioni &quot;Message-ID&quot; e impedisce che i messaggi vengano considerati come spam, in particolare da strumenti come SpamAssassin.

1. Nei **[!UICONTROL DNS masks]** campi, immettete l&#39; **elenco delle maschere** DNS a cui deve essere associata l&#39;istanza. Il server Adobe Campaign  utilizza il nome host visualizzato nelle richieste HTTP per determinare quale istanza raggiungere.

   Il nome host è contenuto tra la stringa **https://** e il primo carattere barra **/** dell&#39;indirizzo del server.

   È possibile definire un elenco di valori separati da virgole.

   I caratteri ? e * caratteri possono essere utilizzati come caratteri jolly per sostituire uno o più caratteri (DNS, porte, ecc.). Ad esempio, il valore **demo*** funzionerà con &quot;https://demo&quot; come con &quot;https://demo:8080&quot; e anche con &quot;https://demo2&quot;.

   I nomi utilizzati devono essere definiti nel DNS. È inoltre possibile informare la corrispondenza tra un nome DNS e un indirizzo IP nel file **c:/windows/system32/drivers/etc/hosts** in Windows e nel file **/etc/hosts** in Linux. È pertanto necessario modificare le impostazioni di connessione per utilizzare questo nome DNS per connettersi all&#39;istanza scelta.

   Il server deve essere identificato con questo nome, in particolare per caricare le immagini nelle e-mail.

   Inoltre, il server deve essere in grado di connettersi a se stesso con questo nome e, se possibile, con un indirizzo di loopback - 127.0.0.1 -, in particolare per consentire l&#39;esportazione dei rapporti in formato PDF.

1. Nell&#39;elenco a **[!UICONTROL Language]** discesa, selezionate la lingua **dell&#39;** istanza: Inglese (USA), inglese (Regno Unito), francese o giapponese.

   Le differenze tra inglese americano e inglese britannico sono descritte in [questa sezione](../../platform/using/adobe-campaign-workspace.md#date-and-time).

   >[!CAUTION]
   >
   >Dopo questo passaggio non è possibile modificare la lingua dell&#39;istanza.  istanze Adobe Campaign non sono multilingue: non è possibile passare da una lingua a un&#39;altra.

1. Fate clic **[!UICONTROL Ok]** per confermare la dichiarazione dell&#39;istanza. Disconnettersi e tornare indietro per dichiarare il database.

   >[!NOTE]
   >
   >L&#39;istanza può essere creata dalla riga di comando. For more on this, refer to [Command lines](../../installation/using/command-lines.md).

