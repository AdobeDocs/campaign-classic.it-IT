---
product: campaign
title: Tracciamento anonimo
description: Scopri come impostare il tracciamento anonimo
feature: Configuration, Instance Settings
role: Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
exl-id: f251eb21-0f3c-4b46-927a-57a3291e705f
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 8%

---

# Tracciamento anonimo{#anonymous-tracking}

Adobe Campaign consente di collegare le informazioni di tracciamento Web raccolte a un destinatario che naviga nel sito in modo anonimo. Quando un utente esplora le pagine con tag del sito web, vengono raccolte queste informazioni di navigazione, in modo che, una volta fatto clic in un’e-mail inviata da Adobe Campaign, vengono identificate e le informazioni vengono automaticamente collegate.

>[!IMPORTANT]
>
>L’impostazione del tracciamento anonimo su un sito web può attivare la raccolta di una quantità significativa di registri di tracciamento, influendo quindi sul funzionamento del database. Configura con attenzione.\
>I registri di tracciamento vengono salvati nel database fino a quando i dati di tracciamento non vengono eliminati. Utilizza la procedura guidata di distribuzione per configurare la frequenza di eliminazione. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../installation/using/deploying-an-instance.md#purging-data).

Per abilitare il tracciamento web anonimo nell’istanza, è necessario configurare i seguenti elementi:

* Il **trackWebVisitors** parametro di **reindirizzamento** elemento del **serverConf.xml** il file del server di tracciamento deve essere impostato su &#39;**true**&#39;, per inserire un cookie permanente (**uuid230**) nei browser di utenti Internet sconosciuti che visitano il sito.
* Il **Tracciamento web anonimo** la modalità deve essere selezionata nella schermata di configurazione del tracciamento della procedura guidata di distribuzione.

  ![](assets/webtracking_anonymous_set.png)

* I moduli web devono essere pubblicati ed eseguiti sul server di tracciamento. L&#39;opzione corrispondente deve essere selezionata nella procedura guidata di distribuzione.

  ![](assets/webtracking_publication_set_for_webapps.png)
