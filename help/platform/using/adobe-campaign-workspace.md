---
product: campaign
title: Area di lavoro di Adobe Campaign
description: Scopri come utilizzare e personalizzare l’area di lavoro di Campaign
feature: Overview
role: Data Engineer
level: Beginner
exl-id: 5f689679-7148-4abd-a9bf-185854c64b13
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '916'
ht-degree: 5%

---

# Area di lavoro di Adobe Campaign{#adobe-campaign-workspace}



## Esplora l’interfaccia di Adobe Campaign {#about-adobe-campaign-interface}

Una volta connesso al database, accedi alla home page di Adobe Campaign, che è una dashboard: è costituita da collegamenti e scelte rapide che ti consentono di accedere alle funzionalità, a seconda dell’installazione e delle configurazioni generali della piattaforma.

Dalla sezione centrale della home page, puoi utilizzare i collegamenti per accedere al portale della documentazione online di Campaign, al forum e al sito web di supporto.

![](assets/d_ncs_user_interface_home.png)

![](assets/do-not-localize/how-to-video.png) Scopri l&#39;area di lavoro di Campaign in [video](#video)

>[!NOTE]
>
>Le funzionalità di Adobe Campaign disponibili nell’istanza dipendono dai moduli e dai componenti aggiuntivi installati. Alcuni di essi potrebbero anche non essere disponibili, a seconda delle autorizzazioni e delle configurazioni specifiche.
>
>Prima di installare qualsiasi modulo o componente aggiuntivo, è necessario verificare il contratto di licenza o contattare il responsabile dell’account Adobe.

### Console e accesso web {#console-and-web-access}

