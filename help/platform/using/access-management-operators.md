---
product: campaign
title: Guida introduttiva agli operatori Campaign
description: Scopri come creare e gestire gli utenti delle campagne
feature: Access Management, Permissions
role: User, Admin
level: Beginner
exl-id: 580282ce-ee30-422a-8724-9c328637cc39
source-git-commit: f05eefc9945c4ead89eb448b6e28c3523559e055
workflow-type: tm+mt
source-wordcount: '1149'
ht-degree: 2%

---

# Creare e gestire gli operatori {#operators}

![](../../assets/common.svg)

## Guida introduttiva agli operatori Campaign  {#about-operators}

Un operatore è un utente Adobe Campaign che dispone delle autorizzazioni per accedere ed eseguire azioni.

Per impostazione predefinita, gli operatori vengono memorizzati nella **[!UICONTROL Administration > Access management > Operators]** nodo.

![](assets/s_ncs_user_list_operators.png)

Gli operatori possono essere creati manualmente o mappati su una directory LDAP esistente.

Viene descritta la procedura completa per la creazione di un operatore in [questa pagina](#creating-an-operator).

Per ulteriori informazioni sull&#39;integrazione di Adobe Campaign e LDAP, consulta [questa pagina](../../installation/using/connecting-through-ldap.md).

>[!IMPORTANT]
>
>Gli operatori devono essere collegati a un&#39;area di sicurezza per accedere a un&#39;istanza. Per ulteriori informazioni sulle aree di protezione in Adobe Campaign, consulta [questa pagina](../../installation/using/security-zones.md).

Gli utenti possono anche connettersi direttamente ad Adobe Campaign utilizzando il proprio Adobe ID. Per ulteriori informazioni, consulta questa [pagina](../../integrations/using/about-adobe-id.md).

## Creare un operatore {#creating-an-operator}

Per creare un nuovo operatore e concedere autorizzazioni, segui i passaggi seguenti:

1. Fai clic sul pulsante **[!UICONTROL New]** sopra l’elenco degli operatori e immettere i dettagli del nuovo operatore.

   ![](assets/s_ncs_user_operator_new.png)

1. Specifica la **[!UICONTROL Identification parameters]** dell&#39;utente: accesso, password e nome. L’operatore utilizzerà l’accesso e la password per accedere ad Adobe Campaign. Una volta effettuato l’accesso, l’utente può modificare la propria password tramite il **[!UICONTROL Tools > Change password]** menu. L’e-mail dell’operatore è essenziale in quanto consente all’operatore di ricevere notifiche, ad esempio durante l’elaborazione delle approvazioni.

   Questa sezione consente anche di collegare un operatore a un’entità organizzativa. Per ulteriori informazioni, consulta la sezione [questa pagina](../../distributed/using/about-distributed-marketing.md).

1. Seleziona le autorizzazioni concesse all’operatore nel **[!UICONTROL Operator access rights]** sezione .

   Per assegnare diritti all’operatore, fai clic sul pulsante **[!UICONTROL Add]** pulsante situato sopra l’elenco dei diritti, quindi seleziona un gruppo di operatori dall’elenco dei gruppi disponibili:

   ![](assets/s_ncs_user_permissions_operators.png)

   Puoi anche selezionare uno o più diritti denominati (consulta [Diritti denominati](#named-rights)). A questo scopo, fai clic sulla freccia a destra del **[!UICONTROL Folder]** e seleziona **[!UICONTROL Named rights]**:

   ![](assets/s_ncs_user_rights_operators.png)

   Seleziona i gruppi e/o i diritti denominati da assegnare e fai clic su **[!UICONTROL OK]** da convalidare.

1. Fai clic su **[!UICONTROL Ok]** per creare l’operatore : il profilo viene aggiunto all’elenco degli operatori esistenti.

   ![](assets/operator_profile_new.png)

>[!NOTE]
>
>Puoi organizzare gli operatori in base alle tue esigenze creando nuove cartelle di operatori. A questo scopo, fai clic con il pulsante destro del mouse sulla cartella dell’operatore e seleziona **[!UICONTROL Add an 'Operators' folder]**.

Una volta creato il profilo dell’operatore, puoi aggiungere o aggiornare le relative informazioni. A questo scopo, fai clic sul pulsante **[!UICONTROL Edit]** scheda .

![](assets/operator_edit_profile.png)

>[!NOTE]
>
>La **[!UICONTROL Session timeout]** consente di regolare il ritardo prima del timeout della sessione FDA. Per ulteriori informazioni, consulta [Informazioni su Federated Data Access](../../installation/using/about-fda.md).

## Definire il fuso orario dell’operatore {#time-zone-of-the-operator}

In **[!UICONTROL General]** è possibile selezionare il fuso orario dell’operatore. Per impostazione predefinita, gli operatori funzionano nel fuso orario del server. Tuttavia, è possibile selezionare un altro fuso orario utilizzando l’elenco a discesa.

La configurazione dei fusi orari è descritta in [questa pagina](../../installation/using/time-zone-management.md).

>[!NOTE]
>
>Le collaborazioni all’interno di diversi fusi orari richiedono l’archiviazione delle date in UTC. Le date vengono convertite nel fuso orario appropriato nei seguenti contesti: quando una data viene visualizzata nel fuso orario utente, quando i file vengono importati ed esportati, quando viene pianificata una consegna e-mail, quando le attività sono pianificate in un flusso di lavoro (pianificazione, attesa, vincolo di tempo, ecc.)
>
>I vincoli e le raccomandazioni collegati a questi contesti sono presentati nelle sezioni correlate della documentazione di Adobe Campaign.

Inoltre, il **[!UICONTROL Regional settings]** elenco a discesa consente di selezionare il formato per visualizzare date e numeri.

## Aggiungi autorizzazioni {#access-rights-options}

Utilizza la **[!UICONTROL Access rights]** per aggiornare i gruppi e i diritti denominati collegati all’operatore .

![](assets/operator_profile_security_options.png)

La **[!UICONTROL Edit the access parameters...]** link consente di accedere alle seguenti opzioni:

* La **[!UICONTROL Disable account]** consente di disabilitare l’account dell’operatore: questo utente non accederà più ad Adobe Campaign.

   >[!NOTE]
   >
   >Anche se il loro account è disabilitato, l’operatore può comunque ricevere avvisi o notifiche da Campaign. Per interrompere l’invio di notifiche Campaign a questo operatore, l’Adobe consiglia di rimuovere l’indirizzo e-mail dal relativo profilo.

* La **[!UICONTROL Forbid access from the rich client]** consente di limitare l’utilizzo di Adobe Campaign a [Accesso Web](../../platform/using/adobe-campaign-workspace.md#console-and-web-access) o tramite API: l’accesso alla console client di Adobe Campaign non è più disponibile.
* È possibile collegare una zona di sicurezza all&#39;operatore. Per ulteriori informazioni, consulta [questa pagina](../../installation/using/security-zones.md).
* Puoi anche definire una maschera IP affidabile utilizzando il collegamento appropriato.

   L’operatore sarà in grado di connettersi ad Adobe Campaign senza immettere la password se l’indirizzo IP è presente in questo elenco.

   Puoi inoltre specificare un set di indirizzi IP che saranno autorizzati a connettersi senza password, come nell’esempio seguente:

   ![](assets/operator_trustip.png)

   >[!NOTE]
   >
   >Per proteggere l’accesso alla piattaforma, devi utilizzare questa opzione con cautela.

* La **[!UICONTROL Restrict to information found in sub-folders of:]** consente di limitare i diritti attribuiti all’operatore di una cartella. Solo le sottocartelle del nodo specificato in questa opzione saranno visibili all’utente:

   ![](assets/s_ncs_user_restrictions_operators.png)

   >[!IMPORTANT]
   >
   >Si tratta di una restrizione molto stretta e va usata con cautela. Un operatore connesso con questo tipo di diritti può visualizzare SOLO il contenuto della cartella specificata e non ha accesso a nessun altro nodo della struttura tramite l&#39;explorer. Tuttavia, a seconda delle funzionalità a cui l’operatore ha accesso (ad esempio: workflow), l&#39;utente può visualizzare i dati solitamente memorizzati in nodi che non sono accessibili.

### Controlla le impostazioni {#check-settings}

La **[!UICONTROL Audit]** consente di visualizzare le informazioni relative all’operatore . Le varie schede vengono aggiunte automaticamente in base alle impostazioni definite nell’area di intervento dell’operatore.

Puoi accedere a:

* Elenco di diritti sulle cartelle collegate all’operatore.

   ![](assets/operator_folder_permissions.png)

   >[!NOTE]
   >
   >Per ulteriori informazioni, consulta [Gestione dell&#39;accesso alle cartelle](#folder-access-management).

* Registro approvazioni operatore.

   ![](assets/operator_profile_validations.png)

* L&#39;elenco dei forum di discussione ai quali sono abbonati.
* Eventi nel loro calendario.
* Elenco delle attività assegnate.

## Operatori predefiniti {#default-operators}

Adobe Campaign utilizza operatori tecnici con profili configurati per impostazione predefinita: Amministratore (&#39;admin&#39;), fatturazione (&#39;billing&#39;), monitoraggio, agente dell&#39;applicazione Web (&#39;webapp&#39;), ecc. Alcune di queste dipendono dalle applicazioni e dalle opzioni installate sulla piattaforma: Gli operatori &#39;central&#39; e &#39;local&#39;, ad esempio, sono visibili solo se è installata l&#39;opzione Distributed Marketing.

>[!IMPORTANT]
>
>Questi operatori tecnici vengono avvisati per impostazione predefinita quando la piattaforma restituisce messaggi di informazioni. Consigliamo vivamente di fornire un&#39;e-mail di contatto per loro.
>
>Per garantire il corretto funzionamento delle applicazioni web, si consiglia inoltre di non definire impostazioni regionali specifiche per l’operatore &quot;webapp&quot;.

Per impostazione predefinita, l’operatore tecnico &quot;webapp&quot; ha il diritto di amministrazione denominato , che può comportare rischi per la sicurezza. Per risolvere questo problema, si consiglia di rimuovere questo diritto. Per eseguire questa operazione:

1. Da **[!UICONTROL Administration > Access management > Named rights]** nodo, fai clic su **[!UICONTROL New]** per creare un diritto e denominarlo WEBAPP.

   ![](assets/s_ncs_default_operators_webapp_right.png)

   I diritti denominati sono descritti nel [Diritti denominati](#named-rights) sezione .

1. Da **[!UICONTROL Administration > Access management > Operators]** , seleziona l&#39;operatore dell&#39;agente delle applicazioni Web (&#39;webapp&#39;).

   Seleziona la **[!UICONTROL Edit]** , quindi la **[!UICONTROL Access rights]** e elimina l&#39;AMMINISTRAZIONE denominata a destra dall&#39;elenco.

   ![](assets/s_ncs_default_operators_webapp_admin_right.png)

   Fai clic su **[!UICONTROL Add]** seleziona il diritto WEBAPP appena creato, quindi salva le modifiche.

   ![](assets/s_ncs_default_operators_webapp_webapp_right.png)

1. Assegna l’operatore &quot;webapp&quot; diritti di accesso in lettura e scrittura dei dati sulle cartelle che riguardano questo operatore, che sono principalmente le cartelle &quot;Recipient&quot;.

   ![](assets/s_ncs_default_operators_webapp_folder_access.png)

   La modifica dei diritti sulle cartelle ad albero è descritta in [Gestione dell&#39;accesso alle cartelle](#folder-access-management) sezione .

>[!NOTE]
>
>Per ulteriori informazioni sulle linee guida sulla sicurezza, consulta [Elenco di controllo per la configurazione di Adobe Campaign Security](https://helpx.adobe.com/it/campaign/kb/acc-security.html).
