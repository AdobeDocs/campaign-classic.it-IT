---
product: campaign
title: Glossario dell’integrazione di Campaign
description: Glossario dell’integrazione di Campaign
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: interaction-overview
exl-id: 9e199b7c-9307-4797-bf86-7940388555bc
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1103'
ht-degree: 0%

---

# Glossario dell’integrazione di Campaign{#i-glossary}



Di seguito è riportata la definizione dei principali elementi di interazione.

* **Ambiente**: set che include un catalogo di offerte e hook (spazi di offerta). Devi creare un ambiente eseguendo il targeting della dimensione. Esistono due tipi di ambienti:

   * **Ambiente di progettazione**: ambiente in cui vengono create le offerte e/o vengono definite le regole di tipologia (regole che determineranno le offerte da presentare o non presentare a una persona mirata). In questo documento sono anche definiti la tabella dei singoli utenti target delle offerte e la tabella per l’archiviazione di tutte le proposte di offerta. Il **[!UICONTROL Design environment]** Il nodo contiene sottocartelle per lo spazio delle offerte, filtri predefiniti e categorie di offerta. Per ogni **[!UICONTROL Design environment]** esiste un valore corrispondente di sola lettura **[!UICONTROL Live environment]**, generato dallo stesso **[!UICONTROL Design environment]**.
   * **Ambiente live**: ambiente collegato a un **[!UICONTROL Design environment]**. Contiene offerte di sola lettura il cui contenuto e la cui idoneità sono stati approvati tramite **[!UICONTROL Design environment]**. Devono essere selezionati per essere presentati su un sito Web o inseriti in un messaggio.

* **Spazio dell’offerta**: cartella che definisce il percorso in cui viene esposta l’offerta. La definizione di uno spazio consente di specificare il canale utilizzato, specificare se può o meno essere utilizzato in modalità unitaria (per impostazione predefinita: solo in modalità batch), creare il contenuto dell’offerta utilizzando le funzioni di rendering e specificare l’offerta delle offerte presentate. Uno spazio è un’interfaccia tra il canale e il motore di offerta.

  >[!IMPORTANT]
  >
  >Uno spazio dell’offerta non è un canale di comunicazione, bensì coincide con una posizione specifica dell’esposizione sul canale. Ad esempio, le offerte esposte su un sito web possono occupare due spazi sulla stessa pagina. In questo caso, avremo quindi due spazi per lo stesso canale.
  >
  >Gli spazi devono essere definiti nelle specifiche e non devono essere modificati durante il progetto.

* **Catalogo delle offerte**: set di offerte definite in Adobe Campaign che possono essere selezionate durante un’interazione. Il catalogo è organizzato gerarchicamente e ogni nodo corrisponde a una categoria.
* **Categoria**: cartella collegata al catalogo delle offerte in un ambiente, che organizza le offerte in base alla natura, alla data di idoneità e al tema dell’applicazione. Una categoria può contenere sottocategorie, che ereditano tutte le caratteristiche della categoria padre. Le regole di idoneità possono essere definite per una categoria in modo da condividerle per più offerte.
* **Temi applicazione**: parole chiave definite nella categoria, che consentono di filtrare le offerte quando vengono presentate a un canale in entrata o in uscita limitando la selezione delle offerte a una o due categorie.

  >[!NOTE]
  >
  >Le categorie figlio ereditano i temi identificati nella categoria padre.

* **Regole di idoneità**: i vincoli applicati a un ambiente, a una categoria o a un’offerta per quanto riguarda il periodo di validità, l’obiettivo e il peso. Ti consentono di verificare che un’offerta sia in linea con il contatto mirato.

  Negli ambienti, le regole di idoneità includono le regole di presentazione applicate alle offerte e alle persone di destinazione.

  Nelle categorie, le regole di idoneità consentono di limitare la validità della categoria nel tempo, definire i temi dell’applicazione e determinare le persone di destinazione. Possono inoltre ricevere un peso moltiplicatore per un determinato periodo di tempo. Questo consente di condividere le regole per le offerte in altre categorie, semplificandone la gestione.

  Nelle offerte, le regole di idoneità ti consentono di limitare la validità delle offerte in tempo e determinare le persone di destinazione.

