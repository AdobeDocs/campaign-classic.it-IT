---
solution: Campaign Classic
product: campaign
title: Configurazione dell’interfaccia
description: Configurazione dell’interfaccia
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 2%

---


# Configurazione dell’interfaccia{#configuring-the-interface}

Per visualizzare e dialogare con la nuova tabella destinatari nell&#39;interfaccia  Adobe Campaign, procedere come segue:

* Creare un nuovo modulo per modificare il contenuto della nuova tabella destinataria.
* Immettete un nuovo tipo nella cartella della struttura ad albero di Esplora risorse.
* Create una nuova applicazione Web per accedere alla tabella personalizzata tramite la home page di  Adobe Campaign.

 Adobe Campaign utilizza una variabile globale &quot;Nms_DefaultRcpSchema&quot; per avviare una finestra di dialogo con il database del destinatario predefinito (nms:destinatario). Questa variabile deve pertanto essere modificata.

1. Passate al nodo **[!UICONTROL Administration>Platform>Options]** dell&#39;esploratore.
1. Modificare il valore della variabile **Nms_DefaultRcpSchema** con il nome dello schema che corrisponde alla tabella del destinatario esterno (in questo caso: cus:single).
1. Salvare le modifiche.

## Creazione di un nuovo modulo {#creating-a-new-form-}

La creazione di un nuovo modulo consente di visualizzare e modificare i dati della tabella del destinatario esterno.

>[!IMPORTANT]
>
>Il nome del modulo deve essere identico al nome dello schema interessato.

1. Passare al nodo **Amministrazione > Configurazione > Moduli di input** dell&#39;elenco di cartelle.
1. Creare un nuovo file **xtk:form** di tipo **form**.
1. Descrivere tutti i controlli e i campi necessari a seconda del modello di tabella.

   >[!NOTE]
   >
   >Per ulteriori informazioni sui file di tipo **form**, fare riferimento a [questa pagina](../../configuration/using/identifying-a-form.md).

   Nell&#39;esempio corrente, il file **form** deve essere basato sullo schema **cus:single** e pertanto avere il layout seguente:

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

1. Vai al nodo **[!UICONTROL Administration>Configuration>Navigation hierarchies]**.
1. Create un nuovo documento **xtk:navtree** di tipo **navtree**.
1. Descrivere tutti i controlli e i campi necessari a seconda del modello di tabella.

   >[!NOTE]
   >
   >Per ulteriori informazioni sui file di tipo **navtree**, fare riferimento a [questa pagina](../../configuration/using/about-navigation-hierarchy.md).

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

