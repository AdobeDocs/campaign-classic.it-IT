---
solution: Campaign Classic
product: campaign
title: Configurazione di più brand
description: Configurazione di più brand
audience: message-center
content-type: reference
topic-tags: instance-configuration
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 2%

---


# Configurazione di più brand{#configuring-multibranding}

Questa sezione descrive una soluzione per configurare gli URL di tracciamento e mirroring delle pagine per marchio, per i messaggi transazionali in  Adobe Campaign.

## Prerequisiti {#prerequisites}

* Tutti gli host devono essere aggiunti al file di configurazione dell&#39;istanza (`config-<instance>.xml`).
* A ogni marchio deve essere assegnato un sottodominio.
* Se il tracciamento Web viene effettuato su pagine HTTPS, è necessario disporre di un certificato HTTPS per tutti i marchi.

## Processo tipico {#typical-process}

Per configurare l&#39;attività di multibranding, è necessario configurare sia le istanze di esecuzione che l&#39;istanza di controllo. Nelle istanze di esecuzione, attenetevi alla procedura seguente:

1. Crea un account esterno per marchio.

   >[!NOTE]
   >
   >La creazione di un account esterno di tipo istanza di esecuzione viene presentata nella sezione Istanza [di](../../message-center/using/creating-a-shared-connection.md#control-instance) controllo.

1. Estendi lo schema nms:extAccount per aggiungere l’URL di tracciamento:

   ```
   <attribute advanced="true" desc="URL of the tracking servers" label="Tracking server URL"
   length="100" name="trackingURL" type="string"/>
   ```

   >[!NOTE]
   >
   >L&#39;estensione di uno schema esistente viene presentata nella sezione [Estensione di uno schema](../../configuration/using/extending-a-schema.md) .

1. Modificare il modulo nms:extAccount:

   ```
   <container label="Message domain branding" type="frame">
        <static type="help"> These parameters are used to override the DNS alias and addresses used during message delivery. When not populated, the values of the 'NmsServer_MirrorPageUrl' and 'NmsEmail_DefaultErrorAddr' options are used.</static>
        <input xpath="@mirrorURL"/>
        <input xpath="@trackingURL"/>
        <input img="nms:sendemail.png" menuId="deliveryMenuBuilder" type="scriptEdit">
               xpath="errorAddress"/>
      </container>
   ```

1. Modificate le opzioni NmsTracking_OpenFormula e NmsTracking_ClickFormula per utilizzare il conto esterno invece di un&#39;opzione globale.

   A questo scopo, sostituire:

   ```
   <%@ include option='NmsTracking_ServerUrl' %>
   ```

   con:

   ```
   <%@ value object="provider" xpath="@trackingURL" %>
   ```

   >[!IMPORTANT]
   >
   >Tali modifiche potrebbero causare conflitti durante l&#39;aggiornamento. Potrebbe essere necessario unire manualmente queste formule con la nuova versione.

Nell&#39;istanza di controllo, è necessario collegare i modelli di consegna e gli account esterni. A tal fine, è necessario:

1. Create un account esterno per marchio con lo stesso nome interno definito al punto 1.
1. Crea un modello di consegna predefinito per marchio.
1. Nel modello di consegna **[!UICONTROL Properties]** , impostare il ciclo sul conto esterno del marchio.

