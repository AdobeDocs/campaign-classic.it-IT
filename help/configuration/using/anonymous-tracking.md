---
product: campaign
title: Tracciamento anonimo
description: Scopri come configurare il tracciamento anonimo
exl-id: f251eb21-0f3c-4b46-927a-57a3291e705f
source-git-commit: 3997412f14666fa61bf71d0f0a0653f5cc042e19
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 5%

---

# Tracciamento anonimo{#anonymous-tracking}

![](../../assets/v7-only.svg)

Adobe Campaign ti consente di collegare le informazioni di web tracking raccolte a un destinatario quando naviga sul tuo sito in modo anonimo. Quando un utente esplora le pagine con tag del sito web, vengono raccolte queste informazioni di navigazione, in modo che una volta fatto clic su un’e-mail inviata da Adobe Campaign, queste vengano identificate e le informazioni vengono automaticamente collegate.

>[!IMPORTANT]
>
>L’impostazione del tracciamento anonimo su un sito web può attivare la raccolta di una quantità significativa di log di tracciamento, con conseguente impatto sul funzionamento del database. Configura con attenzione.\
>I registri di tracciamento vengono salvati nel database fino a quando i dati di tracciamento non vengono eliminati. Utilizza la procedura guidata di distribuzione per configurare la frequenza di eliminazione. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../installation/using/deploying-an-instance.md#purging-data).

Per abilitare il tracciamento Web anonimo nell’istanza, è necessario configurare i seguenti elementi:

* La **trackWebVisitors** del **reindirizzamento** elemento **serverConf.xml** il file del server di tracciamento deve essere impostato su &#39;**true** per inserire un cookie permanente (**uuid230**) nei browser di utenti Internet sconosciuti che visitano il sito.
* La **Tracciamento web anonimo** deve essere selezionata nella schermata di configurazione del tracking della procedura guidata di distribuzione.

   ![](assets/webtracking_anonymous_set.png)

* I moduli web devono essere pubblicati ed eseguiti sul server di tracciamento. L&#39;opzione corrispondente deve essere selezionata nella procedura guidata di distribuzione.

   ![](assets/webtracking_publication_set_for_webapps.png)
