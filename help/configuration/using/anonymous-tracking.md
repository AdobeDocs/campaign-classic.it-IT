---
title: Tracking anonimo
seo-title: Tracking anonimo
description: Tracking anonimo
seo-description: null
page-status-flag: never-activated
uuid: 21ba3657-eabf-4228-9fc0-e72712bf8fe7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 2d2c6ae9-4dba-4b82-a25e-eda65a49572d
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 7%

---


# Tracking anonimo{#anonymous-tracking}

 Adobe Campaign consente di collegare le informazioni di tracciamento Web raccolte a un destinatario quando questi naviga nel sito in modo anonimo. Quando un utente naviga nelle pagine con tag del sito Web, vengono raccolte le informazioni di ricerca, in modo che una volta che fa clic in un messaggio e-mail inviato da  Adobe Campaign, queste vengono identificate e le informazioni vengono automaticamente collegate.

>[!IMPORTANT]
>
>La configurazione del tracciamento anonimo su un sito Web può attivare la raccolta di una quantità significativa di registri di tracciamento, con un impatto sul funzionamento del database. Configuratelo con attenzione.\
>I registri di tracciamento vengono salvati nel database fino a quando i dati di tracciamento non vengono eliminati. Utilizzate la procedura guidata di distribuzione per configurare la frequenza di eliminazione. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../installation/using/deploying-an-instance.md#purging-data).

Per abilitare il tracciamento Web anonimo nell&#39;istanza, è necessario configurare i seguenti elementi:

* Il parametro **trackWebVisitors** dell’elemento **redirection** del file **serverConf.xml** del server di tracciamento deve essere impostato su &#39;**true**&#39;, per inserire un cookie permanente (**uuid230**) nei browser di utenti Internet sconosciuti che visitano il sito.
* La modalità **Anonymous Web Tracking** deve essere selezionata nella schermata di configurazione del tracciamento della distribuzione guidata.

   ![](assets/webtracking_anonymous_set.png)

* I moduli Web e i sondaggi devono essere pubblicati ed eseguiti sul server di tracciamento. L&#39;opzione corrispondente deve essere selezionata nella procedura guidata di distribuzione.

   ![](assets/webtracking_publication_set_for_webapps.png)

