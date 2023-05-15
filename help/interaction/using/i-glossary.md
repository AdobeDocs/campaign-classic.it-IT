---
product: campaign
title: Glossario per l’integrazione di Campaign
description: Glossario per l’integrazione di Campaign
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: interaction
content-type: reference
topic-tags: interaction-overview
exl-id: 9e199b7c-9307-4797-bf86-7940388555bc
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1103'
ht-degree: 0%

---

# Glossario per l’integrazione di Campaign{#i-glossary}



Di seguito è riportata la definizione dei principali elementi di interazione.

* **Ambiente**: set che include un catalogo di offerte e hook (spazi di offerta). È necessario creare un ambiente mediante il targeting della dimensione. Esistono due tipi di ambienti:

   * **Ambiente di progettazione**: ambiente in cui vengono create le offerte e/o vengono definite le regole di tipologia (regole che determineranno le offerte da presentare o meno a una persona target). Anche la tabella dei singoli utenti interessati dalle offerte e la tabella per la memorizzazione di tutte le proposte di offerta sono definite in questo documento. La **[!UICONTROL Design environment]** il nodo contiene sottocartelle per lo spazio di offerta, filtri predefiniti e categorie di offerte. Per ogni **[!UICONTROL Design environment]** esiste una sola lettura corrispondente **[!UICONTROL Live environment]**, generato dallo stesso **[!UICONTROL Design environment]**.
   * **Ambiente live**: ambiente collegato a un **[!UICONTROL Design environment]**. Contiene offerte di sola lettura il cui contenuto e idoneità sono stati approvati tramite il **[!UICONTROL Design environment]**. Devono essere selezionati per essere presentati su un sito Web o inseriti in un messaggio.

* **Spazio offerta**: cartella che definisce il percorso in cui viene esposta l’offerta. La definizione di uno spazio consente di specificare il canale utilizzato, specificare se può essere utilizzato o meno in modalità unitaria (per impostazione predefinita: solo in modalità batch), crea il contenuto dell’offerta utilizzando le funzioni di rendering e specifica l’offerta delle offerte presentate. Uno spazio è un’interfaccia tra il canale e il motore di offerta.

   >[!IMPORTANT]
   >
   >Uno spazio di offerta non è un canale di comunicazione, coincide con una posizione di esposizione specifica sul canale. Ad esempio, le offerte esposte su un sito web possono occupare due spazi sulla stessa pagina. In questo caso, avremo due spazi per lo stesso canale.
   >
   >Gli spazi devono essere definiti nelle specifiche e non devono essere modificati durante il progetto.

* **Catalogo delle offerte**: set di offerte definite in Adobe Campaign che possono essere selezionate durante un’interazione. Il catalogo è organizzato gerarchicamente con ogni nodo corrispondente a una categoria.
* **Categoria**: una cartella collegata al catalogo delle offerte in un ambiente, che organizza le offerte in base alla natura, alla data di idoneità e al tema dell’applicazione. Una categoria può contenere sottocategorie che ereditano tutte le caratteristiche della categoria padre. Le regole di idoneità possono essere definite per una categoria in modo da condividerle per diverse offerte.
* **Temi di applicazione**: parole chiave definite nella categoria , che consentono di filtrare le offerte quando vengono presentate a un canale in entrata o in uscita limitando la selezione delle offerte a una o due categorie.

   >[!NOTE]
   >
   >Le categorie figlio ereditano i temi identificati nella categoria padre.

* **Regole di idoneità**: vincoli applicati a un ambiente, una categoria o un&#39;offerta relativi al periodo di validità, al target e al peso. Ti consentono di garantire che un’offerta sia in linea con il contatto mirato.

   Negli ambienti, le regole di idoneità includono le regole di presentazione applicate alle offerte e alle persone a cui eseguire il targeting.

   Nelle categorie, le regole di idoneità consentono di limitare la validità della categoria nel tempo, definire i temi dell’applicazione e determinare le persone a cui rivolgersi. Possono anche ricevere un peso moltiplicatore per un determinato periodo di tempo. Ciò ti consente di condividere le regole per le offerte in altre categorie e di semplificarne la gestione.

   Nelle offerte, le regole di idoneità ti consentono di limitare la validità delle offerte nel tempo e di determinare le persone a cui rivolgerti.

