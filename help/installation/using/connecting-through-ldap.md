---
product: campaign
title: Connessione tramite LDAP
description: Scopri come utilizzare LDAP per accedere a Campaign
feature: Installation, Instance Settings
badge-v7-prem: label="Solo on-premise/ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 0533cd50-3aa4-4160-9152-e916e149e77f
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '1021'
ht-degree: 0%

---

# Connessione tramite LDAP{#connecting-through-ldap}

## Configurazione di Campaign e LDAP {#configuring-campaign-and-ldap}

>[!NOTE]
>
>La configurazione LDAP è possibile solo per le installazioni on-premise o ibride.

La configurazione LDAP viene eseguita nella procedura guidata di distribuzione. L&#39;opzione **[!UICONTROL LDAP integration]** deve essere selezionata durante il primo passaggio di configurazione. Fare riferimento a [Distribuzione guidata](../../installation/using/deploying-an-instance.md#deployment-wizard).

La finestra consente di configurare l’identificazione degli utenti di Adobe Campaign tramite la directory LDAP specificata.

![](assets/s_ncs_install_deployment_wiz_ldap_01.png)

* Specificare l&#39;indirizzo del server LDAP nel campo **[!UICONTROL LDAP server]**. È possibile aggiungere il numero di porta. Per impostazione predefinita, la porta utilizzata è 389.
* Nell’elenco a discesa, seleziona il metodo di autenticazione per gli utenti:

   * Password crittografata (**md5**)

     Modalità predefinita.

   * Password in testo normale + SSL (**TLS**)

     L&#39;intera procedura di autenticazione (password inclusa) è crittografata. La porta sicura 636 non deve essere utilizzata in questa modalità: Adobe Campaign passa automaticamente alla modalità protetta.

     Quando si utilizza questa modalità di autenticazione, in Linux il certificato viene verificato da una libreria client openLDAP. È consigliabile utilizzare un certificato SSL valido in modo che la procedura di autenticazione sia crittografata. In caso contrario, le informazioni saranno in testo normale.

     Il certificato viene verificato anche in Windows.

   * Gestione LAN di Windows NT (**NTLM**)

     Autenticazione Windows proprietaria. **[!UICONTROL Unique identifier]** è utilizzato solo per il nome di dominio.

   * Autenticazione password distribuita (**DPA**)

     Autenticazione Windows proprietaria. **[!UICONTROL Unique identifier]** viene utilizzato solo per il nome di dominio (domain.com).

   * Password in testo semplice

     Nessuna crittografia (da utilizzare solo nelle fasi di test).

