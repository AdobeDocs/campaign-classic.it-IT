---
product: campaign
title: Tracciamento anonimo
description: Tracciamento anonimo
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
exl-id: f251eb21-0f3c-4b46-927a-57a3291e705f
source-git-commit: ee3d643e4ba607b3d7ca816eabf862b867d1f3f4
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 6%

---

# Tracciamento anonimo{#anonymous-tracking}

Adobe Campaign ti consente di collegare le informazioni di web tracking raccolte a un destinatario quando naviga sul tuo sito in modo anonimo. Quando un utente esplora le pagine con tag del sito web, vengono raccolte queste informazioni di navigazione, in modo che una volta fatto clic su un’e-mail inviata da Adobe Campaign, queste vengano identificate e le informazioni vengono automaticamente collegate.

>[!IMPORTANT]
>
>L’impostazione del tracciamento anonimo su un sito web può attivare la raccolta di una quantità significativa di log di tracciamento, con conseguente impatto sul funzionamento del database. Configura con attenzione.\
>I registri di tracciamento vengono salvati nel database fino a quando i dati di tracciamento non vengono eliminati. Utilizza la procedura guidata di distribuzione per configurare la frequenza di eliminazione. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../installation/using/deploying-an-instance.md#purging-data).

Per abilitare il tracciamento Web anonimo nell’istanza, è necessario configurare i seguenti elementi:

* Il parametro **trackWebVisitors** dell&#39;elemento **redirecting** del file **serverConf.xml** del server di tracciamento deve essere impostato su &#39;**true**&#39; per inserire un cookie permanente (**uuid230** nei browser di utenti Internet sconosciuti che visitano il sito.
* La modalità **Tracciamento Web anonimo** deve essere selezionata nella schermata di configurazione del tracciamento della procedura guidata di distribuzione.

   ![](assets/webtracking_anonymous_set.png)

* I moduli web devono essere pubblicati ed eseguiti sul server di tracciamento. L&#39;opzione corrispondente deve essere selezionata nella procedura guidata di distribuzione.

   ![](assets/webtracking_publication_set_for_webapps.png)
