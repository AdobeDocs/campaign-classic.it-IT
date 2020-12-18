---
solution: Campaign Classic
product: campaign
title: Pubblicazione di modelli
description: Pubblicazione modello messaggio transazionale
audience: message-center
content-type: reference
topic-tags: message-templates
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 2%

---


# Pubblicazione di modelli{#template-publication}

Una volta completato il modello di messaggio creato nell&#39;istanza di controllo, è possibile pubblicarlo su tutte le istanze di esecuzione. La pubblicazione consente di creare automaticamente due modelli di messaggio nell&#39;istanza di esecuzione, per l&#39;invio di messaggi collegati a eventi in tempo reale e batch.

>[!IMPORTANT]
>
>Ricorda di pubblicare il modello ogni volta che apporti modifiche per rendere effettive le modifiche durante la distribuzione dei messaggi transazionali.

>[!NOTE]
>
>Quando si pubblicano modelli di messaggi transazionali, le regole di tipologia vengono automaticamente pubblicate sulle istanze di esecuzione.

1. Nell&#39;istanza di controllo, passare alla cartella **[!UICONTROL Message Center > Transactional message templates]** della struttura.
1. Selezionate il modello da pubblicare sulle istanze di esecuzione.
1. Fai clic su **[!UICONTROL Publish]**.

   ![](assets/messagecenter_publish_model_008.png)

Una volta completata la pubblicazione, entrambi i modelli di messaggio da applicare agli eventi batch e di tipo in tempo reale vengono creati nella struttura dell&#39;istanza di produzione nella cartella **[!UICONTROL Administration > Production > Message Center Execution> Default > Transactional message templates]**.

![](assets/messagecenter_deployed_model_001.png)

>[!NOTE]
>
>Se si sostituisce un campo esistente del modello di messaggi transazionali, ad esempio l&#39;indirizzo del mittente, con un valore vuoto, il campo corrispondente nelle istanze di esecuzione non verrà aggiornato una volta che il messaggio transazionale sarà nuovamente pubblicato. Conterrà comunque il valore precedente. Tuttavia, se si aggiunge un valore non vuoto, il campo corrispondente verrà aggiornato normalmente dopo la pubblicazione successiva.
