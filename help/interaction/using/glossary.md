---
solution: Campaign Classic
product: campaign
title: Glossario
description: Glossario
audience: interaction
content-type: reference
topic-tags: interaction-overview
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1094'
ht-degree: 0%

---


# Glossario{#glossary}

Di seguito è riportata la definizione dei principali elementi di interazione.

* **Ambiente**: set che include un catalogo di offerte e ganci (spazi di offerta). È necessario creare un ambiente con una dimensione di targeting. Esistono due tipi di ambienti:

   * **Ambiente** di progettazione: ambiente in cui vengono create le offerte e/o vengono definite le regole di tipologia (regole che determineranno le offerte da presentare o non presentare a una persona con targeting). Anche la tabella delle persone a cui verranno indirizzate le offerte e la tabella per l&#39;archiviazione di tutte le proposte di offerta sono definite in questo documento. Il **[!UICONTROL Design environment]** nodo contiene sottocartelle dello spazio disponibile, filtri predefiniti e categorie di offerte. Per ogni **[!UICONTROL Design environment]** file è disponibile una sola lettura **[!UICONTROL Live environment]**, generata dallo stesso **[!UICONTROL Design environment]**.
   * **Ambiente** live: ambiente collegato a un **[!UICONTROL Design environment]**. Contiene offerte in sola lettura il cui contenuto e idoneità sono stati approvati tramite **[!UICONTROL Design environment]**. Devono essere selezionati per essere presentati su un sito Web o inseriti in un messaggio.

* **Spazio** offerta: cartella che definisce il percorso in cui l’offerta viene esposta. La definizione di uno spazio consente di specificare il canale utilizzato, specificare se può essere utilizzato o meno in modalità unitaria (per impostazione predefinita: solo in modalità batch), create il contenuto dell&#39;offerta utilizzando le funzioni di rendering e specificate l&#39;offerta delle offerte presentate. Uno spazio è un&#39;interfaccia tra il canale e il motore di offerte.

   >[!IMPORTANT]
   >
   >Uno spazio di offerta non è un canale di comunicazione, ma coincide con una specifica posizione di esposizione sul canale. Ad esempio, le offerte esposte su un sito Web possono occupare due spazi sulla stessa pagina. In questo caso, avremo due spazi per lo stesso canale.
   >
   >Gli spazi devono essere definiti nelle specifiche e non devono essere modificati durante il progetto.

* **Catalogo** offerte: insieme di offerte definite in  Adobe Campaign che possono essere selezionate durante un&#39;interazione. Il catalogo è organizzato gerarchicamente con ciascun nodo corrispondente a una categoria.
* **Categoria**: una cartella collegata al catalogo delle offerte in un ambiente che organizza le offerte in base alla natura, alla data di idoneità e al tema dell&#39;applicazione. Una categoria può contenere sottocategorie che ereditano tutte le caratteristiche della categoria padre. Le regole di idoneità possono essere definite per una categoria in modo da condividerle per più offerte.
* **Temi** applicazione: le parole chiave definite nella categoria, che consentono di filtrare le offerte quando vengono presentate a un canale in entrata o in uscita limitando la selezione delle offerte a una o due categorie.

   >[!NOTE]
   >
   >Le categorie figlio ereditano i temi identificati nella categoria principale.

* **Regole** di ammissibilità: vincoli applicati a un ambiente, categoria o offerta per quanto riguarda il periodo di validità, il target e il peso. Consentono di garantire che un&#39;offerta sia in linea con il contatto di destinazione.

   Negli ambienti, le regole di idoneità includono le regole di presentazione applicate alle offerte e alle persone a cui eseguire il targeting.

   Nelle categorie, le regole di idoneità consentono di limitare la validità della categoria nel tempo, definire i temi dell&#39;applicazione e determinare le persone a cui eseguire il targeting. Possono inoltre ricevere un peso moltiplicatore per un determinato periodo di tempo. Questo consente di condividere le regole per le offerte in altre categorie e di semplificarne la gestione.

   Nelle offerte, le regole di idoneità consentono di limitare la validità delle offerte nel tempo e di determinare le persone a cui destinare il targeting.

