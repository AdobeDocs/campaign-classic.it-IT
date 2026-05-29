---
product: campaign
title: Area di lavoro di Adobe Campaign
description: Scopri come utilizzare e personalizzare l’area di lavoro di Campaign
feature: Overview
role: Developer
level: Beginner
exl-id: 5f689679-7148-4abd-a9bf-185854c64b13
TQID: https://experienceleague.adobe.com/eM26PQIIHJHC-7-QqVYaC9uHcvrYIpi87vMB4eTmVlg
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: afa4204e-6d08-4e29-bc35-26aafb656d48
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
subfeature_v2:
  - id: f529d0bd-1401-4c88-9833-43228cc1d40f
  - id: d6330382-c886-4f7a-a4f7-74e3f36c0d9c
  - id: f5293531-9312-4099-bfa3-9e67df6a8750
  - id: efa38731-2723-4334-8d8b-a778af834835
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 1316
ht-degree: 5%

---

# Area di lavoro di Adobe Campaign {#adobe-campaign-workspace}

## Esplora l’interfaccia di Adobe Campaign {#about-adobe-campaign-interface}

Una volta connessi al database, si accede alla home page di Adobe Campaign. Questa pagina è il tuo dashboard: è composta da collegamenti e scelte rapide che ti consentono di accedere alle funzionalità, a seconda dell’installazione e delle configurazioni generali della piattaforma.

Dalla sezione centrale della home page, puoi utilizzare i collegamenti per accedere al portale della documentazione di Campaign, alla community e al sito web dell’Assistenza clienti di Adobe.

![](assets/d_ncs_user_interface_home.png)

![](assets/do-not-localize/how-to-video.png) Scopri l&#39;area di lavoro di Campaign in [video](#video)

>[!NOTE]
>
>Le funzionalità di Adobe Campaign disponibili nell’istanza dipendono dai moduli e dai componenti aggiuntivi installati. Alcuni di essi potrebbero anche non essere disponibili, a seconda delle autorizzazioni e delle configurazioni specifiche.
>
>Prima di installare qualsiasi modulo o componente aggiuntivo, è necessario verificare il contratto di licenza o contattare il responsabile commerciale di Adobe.

### Console e accesso web {#console-and-web-access}

