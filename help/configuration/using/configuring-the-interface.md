---
title: Configurazione dell'interfaccia
seo-title: Configurazione dell'interfaccia
description: Configurazione dell'interfaccia
seo-description: null
page-status-flag: never-activated
uuid: 101ba02f-da43-4dcc-b9ff-6e5ca848fc5d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: 8fb9ff23-17a7-4425-9195-738d6fd914dc
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Configurazione dell&#39;interfaccia{#configuring-the-interface}

Per visualizzare e dialogare con la nuova tabella destinatari nell&#39;interfaccia di Adobe Campaign, effettua i seguenti passaggi:

* Creare un nuovo modulo per modificare il contenuto della nuova tabella destinataria.
* Immettete un nuovo tipo nella cartella della struttura ad albero di Esplora risorse.
* Crea una nuova applicazione Web per accedere alla tabella personalizzata tramite la home page di Adobe Campaign.

Adobe Campaign utilizza una variabile globale &quot;Nms_DefaultRcpSchema&quot; per dialogare con il database dei destinatari predefinito (nms:destinatario). Questa variabile deve pertanto essere modificata.

1. Passate al **[!UICONTROL Administration>Platform>Options]** nodo dell&#39;esploratore.
1. Modificare il valore della variabile **Nms_DefaultRcpSchema** con il nome dello schema che corrisponde alla tabella del destinatario esterno (in questo caso: cus:single).
1. Salvare le modifiche.

## Creazione di un nuovo modulo {#creating-a-new-form-}

La creazione di un nuovo modulo consente di visualizzare e modificare i dati della tabella del destinatario esterno.

>[!CAUTION]
>
>Il nome del modulo deve essere identico al nome dello schema interessato.

1. Andate al nodo **Amministrazione > Configurazione > Moduli** di input dell&#39;elenco di esplorazione.
1. Creare un nuovo file **xtk:form** type **form** .
1. Descrivere tutti i controlli e i campi necessari a seconda del modello di tabella.

   >[!NOTE]
   >
   >Per ulteriori informazioni sui file dei tipi di **modulo** , consultare [questa pagina](../../configuration/using/identifying-a-form.md).

   Nell&#39;esempio corrente, il file del **modulo** deve essere basato sullo schema **cus:single** e pertanto avere il layout seguente:

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

1. Salvate la creazione.

## Creazione di un nuovo tipo di cartella nella gerarchia di navigazione {#creating-a-new-type-of-folder-in-the-navigation-hierarchy}

1. Vai al **[!UICONTROL Administration>Configuration>Navigation hierarchies]** nodo.
1. Create un nuovo documento **xtk:navtree** type **navtree** .
1. Descrivere tutti i controlli e i campi necessari a seconda del modello di tabella.

   >[!NOTE]
   >
   >Per ulteriori informazioni sui file di **tipo navtree** , consultare [questa pagina](../../configuration/using/about-navigation-hierarchy.md).

   Nell&#39;esempio corrente, il file **navtree** deve essere basato sullo schema **cus:single** e pertanto avere il seguente modulo:

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

1. Salvate la creazione.