La piattaforma Adobe Campaign è accessibile tramite una console o un browser Internet. Vedere i browser compatibili nella [matrice di compatibilità](../../rn/using/compatibility-matrix.md#Browsers).

L’interfaccia di accesso web è simile all’interfaccia della console. Da un browser, puoi utilizzare le stesse funzioni di navigazione e visualizzazione della console, ma puoi eseguire solo un set ridotto di azioni sulle campagne. Ad esempio, puoi visualizzare e annullare le campagne, ma non puoi modificarle. Per un determinato operatore, viene visualizzata una campagna con le seguenti opzioni nella console:

![Dal dashboard di una campagna, l&#39;operatore può visualizzare e annullare una campagna, ma anche modificarla e aggiungervi consegne, documenti e attività.](assets/operation_from_console.png)

Mentre con l’accesso web, le opzioni consentono principalmente la visualizzazione di:

![Da un browser, lo stesso operatore può solo visualizzare e annullare la campagna.](assets/operation_from_web.png)

Ulteriori informazioni su [tramite l&#39;interfaccia Web](../../campaign/using/accessing-marketing-campaigns.md#using-the-web-interface-).

### Lingue {#languages}

La lingua viene selezionata al momento dell’installazione dell’istanza di Adobe Campaign Classic.

![](assets/language.png)

Puoi scegliere tra cinque lingue diverse:

* Inglese (Regno Unito)
* Inglese (Stati Uniti)
* Francese
* Tedesco
* Giapponese

La lingua scelta per l’istanza di Adobe Campaign Classic potrebbe influire sui formati di data e ora. Per ulteriori informazioni, consulta questa [sezione](../../platform/using/adobe-campaign-workspace.md#date-and-time).

Per ulteriori informazioni su come creare un&#39;istanza, consulta questa [pagina](../../installation/using/creating-an-instance-and-logging-on.md).

>[!CAUTION]
>
>Una volta creata l’istanza, non è possibile cambiare la lingua.

## Nozioni di base sulla navigazione {#navigation-basics}

### Sfoglia pagine {#browsing-pages}

Le varie funzionalità della piattaforma sono suddivise in funzionalità principali: utilizza i collegamenti riportati nella sezione superiore dell’interfaccia per accedervi.

![](assets/overview_home.png)

L’elenco delle funzionalità di base a cui puoi accedere dipende dai pacchetti e dai componenti aggiuntivi installati e dai tuoi diritti di accesso.

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

È possibile creare un nuovo elemento (consegna, applicazione Web, flusso di lavoro, ecc.) utilizzando i tasti di scelta rapida nella sezione **[!UICONTROL Create]** a sinistra dello schermo. Utilizza il pulsante **[!UICONTROL Create]** sopra l&#39;elenco per aggiungere nuovi elementi all&#39;elenco.

Ad esempio, nella pagina di consegna, utilizza il pulsante **[!UICONTROL Create]** per creare una nuova consegna.

![](assets/d_ncs_user_interface_tab_add_del.png)


## Formati e unità {#formats-and-units}

### Data e ora {#date-and-time}

La lingua dell’istanza Adobe Campaign Classic influisce sui formati di data e ora.

La lingua viene selezionata durante l’installazione di Campaign e non può essere modificata in seguito. È possibile selezionare: Inglese (Stati Uniti), Inglese (Italia), Francese, Tedesco o Giapponese. Per ulteriori informazioni, consulta [questa pagina](../../installation/using/creating-an-instance-and-logging-on.md).

Le principali differenze tra l&#39;inglese americano e l&#39;inglese britannico sono:

<table> 
 <thead> 
  <tr> 
   <th> Formati<br /> </th> 
   <th> Inglese (Stati Uniti)<br /> </th> 
   <th> Inglese (EN)<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Data<br /> </td> 
   <td> La settimana inizia di domenica<br /> </td> 
   <td> La settimana inizia il lunedì<br /> </td> 
  </tr> 
  <tr> 
   <td> Data breve<br /> </td> 
   <td> <p>%2M/%2D/%4Y</p><p><strong>es: 09/25/2018</strong></p> </td> 
   <td> <p>%2D/%2M/%4Y</p><p><strong>es: 25/09/2018</strong></p> </td> 
  </tr> 
  <tr> 
   <td> Data breve con ora<br /> </td> 
   <td> <p>%2M/%2D/%4Y %I:%2N:%2S %P</p><p><strong>es: 09/25/2018 10:47:25 PM</strong></p> </td> 
   <td> <p>%2D/%2M/%4Y %2H:%2N:%2S</p><p><strong>es: 25/09/2018 22:47:25</strong></p> </td> 
  </tr> 
 </tbody> 
</table>

### Aggiungere valori in un’enumerazione {#add-values-in-an-enumeration}

Utilizzando i campi di input con un elenco a discesa, puoi immettere un valore di enumerazione, che può essere memorizzato e quindi offerto come opzione nell’elenco a discesa. Ad esempio, nel campo **[!UICONTROL City]** della scheda **[!UICONTROL General]** di un profilo destinatario, puoi immettere Londra. Quando premi Invio per confermare questo valore, viene visualizzato un messaggio in cui viene richiesto se desideri salvare questo valore per l’enumerazione associata al campo.

![](assets/s_ncs_user_wizard_email_bat_substitute_email.png)

Se si fa clic su **[!UICONTROL Yes]**, questo valore sarà disponibile nella casella combinata del campo pertinente (in questo caso: **[!UICONTROL London]**).

>[!NOTE]
>
>Le enumerazioni (note anche come &quot;elenchi dettagliati&quot;) sono gestite dall&#39;amministratore tramite la sezione **[!UICONTROL Administration > Platform > Enumerations]**. Per ulteriori informazioni, consulta [Gestione delle enumerazioni](../../platform/using/managing-enumerations.md).

### Unità predefinite {#default-units}

Nei campi che esprimono una durata (ad esempio periodo di validità delle risorse di una consegna, scadenza dell&#39;approvazione per un&#39;attività, ecc.), il valore può essere espresso nelle seguenti **unità**:

* **[!UICONTROL s]** per secondi,
* **[!UICONTROL mn]** per minuti,
* **[!UICONTROL h]** per ore,
* **[!UICONTROL d]** per giorni.

![](assets/enter_unit_sample.png)

## Video tutorial {#video}

Questo video presenta l’area di lavoro di Campaign Classic.

>[!VIDEO](https://video.tv.adobe.com/v/35130?quality=12)

Ulteriori video dimostrativi di Campaign Classic sono disponibili [qui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=it).
