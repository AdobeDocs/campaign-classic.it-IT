---
product: campaign
title: Definire il layout dei moduli web
description: Definire il layout dei moduli web
feature: Web Forms
exl-id: 23ca17f8-de1a-4f9c-8357-3965dc3329b1
source-git-commit: b6f1556cf49492cefaf61c29a058584b0ccee16a
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 2%

---

# Definire il layout dei moduli web{#defining-web-forms-layout}

![](../../assets/common.svg)

## Creazione di contenitori {#creating-containers}

I contenitori consentono di combinare i campi di una pagina e di configurarne il layout; per organizzare gli elementi nella pagina.

Per ogni pagina del modulo, i contenitori vengono creati tramite il **[!UICONTROL Containers]** pulsante della barra degli strumenti.

![](assets/s_ncs_admin_survey_containers_add.png)

Utilizza un contenitore per raggruppare gli elementi della pagina senza aggiungere un’etichetta al rendering finale. Gli elementi sono raggruppati nella sottostruttura del contenitore. I contenitori standard consentono di gestire il layout.

Ad esempio:

![](assets/s_ncs_admin_survey_containers_std_arbo.png)

La posizione delle etichette viene applicata agli elementi posizionati sotto il contenitore nella gerarchia. Se necessario, può essere sovraccaricato per ogni elemento. Aggiungere o rimuovere colonne per modificare il layout. Vedi [Posizionamento dei campi nella pagina](#positioning-the-fields-on-the-page).

Nell’esempio precedente, il rendering sarà il seguente:

![](assets/s_ncs_admin_survey_containers_std_ex.png)

## Posizionamento dei campi nella pagina {#positioning-the-fields-on-the-page}

Il layout del modulo Web viene definito pagina per pagina in ciascun contenitore e può essere sovraccaricato, se necessario.

Le pagine sono suddivise in colonne: ogni pagina contiene un certo numero di colonne. Ogni campo della pagina occupa **n** celle. I contenitori occupano anche un certo numero di colonne e i campi che contengono occupano un certo numero di celle.

Per impostazione predefinita, le pagine sono create su una singola colonna e ogni elemento occupa una cella. Ciò significa che i campi vengono visualizzati uno sotto l’altro, ciascuno dei quali occupa un’intera linea, come illustrato di seguito:

![](assets/s_ncs_admin_survey_container_ex.png)

Nell’esempio seguente, la configurazione predefinita è stata mantenuta. La pagina occupa una singola colonna che include quattro contenitori.

![](assets/s_ncs_admin_survey_container_ex0.png)

Ogni contenitore occupa una colonna e ogni elemento occupa una cella:

![](assets/s_ncs_admin_survey_container_ex0a.png)

Il rendering è il seguente:

![](assets/s_ncs_admin_survey_container_ex0_rend.png)

È possibile adattare i parametri di visualizzazione per ottenere il rendering seguente:

![](assets/s_ncs_admin_survey_container_ex1_rend.png)

Nell’esempio di rendering precedente, ogni campo di input, titolo e immagine occupa una cella nelle colonne dei contenitori.

Puoi modificare la formattazione in ogni contenitore. Nel nostro esempio, puoi distribuire il contenuto del contenitore 4 su due colonne e distribuire gli elementi.

![](assets/s_ncs_admin_survey_container_ex2_rend.png)

Il titolo e l’elenco occupano una cella ciascuna (e quindi un’intera riga del contenitore) e la casella di controllo si estende su due celle. Il numero di celle attribuite al campo di input è definito nella **[!UICONTROL General]** oppure **[!UICONTROL Advanced]** , in base al tipo di campo:

![](assets/s_ncs_admin_survey_container_ex2.png)

## Definizione della posizione delle etichette {#defining-the-position-of-labels}

È possibile definire l’allineamento di campi ed etichette nel modulo.

Per impostazione predefinita, i parametri di visualizzazione dei campi e di altro contenuto della pagina vengono ereditati dalla configurazione generale del modulo, dalla configurazione della pagina o dalla configurazione del contenitore principale, se presente.

I parametri di visualizzazione globali per l’intero modulo sono specificati nella casella delle proprietà del modulo. La **[!UICONTROL Rendering]** consente di selezionare la posizione delle etichette.

![](assets/s_ncs_admin_survey_label_position.png)

Questa posizione può essere sovraccaricata per ogni pagina, contenitore e campo, tramite **[!UICONTROL Advanced]** scheda .

Sono supportati i seguenti allineamenti:

* Ereditato: l’allineamento viene ereditato dall’elemento padre (valore predefinito), ovvero l’eventuale contenitore principale, oppure dalla pagina.
* Sinistra/Destra: l’etichetta è posizionata a destra o a sinistra del campo,
* Sopra/sotto: l’etichetta è posizionata sopra o sotto il campo,
* Nascosto: l’etichetta non viene visualizzata.
