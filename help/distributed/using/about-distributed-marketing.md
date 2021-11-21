---
product: campaign
title: Marketing distribuito campagna
description: Guida introduttiva al marketing distribuito
audience: campaign
content-type: reference
topic-tags: distributed-marketing
exl-id: c166409b-e040-491e-840a-a41310935d75
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1132'
ht-degree: 0%

---

# Guida introduttiva al marketing distribuito{#about-distributed-marketing}

![](../../assets/v7-only.svg)

Adobe Campaign offre un **Marketing distribuito** domanda di realizzazione di campagne di cooperazione tra enti centrali (sedi centrali, dipartimenti di marketing, ecc.) e gli enti locali (punti vendita, agenzie regionali, ecc.). Questa cooperazione si basa su un&#39;area di lavoro condivisa nota come **[!UICONTROL list of campaign packages]**, in cui vengono offerti modelli e istanze di campagne create a livello centrale alle entità locali.

L’entità centrale fornisce campagne che gli enti locali possono utilizzare. Le campagne vengono materializzate da pacchetti che rappresentano campagne locali o collaborative. Per utilizzare una campagna, l’entità locale deve ordinarla e l’ordine deve essere approvato.

>[!CAUTION]
>
>Il modulo Marketing distribuito è un **Campaign** opzione . Controlla il contratto di licenza.

## Terminologia {#terminology}

* **Enti centrali**

   Le entità centrali sono composte da operatori di marketing incaricati di specificare le comunicazioni e assistere le entità locali nell&#39;esecuzione della loro campagna di marketing.

   Il modulo di marketing distribuito consente all’entità centrale di:

   * impostare pacchetti di campagne di marketing per le entità locali,
   * aumentare il grado di autonomia delle entità locali per quanto riguarda la loro scelta nella comunicazione clienti/potenziali, nel targeting, nei contenuti, ecc.
   * gestire e controllare i costi,
   * gestire una rete di agenzie.

* **Entità locali**

   Gli enti locali possono essere agenzie, negozi o gruppi di operatori locali specifici (gestori di paesi o regioni, brand manager, ecc.).

   Distributed Marketing consente agli enti locali di avere più autonomia ottimizzando i costi di esecuzione.

* **Localizzazione**

   La localizzazione è la capacità di un&#39;entità locale di modificare il target e il contenuto di una campagna. Il livello possibile di localizzazione dipende dal tipo di campagna e dalla sua implementazione.

* **Elenco dei pacchetti delle campagne**

   L’elenco dei pacchetti campagna contiene le campagne disponibili per le entità locali.

* **Pacchetto campagna**

   Modello (o istanza di campagna) creato da un’entità centrale e reso disponibile a un set di entità locali.

* **Campagna locale**

   Una campagna locale è un&#39;istanza creata da un modello a cui si fa riferimento nell&#39;elenco di **[!UICONTROL campaign packages]** con **programma di esecuzione specifico**. Il suo obiettivo è soddisfare un&#39;esigenza di comunicazione locale utilizzando un modello di campagna configurato e configurato dall&#39;entità centrale.

   Il grado di autonomia dell&#39;entità locale dipende dall&#39;implementazione utilizzata.

   Fai riferimento a [Creazione di una campagna locale](creating-a-local-campaign.md).

* **Campagna collaborativa**

   Una campagna collaborativa è una campagna di cui **il programma di esecuzione è definito** dall&#39;ente centrale, che l&#39;ente locale può utilizzare. Il contenuto rimane lo stesso per ogni entità locale, ma i costi sono condivisi. Per partecipare, gli enti locali si abbonano alla campagna collaborativa.

   * **[!UICONTROL Collaborative campaign (by form)]**: consigliata per campagne che coinvolgono fino a 300 enti locali. L’entità locale può immettere parametri predefiniti per il targeting e la personalizzazione del contenuto in un modulo web. Il modulo può essere un modulo Adobe Campaign o un modulo esterno (client extranet). Un amministratore funzionale può definire e configurare il modulo in base a un modello di modulo definito dall’integratore. Per ordinare la campagna, l’entità locale necessita solo dell’accesso web.
   * **[!UICONTROL Collaborative campaign (by campaign)]**: consigliato per campagne rivolte a decine di enti locali. Questo tipo di campagna crea campagne figlio per ogni entità locale. Una volta che **[!UICONTROL collaborative campaign (by campaign)]** viene approvata dall’entità centrale, la campagna viene resa disponibile all’entità locale, che può modificarla. L’esecuzione viene sincronizzata automaticamente tra le campagne padre e figlio. L’entità locale deve avere accesso a un’istanza per ordinare una campagna e parteciparvi.
   * **[!UICONTROL Collaborative campaign (by target approval)]**: consigliato per campagne rivolte a diverse migliaia di enti locali. L&#39;entità locale riceve un elenco di contatti predefinito dall&#39;entità centrale. L’entità locale decide se mantenere o meno determinati contatti in base al contenuto della campagna, tramite un modulo web. Le entità locali sono dedotte dall&#39;elenco dei contatti selezionati. Per partecipare alla campagna, l’entità locale ha solo bisogno dell’accesso web.
   * **[!UICONTROL Collaborative campaign (simple)]**: questa modalità assicura la compatibilità con i processi di esecuzione specifici delle versioni precedenti.

   Fai riferimento a [Creazione di una campagna collaborativa](creating-a-collaborative-campaign.md).

