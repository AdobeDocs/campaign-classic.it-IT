---
product: campaign
title: Esempi di app Facebook
description: Esempi di app Facebook
audience: social
content-type: reference
topic-tags: annexes
exl-id: 3b8c7db4-9c55-42f6-8e09-e5ab781efe8f
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1981'
ht-degree: 1%

---

# Esempi di app Facebook{#examples-of-facebook-apps}

Quando un utente fa clic sulla scheda di un&#39;applicazione Facebook, questa viene visualizzata in uno spazio largo 810 pixel. Adobe Campaign utilizza un’applicazione web di tipo Facebook per consentire di definire e personalizzare il contenuto visualizzato nell’applicazione Facebook, facilitando quindi l’acquisizione dei profili.

>[!NOTE]
>
>È inoltre possibile integrare Adobe Campaign con un’applicazione Facebook sviluppata da un partner. In questo caso, non è necessario utilizzare l’applicazione web Adobe Campaign per acquisire profili Facebook. Per ulteriori informazioni, consulta [Configurazione di account esterni](../../social/using/creating-a-facebook-application.md#configuring-external-accounts).

![](assets/social_webapp_fb_000.png)

>[!IMPORTANT]
>
>Attieniti ai passaggi di configurazione descritti in [Creazione di un&#39;applicazione Facebook](../../social/using/creating-a-facebook-application.md).

>[!NOTE]
>
>Questa sezione descrive gli elementi collegati alle applicazioni web di tipo Facebook. Tutti gli elementi condivisi con le applicazioni web standard sono descritti in [questa sezione](../../web/using/about-web-applications.md).

Gli esempi di applicazioni web di tipo Facebook descritti di seguito sono:

* Come creare un&#39;applicazione Facebook in 7 passaggi. Fare riferimento a [Avvio rapido: creazione di un&#39;applicazione Facebook in 7 passaggi](#quick-start--creating-a-facebook-application-in-7-steps).
* Come inoltrare le impostazioni a un&#39;applicazione Facebook. Fare riferimento a [Come inoltrare le impostazioni a un&#39;applicazione Facebook?](#how-to-forward-settings-to-a-facebook-application-).
* Come acquisire i dati della ventola. Fare riferimento a [Come acquisire i dati della ventola?](#how-to-acquire-fan-data-).

>[!IMPORTANT]
>
>Questi semplici casi d’uso sono forniti come esempi per illustrare le funzionalità delle applicazioni web di tipo Facebook.

## Raccomandazioni {#recommendations}

Le seguenti limitazioni sono collegate direttamente a Facebook:

* Devi creare tutte le tue applicazioni web in HTTPS.
* Un&#39;applicazione Facebook visualizzata tramite una scheda ha una larghezza di 810 pixel.

## Avvio rapido: creazione di un&#39;applicazione Facebook in 7 passaggi {#quick-start--creating-a-facebook-application-in-7-steps}

Questo esempio fornisce un processo dettagliato su come visualizzare un’applicazione integrata in Adobe Campaign in Facebook. In questo caso, vogliamo creare un&#39;applicazione che ti consenta di visualizzare il messaggio **Benvenuto** quando l&#39;utente fa clic sulla scheda dell&#39;applicazione (**App01**).

Per creare questa applicazione, esegui i seguenti passaggi:

1. Crea un&#39;applicazione su Facebook ( [https://developers.facebook.com/apps](https://developers.facebook.com/apps)). Per ulteriori informazioni, consulta: [Creazione di un&#39;applicazione Facebook](../../social/using/publishing-on-facebook-walls.md#creating-a-facebook-application).

   ![](assets/social_create_facebook_app_002.png)

1. Crea un account esterno di tipo **[!UICONTROL Facebook Connect]** e immetti i parametri dell’applicazione Facebook. Per ulteriori informazioni, consulta: [Configurazione di account esterni](../../social/using/creating-a-facebook-application.md#configuring-external-accounts).

   ![](assets/social_quick_start_2.png)

1. Immetti i collegamenti **[!UICONTROL Terms of service]** e **[!UICONTROL Privacy policy]** da visualizzare nella schermata di richiesta delle autorizzazioni di Facebook. Per ulteriori informazioni, consulta: [Inserimento dei termini del servizio e dei collegamenti all&#39;informativa sulla privacy](../../social/using/creating-a-facebook-application.md#entering-the-terms-of-service-and-privacy-policy-links).

   ![](assets/social_quick_start_1.png)

1. Crea un&#39;applicazione web di tipo Facebook in Adobe Campaign. Per ulteriori informazioni, consulta: [Creazione di un&#39;applicazione Web di tipo Facebook](../../social/using/creating-a-facebook-application.md#creating-a-facebook-type-web-application).

   ![](assets/social_webapp_005.png)

1. Modifica l&#39;applicazione web. In questo esempio, abbiamo aggiunto un’attività **[!UICONTROL Page]** e definito un titolo per essa.

   ![](assets/social_quick_start_4.png)

1. Distribuisci l&#39;applicazione.

   ![](assets/social_webapp_004.png)

1. Configura l’applicazione Facebook in modo che venga visualizzata come una scheda nella pagina Facebook. Per ulteriori informazioni, consulta: [Configurazione delle schede Facebook](../../social/using/creating-a-facebook-application.md#configuring-facebook-tabs).

   ![](assets/social_quick_start_5.png)

![](assets/social_quick_start_6.png)

Controlla che la scheda dell&#39;applicazione **App01** sia visualizzata sulla tua pagina Facebook. Facendo clic su di essa, viene visualizzato un messaggio **Benvenuti** .

![](assets/social_webapp_042.png)

## Come inoltrare le impostazioni a un&#39;applicazione Facebook? {#how-to-forward-settings-to-a-facebook-application-}

>[!IMPORTANT]
>
>Segui i passaggi di configurazione descritti in [Creazione di un&#39;applicazione Facebook](../../social/using/creating-a-facebook-application.md).

Nell’esempio 1, abbiamo personalizzato la visualizzazione della pagina Facebook in base al valore nel campo **[!UICONTROL Fan of the page]** . È inoltre possibile elaborare il campo **[!UICONTROL Application settings]** . Questo campo ti consente di recuperare i dati contenuti in un collegamento generato da Adobe Campaign tramite Facebook.

Prendiamo l’esempio di un’azienda che decide di inviare una campagna e-mail. Nella consegna, un collegamento punta all’applicazione Facebook. Questo collegamento è personalizzato grazie al parametro **[!UICONTROL app_data]** aggiunto alla fine dell’URL. Il valore di questo parametro potrebbe essere un indicatore che riflette la significatività del cliente. Nel nostro esempio, i valori del parametro **[!UICONTROL app_data]** sono **[!UICONTROL big]** (cliente significativo) e **[!UICONTROL small]** (cliente meno significativo).

Una volta personalizzato, l’URL si presenta così:

* `http://<path of the Facebook application>&app_data=big` (per un cliente significativo)
* `http://<path of the Facebook application>&app_data=small` (per un cliente meno significativo)

Tra i dati anonimi inoltrati ad Adobe Campaign da Facebook, viene raccolto il valore del campo **[!UICONTROL Application parameters]**, consentendo così ad Adobe Campaign di personalizzare la visualizzazione dell’applicazione in base a questo parametro.

Se l’utente è un cliente significativo (il valore del parametro **[!UICONTROL app_data]** è **[!UICONTROL big]**), viene visualizzata l’immagine seguente:

![](assets/social_webapp_017.png)

Se l’utente è un cliente meno significativo (il valore del parametro **[!UICONTROL app_data]** è **[!UICONTROL small]**), viene visualizzata l’immagine seguente:

![](assets/social_webapp_016.png)

Per ricreare questo caso d’uso, abbiamo creato un’applicazione web composta dai seguenti elementi:

* Un&#39;attività **[!UICONTROL Test]** basata sul campo **[!UICONTROL Application parameter]**.
* due pagine che contengono le immagini da visualizzare in base al valore del campo **[!UICONTROL Application parameter]** .

![](assets/social_webapp_018.png)

## Come acquisire i dati del ventilatore? {#how-to-acquire-fan-data-}

>[!IMPORTANT]
>
>Segui i passaggi di configurazione descritti in [Creazione di un&#39;applicazione Facebook](../../social/using/creating-a-facebook-application.md).

Questo esempio mostra come entrare in contatto con gli utenti di Facebook e offrire loro la condivisione delle informazioni sul loro profilo. Prendiamo l&#39;esempio di un&#39;azienda che vuole acquisire prospettive e organizza un concorso sulla sua pagina Facebook per attrarle.

Ogni volta che un utente fa clic sulla scheda **[!UICONTROL App03]** , gli chiediamo se desidera partecipare al concorso.

![](assets/social_webapp_fb_000.png)

Se decidono di partecipare al concorso, offriamo loro di condividere le loro informazioni di profilo.

![](assets/social_webapp_021.png)

Se accettano di condividere le informazioni, viene visualizzata la seguente schermata.

![](assets/social_webapp_022.png)

Per creare questo caso d’uso, abbiamo creato un’applicazione web che include i seguenti elementi:

* un’attività **[!UICONTROL Test]**
* tre pagine
* un&#39;attività **[!UICONTROL Access control]**
* un’attività **[!UICONTROL Pre-loading]**
* un’attività **[!UICONTROL Save]**
* un&#39;attività **[!UICONTROL End]**

![](assets/social_webapp_019.png)

### Attività di test {#test-activity}

L’attività **[!UICONTROL Test]** è basata sul campo **[!UICONTROL ID]** e **[!UICONTROL Application parameters]** .

![](assets/social_webapp_023.png)

È costituito da tre rami:

* **[!UICONTROL identifier (UID) is empty]** : l’identificatore viene inoltrato da Facebook solo se l’utente ha già accettato di condividere le proprie informazioni. Il primo ramo dell’ attività **[!UICONTROL Test]** ti consente di rendere il concorso disponibile solo agli utenti che non sono mai entrati, ovvero quelli con un ID vuoto.
* **[!UICONTROL application parameter equals 'thanks']** : per eliminare un errore di visualizzazione collegato a Facebook, la pagina finale dell’applicazione web punta all’URL dell’applicazione Facebook a cui viene aggiunto il  **[!UICONTROL app_data]** parametro utilizzando il  **[!UICONTROL thanks]** valore (per ulteriori informazioni, consulta:  [Attività](#end-activity) finale). Il secondo ramo ti consente di scoprire se l’utente proviene dall’attività **[!UICONTROL End]** del primo ramo (e se è appena entrato nel concorso) per visualizzare un messaggio di ringraziamento. Per ulteriori informazioni sull’utilizzo di parametri URL aggiuntivi, consulta: [Come inoltrare le impostazioni a un&#39;applicazione Facebook?](#how-to-forward-settings-to-a-facebook-application-).
* **[!UICONTROL Default branch]** : se l’utente è già entrato nel concorso (ID già inserito) in una data precedente (parametro di applicazione diverso da  **[!UICONTROL thanks]**), verrà visualizzata una pagina in cui si informa che è già entrato.

### Pagina della concorrenza {#competition-page}

Per eliminare l’errore di visualizzazione collegato a Facebook, devi anche selezionare **[!UICONTROL Parent window]** o **[!UICONTROL In the top window]** nel campo **[!UICONTROL Window]** della pagina del concorso.

![](assets/social_webapp_028.png)

### Attività di controllo accessi {#access-control-activity}

L’ attività **[!UICONTROL Access control]** ti consente di visualizzare la pagina di richiesta delle autorizzazioni Facebook quando l’utente entra nel concorso. Se accettano di condividere le informazioni, queste vengono recuperate durante il precaricamento. Per ulteriori informazioni, consulta: [Attività di precaricamento](#pre-loading-activity).

Se in precedenza hai inserito l’account esterno durante la creazione dell’applicazione web (consulta [Creazione di un’applicazione web di tipo Facebook](../../social/using/creating-a-facebook-application.md#creating-a-facebook-type-web-application)) non è necessario modificare l’attività. In caso contrario, vai al campo **[!UICONTROL Application]** e seleziona l’account esterno collegato all’applicazione Facebook.

![](assets/social_webapp_024.png)

### Attività di precaricamento {#pre-loading-activity}

Selezionare l’origine dati da utilizzare per il precaricamento:

* **[!UICONTROL Marketing database]** : questa opzione consente di precaricare i dati tramite il database Adobe Campaign.
* **[!UICONTROL Facebook]** : questa opzione consente di precaricare i dati utilizzando Facebook.

![](assets/social_webapp_029.png)

**Database di marketing**

Questa opzione ti consente di recuperare i dati di un profilo esistente nella tabella dei visitatori. La verifica viene eseguita in base all&#39;Facebook ID esterno recuperato quando l&#39;utente fa clic sulla scheda dell&#39;applicazione Facebook. Se si aggiunge un modulo dopo l&#39;attività **[!UICONTROL Pre-loading]**, i campi che contengono informazioni nel database vengono precaricati.

![](assets/social_webapp_030.png)

>[!NOTE]
>
>Per ulteriori informazioni sul precaricamento dei dati tramite il database Adobe Campaign, consulta [questa sezione](../../web/using/publishing-a-web-form.md#pre-loading-the-form-data).

**Facebook**

Questa opzione ti consente di definire le informazioni del profilo Facebook da raccogliere, tra quelle che l’utente ha accettato di condividere, al fine di salvarlo.

![](assets/social_webapp_025.png)

L’opzione **[!UICONTROL Database information]** ti consente di raccogliere i dati seguenti:

* **[!UICONTROL External ID]**: ID utente
* **[!UICONTROL Gender]**: genere dell&#39;utente
* **[!UICONTROL Verified]** : questo campo specifica se l&#39;utente dispone o meno di un account Facebook verificato.
* **[!UICONTROL Full name]**: nome completo dell&#39;utente
* **[!UICONTROL First name]**: nome utente
* **[!UICONTROL Last name]**: cognome dell’utente
* **[!UICONTROL Language]**: lingua dell&#39;utente

Puoi anche decidere di raccogliere la foto del profilo, l’elenco degli amici, l’indirizzo e-mail, la data di nascita, gli interessi e la posizione selezionando le caselle appropriate.

Prima di fare clic su **[!UICONTROL Ok]**, selezionare la casella **[!UICONTROL I agree to comply with Facebook conditions of use]**.

>[!NOTE]
>
>Se selezioni una o più caselle nella sezione **[!UICONTROL Private information]** , nella schermata di richiesta delle autorizzazioni di Facebook viene visualizzata automaticamente la richiesta di accesso per questi dati.
>
>Per poter raccogliere le informazioni selezionate, l’utente deve acconsentire a condividerle.
>
>Se desideri entrambi i tipi di precaricamento (tramite Adobe Campaign e tramite Facebook), aggiungi due caselle di precaricamento una dopo l’altra.

### Salva attività {#save-activity}

L’attività **[!UICONTROL Save]** ti consente di memorizzare le informazioni raccolte durante le fasi precedenti nella tabella dei visitatori.

Se il profilo esiste già nella tabella dei visitatori, i loro dati vengono aggiornati con i nuovi dati raccolti.

Se il profilo non esiste nel database e l’indirizzo e-mail dell’utente Facebook è stato raccolto, un visitatore verrà creato nella tabella dei visitatori.

![](assets/social_webapp_026.png)

1. Nel campo **[!UICONTROL Visitor creation folder]** , seleziona la cartella in cui verrà creato il profilo. Nel caso di un&#39;applicazione Web di tipo Facebook, la cartella di creazione predefinita è **[!UICONTROL Visitors]**.
1. Nel campo **[!UICONTROL Reconciliation mode]** , seleziona la modalità di riconciliazione da utilizzare:

   * **[!UICONTROL Automatic]** : La riconciliazione viene effettuata in base a e-mail, cognome, nome e data di nascita.
   * **[!UICONTROL Manual]** : Selezionare una o più chiavi di riconciliazione.
   * **[!UICONTROL None]** : Non avrà luogo alcuna riconciliazione.

1. Nel campo **[!UICONTROL Mapping]** , seleziona lo schema su cui desideri eseguire la riconciliazione.

   >[!IMPORTANT]
   >
   >Assicurati che i campi della scheda **[!UICONTROL Social networks]** siano immessi correttamente nella mappatura della consegna. Le mappature di consegna sono accessibili tramite il nodo **[!UICONTROL Administration > Campaign management > Target mappings]** .

1. Puoi selezionare una cartella di ricerca per la riconciliazione e una cartella di creazione per i nuovi profili. Se i campi sono vuoti, i profili vengono ricercati e creati nella cartella predefinita dello schema di mappatura.

### Attività fine {#end-activity}

Per ignorare l’errore di visualizzazione collegato a Facebook, devi selezionare la casella **[!UICONTROL Use an external URL]** e immettere l’URL dell’applicazione Facebook, seguita dal parametro **[!UICONTROL app_data]** e da un valore. Questo valore verrà utilizzato nell&#39;attività **[!UICONTROL Test]** per rilevare se l&#39;utente è appena entrato nel concorso e per visualizzare un messaggio di ringraziamento, se applicabile. Per ulteriori informazioni, consulta: [Attività di test](#test-activity).

Nel nostro esempio, il valore utilizzato è **thank**.

![](assets/social_webapp_027.png)

### Schermata dei dettagli di un visitatore {#details-screen-of-a-visitor}

Proprio come per i follower di Twitter (consulta: [Principio operativo](../../social/using/publishing-on-twitter.md#operating-principle)), i profili Facebook recuperati sono memorizzati nella tabella dei visitatori. Per visualizzare l’elenco dei visitatori, passa al nodo **[!UICONTROL Profiles and Targets > Visitors]** .

Ogni potenziale cliente Facebook che accetta di condividere le proprie informazioni di profilo viene aggiunto all’elenco dei visitatori. Se la casella **[!UICONTROL Friends]** è selezionata nell&#39;attività **[!UICONTROL Pre-load]** (consulta: [Attività di precaricamento](#pre-loading-activity)), vengono aggiunti anche gli amici.

![](assets/social_webapp_037.png)

Nella sezione **[!UICONTROL Summary]** della finestra dei dettagli del visitatore, sono disponibili due stati possibili per l&#39;indicatore **[!UICONTROL New Contact]**:

![](assets/social_webapp_038.png)

Se viene visualizzato un segno di spunta verde, significa che il visitatore non è stato riconciliato con alcun destinatario. In questo caso, nell’elenco dei destinatari viene creato un nuovo profilo.

![](assets/social_webapp_039.png)

Una croce rossa indica che il visitatore è stato riconciliato con un destinatario. Puoi fare clic sulla lente di ingrandimento a destra del campo **[!UICONTROL Recipient]** per visualizzare il destinatario corrispondente.

![](assets/social_webapp_040.png)

Vai alla finestra dei dettagli di un destinatario per visualizzare il visitatore corrispondente, se applicabile. Seleziona la scheda **[!UICONTROL Others]** , quindi fai doppio clic sul nome del visitatore nella sezione **[!UICONTROL Web identities]** .

![](assets/social_webapp_041.png)

La schermata **[!UICONTROL Activities]** della pagina dei dettagli di un visitatore contiene le seguenti informazioni:

* Attività fan di tipo &quot;Open Graph&quot;: musica giocata, video guardati, articoli letti e deduzioni delle applicazioni installate (Deezer, Spotify, Dailymotion, Yahoo News, ecc.)

   ![](assets/social_facebook_activities.png)

* &quot;Mi piace&quot; e commenti aggiunti dal fan in seguito alle consegne inviate da Adobe Campaign
* pagine apprezzate dal fan
* check-in della ventola

   ![](assets/social_facebook_checkins.png)

   >[!NOTE]
   >
   >Per consentire ad Adobe Campaign di raccogliere i check-in di una ventola, è necessario fare clic sul pulsante **[!UICONTROL Subscribe]** nella schermata di configurazione del servizio. Per ulteriori informazioni, consulta [Configurazione di account esterni](../../social/using/creating-a-facebook-application.md#configuring-external-accounts).

## Come precaricare i campi di un modulo utilizzando i dati di profilo di Facebook {#how-to-pre-load-the-fields-of-a-form-using-facebook-profile-data}

L’applicazione **[!UICONTROL Social Marketing]** consente inoltre di aggiungere un pulsante a un modulo per precaricare i campi utilizzando le informazioni sul profilo di Facebook. Questa opzione, disponibile in tutti i modelli di applicazione web (**[!UICONTROL Page]** attività di tipo ), è descritta in [questa sezione](../../web/using/static-elements-in-a-web-form.md#inserting-html-content).

![](assets/social_webapp_035.png)

>[!NOTE]
>
>Prima di iniziare a utilizzare questa funzione, è necessario creare un&#39;applicazione Facebook e un account esterno di tipo **[!UICONTROL Facebook Connect]**. Per ulteriori informazioni, consulta [Configurazione di account esterni](../../social/using/creating-a-facebook-application.md#configuring-external-accounts).
