---
solution: Campaign Classic
product: campaign
title: Configurazione dell’interfaccia
description: Configurazione dell’interfaccia
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
exl-id: 9f50f258-845e-4895-b1ef-b73744dea326
translation-type: tm+mt
source-git-commit: d7eabfbebf016d2632d95d34a5b36719ccc1d88a
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 2%

---

# Configurazione dell’interfaccia{#configuring-the-interface}

Per visualizzare e dialogare con la nuova tabella dei destinatari nell’interfaccia di Adobe Campaign, procedi come segue:

* Crea un nuovo modulo per modificare il contenuto della nuova tabella dei destinatari.
* Immettere un nuovo tipo nella cartella della struttura ad albero dell&#39;elenco di cartelle.
* Crea una nuova applicazione web per accedere alla tabella personalizzata tramite la home page di Adobe Campaign.

Adobe Campaign utilizza una variabile globale &quot;Nms_DefaultRcpSchema&quot; per aprire una finestra di dialogo con il database dei destinatari predefinito (nms:recipient). Questa variabile deve pertanto essere modificata.

1. Passa al nodo **[!UICONTROL Administration>Platform>Options]** dell&#39;esploratore.
1. Modifica il valore della variabile **Nms_DefaultRcpSchema** con il nome dello schema che corrisponde alla tabella dei destinatari esterni (in questo caso: cus:individuale).
1. Salva le modifiche.

## Creazione di un nuovo modulo {#creating-a-new-form-}

La creazione di un nuovo modulo consente di visualizzare e modificare i dati della tabella dei destinatari esterna.

>[!IMPORTANT]
>
>Il nome del modulo deve essere identico al nome dello schema interessato.

1. Vai al nodo **Amministrazione > Configurazione > Moduli di input** dell&#39;esploratore.
1. Crea un nuovo file **xtk:form** di tipo **form**.
1. Descrivere tutti i controlli e i campi necessari a seconda del modello di tabella.

   >[!NOTE]
   >
   >Per ulteriori informazioni sui file di tipo **form**, consulta [questa pagina](../../configuration/using/identifying-a-form.md).

   Nel nostro esempio corrente, il file **form** deve essere basato sullo schema **cus:Singolo** e quindi avere il seguente layout:

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

1. Passa al nodo **[!UICONTROL Administration>Configuration>Navigation hierarchies]** .
1. Crea un nuovo documento di tipo **xtk:navtree** **navtree**.
1. Descrivere tutti i controlli e i campi necessari a seconda del modello di tabella.

   >[!NOTE]
   >
   >Per ulteriori informazioni sui file di tipo **navtree**, consulta [questa pagina](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarchy).

   Nell&#39;esempio corrente, il file **navtree** deve essere basato sullo schema **cus:Singolo** e quindi avere il seguente modulo:

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