**Ordinamento dei pacchetti delle campagne**

Se un’entità locale si registra per una campagna, questa viene trasformata in un ordine che raggruppa tutte le informazioni relative alla localizzazione della campagna.

## Area di lavoro {#workspace}

L’elenco dei pacchetti della campagna è accessibile dal **Campagne** scheda: fai clic su **[!UICONTROL Campaign packages]** link.

![](assets/mkg_dist_home_local_op.png)

Questa finestra consente a tutti gli operatori locali di visualizzare le campagne disponibili per la propria agenzia locale.

Nel caso delle agenzie centrali, questa finestra visualizza tutti i pacchetti disponibili nell’elenco dei pacchetti delle campagne e offre collegamenti aggiuntivi per la modifica dell’elenco.

## Operatori ed entità {#operators-and-entities}

Iniziare specificando gli operatori di entità centrale e locale tramite il **[!UICONTROL Access management]** cartella.

![](assets/s_advuser_mkg_dist_tree.png)

### Operatori {#operators}

È necessario creare operatori centrali e locali.

Gli operatori centrali devono appartenere al **[!UICONTROL Central management]** gruppo di operatori o avere **[!UICONTROL CENTRAL]** a destra.

Gli operatori locali devono appartenere al **[!UICONTROL Local management]** gruppo di operatori o avere **[!UICONTROL LOCAL]** a destra. Devono anche essere collegati alla loro entità locale.

![](assets/s_advuser_mkg_dist_local_create.png)

### Entità organizzative {#organizational-entities}

Per creare un’entità organizzativa, fai clic sul pulsante **[!UICONTROL Administration > Access management > Organizational entities]** e fai clic sul **[!UICONTROL New]** sopra l’elenco delle entità.

![](assets/s_advuser_mkg_dist_local_list.png)

Ogni entità organizzativa contiene informazioni di identificazione (etichetta, nome interno, informazioni di contatto, ecc.) e i gruppi coinvolti nel processo di approvazione dell&#39;ordine. Sono definiti nella **[!UICONTROL Notifications and approvals]** nella sezione **[!UICONTROL General]** scheda .

* Definisci un gruppo di notifica del pacchetto: gli operatori di questo gruppo riceveranno una notifica ogni volta che un nuovo pacchetto viene aggiunto all’elenco dei pacchetti di campagna e ogni volta che una campagna diventa disponibile.
* Selezionare il gruppo di revisori incaricati di approvare gli ordini, ovvero quelli incaricati di approvare le campagne ordinate dall’entità locale.
* Infine, seleziona il gruppo di revisori incaricati di approvare la campagna locale (target, contenuto, budget, ecc.). Questo gruppo può essere aggiunto a quando si ordina una campagna, a seconda del modello.

>[!NOTE]
>
>Il processo di approvazione viene presentato nella [Processo di approvazione](creating-a-local-campaign.md#approval-process) sezione .

## Implementazione {#implementation}

Le campagne Distributed Marketing vengono create e pubblicate dall&#39;entità centrale. Essi possono essere utilizzati sia dagli enti locali che da quelli centrali, a seconda delle necessità.

La procedura di implementazione dipende dal tipo di pacchetto della campagna utilizzato e dai livelli di delega delle entità locali.

### Attività di integrazione {#integrator-side}

1. Creare entità locali.
1. Collega i destinatari agli operatori che gestiscono le entità locali.

   ![](assets/mkg_dist_local_entity_association.png)

1. Specificare diritti e regole di navigazione per le entità locali
1. Specifica il set di campi necessari per la localizzazione della campagna:

   * definizione dell&#39;obiettivo e dimensione massima,
   * definizione del contenuto,
   * programma di esecuzione (data di contatto e data di estrazione), **solo per gli operatori locali**,
   * estensione dello schema dell&#39;ordine con tutti i campi aggiuntivi necessari.

1. Creare un modulo web (Adobe o extranet) che consenta di visualizzare i parametri di localizzazione, valutare la destinazione e il budget, nonché visualizzare in anteprima il contenuto e approvare l’ordine.

   Per **campagne collaborative (per approvazione target)**, crea la tabella in cui verranno salvate le approvazioni per ogni entità locale.

### Attività di amministrazione funzionale {#functional-administrator-side}

Questi passaggi devono essere eseguiti durante la creazione di ogni campagna.

1. Aggiorna il modulo con i campi utilizzati per la localizzazione della campagna.
1. Crea un&#39;istanza da un modello di campagna appropriato (campagna collaborativa) o duplica il modello di campagna (campagna locale).
1. Configura la campagna con i campi di localizzazione e il riferimento al modulo.
1. Pubblica la campagna.

### Attività dell&#39;operatore locale {#local-operator-side}

Queste azioni devono essere eseguite per ogni campagna.

1. Una volta ricevuta la notifica della disponibilità del pacchetto della campagna, specifica il percorso della campagna (facoltativo).
1. Valutare l’obiettivo, il budget, ecc.
1. Visualizzare l&#39;anteprima del contenuto della campagna.
1. Ordina la campagna.
