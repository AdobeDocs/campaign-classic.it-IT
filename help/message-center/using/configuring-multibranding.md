---
title: Configurazione di più brand
seo-title: Configurazione di più brand
description: Configurazione di più brand
seo-description: null
page-status-flag: never-activated
uuid: 61b4235c-da03-4da8-b14b-7ffb12c8d4c8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: instance-configuration
discoiquuid: 907d82c8-9262-4952-b8df-21144dd55824
translation-type: tm+mt
source-git-commit: 95dff2f3704e316e9ec9e454a8f3fb9835508ccd
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 3%

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