* **Arbitrato**: selezione di offerte che verranno visualizzate in un ambiente (offerte idonee). Il principio di arbitraggio classifica le offerte per priorità in base ai criteri definiti nelle categorie, nelle offerte e nelle offerte contestuali.
* **Contatto**: un contatto da un&#39;interazione in entrata. Durante l&#39;elaborazione delle chiamate del motore, il contatto è associato a una dimensione di targeting. Esistono due tipi di contatti:

   * **[!UICONTROL Identified contact]** : un contatto che è stato volontariamente identificato sul canale. Nelle interazioni in uscita, il contatto viene identificato automaticamente.
   * **[!UICONTROL Anonymous contact]** : un contatto che non si è iscritto volontariamente attraverso il canale ma che può essere implicitamente identificato tramite un cookie. Questa terminologia viene utilizzata solo per le interazioni in entrata.

      >[!NOTE]
      >
      >I contatti anonimi non identificati sono attribuiti alla dimensione di targeting dei visitatori.

* **Interazione** in uscita: chiamare il motore di interazione da un elenco di contatti (utilizzato per inviare e-mail, posta diretta, ecc.). Le stesse regole e procedure vengono applicate a ogni contatto. Questo tipo di interazione viene generalmente elaborato in modalità batch.
* **Interazione** in entrata: interazione a seguito di una chiamata in arrivo generata dall&#39;azione di un contatto sul canale. Questo tipo di interazione viene generalmente elaborato in modalità unitaria.
* **Modalità** batch: la modalità batch consente di selezionare l&#39;offerta migliore per un set di contatti. Le regole di ammissibilità/priorità vengono applicate a tutti i contatti del set. Questa modalità è generalmente utilizzata per le interazioni in uscita.
* **Modalità** unitaria: viene elaborato un singolo contatto alla volta. Questa modalità è generalmente utilizzata per le interazioni in entrata e i messaggi transazionali.
* **Modalità** di identificazione: si riferisce allo stato di un contatto.

   * **[!UICONTROL explicit]** : il contatto viene identificato dopo il suo login all&#39;interfaccia del canale.
   * **[!UICONTROL implicit]** : il contatto è stato identificato da un cookie (permanente o sessione). Può essere trattato come un contatto anonimo o identificato.
   * **[!UICONTROL anonymous]** : il contatto non può essere identificato.

* **Offerta** ammissibile: offrire in base ai vincoli definiti a monte che possono essere offerti in modo coerente a un target.
* **Regole** presentazione: regole di tipologia a cui si fa riferimento nell&#39;ambiente delle offerte, che consentono di escludere alcune offerte tenendo conto della cronologia delle offerte.
* **Peso**: formule che consentono di calcolare con precisione la rilevanza di un&#39;offerta, al fine di selezionare l&#39;offerta più rilevante. I pesi sono definiti nelle offerte. Le offerte ammissibili sono prese in considerazione in ordine decrescente di peso.
* **Funzione** di rendering: funzione definita nello spazio dell&#39;offerta per costruire la sua rappresentazione basata sugli attributi definiti nell&#39;offerta. Sono disponibili tre diverse modalità di rendering: HTML, XML e testo.
* **Proposta** di offerta: risultato dell’azione che consiste nel presentare una o più offerte a un contatto in un dato spazio (ad esempio banner su un sito Web, e-mail o SMS). Questo risultato viene memorizzato nella tabella delle proposte di offerta. Tuttavia, non è obbligatorio salvare le proposte.
* **Simulazione**: che consente di testare la presentazione dell&#39;offerta sui destinatari desiderati prima di inviare effettivamente le offerte.
* **Anteprima**: anteprima dell’offerta così come viene visualizzata nella relativa cartella. È accessibile dalla finestra delle impostazioni dell&#39;offerta o dal profilo di contatto.
* **Filtri** predefiniti: le regole di filtro predefinite possono tenere conto dei parametri delle offerte (ad esempio, un codice delle offerte). Possono essere riutilizzati dopo la creazione delle offerte.
* **Rappresentazione** offerta: informazioni utilizzate dal canale per visualizzare l&#39;offerta. La rappresentazione dell&#39;offerta può essere costruita dalla funzione di rendering dello spazio su cui l&#39;offerta è rappresentata o inserita direttamente nell&#39;interfaccia (ad esempio, nel blocco HTML). Un&#39;offerta può essere rappresentata da uno spazio.
* **Processo** di transizione: un processo attivato in un ambiente identificato, responsabile di indirizzare la chiamata a un ambiente anonimo se il contatto non è stato identificato esplicitamente e/o implicitamente.