La piattaforma Adobe Campaign è accessibile tramite una console o un browser Internet. Vedere i browser compatibili nella [matrice di compatibilità](../../rn/using/compatibility-matrix.md#Browsers).

L’interfaccia di accesso web è simile all’interfaccia della console. Da un browser, puoi utilizzare le stesse funzioni di navigazione e visualizzazione della console, ma puoi eseguire solo un set ridotto di azioni sulle campagne. Ad esempio, puoi visualizzare e annullare le campagne, ma non puoi modificarle. Per un determinato operatore, viene visualizzata una campagna con le seguenti opzioni nella console:

![Dal dashboard di una campagna, l&#39;operatore può visualizzare e annullare una campagna, ma anche modificarla e aggiungervi consegne, documenti e attività.](assets/operation_from_console.png)

Mentre con l’accesso web, le opzioni consentono principalmente la visualizzazione di:

![Da un browser, lo stesso operatore può solo visualizzare e annullare la campagna.](assets/operation_from_web.png)

Ulteriori informazioni sull&#39;utilizzo dell&#39;interfaccia Web sono disponibili nella [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-create.html?lang=it#use-the-web-interface-){target=_blank}.

### Lingue {#languages}

La lingua viene selezionata al momento dell’installazione dell’istanza di Adobe Campaign Classic.

![](assets/language.png)

Puoi scegliere tra le seguenti lingue:

* Inglese (Regno Unito)
* Inglese (Stati Uniti)
* Francese
* Tedesco
* Giapponese

La lingua scelta per l’istanza di Adobe Campaign Classic potrebbe influire sui formati di data e ora. Per ulteriori informazioni, consulta la [documentazione di Campaign v8 (console)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/new/campaign-ui){target=_blank}.

Per ulteriori informazioni su come creare un&#39;istanza, consulta questa [pagina](../../installation/using/creating-an-instance-and-logging-on.md).

>[!CAUTION]
>
>Una volta creata l’istanza, non è possibile cambiare la lingua.

## Nozioni di base sulla navigazione {#navigation-basics}

Le varie funzionalità della piattaforma sono suddivise in funzionalità principali: utilizza i collegamenti riportati nella sezione superiore dell’interfaccia per accedervi.

![](assets/overview_home.png)

L’elenco delle funzionalità di base a cui puoi accedere dipende dai pacchetti e dai componenti aggiuntivi installati e dai tuoi diritti di accesso.

### Sfoglia pagine {#browsing-pages}

Ogni funzionalità include una serie di funzionalità basate su esigenze correlate alle attività e sul contesto di utilizzo. Ad esempio, il collegamento **[!UICONTROL Profiles and targets]** ti consente di accedere agli elenchi dei destinatari, ai servizi di abbonamento, ai flussi di lavoro di targeting esistenti e alle scelte rapide per la creazione di questi elementi.

Gli elenchi sono disponibili tramite il collegamento **[!UICONTROL Lists]** nella sezione a sinistra dell&#39;interfaccia **[!UICONTROL Profiles and Targets]**.

![](assets/recipient_list_overview.png)

### Utilizzare le schede {#using-tabs}

* Quando fai clic su una funzionalità di base o su un collegamento, la pagina pertinente sostituisce la pagina corrente. Per tornare alla pagina precedente, fare clic sul pulsante **[!UICONTROL Back]** sulla barra degli strumenti. Per tornare alla home page, fare clic sul pulsante **[!UICONTROL Home]**.

  ![](assets/d_ncs_user_interface_back_home_buttons.png)

* Nel caso di un menu o di un collegamento a una schermata di visualizzazione (ad esempio un’applicazione web, un programma, una consegna, un rapporto, ecc.), la pagina corrispondente viene visualizzata in un’altra scheda. Questo consente di navigare da una pagina all’altra utilizzando le schede.

  ![](assets/d_ncs_user_interface_tabs.png)

### Creare un elemento {#creating-an-element}

Ogni sezione sulle funzionalità di base ti consente di sfogliare tra gli elementi disponibili. A tale scopo, utilizzare le scelte rapide della sezione **[!UICONTROL Browsing]**. Il collegamento **[!UICONTROL Other choices]** consente di accedere a tutte le altre pagine, indipendentemente dall&#39;ambiente.

Puoi creare un nuovo elemento (consegna, applicazione web, flusso di lavoro, ecc.) utilizzo delle scelte rapide nella sezione **[!UICONTROL Create]** a sinistra dello schermo. Utilizza il pulsante **[!UICONTROL Create]** sopra l&#39;elenco per aggiungere nuovi elementi all&#39;elenco.

Ad esempio, nella pagina della consegna, utilizza il pulsante **[!UICONTROL Create]** per creare una nuova consegna.

![](assets/d_ncs_user_interface_tab_add_del.png)


## Utilizzare Adobe Campaign Explorer {#using-adobe-campaign-explorer}

Adobe Campaign Explorer è accessibile tramite l’icona della barra degli strumenti. Consente di accedere a tutte le funzionalità di Adobe Campaign, alle schermate di configurazione e a una visualizzazione più dettagliata di alcuni elementi della piattaforma.

Per ulteriori informazioni su Adobe Campaign Explorer, consulta queste pagine nella **documentazione di Campaign v8 (console)**:

* [Panoramica dell’interfaccia utente di Campaign](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/new/campaign-ui){target=_blank}

* [Impostazioni interfaccia utente di Campaign](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/config/configuration/ui-settings){target=_blank}

* [Gestire cartelle e visualizzazioni in Esplora risorse](https://experienceleague.adobe.com/it/docs/campaign/campaign-v8/config/configuration/folders-and-views){target=_blank}


## Utilizzare i dati {#work-with-data}

### Filtrare i dati {#filters}

Il filtro dei dati consiste nel restringere un set di dati solo ai record che corrispondono a criteri specifici. Questo sottoinsieme può quindi essere utilizzato per azioni mirate (come aggiornamenti o creazione di tipi di pubblico) o per l’analisi.

Durante la navigazione in Campaign, i dati vengono visualizzati negli elenchi. Puoi applicare filtri incorporati per accedere rapidamente a un sottoinsieme definito, ad esempio indirizzi messi in quarantena, destinatari non mirati o record all’interno di un intervallo di età o di una data di creazione specifici. Inoltre, puoi creare filtri personalizzati, salvarli per utilizzi futuri e condividerli con altri utenti di Campaign.

Scopri come **accedere, progettare e condividere filtri** nella [documentazione di Campaign v8 (console)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/audience/create-filters){target=_blank}.

### Eseguire query sul database{#about-queries-in-campaign}

Lo strumento di query è disponibile a vari livelli dell’applicazione e può essere utilizzato per definire popolazioni target, segmentare i clienti, estrarre e filtrare i registri di tracciamento, creare filtri e altro ancora.

+++Informazioni sull’editor di query generico

Fornisce un assistente dedicato, l&#39;editor di query generico, accessibile dal menu **[!UICONTROL Tools > Generic query editor...]**. Questo editor consente alle query di database di estrarre, organizzare, raggruppare e ordinare le informazioni. Ad esempio, può recuperare i destinatari che hanno fatto clic più di n volte su un collegamento a una newsletter durante un determinato periodo di tempo.

L’editor di query generico centralizza tutte le funzionalità di query. Consente la creazione e l’archiviazione di filtri di restrizione, che possono quindi essere riutilizzati in altri contesti, ad esempio la casella Query di un flusso di lavoro di targeting.

![Accedere all&#39;editor delle query e selezionare una tabella](assets/query_editor_nveau_21.png)

+++

>[!BEGINTABS]

>[!TAB Eseguire una query sul database]

I passaggi per creare una query sono descritti in dettaglio nella **[documentazione di Campaign v8 (console)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/data/query/query-editor){target=_blank}**


[![immagine](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/data/query/query-editor){target=_blank}


>[!TAB Aggiungere una query in un flusso di lavoro]

Scopri i passaggi chiave relativi alla creazione di query nel contesto di un flusso di lavoro nella **[documentazione di Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/automation/workflows/wf-activities/targeting-activities/query){target=_blank}**

[![immagine](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/en/docs/campaign/automation/workflows/wf-activities/targeting-activities/query){target=_blank}

>[!TAB Condizioni filtro]

Per progettare la query, è necessario selezionare le condizioni di filtro nell’editor delle query. Le funzionalità disponibili e i casi di utilizzo sono descritti in dettaglio nella **[documentazione di Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/data/query/filter-conditions){target=_blank}**

[![immagine](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/data/query/filter-conditions){target=_blank}

>[!ENDTABS]

### Gestisci elenchi {#manage-and-customize-lists}

Nella console client di Campaign, i dati vengono visualizzati in elenchi. È possibile adattare questi elenchi alle proprie esigenze. Ad esempio, puoi aggiungere colonne, filtrare dati, contare record, salvare e condividere le impostazioni.

Scopri come **gestire e personalizzare gli elenchi** nella [documentazione di Campaign v8 (console)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/config/configuration/ui-settings#customize-lists){target=_blank}.

### Gestire le enumerazioni{#managing-enumerations}

Un’enumerazione (detta anche elenco dettagliato) è un elenco predefinito di valori che è possibile utilizzare per compilare determinati campi. Le enumerazioni consentono di standardizzare i valori dei campi, rendendo più coerente l&#39;immissione dei dati e semplificando le query.

Una volta definiti, i valori vengono visualizzati in un elenco a discesa. Un valore può essere selezionato direttamente o immesso utilizzando l’input predittivo, che suggerisce e completa le voci corrispondenti. Alcuni campi includono enumerazioni predefinite; se necessario, è possibile creare enumerazioni aggiuntive.

Scopri come **utilizzare le enumerazioni** nella [documentazione di Adobe Campaign v8 (console)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/config/settings/enumerations){target=_blank}.

## Video tutorial {#video}

Questo video presenta l’area di lavoro di Campaign Classic.

>[!VIDEO](https://video.tv.adobe.com/v/35130?quality=12)
