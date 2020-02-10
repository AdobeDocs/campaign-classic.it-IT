---
title: Implementazione
seo-title: Implementazione
description: Implementazione
seo-description: null
page-status-flag: never-activated
uuid: 12b5fbbf-fe0d-4598-8845-f7b8ee7672c3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: use-case
discoiquuid: ac1c0a00-41ef-4cc2-bb51-2808ef400bb1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Implementazione{#implementation}

Ecco un diagramma con i diversi passaggi coinvolti in questo scenario.

![](assets/message-center-uc1.png)

Innanzitutto, iniziare progettando l&#39;allegato. Consultate questo [articolo](../../delivery/using/attaching-files.md#attach-a-personalized-file). Questo consente di allegare i file a un&#39;e-mail, anche se non sono ospitati nell&#39;istanza di esecuzione.

Potete inviare le e-mail tramite un trigger di messaggio SOAP. Per ulteriori informazioni sulle richieste SOAP, vedere la descrizione [dell&#39;](../../message-center/using/event-description.md)evento. Nella chiamata SOAP è presente un parametro URL (attachmentURL).

Durante la progettazione del messaggio e-mail, fate clic su **[!UICONTROL Attachment]** . Nella **[!UICONTROL Attachment definition]** schermata, immettere il parametro SOAP attachment:

```
<%= rtEvent.ctx.attachementUrl %>
```

Quando il messaggio viene elaborato/distribuito, il sistema riceve il file dalla posizione remota (server di terze parti) e lo allega al singolo messaggio.

Poiché questo parametro può essere una variabile, deve accettare la variabile URL remota completa del file, inviata tramite la chiamata SOAP.

![](assets/message-center-uc2.png)

