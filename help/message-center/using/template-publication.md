---
solution: Campaign Classic
product: campaign
title: Pubblicazione di modelli
description: Pubblicazione modello messaggio transazionale
audience: message-center
content-type: reference
topic-tags: message-templates
translation-type: tm+mt
source-git-commit: 02dee9c4cc03784ccc20f147f816798248bd10f2
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 2%

---


# Pubblicazione di modelli{#template-publication}

Al termine del modello di messaggio creato nell’istanza di controllo, potete pubblicarlo. Questo processo verrà anche pubblicato su tutte le istanze di esecuzione.

La pubblicazione consente di creare automaticamente due modelli di messaggio per le istanze di esecuzione, per inviare messaggi collegati a eventi in tempo reale e batch.

>[!NOTE]
>
>Quando si pubblicano modelli di messaggi transazionali, anche le regole di tipologia vengono pubblicate automaticamente sulle istanze di esecuzione.

>[!IMPORTANT]
>
>Ogni volta che apporti modifiche a un modello, accertati di pubblicarlo nuovamente affinché tali modifiche siano effettive durante la distribuzione dei messaggi transazionali.

1. Nell&#39;istanza di controllo, passare alla cartella **[!UICONTROL Message Center > Transactional message templates]** della struttura.
1. Selezionate il modello da pubblicare sulle istanze di esecuzione.
1. Fai clic su **[!UICONTROL Publish]**.

   ![](assets/messagecenter_publish_model_008.png)

Una volta completata la pubblicazione, entrambi i modelli di messaggio da applicare agli eventi batch e di tipo in tempo reale vengono creati nella struttura dell&#39;istanza di produzione nella cartella **[!UICONTROL Administration > Production > Message Center Execution> Default > Transactional message templates]**.

![](assets/messagecenter_deployed_model_001.png)

Dopo la pubblicazione di un modello, se viene attivato l&#39;evento corrispondente, l&#39;istanza di esecuzione riceverà l&#39;evento, lo collegherà al modello transazionale e invierà il messaggio transazionale corrispondente a ciascun destinatario.

>[!NOTE]
>
>Se si sostituisce un campo esistente del modello di messaggi transazionali, ad esempio l&#39;indirizzo del mittente, con un valore vuoto, il campo corrispondente nelle istanze di esecuzione non verrà aggiornato una volta che il messaggio transazionale sarà nuovamente pubblicato. Conterrà comunque il valore precedente.
>
>Tuttavia, se si aggiunge un valore non vuoto, il campo corrispondente verrà aggiornato normalmente dopo la pubblicazione successiva.