* **Arbitrato**: selezione delle offerte che verranno visualizzate in un ambiente (offerte idonee). Il principio di arbitraggio classifica le offerte per priorità in base ai criteri definiti nelle categorie, offerte e offerte di contesto.
* **Contatto**: un contatto da un&#39;interazione in entrata. Durante l’elaborazione della chiamata del motore, il contatto è associato a una dimensione di targeting. Esistono due tipi di contatti:

   * **[!UICONTROL Identified contact]** : un contatto volontariamente identificato sul canale. Nelle interazioni in uscita, il contatto viene identificato automaticamente.
   * **[!UICONTROL Anonymous contact]** : un contatto che non si è iscritto volontariamente attraverso il canale ma può essere identificato implicitamente tramite un cookie. Questa terminologia viene utilizzata solo per le interazioni in entrata.

      >[!NOTE]
      >
      >I contatti anonimi non identificati sono attribuiti alla dimensione di targeting del visitatore.

* **Interazione in uscita**: chiama al motore di interazione da un elenco di contatti (utilizzato per la consegna di e-mail, direct mailing, ecc.). Le stesse regole e procedure vengono applicate a ogni contatto. Questo tipo di interazione viene generalmente elaborato in modalità batch.
* **Interazione in entrata**: interazione successiva a una chiamata in arrivo generata dall&#39;azione di un contatto sul canale. Questo tipo di interazione viene generalmente elaborato in modalità unitaria.
* **Modalità batch**: la modalità batch consente di selezionare l&#39;offerta migliore per un set di contatti. Le regole di idoneità/priorità vengono applicate a tutti i contatti del set. Questa modalità viene generalmente utilizzata per le interazioni in uscita.
* **Modalità unitaria**: viene elaborato un unico contatto alla volta. Questa modalità è generalmente utilizzata per le interazioni in entrata e i messaggi transazionali.
* **Modalità di identificazione**: si riferisce allo stato di un contatto.

   * **[!UICONTROL explicit]** : il contatto viene identificato dopo il loro accesso all&#39;interfaccia del canale.
   * **[!UICONTROL implicit]** : il contatto è stato identificato da un cookie (permanente o sessione). Può essere elaborato come contatto anonimo o identificato.
   * **[!UICONTROL anonymous]** : non è possibile identificare il contatto.

* **Offerta idonea**: offerta conforme ai vincoli definiti a monte che possono essere offerti in modo coerente a un target.
* **Regole di presentazione**: regole di tipologia a cui si fa riferimento nell’ambiente delle offerte, che consentono di escludere alcune offerte tenendo conto della cronologia delle proposte.
* **Peso**: formule che consentono di calcolare con precisione la rilevanza di un’offerta, al fine di selezionare l’offerta più pertinente. I pesi sono definiti nelle offerte. Le offerte ammissibili sono prese in considerazione in ordine decrescente di peso.
* **Funzione di rendering**: funzione definita nello spazio di offerta per creare la relativa rappresentazione dell’offerta in base agli attributi definiti nell’offerta. Esistono tre diverse modalità di rendering della funzione: HTML, XML e testo.
* **Proposta di offerta**: risultato dell’azione che consiste nel presentare una o più offerte a un contatto in un dato spazio (ad esempio banner su un sito web, e-mail o SMS). Questo risultato viene memorizzato nella tabella delle proposte di offerta. Tuttavia, non è obbligatorio salvare le proposte.
* **Simulazione**: che consente di testare la presentazione dell’offerta sui destinatari desiderati prima di inviare effettivamente le offerte.
* **Anteprima**: anteprima dell’offerta così come viene visualizzata nella relativa cartella. È accessibile dalla finestra delle impostazioni dell’offerta o dal profilo del contatto.
* **Filtri predefiniti**: le regole di filtro predefinite possono tenere conto dei parametri delle offerte (ad esempio, un codice di offerta). Possono essere riutilizzati dopo la creazione delle offerte.
* **Rappresentazione dell’offerta**: informazioni utilizzate dal canale per visualizzare l’offerta. La rappresentazione dell’offerta può essere creata a partire dalla funzione di rendering dello spazio su cui l’offerta è rappresentata o inserita direttamente nell’interfaccia (ad esempio, nel blocco HTML). Un&#39;offerta può essere rappresentata da uno spazio.
* **Processo di transizione**: un processo attivato in un ambiente identificato, responsabile dell&#39;indirizzamento della chiamata a un ambiente anonimo se il contatto non è stato esplicitamente e/o implicitamente identificato.
