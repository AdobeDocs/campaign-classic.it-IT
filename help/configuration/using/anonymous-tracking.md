---
solution: Campaign Classic
product: campaign
title: Tracking anonimo
description: Tracking anonimo
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 6%

---


# Tracking anonimo{#anonymous-tracking}

 Adobe Campaign consente di collegare le informazioni di tracciamento Web raccolte a un destinatario quando questi naviga nel sito in modo anonimo. Quando un utente naviga nelle pagine con tag del sito Web, vengono raccolte le informazioni di ricerca, in modo che una volta che fa clic in un messaggio e-mail inviato da  Adobe Campaign, queste vengono identificate e le informazioni vengono automaticamente collegate.

>[!IMPORTANT]
>
>La configurazione del tracciamento anonimo su un sito Web può attivare la raccolta di una quantità significativa di registri di tracciamento, con un impatto sul funzionamento del database. Configuratelo con attenzione.\
>I registri di tracciamento vengono salvati nel database fino a quando i dati di tracciamento non vengono eliminati. Utilizzate la procedura guidata di distribuzione per configurare la frequenza di eliminazione. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../installation/using/deploying-an-instance.md#purging-data).

Per abilitare il tracciamento Web anonimo nell&#39;istanza, è necessario configurare i seguenti elementi:

* Il parametro **trackWebVisitors** dell&#39;elemento **redirection** dell&#39;elemento **serverConf.xml** del server di tracciamento deve essere impostato su &#39;**true**&#39;, per inserire un cookie permanente (**uuid230**) nei browser di utenti Internet sconosciuti che visitano il sito.
* La modalità **Anonymous Web Tracking** deve essere selezionata nella schermata di configurazione del tracciamento della distribuzione guidata.

   ![](assets/webtracking_anonymous_set.png)

* I moduli Web e i sondaggi devono essere pubblicati ed eseguiti sul server di tracciamento. L&#39;opzione corrispondente deve essere selezionata nella procedura guidata di distribuzione.

   ![](assets/webtracking_publication_set_for_webapps.png)

