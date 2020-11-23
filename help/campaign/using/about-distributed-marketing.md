---
solution: Campaign Classic
product: campaign
title: Informazioni sul marketing distribuito
description: Informazioni sul marketing distribuito
audience: campaign
content-type: reference
topic-tags: distributed-marketing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1129'
ht-degree: 1%

---


# Informazioni sul marketing distribuito{#about-distributed-marketing}

## Introduzione {#introduction}

 Adobe Campaign offre un&#39;applicazione **Distributed Marketing** per l&#39;implementazione di campagne di cooperazione tra entità centrali (sedi centrali, dipartimenti di marketing, ecc.) ed enti locali (punti di vendita, agenzie regionali, ecc.). Questa collaborazione si basa su un&#39;area di lavoro condivisa nota come **[!UICONTROL list of campaign packages]**, in cui i modelli e le istanze delle campagne create a livello centrale vengono offerti alle entità locali.

L&#39;entità centrale fornisce campagne che gli enti locali possono utilizzare. Le campagne vengono materializzate da pacchetti che rappresentano campagne locali o collaborative. Per utilizzare una campagna, l&#39;entità locale deve ordinarla e l&#39;ordine deve essere approvato.

>[!CAUTION]
>
>Il modulo Distributed Marketing è un&#39;opzione **Campaign** . Controlla il contratto di licenza.

## Terminologia {#terminology}

### Enti centrali {#central-entities}

Le entità centrali sono composte da operatori di marketing incaricati di specificare le comunicazioni e assistere gli enti locali nell&#39;esecuzione della loro campagna di marketing.

Il modulo di marketing distribuito consente all&#39;entità centrale di:

* impostare pacchetti campagna di marketing per entità locali,
* aumentare il grado di autonomia delle entità locali rispetto alla loro scelta nella comunicazione con i clienti/potenziali, nel targeting, nei contenuti, ecc.
* gestire e controllare i costi,
* gestire una rete di agenzie.

### Entità locali {#local-entities}

Gli enti locali possono essere agenzie, negozi o gruppi di operatori locali specifici (gestori di paesi o regioni, brand manager, ecc.).

Distributed Marketing consente agli enti locali di avere più autonomia ottimizzando i costi di esecuzione.

### Localizzazione {#localization}

La localizzazione è la capacità di un&#39;entità locale di modificare la destinazione e il contenuto di una campagna. Il possibile livello di localizzazione dipende dal tipo di campagna e dalla sua implementazione.

### Elenco di pacchetti campagna {#list-of-campaign-packages}

L&#39;elenco dei pacchetti campagna contiene le campagne disponibili per le entità locali.

### Pacchetto campagna {#campaign-package}

Modello (o istanza di campagna) creato da un&#39;entità centrale e reso disponibile a un set di entità locali.

### Campagna locale {#local-campaign}

Una campagna locale è un&#39;istanza creata da un modello a cui si fa riferimento nell&#39;elenco di **[!UICONTROL campaign packages]** con una pianificazione **di esecuzione** specifica. L&#39;obiettivo è soddisfare le esigenze di comunicazione locale utilizzando un modello di campagna configurato e configurato dall&#39;entità centrale.

Il grado di autonomia dell&#39;entità locale dipende dall&#39;attuazione utilizzata.

Fate riferimento a [Creazione di una campagna](../../campaign/using/creating-a-local-campaign.md)locale.

### Campagna collaborativa {#collaborative-campaign}

Una campagna collaborativa è una campagna la cui pianificazione di **esecuzione è definita** dall&#39;entità centrale, che può essere utilizzata dall&#39;entità locale. Il contenuto rimane lo stesso per ogni entità locale, ma i costi vengono condivisi. Per partecipare, gli enti locali si iscrivono alla campagna collaborativa.

* **[!UICONTROL Collaborative campaign (by form)]**: consigliato per campagne che coinvolgono fino a 300 entità locali. L&#39;entità locale può immettere parametri predefiniti per il targeting e la personalizzazione del contenuto in un modulo Web. Il modulo può essere un modulo Adobe Campaign  o un modulo esterno (client extranet). Un amministratore funzionale può definire e configurare il modulo in base a un modello di modulo definito dall&#39;integratore. Per ordinare la campagna, l&#39;entità locale ha solo bisogno dell&#39;accesso Web.
* **[!UICONTROL Collaborative campaign (by campaign)]**: consigliato per campagne indirizzate a dozzine di entità locali. Questo tipo di campagna crea campagne figlio per ogni entità locale. Una volta **[!UICONTROL collaborative campaign (by campaign)]** approvata dall&#39;entità centrale, la campagna viene resa disponibile all&#39;entità locale, che può modificarla. L&#39;esecuzione viene sincronizzata automaticamente tra le campagne padre e figlio. L&#39;entità locale deve avere accesso a un&#39;istanza per ordinare una campagna e parteciparvi.
* **[!UICONTROL Collaborative campaign (by target approval)]**: consigliato per campagne indirizzate a diverse migliaia di enti locali. L&#39;entità locale riceve un elenco di contatti predefinito dall&#39;entità centrale. L&#39;entità locale decide se mantenere o meno determinati contatti in base al contenuto della campagna, tramite un modulo Web. Le entità locali sono dedotte dall&#39;elenco dei contatti selezionati. Per partecipare alla campagna, l&#39;entità locale ha solo bisogno dell&#39;accesso Web.
* **[!UICONTROL Collaborative campaign (simple)]**: questa modalità assicura la compatibilità con i processi di esecuzione specifici delle versioni precedenti.

