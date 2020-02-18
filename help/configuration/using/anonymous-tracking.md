---
title: Tracciamento anonimo
seo-title: Tracciamento anonimo
description: Tracciamento anonimo
seo-description: null
page-status-flag: never-activated
uuid: 21ba3657-eabf-4228-9fc0-e72712bf8fe7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 2d2c6ae9-4dba-4b82-a25e-eda65a49572d
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# Tracciamento anonimo{#anonymous-tracking}

Adobe Campaign consente di collegare le informazioni di tracciamento Web raccolte a un destinatario quando questi sfoglia il sito in modo anonimo. Quando un utente esplora le pagine con tag del sito Web, vengono raccolte le informazioni di ricerca, in modo che una volta che fa clic in un messaggio e-mail inviato da Adobe Campaign, queste vengono identificate e le informazioni vengono automaticamente collegate.

>[!IMPORTANT]
>
>La configurazione del tracciamento anonimo su un sito Web può attivare la raccolta di una quantità significativa di registri di tracciamento, con un impatto sul funzionamento del database. Configuratelo con attenzione.\
>I registri di tracciamento vengono salvati nel database fino all’eliminazione dei dati di tracciamento. Utilizzate la procedura guidata di distribuzione per configurare la frequenza di eliminazione. For more on this, refer to [this section](../../installation/using/deploying-an-instance.md#purging-data).

Per abilitare il tracciamento Web anonimo nell&#39;istanza, è necessario configurare i seguenti elementi:

* Il parametro **trackWebVisitors** dell’elemento **redirection** del file **serverConf.xml** del server di tracciamento deve essere impostato su &#39;**true**&#39;, per inserire un cookie permanente (**uuid230**) nei browser di utenti Internet sconosciuti che visitano il sito.
* La modalità **Anonymous Web Tracking** deve essere selezionata nella schermata di configurazione del tracciamento della distribuzione guidata.

   ![](assets/webtracking_anonymous_set.png)

* I moduli Web e i sondaggi devono essere pubblicati ed eseguiti sul server di tracciamento. L&#39;opzione corrispondente deve essere selezionata nella procedura guidata di distribuzione.

   ![](assets/webtracking_publication_set_for_webapps.png)

