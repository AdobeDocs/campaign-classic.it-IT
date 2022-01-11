---
product: campaign
title: Area di lavoro di Adobe Campaign
description: Scopri come utilizzare e personalizzare l’area di lavoro di Campaign
feature: Overview
role: Data Engineer
level: Beginner
exl-id: 5f689679-7148-4abd-a9bf-185854c64b13
source-git-commit: 1d32161d60f6b382188012b104c642f504e28645
workflow-type: tm+mt
source-wordcount: '909'
ht-degree: 5%

---

# Area di lavoro di Adobe Campaign{#adobe-campaign-workspace}

![](../../assets/common.svg)

## Interfaccia di Adobe Campaign {#about-adobe-campaign-interface}

Una volta connesso al database, potrai accedere alla home page di Adobe Campaign, che è un dashboard: è costituito da collegamenti e collegamenti che consentono di accedere alle funzionalità, a seconda dell’installazione e delle configurazioni generali della piattaforma.

Dalla sezione centrale della home page, puoi utilizzare i collegamenti per accedere al portale della documentazione online Campaign, al forum e al sito web di supporto.

![](assets/d_ncs_user_interface_home.png)

![](assets/do-not-localize/how-to-video.png)[ Scopri l’area di lavoro di Campaign nel video](#video)

>[!NOTE]
>
>Le funzionalità di Adobe Campaign disponibili nell’istanza dipendono dai moduli e dai componenti aggiuntivi installati. Alcune potrebbero anche non essere disponibili, a seconda delle autorizzazioni e delle configurazioni specifiche.
>
>Prima di installare qualsiasi modulo o componente aggiuntivo, è necessario controllare il contratto di licenza o contattare l&#39;amministratore dell&#39;account Adobe.

### Console e accesso web {#console-and-web-access}

La piattaforma Adobe Campaign è accessibile tramite una console o tramite un browser Internet. Vedi i browser compatibili nella [matrice di compatibilità](../../rn/using/compatibility-matrix.md#Browsers).

L’interfaccia di accesso web è simile a quella della console. Da un browser, puoi utilizzare le stesse funzioni di navigazione e visualizzazione della console, ma puoi eseguire solo un set ridotto di azioni sulle campagne. Ad esempio, puoi visualizzare e annullare le campagne, ma non modificarle. Per un determinato operatore, nella console viene visualizzata una campagna con le seguenti opzioni:

![Dal dashboard di una campagna, l’operatore può visualizzare e annullare una campagna, ma anche modificarla e aggiungervi consegne, documenti e attività.](assets/operation_from_console.png)

Mentre con l&#39;accesso al web, le opzioni consentiranno principalmente la visualizzazione:

![Da un browser, lo stesso operatore può solo visualizzare e annullare la campagna.](assets/operation_from_web.png)

Ulteriori informazioni [utilizzo dell’interfaccia web](../../campaign/using/accessing-marketing-campaigns.md#using-the-web-interface-).

### Lingue {#languages}

La lingua viene selezionata durante l’installazione dell’istanza Adobe Campaign Classic.

![](assets/language.png)

Puoi scegliere tra cinque lingue diverse:

* Inglese (Regno Unito)
* Inglese (Stati Uniti)
* Francese
* Tedesco
* Giapponese

La lingua scelta per l’istanza Adobe Campaign Classic potrebbe influire sui formati di data e ora. Per ulteriori informazioni, consulta questa [sezione](../../platform/using/adobe-campaign-workspace.md#date-and-time).

Per ulteriori informazioni su come creare un’istanza, consulta questo [page](../../installation/using/creating-an-instance-and-logging-on.md).

>[!CAUTION]
>
>Una volta creata l’istanza, non è possibile cambiare la lingua.

## Nozioni di base sulla navigazione {#navigation-basics}

### Sfoglia pagine {#browsing-pages}

Le varie funzionalità della piattaforma sono suddivise in funzionalità principali: utilizza i collegamenti visualizzati nella sezione superiore dell’interfaccia per accedervi.

![](assets/overview_home.png)

L’elenco delle funzionalità di base a cui puoi accedere dipende dai pacchetti e dai componenti aggiuntivi installati e dai diritti di accesso.

Ogni funzionalità include un set di funzionalità in base alle esigenze relative alle attività e al contesto di utilizzo. Ad esempio, il **[!UICONTROL Profiles and targets]** link ti porta agli elenchi dei destinatari, ai servizi di abbonamento, ai flussi di lavoro di targeting esistenti e alle scelte rapide per la creazione di questi elementi.

Gli elenchi sono disponibili tramite **[!UICONTROL Lists]** nella sezione a sinistra del **[!UICONTROL Profiles and Targets]** interfaccia.

![](assets/recipient_list_overview.png)

### Usa schede {#using-tabs}

* Quando fai clic su una funzionalità di base o su un collegamento, la pagina corrispondente sostituisce la pagina corrente. Per tornare alla pagina precedente, fai clic sul pulsante **[!UICONTROL Back]** sulla barra degli strumenti. Per tornare alla home page, fai clic sul pulsante **[!UICONTROL Home]** pulsante .

   ![](assets/d_ncs_user_interface_back_home_buttons.png)

* Nel caso di un menu o di un collegamento a una schermata di visualizzazione (ad esempio un’applicazione web, un programma, una consegna, un rapporto, ecc.), la pagina corrispondente viene visualizzata in un’altra scheda. Questo consente di spostarsi da una pagina all’altra utilizzando le schede.

   ![](assets/d_ncs_user_interface_tabs.png)

### Creare un elemento {#creating-an-element}

Ogni sezione delle funzionalità di base consente di navigare tra gli elementi disponibili. A questo scopo, utilizza le scelte rapide **[!UICONTROL Browsing]** sezione . La **[!UICONTROL Other choices]** link ti consente di accedere a tutte le altre pagine, indipendentemente dall’ambiente.

Puoi creare un nuovo elemento (consegna, applicazione Web, flusso di lavoro, ecc.) utilizzo delle scelte rapide **[!UICONTROL Create]** a sinistra dello schermo. Utilizza la **[!UICONTROL Create]** per aggiungere nuovi elementi all’elenco.

Ad esempio, nella pagina di consegna, utilizza il **[!UICONTROL Create]** per creare una nuova consegna.

![](assets/d_ncs_user_interface_tab_add_del.png)


## Formati e unità {#formats-and-units}

### Data e ora {#date-and-time}

La lingua dell’istanza Adobe Campaign Classic influisce sui formati di data e ora.

La lingua viene selezionata al momento dell’installazione di Campaign e non può essere modificata in seguito. Puoi selezionare: Inglese (USA), inglese (EN), francese, tedesco o giapponese. Per ulteriori informazioni, consulta [questa pagina](../../installation/using/creating-an-instance-and-logging-on.md).

Le principali differenze tra inglese americano e inglese britannico sono:

<table> 
 <thead> 
  <tr> 
   <th> Formati<br /> </th> 
   <th> Inglese (Stati Uniti)<br /> </th> 
   <th> Inglese (IT)<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Data<br /> </td> 
   <td> La settimana inizia la domenica<br /> </td> 
   <td> La settimana inizia il lunedì<br /> </td> 
  </tr> 
  <tr> 
   <td> Data breve<br /> </td> 
   <td> <p>%2M/%2D/%4Y</p><p><strong>ex: 25/09/2018</strong></p> </td> 
   <td> <p>%2D/%2M/%4Y</p><p><strong>ex: 09/25/2018</strong></p> </td> 
  </tr> 
  <tr> 
   <td> Data breve con ora<br /> </td> 
   <td> <p>%2M/%2D/%4Y %I:%2N:%2S %P</p><p><strong>ex: 25/09/2018 10:47:25</strong></p> </td> 
   <td> <p>%2D/%2M/%4Y %2H:%2N:%2S</p><p><strong>ex: 09/25/2018 22:47:25</strong></p> </td> 
  </tr> 
 </tbody> 
</table>

### Aggiungere valori in un’enumerazione {#add-values-in-an-enumeration}

Utilizzando i campi di input con un elenco a discesa, puoi immettere un valore di enumerazione, che può essere memorizzato e quindi offerto come opzione nell’elenco a discesa. Ad esempio, nella **[!UICONTROL City]** campo **[!UICONTROL General]** scheda di un profilo destinatario, puoi accedere a Londra. Quando si preme Invio per confermare questo valore, viene richiesto se si desidera salvare questo valore per l&#39;enumerazione associata al campo.

![](assets/s_ncs_user_wizard_email_bat_substitute_email.png)

Se fai clic su **[!UICONTROL Yes]**, questo valore sarà disponibile nella casella combinata del campo pertinente (in questo caso: **[!UICONTROL London]**).

>[!NOTE]
>
>Le enumerazioni (dette anche &quot;elenchi dettagliati&quot;) sono gestite dall’amministratore tramite il **[!UICONTROL Administration > Platform > Enumerations]** sezione . Per ulteriori informazioni, consulta [Gestione delle enumerazioni](../../platform/using/managing-enumerations.md).

### Unità predefinite {#default-units}

Nei campi che esprimono una durata (ad esempio il periodo di validità delle risorse di una consegna, il termine di approvazione di un&#39;attività, ecc.), il valore può essere espresso nel seguente **unità**:

* **[!UICONTROL s]** per secondi,
* **[!UICONTROL mn]** per i minuti,
* **[!UICONTROL h]** per ore,
* **[!UICONTROL d]** per giorni.

![](assets/enter_unit_sample.png)

## Video tutorial {#video}

Questo video presenta lo spazio di lavoro di Campaign Classic.

>[!VIDEO](https://video.tv.adobe.com/v/35130?quality=12)

Sono disponibili ulteriori video dimostrativi su Campaign Classic [qui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=it).
