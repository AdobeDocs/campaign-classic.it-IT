---
solution: Campaign Classic
product: campaign
title: Limitazione della vista PII
description: Limitazione della vista PII
audience: configuration
content-type: reference
topic-tags: editing-schemas
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 2%

---


# Limitazione della vista PII{#restricting-pii-view}

## Panoramica {#overview}

Alcuni clienti hanno bisogno che gli utenti di marketing siano in grado di accedere ai record di dati ma non desiderano che visualizzino informazioni personali (PII), come nome, cognome o indirizzo e-mail.  Adobe Campaign propone un modo per proteggere la privacy e impedire che i dati vengano utilizzati in modo improprio dagli operatori regolari delle campagne.

## Implementazione {#implementation}

Un nuovo attributo che può essere applicato a qualsiasi elemento o attributo è stato aggiunto agli schemi, completa l&#39;attributo esistente **[!UICONTROL visibleIf]** . Questo attributo è: **[!UICONTROL accessibleIf]** . Quando contiene un&#39;espressione XTK correlata al contesto utente corrente, può utilizzare **[!UICONTROL HasNamedRight]** o **[!UICONTROL $(login)]** , ad esempio.

È possibile trovare un esempio di estensione dello schema destinatario che mostra l&#39;uso seguente:

```
<srcSchema desc="Recipient table (profiles" entitySchema="xtk:srcSchema" extendedSchema="nms:recipient"
           img="nms:recipient.png" label="Recipients" labelSingular="Recipient"
           name="recipient" namespace="sec" xtkschema="xtk:srcSchema">
  <element desc="Recipient table (profiles" img="nms:recipient.png" label="Recipients"
           labelSingular="Recipient" name="recipient">
    <attribute name="firstName" accessibleIf="$(login)=='admin'"/>
    <attribute name="lastName" visibleIf="$(login)=='admin'"/>
    <attribute name="email" accessibleIf="$(login)=='admin'"/>
  </element>
</srcSchema>
```

Le proprietà principali sono:

* **[!UICONTROL visibleIf]** : nasconde i campi dai metadati, pertanto non è possibile accedervi all&#39;interno di una visualizzazione schema, una selezione di colonne o un generatore di espressioni. Ma questo non nasconde alcun dato, se il nome del campo viene immesso manualmente in un&#39;espressione, il valore viene visualizzato.
* **[!UICONTROL accessibleIf]** : nasconde i dati (sostituendoli con valori vuoti) dalla query risultante. Se visibleSe è vuoto, allora ottiene la stessa espressione di **[!UICONTROL accessibleIf]** .

Di seguito sono riportate le conseguenze dell&#39;utilizzo di questo attributo in Campaign:

* I dati non verranno visualizzati utilizzando un editor query generico nella console,
* I dati non saranno visibili negli elenchi di panoramica e nell&#39;elenco di record (console).
* I dati diventeranno di sola lettura in visualizzazione dettagliata.
* I dati saranno utilizzabili solo all&#39;interno di filtri (il che significa che utilizzando alcune strategie di dicotomia, è ancora possibile indovinare i valori).
* Qualsiasi espressione creata utilizzando un campo con restrizioni diventa anch&#39;essa soggetta a restrizioni: lower(@email) diventa accessibile come @email.
* In un flusso di lavoro, potete aggiungere la colonna con restrizioni alla popolazione di destinazione come una colonna aggiuntiva della transizione, ma resta inaccessibile per  utenti Adobe Campaign.
* Quando si memorizza la popolazione di destinazione in un gruppo (elenco), le caratteristiche dei campi memorizzati sono le stesse dell&#39;origine dei dati.
* Per impostazione predefinita, i dati non sono accessibili al codice JS.

## Raccomandazioni {#recommendations}

In ogni consegna, gli indirizzi e-mail vengono copiati nelle **[!UICONTROL broadLog]** e nelle **[!UICONTROL forecastLog]** tabelle: di conseguenza, anche questi campi devono essere protetti.

Di seguito è riportato un esempio di estensione della tabella di registro per implementare quanto segue:

```
<srcSchema entitySchema="xtk:srcSchema" extendedSchema="nms:broadLogRcp" img="nms:broadLog.png"
           label="Recipient delivery logs" labelSingular="Recipient delivery log"
           name="broadLogRcp" namespace="sec" xtkschema="xtk:srcSchema">
  <element img="nms:broadLog.png" label="Recipient delivery logs" labelSingular="Recipient delivery log"
           name="broadLogRcp">
    <attribute accessibleIf="$(login)=='admin'" name="address"/>
  </element>
</srcSchema>
<srcSchema desc="Delivery messages being prepared." entitySchema="xtk:srcSchema"
           extendedSchema="nms:tmpBroadcast" img="" label="Messages being prepared"
           labelSingular="Message" name="tmpBroadcast" namespace="sec" xtkschema="xtk:srcSchema">
  <element desc="Delivery messages being prepared." label="Messages being prepared"
           labelSingular="Message" name="tmpBroadcast">
    <attribute accessibleIf="$(login)=='admin'" name="address"/>
  </element>
</srcSchema>
<srcSchema entitySchema="xtk:srcSchema" extendedSchema="nms:excludeLogRcp" img="nms:excludeLog.png"
           label="Recipient exclusion logs" labelSingular="Recipient exclusion log"
           name="excludeLogRcp" namespace="sec" xtkschema="xtk:srcSchema">
  <element img="nms:excludeLog.png" label="Recipient exclusion logs" labelSingular="Recipient exclusion log"
           name="excludeLogRcp">
    <attribute accessibleIf="$(login)=='admin'" name="address"/>
  </element>
</srcSchema>
```

>[!NOTE]
>
>Questa limitazione si applica agli utenti non tecnici: un utente tecnico, con le relative autorizzazioni, sarà in grado di recuperare i dati. Questo metodo non è pertanto sicuro al 100%.

