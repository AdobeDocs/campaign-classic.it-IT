---
product: campaign
title: Tracciamento anonimo
description: Scopri come impostare il tracciamento anonimo
feature: Configuration, Instance Settings
role: Developer
exl-id: f251eb21-0f3c-4b46-927a-57a3291e705f
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 5%

---

# Tracciamento anonimo{#anonymous-tracking}

Adobe Campaign consente di collegare le informazioni di tracciamento Web raccolte a un destinatario che naviga nel sito in modo anonimo. Quando un utente esplora le pagine con tag del sito web, vengono raccolte queste informazioni di navigazione, in modo che, una volta fatto clic in un’e-mail inviata da Adobe Campaign, vengono identificate e le informazioni vengono automaticamente collegate.

>[!IMPORTANT]
>
>L’impostazione del tracciamento anonimo su un sito web può attivare la raccolta di una quantità significativa di registri di tracciamento, influendo quindi sul funzionamento del database. Configura con attenzione.\
>I registri di tracciamento vengono salvati nel database fino a quando i dati di tracciamento non vengono eliminati. Utilizza la procedura guidata di distribuzione per configurare la frequenza di eliminazione. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../installation/using/deploying-an-instance.md#purging-data).

Per abilitare il tracciamento web anonimo nell’istanza, è necessario configurare i seguenti elementi:

* Il parametro **trackWebVisitors** dell&#39;elemento **redirection** del file **serverConf.xml** del server di tracciamento deve essere impostato su &#39;**true**&#39; per inserire un cookie permanente (**uuid230**) nei browser di utenti Internet sconosciuti che visitano il sito.
* La modalità **Tracciamento Web anonimo** deve essere selezionata nella schermata di configurazione del tracciamento della distribuzione guidata.

  ![](assets/webtracking_anonymous_set.png)

* I moduli web devono essere pubblicati ed eseguiti sul server di tracciamento. L&#39;opzione corrispondente deve essere selezionata nella procedura guidata di distribuzione.

  ![](assets/webtracking_publication_set_for_webapps.png)
