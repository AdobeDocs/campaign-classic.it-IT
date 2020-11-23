---
solution: Campaign Classic
product: campaign
title: Dati di personalizzazione
description: Dati di personalizzazione
audience: message-center
content-type: reference
topic-tags: message-templates
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 3%

---


# Dati di personalizzazione{#personalization-data}

È possibile utilizzare i dati nel modello di messaggio per testare la personalizzazione dei messaggi transazionali. Questa funzionalità viene utilizzata per generare un&#39;anteprima o inviare una prova. Se installate il modulo **Consegne** , questi dati consentono di visualizzare un rendering dei messaggi per i vari provider di accesso a Internet (rendering **Inbox**: per ulteriori informazioni, consultare [questa sezione](../../delivery/using/inbox-rendering.md)).

Lo scopo di questi dati è quello di verificare i messaggi prima della consegna finale. Questi messaggi non coincidono con i dati effettivi che devono essere elaborati dal Centro messaggi. Tuttavia, la struttura XML deve essere identica a quella dell&#39;evento memorizzato nell&#39;istanza di esecuzione, come illustrato di seguito.

![](assets/messagecenter_create_custo_006.png)

Queste informazioni consentono di personalizzare il contenuto dei messaggi utilizzando i tag di personalizzazione (per ulteriori informazioni, vedere [Creazione di contenuti](../../message-center/using/creating-message-content.md)dei messaggi).

1. Nel modello del messaggio, fai clic sulla **[!UICONTROL Seed addresses]** scheda.
1. Nel contenuto dell&#39;evento, immettete le informazioni di prova in formato XML.

   ![](assets/messagecenter_create_custo_001.png)
