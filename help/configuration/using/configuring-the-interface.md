---
product: campaign
title: Configurare l’interfaccia
description: Scopri come configurare l’interfaccia di Campaign
feature: Application Settings
role: Developer
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
exl-id: 9f50f258-845e-4895-b1ef-b73744dea326
TQID: https://experienceleague.adobe.com/KUwDwl9noj6RJa0wn6ZEVnCBRLdOUMoSTf-5b1PrH-g
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
role_v2: id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
subfeature_v2: []
source-git-commit: bb41e9407ab5853b0194bb325bbf3f17bc3ea232
workflow-type: tm+mt
source-wordcount: 297
ht-degree: 0%

---

# Configurare l’interfaccia{#configuring-the-interface}

Per visualizzare e dialogare con la nuova tabella dei destinatari nell’interfaccia di Adobe Campaign, effettua le seguenti operazioni:

* Crea un nuovo modulo per modificare il contenuto della nuova tabella dei destinatari.
* Immettere un nuovo tipo nella cartella della struttura di esplorazione.
* Crea una nuova applicazione web per accedere alla tabella personalizzata tramite la pagina Home di Adobe Campaign.

Adobe Campaign utilizza una variabile globale &quot;Nms_DefaultRcpSchema&quot; per la finestra di dialogo con il database dei destinatari predefinito (nms:recipient). Occorre pertanto modificare tale variabile.

1. Vai al nodo **[!UICONTROL Administration>Platform>Options]** dell&#39;Explorer.
1. Modificare il valore della variabile **Nms_DefaultRcpSchema** con il nome dello schema corrispondente alla tabella dei destinatari esterna (in questo caso: cus:individual).
1. Salva le modifiche.

## Creazione di un nuovo modulo {#creating-a-new-form-}

La creazione di un nuovo modulo consente di visualizzare e modificare i dati della tabella dei destinatari esterna.

>[!IMPORTANT]
>
>Il nome del modulo deve essere identico al nome dello schema a cui si riferisce.

1. Vai al nodo **Amministrazione > Configurazione > Moduli di input** dell&#39;Explorer.
1. Crea un nuovo file **form** di tipo **xtk:form**.
1. Descrivere tutti i campi di monitoraggio e i campi necessari a seconda del modello di tabella.

   >[!NOTE]
   >
   >Per ulteriori informazioni sui file di tipo **modulo**, vedere [questa pagina](../../configuration/using/identifying-a-form.md).

   Nell&#39;esempio corrente, il file **form** deve essere basato sullo schema **cus:individual** e quindi avere il seguente layout:

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

1. Passare al nodo **[!UICONTROL Administration>Configuration>Navigation hierarchies]**.
1. Crea un nuovo documento di tipo **xtk:navtree** **navtree**.
1. Descrivere tutti i campi di monitoraggio e i campi necessari a seconda del modello di tabella.

   Nell&#39;esempio corrente, il file **navtree** deve essere basato sullo schema **cus:individual** e quindi avere il seguente formato:

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