Fate riferimento a [Creazione di una campagna](../../campaign/using/creating-a-collaborative-campaign.md)collaborativa.

### Ordinare pacchetti campagna {#ordering-campaign-packages}

Se un&#39;entità locale si registra per una campagna, questo viene trasformato in un ordine che raggruppa tutte le informazioni relative alla localizzazione della campagna.

## Area di lavoro {#workspace}

È possibile accedere all&#39;elenco dei pacchetti campagna dall&#39;universo **Campagne** : fare clic sul **[!UICONTROL Campaign packages]** collegamento.

![](assets/mkg_dist_home_local_op.png)

Questa finestra consente a tutti gli operatori locali di visualizzare le campagne disponibili per la propria agenzia locale.

Nel caso delle agenzie centrali, questa finestra visualizza tutti i pacchetti disponibili nell&#39;elenco dei pacchetti delle campagne e offre collegamenti aggiuntivi per la modifica dell&#39;elenco.

## Operatori ed entità {#operators-and-entities}

Iniziate specificando gli operatori di entità centrale e locale tramite la **[!UICONTROL Access management]** cartella.

![](assets/s_advuser_mkg_dist_tree.png)

### Operatori {#operators}

È necessario creare operatori centrali e locali.

Gli operatori centrali devono appartenere al gruppo di **[!UICONTROL Central management]** operatori o avere il diritto **[!UICONTROL CENTRAL]** denominato.

Gli operatori locali devono appartenere al gruppo di **[!UICONTROL Local management]** operatori o avere il diritto **[!UICONTROL LOCAL]** denominato. Devono anche essere collegati alla loro entità locale.

![](assets/s_advuser_mkg_dist_local_create.png)

### Entità organizzative {#organizational-entities}

Per creare un&#39;entità organizzativa, fate clic sul **[!UICONTROL Administration > Access management > Organizational entities]** nodo e fate clic sull&#39; **[!UICONTROL New]** icona sopra l&#39;elenco delle entità.

![](assets/s_advuser_mkg_dist_local_list.png)

Ogni entità organizzativa contiene informazioni di identificazione (etichetta, nome interno, informazioni di contatto, ecc.) e i gruppi coinvolti nel processo di approvazione dell&#39;ordine. Questi sono definiti nella **[!UICONTROL Notifications and approvals]** sezione trovata nella **[!UICONTROL General]** scheda.

* Definire un gruppo di notifiche di pacchetto: gli operatori di questo gruppo riceveranno una notifica ogni volta che un nuovo pacchetto viene aggiunto all&#39;elenco dei pacchetti campagna e ogni volta che una campagna diventa disponibile.
* Selezionare il gruppo di revisori incaricati di approvare gli ordini, ovvero quelli incaricati di approvare le campagne ordinate dall&#39;entità locale.
* Infine, selezionate il gruppo di revisori incaricati di approvare la campagna locale (target, contenuto, budget, ecc.). Questo gruppo può essere aggiunto al momento dell&#39;ordine di una campagna, a seconda del modello.

>[!NOTE]
>
>Il processo di approvazione viene presentato nella sezione Processo [di](../../campaign/using/creating-a-local-campaign.md#approval-process) approvazione.

## Implementazione {#implementation}

Le campagne Distributed Marketing vengono create e pubblicate dall&#39;entità centrale. Possono essere utilizzati sia dalle entità locali che da quelle centrali, a seconda delle necessità.

La procedura di implementazione dipende dal tipo di pacchetto campagna utilizzato e dai livelli di delega delle entità locali.

### Lato integratore {#integrator-side}

1. Creare entità locali.
1. Collegare i destinatari agli operatori che gestiscono le entità locali.

   ![](assets/mkg_dist_local_entity_association.png)

1. Specificare i diritti e le regole di navigazione per le entità locali
1. Specificate il set di campi necessari per la localizzazione della campagna:

   * definizione del target e dimensione massima,
   * definizione del contenuto,
   * programma di esecuzione (data di contatto e data di estrazione), solo **** per gli operatori locali,
   * estensione dello schema di ordine con tutti i campi aggiuntivi necessari.

1. Creare un modulo Web ( Adobe o extranet) che consenta di visualizzare i parametri di localizzazione, valutare la destinazione e il budget, nonché visualizzare in anteprima il contenuto e approvare l&#39;ordine.

   Per campagne **collaborative (per approvazione target)**, create la tabella in cui verranno salvate le approvazioni per ogni entità locale.

### lato amministratore funzionale {#functional-administrator-side}

Questi passaggi devono essere eseguiti durante la creazione di ogni campagna.

1. Aggiornare il modulo con i campi utilizzati per la localizzazione della campagna.
1. Create un&#39;istanza da un modello di campagna appropriato (campagna collaborativa) o duplicate il modello di campagna (campagna locale).
1. Configurare la campagna con i campi di localizzazione e il riferimento al modulo.
1. Pubblicate la campagna.

### Lato operatore locale {#local-operator-side}

Tali misure devono essere attuate per ogni campagna.

1. Dopo aver ricevuto la notifica della disponibilità del pacchetto della campagna, specificate il percorso della campagna (facoltativo).
1. Valutare l&#39;obiettivo, il budget, ecc.
1. Visualizzare l&#39;anteprima del contenuto della campagna.
1. Ordinate la campagna.

