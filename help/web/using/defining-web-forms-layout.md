---
title: Definizione del layout dei moduli web
seo-title: Definizione del layout dei moduli web
description: Definizione del layout dei moduli web
seo-description: null
page-status-flag: never-activated
uuid: ae8659d0-3608-44dd-93ec-33c418a66ad0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-forms
discoiquuid: 67d1d39b-3a5f-4ed6-8fcf-570891043b10
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 3%

---


# Definizione del layout dei moduli web{#defining-web-forms-layout}

## Creazione di contenitori {#creating-containers}

I contenitori consentono di combinare i campi di una pagina e configurarne il layout; per organizzare gli elementi nella pagina.

Per ciascuna pagina del modulo, i contenitori vengono creati mediante il **[!UICONTROL Containers]** pulsante della barra degli strumenti.

![](assets/s_ncs_admin_survey_containers_add.png)

Utilizzate un contenitore per raggruppare gli elementi della pagina senza aggiungere un&#39;etichetta al rendering finale. Gli elementi sono raggruppati nella sottostruttura ad albero contenitore. I contenitori standard consentono di gestire il layout.

Ad esempio:

![](assets/s_ncs_admin_survey_containers_std_arbo.png)

La posizione delle etichette viene applicata agli elementi posizionati sotto il contenitore nella gerarchia. Può essere sovraccaricato per ogni elemento, se necessario. Aggiungete o rimuovete colonne per modificare il layout. Consultate [Posizionamento dei campi sulla pagina](#positioning-the-fields-on-the-page).

Nell&#39;esempio precedente, il rendering sarà il seguente:

![](assets/s_ncs_admin_survey_containers_std_ex.png)

## Posizionamento dei campi sulla pagina {#positioning-the-fields-on-the-page}

Il layout del modulo Web è definito pagina per pagina in ciascun contenitore e può essere sovraccaricato per ogni controllo.

Le pagine sono suddivise in colonne: ogni pagina contiene un certo numero di colonne. Ogni campo della pagina occupa **una** cella. I contenitori occupano anche un certo numero di colonne e i campi che contengono occupano un certo numero di celle

Per impostazione predefinita, le pagine sono create su una singola colonna e ogni elemento occupa una cella. Ciò significa che i campi sono visualizzati uno sotto l&#39;altro, ciascuno dei quali occupa un&#39;intera linea, come mostrato di seguito:

![](assets/s_ncs_admin_survey_container_ex.png)

Nell&#39;esempio seguente è stata mantenuta la configurazione predefinita. La pagina occupa una singola colonna che include quattro contenitori.

![](assets/s_ncs_admin_survey_container_ex0.png)

Ogni contenitore occupa una colonna e ogni elemento occupa una cella:

![](assets/s_ncs_admin_survey_container_ex0a.png)

Il rendering è il seguente:

![](assets/s_ncs_admin_survey_container_ex0_rend.png)

Potete adattare i parametri di visualizzazione per ottenere il seguente rendering:

![](assets/s_ncs_admin_survey_container_ex1_rend.png)

Nell&#39;esempio di rendering precedente, ciascun campo di input, titolo e immagine occupa una cella nelle colonne dei contenitori.

Potete modificare la formattazione in ciascun contenitore. Nel nostro esempio, potete distribuire il contenuto del contenitore 4 su due colonne e distribuire gli elementi.

![](assets/s_ncs_admin_survey_container_ex2_rend.png)

Il titolo e l’elenco occupano una cella ciascuna (e quindi un’intera riga del contenitore) e la casella di controllo si estende su due celle. Il numero di celle attribuito al campo di input è definito nella **[!UICONTROL General]** scheda o nella **[!UICONTROL Advanced]** scheda, in base al tipo di campo:

![](assets/s_ncs_admin_survey_container_ex2.png)

## Definizione della posizione delle etichette {#defining-the-position-of-labels}

È possibile definire l&#39;allineamento dei campi e delle etichette nel modulo.

Per impostazione predefinita, i parametri di visualizzazione per i campi e altro contenuto della pagina sono ereditati dalla configurazione generale del modulo, dalla configurazione della pagina o dalla configurazione del contenitore principale, se esistente.

I parametri di visualizzazione globali per l&#39;intero modulo sono specificati nella casella delle proprietà del modulo. La **[!UICONTROL Rendering]** scheda consente di selezionare la posizione delle etichette.

![](assets/s_ncs_admin_survey_label_position.png)

Questa posizione può essere sovraccaricata per ogni pagina, contenitore e campo tramite la **[!UICONTROL Advanced]** scheda.

Sono supportati i seguenti allineamenti:

* Ereditato: l&#39;allineamento viene ereditato dall&#39;elemento padre (valore predefinito), ovvero dal contenitore principale, se presente, oppure dalla pagina.
* Sinistra/Destra: l&#39;etichetta è posizionata a destra o a sinistra del campo,
* Sopra/sotto: l&#39;etichetta è posizionata sopra o sotto il campo,
* Nascosto: l&#39;etichetta non viene visualizzata.

