---
product: campaign
title: Configurare l’interfaccia
description: Scopri come configurare l’interfaccia di Campaign
feature: Application Settings
role: Data Engineer, Developer
badge-v7: label="v7" type="Informative" tooltip="Applicabile a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
exl-id: 9f50f258-845e-4895-b1ef-b73744dea326
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---

# Configurare l’interfaccia{#configuring-the-interface}

Per visualizzare e dialogare con la nuova tabella dei destinatari nell’interfaccia di Adobe Campaign, effettua le seguenti operazioni:

* Crea un nuovo modulo per modificare il contenuto della nuova tabella dei destinatari.
* Immettere un nuovo tipo nella cartella della struttura di esplorazione.
* Crea una nuova applicazione web per accedere alla tabella personalizzata tramite la pagina Home di Adobe Campaign.

Adobe Campaign utilizza una variabile globale &quot;Nms_DefaultRcpSchema&quot; per la finestra di dialogo con il database dei destinatari predefinito (nms:recipient). Occorre pertanto modificare tale variabile.

1. Vai a **[!UICONTROL Administration>Platform>Options]** nodo dell&#39;explorer.
1. Modifica il valore del **Nms_DefaultRcpSchema** variabile con il nome dello schema che corrisponde alla tabella dei destinatari esterni (in questo caso: cus:individual).
1. Salva le modifiche.

## Creazione di un nuovo modulo {#creating-a-new-form-}

La creazione di un nuovo modulo consente di visualizzare e modificare i dati della tabella dei destinatari esterna.

>[!IMPORTANT]
>
>Il nome del modulo deve essere identico al nome dello schema a cui si riferisce.

1. Vai a **Administration > Configuration > Input forms** nodo dell&#39;explorer.
1. Crea un nuovo **xtk:form** tipo **modulo** file.
1. Descrivere tutti i campi di monitoraggio e i campi necessari a seconda del modello di tabella.

   >[!NOTE]
   >
   >Per ulteriori informazioni su **modulo** file di testo, fare riferimento a [questa pagina](../../configuration/using/identifying-a-form.md).

   Nel nostro esempio corrente, il **modulo** il file deve essere basato su **cus:individuale** e hanno quindi il seguente layout:

   ```
   <container colspan="2">
       <input xpath="@id"/>
       <static type="separator"/>
   </container>
   <container colcount="2">
       <input xpath="@lastName"/>
       <input xpath="@firstName"/>
       <input xpath="@email"/>
       <input xpath="@mobile"/>
   </container> 
   ```

1. Salva la creazione.

## Creazione di un nuovo tipo di cartella nella gerarchia di navigazione {#creating-a-new-type-of-folder-in-the-navigation-hierarchy}

1. Vai a **[!UICONTROL Administration>Configuration>Navigation hierarchies]** nodo.
1. Crea un nuovo **xtk:navtree** tipo **navtree** documento.
1. Descrivere tutti i campi di monitoraggio e i campi necessari a seconda del modello di tabella.

   >[!NOTE]
   >
   >Per ulteriori informazioni su **navtree** file di testo, fare riferimento a [questa pagina](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarchy).

   Nell&#39;esempio corrente, il **navtree** il file deve essere basato su **cus:individuale** e hanno quindi il seguente formato:

   ```
    <model name="root">
       <nodeModel img="nms:usergrp.png" label="My recipient table" name="cusindividual">
         <view name="listdet" schema="cus:individual" type="listdet">
           <columns>
             <node xpath="@id"/>
             <node xpath="@lastName"/>
             <node xpath="@firstName"/>
             <node xpath="@email"/>
             <node xpath="@mobile"/>
           </columns>
         </view>
       </nodeModel>
   </model>
   ```

1. Salva la creazione.
