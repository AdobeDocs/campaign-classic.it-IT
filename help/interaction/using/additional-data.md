---
solution: Campaign Classic
product: campaign
title: Dati aggiuntivi
description: Dati aggiuntivi
audience: interaction
content-type: reference
topic-tags: advanced-parameters
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '717'
ht-degree: 0%

---


# Dati aggiuntivi{#additional-data}

Durante una chiamata al motore di interazione, puoi trasferire informazioni aggiuntive contestuali. Questi dati possono provenire dai dati di destinazione memorizzati nella tabella di lavoro di un flusso di lavoro (canale in uscita) o dai dati delle chiamate inviate dal sito Web durante la chiamata (canale in ingresso). Potete utilizzare questi dati aggiuntivi nelle regole di idoneità, nella personalizzazione delle offerte e anche memorizzarli in una tabella delle proposte.

Per il canale in ingresso, può essere utile recuperare informazioni come la lingua del browser delle persone che consultano l&#39;offerta, o il nome dell&#39;agente del call center, ad esempio. Potete quindi utilizzare i dati di questa chiamata nelle regole di idoneità per presentare un&#39;offerta solo a coloro che visualizzano la pagina Web in francese o inglese.

In un flusso di lavoro di targeting (canale in uscita), potete utilizzare i dati di destinazione durante una chiamata al motore. Ad esempio, è possibile arricchire la destinazione con i dati provenienti da una transazione collegata a un destinatario o da un database esterno tramite FDA.

## Configurazione dati aggiuntivi {#additional-data-configuration}

È necessario estendere lo schema di interazione **** nms:collegato all&#39;ambiente e dichiarare l&#39;elenco dei campi aggiuntivi che verranno utilizzati durante una chiamata al motore di interazione. Quando si crea la regola di idoneità o si personalizza un&#39;offerta, questi campi saranno accessibili dal nodo **Interazione** (fare riferimento a [Utilizzo di dati](#using-additional-data)aggiuntivi).

Per il canale in entrata, devi aggiungere i campi dati della chiamata al nodo **Interaction** .

```
<element label="Interactions" labelSingular="Interaction" name="interaction">
  <attribute label="Navigation language" name="navigationLanguage" type="string"/>
</element>
```

>[!NOTE]
>
>Le raccolte XML sono supportate nel canale in entrata, ma i collegamenti ad altri schemi non lo sono.

Per il canale in uscita, devi aggiungere un elemento **targetData** contenente i campi aggiuntivi nel nodo **Interaction** .

```
<element label="Interactions" labelSingular="Interaction" name="interaction">
  <element name="targetData">
    <attribute label="Date of last transaction" name="lastTransactionDate" type="datetime"/>
  </element>
</element>
```

>[!NOTE]
>
>Le raccolte non sono supportate per il canale in uscita. Tuttavia, potete creare collegamenti ad altri schemi.

Se si desidera memorizzare questi dati nella tabella delle proposizioni, è inoltre necessario estendere lo schema **nms:propositionRcp** e dichiarare questi campi.

```
<element label="Recipient offer propositions" labelSingular="Recipient offer proposition" name="propositionRcp">
  <attribute label="Last transaction date" name="lastTransactionDate" type="datetime"/>
  <attribute label="Navigation language" name="navigationLanguage" type="string"/>
</element>
```

## Implementazione di dati aggiuntivi {#additional-data-implementation}

### Canale di input (pagina Web) {#input-channel--web-page-}

Per trasferire dati aggiuntivi quando si chiama il motore, è necessario aggiungere la variabile **interactiveGlobalCtx** al codice JavaScript della pagina Web. Inserire il nodo **Interazione** contenente i dati della chiamata in questa variabile. È necessario rispettare la stessa struttura xml presente nello schema **nms:interactive** . Consultare: [Configurazione](#additional-data-configuration)dati aggiuntiva.

```
interactionGlobalCtx = "<interaction navigationLanguage='"+myLanguage+"'/>";
```

### Canale di uscita {#output-channel}

È necessario creare un flusso di lavoro di targeting che carichi dati aggiuntivi nella tabella di lavoro rispettando la stessa struttura xml e gli stessi nomi interni come nello schema **nms:interactive** . Consultare: [Configurazione](#additional-data-configuration)dati aggiuntiva.

## Utilizzo di dati aggiuntivi {#using-additional-data}

### Regole di ammissibilità {#eligibility-rules}

Potete utilizzare i dati aggiuntivi nelle regole di idoneità per offerte, categorie e pesi.

Ad esempio, potete scegliere di presentare l’offerta solo alle persone che visualizzano la pagina in inglese.

![](assets/ita_calldata_query.png)

>[!NOTE]
>
>È necessario limitare la regola sui canali per i quali i dati sono definiti. Nel nostro esempio, stiamo limitando la regola sul canale Web in ingresso (**[!UICONTROL Taken into account if]** campo).

### Personalizzazione {#personalization}

Potete inoltre utilizzare questi dati aggiuntivi durante la personalizzazione di un&#39;offerta. Ad esempio, è possibile aggiungere una condizione per il linguaggio di navigazione

![](assets/ita_calldata_perso.png)

>[!NOTE]
>
>Devi limitare la personalizzazione sui canali per i quali i dati sono definiti. Nel nostro esempio, stiamo limitando la regola sul canale web in entrata.

Se avete personalizzato un&#39;offerta utilizzando dati aggiuntivi, per impostazione predefinita questi dati non vengono visualizzati nell&#39;anteprima perché non sono disponibili nel database. Nella **[!UICONTROL Example of call data]** scheda dell&#39;ambiente, è necessario aggiungere esempi di valori da utilizzare nell&#39;anteprima. Rispettare la stessa struttura xml presente nell&#39;estensione **nms:interactive** schema. Per ulteriori informazioni, consulta Configurazione [dati](#additional-data-configuration)aggiuntivi.

![](assets/ita_calldata_preview.png)

Durante l&#39;anteprima, fate clic **[!UICONTROL Content personalization options for the preview]** e selezionate un valore nel **[!UICONTROL Call data]** campo.

![](assets/ita_calldata_preview2.png)

### Archiviazione {#storage}

Durante una chiamata al motore, potete memorizzare dati aggiuntivi nella tabella delle proposte per arricchire il database. Questi dati possono essere utilizzati, ad esempio nei rapporti, nei calcoli sul ROI o per processi successivi.

>[!NOTE]
>
>È necessario estendere lo schema **nms:propositionRcp** e dichiarare i campi che conterranno i dati da memorizzare. Per ulteriori informazioni: [Configurazione](#additional-data-configuration)dati aggiuntiva.

Nello spazio delle offerte, andate alla **[!UICONTROL Storage]** scheda e fate clic sul **[!UICONTROL Add]** pulsante.

Nella **[!UICONTROL Storage path]** colonna, selezionare il campo di memorizzazione nella tabella delle proposte. Nella **[!UICONTROL Expression]** colonna, selezionare il campo aggiuntivo nel **[!UICONTROL Interaction]** nodo.

È possibile recuperare i dati delle chiamate quando la proposta viene generata o quando viene accettata (quando la persona fa clic sull&#39;offerta).

![](assets/ita_calldata_storage.png)

