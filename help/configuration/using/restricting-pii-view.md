---
product: campaign
title: Limitare la visualizzazione di dati personali
description: Scopri come limitare la visualizzazione delle PI
feature: PI
role: Data Engineer, Developer
exl-id: 0f32d62d-a10a-4feb-99fe-4679b98957d4
source-git-commit: e198defd60f4b12681025b04b12a1498df015047
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 1%

---

# Limitare la visualizzazione di dati personali{#restricting-pii-view}

## Panoramica {#overview}

Alcuni clienti hanno bisogno che gli utenti marketing possano accedere ai record di dati, ma non desiderano che visualizzino dati personali (PII, Personally Identifiable Information) come nome, cognome o indirizzo e-mail. Adobe Campaign propone un modo per proteggere la privacy e prevenire l’utilizzo improprio dei dati da parte degli operatori regolari delle campagne.

## Implementazione {#implementation}

Un nuovo attributo che può essere applicato a qualsiasi elemento o attributo è stato aggiunto agli schemi. Completa l&#39;attributo esistente **[!UICONTROL visibleIf]**. Questo attributo è: **[!UICONTROL accessibleIf]** . Quando contiene un&#39;espressione XTK correlata al contesto utente corrente, può sfruttare **[!UICONTROL HasNamedRight]** o **[!UICONTROL $(login)]**, ad esempio.

Di seguito è riportato un esempio di estensione dello schema del destinatario, con questo utilizzo:

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

* **[!UICONTROL visibleIf]** : nasconde i campi dai metadati, pertanto non è possibile accedervi all&#39;interno di una visualizzazione schema, di una selezione di colonne o di un generatore di espressioni. Tuttavia, se il nome del campo viene immesso manualmente in un’espressione, il valore non viene nascosto.
* **[!UICONTROL accessibleIf]** : nasconde i dati (sostituendoli con valori vuoti) dalla query risultante. Se visibleIf è vuoto, ottiene la stessa espressione di **[!UICONTROL accessibleIf]**.

Di seguito sono riportate le conseguenze dell’utilizzo di questo attributo in Campaign:

* I dati non verranno visualizzati utilizzando un editor di query generico nella console,
* I dati non saranno visibili negli elenchi di panoramica e negli elenchi di record (console).
* I dati diventeranno di sola lettura nella vista dettagliata.
* I dati saranno utilizzabili solo all’interno dei filtri (il che significa che utilizzando alcune strategie di dicotomia è ancora possibile indovinare i valori).
* Qualsiasi espressione creata utilizzando un campo con restrizioni diventa limitata a: lower(@email) diventa accessibile quanto @email.
* In un flusso di lavoro, puoi aggiungere la colonna con restrizioni alla popolazione target come colonna aggiuntiva della transizione, ma non è ancora accessibile agli utenti di Adobe Campaign.
* Quando si archivia la popolazione target in un gruppo (elenco), le caratteristiche dei campi memorizzati sono le stesse dell’origine dei dati.
* Per impostazione predefinita, i dati non sono accessibili al codice JS.

>[!IMPORTANT]
>
>L&#39;utilizzo dell&#39;attributo **accessibleIf** nei parametri critici (ad esempio quelli nelle chiavi composite) può causare errori per gli utenti che non sono autorizzati a leggere i dati a causa di dati nascosti. Questo può causare errori di query o comportamenti imprevisti. Assicurati che i parametri essenziali siano accessibili per evitare interruzioni.

## Raccomandazioni {#recommendations}

In ogni consegna, gli indirizzi e-mail vengono copiati nelle tabelle **[!UICONTROL broadLog]** e **[!UICONTROL forecastLog]**: di conseguenza, anche questi campi devono essere protetti.

Di seguito è riportato un esempio di estensione della tabella di registro per implementare questo:

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
>Questa restrizione si applica agli utenti non tecnici: un utente tecnico, con le relative autorizzazioni, potrà recuperare i dati. Questo metodo non è quindi sicuro al 100%.
