---
product: campaign
title: Dati aggiuntivi
description: Dati aggiuntivi
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: 01adb584-5308-4d41-a6f1-223a97efa10f
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '717'
ht-degree: 0%

---

# Dati aggiuntivi{#additional-data}

Durante una chiamata al motore di interazione, puoi trasferire informazioni aggiuntive contestuali. Questi dati possono provenire dai dati di destinazione memorizzati nella tabella di lavoro di un flusso di lavoro (canale in uscita) o dai dati di chiamata inviati dal sito web durante la chiamata (canale in entrata). Puoi utilizzare questi dati aggiuntivi nelle regole di idoneità, nella personalizzazione delle offerte e anche memorizzarli in una tabella di proposte.

Per il canale in entrata, può essere utile recuperare informazioni come la lingua del browser delle persone che consultano l’offerta o il nome dell’agente del call center, ad esempio. Puoi quindi utilizzare i dati di questa chiamata nelle regole di idoneità per presentare un’offerta solo alle persone che visualizzano la pagina web in francese o inglese.

In un flusso di lavoro di targeting (canale in uscita), puoi utilizzare i dati di destinazione durante una chiamata al motore. Ad esempio, puoi arricchire il target con i dati provenienti da una transazione collegata al destinatario o da un database esterno tramite l’FDA.

## Configurazione dati aggiuntivi {#additional-data-configuration}

È necessario estendere lo schema **nms:relation** collegato all&#39;ambiente e dichiarare l&#39;elenco dei campi aggiuntivi che verranno utilizzati durante una chiamata al motore di interazione. Durante la creazione della regola di idoneità o la personalizzazione di un&#39;offerta, questi campi diventeranno accessibili dal nodo **Interazione** (consulta [Utilizzo di dati aggiuntivi](#using-additional-data)).

Per il canale in entrata, devi aggiungere i campi dei dati della chiamata nel nodo **Interaction** .

```
<element label="Interactions" labelSingular="Interaction" name="interaction">
  <attribute label="Navigation language" name="navigationLanguage" type="string"/>
</element>
```

>[!NOTE]
>
>Le raccolte XML sono supportate sul canale in entrata, ma i collegamenti ad altri schemi non lo sono.

Per il canale in uscita, devi aggiungere un elemento **targetData** contenente i campi aggiuntivi nel nodo **Interazione** .

```
<element label="Interactions" labelSingular="Interaction" name="interaction">
  <element name="targetData">
    <attribute label="Date of last transaction" name="lastTransactionDate" type="datetime"/>
  </element>
</element>
```

>[!NOTE]
>
>Le raccolte non sono supportate per il canale in uscita. Tuttavia, puoi creare collegamenti ad altri schemi.

Se desideri memorizzare questi dati nella tabella delle proposte, devi anche estendere lo schema **nms:propositionRcp** e dichiarare questi campi.

```
<element label="Recipient offer propositions" labelSingular="Recipient offer proposition" name="propositionRcp">
  <attribute label="Last transaction date" name="lastTransactionDate" type="datetime"/>
  <attribute label="Navigation language" name="navigationLanguage" type="string"/>
</element>
```

## Implementazione di dati aggiuntivi {#additional-data-implementation}

### Canale di input (pagina web) {#input-channel--web-page-}

Per trasferire dati aggiuntivi durante la chiamata al motore, devi aggiungere la variabile **actionGlobalCtx** nel codice JavaScript della pagina web. Inserisci in questa variabile il nodo **Interaction** contenente i dati della chiamata . È necessario rispettare la stessa struttura xml presente nello schema **nms:action**. Fai riferimento a: [Configurazione dati aggiuntivi](#additional-data-configuration).

```
interactionGlobalCtx = "<interaction navigationLanguage='"+myLanguage+"'/>";
```

### Canale di uscita {#output-channel}

È necessario creare un flusso di lavoro di targeting che carichi dati aggiuntivi nella tabella di lavoro rispettando la stessa struttura xml e gli stessi nomi interni dello schema **nms:relation**. Fai riferimento a: [Configurazione dati aggiuntivi](#additional-data-configuration).

## Utilizzo di dati aggiuntivi {#using-additional-data}

### Regole di idoneità {#eligibility-rules}

Puoi utilizzare i dati aggiuntivi nelle regole di idoneità per offerte, categorie e pesi.

Ad esempio, puoi scegliere di presentare l’offerta solo alle persone che visualizzano la pagina in inglese.

![](assets/ita_calldata_query.png)

>[!NOTE]
>
>Devi limitare la regola sui canali per i quali sono definiti i dati. Nel nostro esempio, limitiamo la regola sul canale web in entrata (**[!UICONTROL Taken into account if]** campo ).

### Personalizzazione {#personalization}

Puoi inoltre utilizzare questi dati aggiuntivi durante la personalizzazione di un’offerta. Ad esempio, puoi aggiungere una condizione per il linguaggio di navigazione

![](assets/ita_calldata_perso.png)

>[!NOTE]
>
>Devi limitare la personalizzazione sui canali per i quali i dati sono definiti. Nel nostro esempio, limitiamo la regola sul canale web in entrata.

Se hai personalizzato un’offerta utilizzando dati aggiuntivi, questi dati non verranno visualizzati nell’anteprima per impostazione predefinita perché non sono disponibili nel database. Nella scheda **[!UICONTROL Example of call data]** dell’ambiente è necessario aggiungere esempi di valori da utilizzare nell’anteprima. Rispetta la stessa struttura xml presente nell&#39;estensione dello schema **nms:relation**. Per ulteriori informazioni, consulta [Configurazione dati aggiuntivi](#additional-data-configuration).

![](assets/ita_calldata_preview.png)

Durante l&#39;anteprima, fai clic su **[!UICONTROL Content personalization options for the preview]** e seleziona un valore nel campo **[!UICONTROL Call data]** .

![](assets/ita_calldata_preview2.png)

### Storage {#storage}

Durante una chiamata al motore, puoi memorizzare dati aggiuntivi nella tabella delle proposte per arricchire il database. Questi dati possono essere utilizzati, ad esempio nei rapporti, nei calcoli sul ROI o per processi successivi.

>[!NOTE]
>
>È necessario estendere lo schema **nms:propositionRcp** e dichiarare i campi che conterranno i dati da memorizzare. Per ulteriori informazioni: [Configurazione dati aggiuntivi](#additional-data-configuration).

Nello spazio di offerta, vai alla scheda **[!UICONTROL Storage]** e fai clic sul pulsante **[!UICONTROL Add]** .

Nella colonna **[!UICONTROL Storage path]** , seleziona il campo di archiviazione nella tabella delle proposte. Nella colonna **[!UICONTROL Expression]** , seleziona il campo aggiuntivo nel nodo **[!UICONTROL Interaction]** .

Puoi recuperare i dati delle chiamate quando la proposta viene generata o quando viene accettata (quando la persona fa clic sull’offerta).

![](assets/ita_calldata_storage.png)