* **Arbitraggio**: selezionando le offerte che verranno visualizzate in un ambiente (offerte idonee). Il principio di arbitraggio classifica le offerte per priorità in base ai criteri definiti nelle categorie, nelle offerte e nelle offerte contestuali.
* **Contatto**: un contatto da un’interazione in entrata. Durante l’elaborazione delle chiamate al motore, il contatto è associato a una dimensione di targeting. Esistono due tipi di contatti:

   * **[!UICONTROL Identified contact]** : contatto che è stato identificato volontariamente sul canale. Nelle interazioni in uscita, il contatto viene identificato automaticamente.
   * **[!UICONTROL Anonymous contact]** : un contatto che non si è abbonato volontariamente tramite il canale, ma che può essere identificato implicitamente tramite un cookie. Questa terminologia viene utilizzata solo per le interazioni in ingresso.

     >[!NOTE]
     >
     >I contatti anonimi non identificati vengono attribuiti alla dimensione di targeting dei visitatori.

* **Interazione in uscita**: chiamata al motore di interazione da un elenco di contatti (utilizzato per la consegna di e-mail, direct mailing, ecc.). A ogni contatto vengono applicate le stesse regole e le stesse procedure. Questo tipo di interazione viene generalmente elaborato in modalità batch.
* **Interazione in entrata**: interazione successiva a una chiamata in arrivo generata dall’azione di un contatto sul canale. Questo tipo di interazione viene generalmente elaborato in modalità unitaria.
* **Modalità batch**: la modalità batch ti consente di selezionare l’offerta migliore per un set di contatti. Le regole di idoneità/definizione delle priorità vengono applicate a tutti i contatti del set. Questa modalità viene generalmente utilizzata per le interazioni in uscita.
* **Modalità unitaria**: viene elaborato un singolo contatto alla volta. Questa modalità viene generalmente utilizzata per le interazioni in entrata e i messaggi transazionali.
* **Modalità di identificazione**: fa riferimento allo stato di un contatto.

   * **[!UICONTROL explicit]** : il contatto viene identificato dopo il suo accesso all’interfaccia del canale.
   * **[!UICONTROL implicit]** : il contatto è stato identificato da un cookie (permanente o sessione). Può essere elaborato come contatto anonimo o identificato.
   * **[!UICONTROL anonymous]** : impossibile identificare il contatto.

* **Offerta idonea**: offerta che soddisfa i vincoli definiti a monte e che può essere offerta in modo coerente a un target.
* **Regole di presentazione**: regole di tipologia a cui si fa riferimento nell’ambiente delle offerte, che ti consentono di escludere alcune offerte tenendo conto della cronologia delle proposte.
* **Spessore**: formule che consentono di calcolare con precisione la rilevanza di un’offerta, al fine di selezionare l’offerta più pertinente. I pesi sono definiti nelle offerte. Le offerte idonee vengono prese in considerazione in ordine decrescente di peso.
* **Funzione di rendering**: funzione definita nello spazio dell’offerta al fine di costruirne la rappresentazione in base agli attributi definiti nell’offerta. Esistono tre diverse modalità di funzione di rendering: HTML, XML e testo.
* **Proposta di offerta**: risultato dell’azione che consiste nel presentare una o più offerte a un contatto in un determinato spazio (ad esempio, banner su un sito web, e-mail o SMS). Questo risultato viene memorizzato nella tabella delle proposte di offerta. Tuttavia, non è obbligatorio salvare le proposte.
* **Simulazione**: modulo che consente di testare la presentazione delle offerte sui destinatari target prima di inviarle effettivamente.
* **Anteprima**: anteprima dell’offerta così come viene visualizzata nella sua cartella. È accessibile dalla finestra delle impostazioni dell’offerta o dal profilo di contatto.
* **Filtri predefiniti**: regole di filtro predefinite possono tenere conto dei parametri dell’offerta (ad esempio, un codice offerta). Possono essere riutilizzati dopo la creazione delle offerte.
* **Rappresentazione dell’offerta**: informazioni utilizzate dal canale per visualizzare l’offerta. La rappresentazione dell’offerta può essere realizzata a partire dalla funzione di rendering dello spazio in cui l’offerta viene rappresentata o immessa direttamente nell’interfaccia (ad esempio, nel blocco HTML). Un’offerta può essere rappresentata da uno spazio.
* **Processo di transizione**: processo attivato in un ambiente identificato, responsabile di indirizzare la chiamata a un ambiente anonimo se il contatto non è stato identificato in modo esplicito e/o implicito.
