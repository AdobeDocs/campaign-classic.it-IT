---
title: Creazione del contenuto del messaggio
seo-title: Creazione del contenuto del messaggio
description: Creazione del contenuto del messaggio
seo-description: null
page-status-flag: never-activated
uuid: 4ee013fc-fba2-4120-b796-dd4008000ea9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: message-templates
discoiquuid: 1f420652-c9af-4a49-8d5c-a640e960aced
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 4%

---


# Creazione del contenuto del messaggio{#creating-message-content}

La definizione del contenuto dei messaggi transazionali è la stessa utilizzata per le consegne regolari in  Adobe Campaign. Ad esempio, per la consegna tramite e-mail potete creare contenuto in formato HTML o testo, aggiungere allegati o personalizzare l&#39;oggetto di consegna. Per ulteriori informazioni, consulta il capitolo sulla consegna [delle e-](../../delivery/using/about-email-channel.md)mail.

>[!CAUTION]
>
>Le immagini incluse nel messaggio devono essere accessibili al pubblico.  Adobe Campaign non fornisce alcun meccanismo di caricamento delle immagini per i messaggi transazionali.\
>A differenza di JSSP o webApp, non `<%=` dispone di escape predefinito.
>
>In questo caso, è necessario eseguire correttamente l&#39;escape di ogni dato proveniente dall&#39;evento. Questa escape dipende dalla modalità di utilizzo del campo. Ad esempio, all’interno di un URL, utilizzate encodeURIComponent. Per essere visualizzato nell’HTML, è possibile utilizzare escapeXMLString.

Una volta definito il contenuto del messaggio, potete integrare le informazioni sull&#39;evento nel corpo del messaggio e personalizzarlo. Le informazioni sull’evento vengono inserite nel corpo del testo grazie ai tag di personalizzazione.

![](assets/messagecenter_create_content_001.png)

* Tutti i campi di personalizzazione provengono dal payload.
* È possibile fare riferimento a uno o più blocchi di personalizzazione in un messaggio transazionale. Il contenuto del blocco verrà aggiunto al contenuto del recapito durante la pubblicazione nell&#39;istanza di esecuzione.

Per inserire tag di personalizzazione nel corpo di un messaggio e-mail, effettua i seguenti passaggi:

1. Nel modello del messaggio, fai clic sulla scheda che corrisponde al formato dell&#39;e-mail (HTML o testo).
1. Immettere il corpo del messaggio.
1. Nel corpo del testo, inserite il tag utilizzando i **[!UICONTROL Real time events>Event XML]** menu.

   ![](assets/messagecenter_create_custo_002.png)

1. Compilate il tag utilizzando la sintassi seguente: **nome** dell&#39;elemento.@nome **** attributo come mostrato di seguito.

   ![](assets/messagecenter_create_custo_003.png)