* Selezionare la modalità di autenticazione utente: **[!UICONTROL Automatically compute the unique user identifier]** (vedere il passaggio [Calcolo del nome distinto](#distinguished-name-calculation)) o **[!UICONTROL Search the unique user identifier in the directory]** (vedere il passaggio [Ricerca di identificatori](#searching-for-identifiers)).

## Compatibilità {#compatibility}

I sistemi compatibili dipendono dal meccanismo di autenticazione selezionato. Di seguito è riportata una matrice di compatibilità dei sistemi operativi e dei server LDAP.

<table> 
 <thead> 
  <tr> 
   <th> </th> 
   <th> OpenLDAP<br /> </th> 
   <th> Active Directory<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> md5<br /> </td> 
   <td> Windows, Linux<br /> </td> 
   <td> Linux<br /> </td> 
  </tr> 
  <tr> 
   <td> TLS<br /> </td> 
   <td> Linux<br /> </td> 
   <td> Windows, Linux<br /> </td> 
  </tr> 
  <tr> 
   <td> NTLM e DPA<br /> </td> 
   <td> </td> 
   <td> Windows<br /> </td> 
  </tr> 
  <tr> 
   <td> testo normale<br /> </td> 
   <td> Windows, Linux<br /> </td> 
   <td> Windows, Linux<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Calcolo del nome distinto {#distinguished-name-calculation}

Se si desidera calcolare gli identificatori del nome distinto (DN), il passaggio successivo della procedura guidata di distribuzione consente di configurare la modalità di calcolo.

![](assets/s_ncs_install_deployment_wiz_ldap_02.png)

* Specificare l&#39;identificatore univoco dell&#39;utente nella directory (Nome distinto - DN) nel campo **[!UICONTROL Distinguished Name]**.

  **[!UICONTROL (login)]** verrà sostituito con l&#39;identificatore dell&#39;operatore Adobe Campaign.

  >[!CAUTION]
  >
  >L&#39;impostazione **[!UICONTROL dc]** deve essere in minuscolo.

* Selezionare l&#39;opzione **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** per sincronizzare le associazioni utente e gruppo nella directory LDAP e le associazioni utente e gruppo in Adobe Campaign.

  Quando si seleziona questa opzione, **[!UICONTROL Application level DN used for the search]** e **[!UICONTROL Password of the application login]** sono abilitati.

  Se si compilano questi due campi, Adobe Campaign si connette al server LDAP con il proprio login e la propria password. Se sono vuoti, Adobe Campaign si connette al server in modo anonimo.

## Ricerca di identificatori {#searching-for-identifiers}

Se si sceglie di cercare un identificatore, la procedura guidata di distribuzione consente di configurare la ricerca.

* Nei campi **[!UICONTROL Application level DN used for the search]** e **[!UICONTROL Password of the application login]**, fornisci l&#39;identificatore e la password con cui Adobe Campaign si connette per cercare l&#39;identificatore. Se sono vuoti, Adobe Campaign si connette al server in modo anonimo.
* Specificare i campi **[!UICONTROL Base identifier]** e **[!UICONTROL Search scope]** per determinare un sottoinsieme della directory LDAP da cui avviare la ricerca.

  Seleziona la modalità desiderata nell’elenco a discesa:

  ![](assets/s_ncs_install_deployment_wiz_ldap_03.png)

   1. **[!UICONTROL Recursive (default mode)]**.

      La ricerca nella directory LDAP viene eseguita completamente, a partire da un determinato livello.

   1. **[!UICONTROL Limited to the base]**.

      Tutti gli attributi sono inclusi nella ricerca.

   1. **[!UICONTROL Limited to the first sub-level of the base]**.

      La ricerca viene eseguita su tutti gli attributi della directory a partire dal primo livello dell&#39;attributo.

* Il campo **[!UICONTROL Filter]** consente di specificare un elemento per perfezionare l&#39;ambito della ricerca.

## Configurazione delle autorizzazioni LDAP {#configuring-ldap-authorizations}

Questa finestra viene visualizzata quando si seleziona l&#39;opzione **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]**.

![](assets/s_ncs_install_deployment_wiz_ldap_04.png)

È necessario specificare diversi parametri per trovare il gruppo o i gruppi a cui appartiene l&#39;utente e i diritti corrispondenti, ad esempio:

* il campo **[!UICONTROL Database identifier]**,
* il campo **[!UICONTROL Search scope]**,

  >[!NOTE]
  >
  >Se si è scelto di cercare il DN, è possibile selezionare **[!UICONTROL Reuse the DN search parameters]** per riportare i valori selezionati per il DN e l&#39;ambito di ricerca dalla schermata precedente.

* il campo **[!UICONTROL Rights search filter]**, in base all&#39;accesso e al nome distinto dell&#39;utente,
* il campo **[!UICONTROL Attribute containing the group or authorization name]** relativo all&#39;utente,
* il campo **[!UICONTROL Association mask]** che abilita l&#39;estrazione del nome del gruppo in Adobe Campaign e dei diritti associati. Puoi utilizzare espressioni regolari per cercare il nome.
* Selezionare **[!UICONTROL Enable the connection of users declared in the LDAP directory if the operator is not declared in Adobe Campaign]** in modo che all&#39;utente vengano concessi automaticamente i diritti di accesso alla connessione.

Fare clic su **[!UICONTROL Save]** per completare la configurazione dell&#39;istanza.

## Gestione degli operatori {#managing-operators}

Dopo aver confermato la configurazione, è necessario definire quali operatori Adobe Campaign vengono gestiti tramite la directory LDAP.

Per utilizzare la directory LDAP per autenticare un operatore, modificare il profilo corrispondente e fare clic sul collegamento **[!UICONTROL Edit the access parameters]**. Selezionare l&#39;opzione **[!UICONTROL Use LDAP for authentication]**: il campo **[!UICONTROL Password]** è disattivato per questo operatore.

![](assets/s_ncs_install_operator_in_ldap.png)

## Casi d’uso {#use-cases}

Questa sezione fornisce alcuni semplici casi d’uso per aiutarti a ottenere le configurazioni più appropriate in base alle tue esigenze.

1. Un utente è stato creato nella directory LDAP ma non in Adobe Campaign.

   Adobe Campaign può essere configurato in modo che l’utente acceda alla piattaforma tramite la propria autenticazione LDAP. Adobe Campaign deve essere in grado di controllare la validità della combinazione ID/password nella directory LDAP, in modo che l’operatore possa essere creato all’istante in Adobe Campaign. Per eseguire questa operazione, selezionare l&#39;opzione **[!UICONTROL Enable the connection of users declared in the LDAP directory if the operator is not declared in Adobe Campaign]**. In questo caso, è necessario configurare anche la sincronizzazione dei gruppi: è necessario selezionare l&#39;opzione **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]**.

1. L&#39;utente è stato creato in Adobe Campaign ma non nella directory LDAP.

   Non saranno in grado di accedere ad Adobe Campaign.

1. Nella directory LDAP è presente un gruppo che non esiste in Adobe Campaign.

   Questo gruppo non verrà creato in Adobe Campaign. È necessario creare il gruppo e sincronizzarlo per abilitare una corrispondenza tramite l&#39;opzione **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]**.

1. I gruppi esistono in Adobe Campaign e la directory LDAP viene attivata dopo l’evento: i gruppi di utenti in Adobe Campaign non vengono sostituiti automaticamente con il contenuto dei gruppi LDAP. Analogamente, se un gruppo esiste solo in Adobe Campaign, non è possibile aggiungervi utenti LDAP finché il gruppo non è stato creato e sincronizzato in LDAP.

   I gruppi non vengono mai creati al volo, né da Adobe Campaign né da LDAP. Devono essere create singolarmente, sia in Adobe Campaign che nella directory LDAP.

   I nomi dei gruppi nella directory LDAP devono coincidere con i nomi dei gruppi di Adobe Campaign. La relativa maschera di associazione è definita nell’ultimo passaggio di configurazione della procedura guidata di distribuzione: Adobe Campaign_(.&#42;), ad esempio.
