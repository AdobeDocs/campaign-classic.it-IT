---
title: Connessione tramite LDAP
description: 'Scopri come utilizzare LDAP per accedere a Campaign '
page-status-flag: never-activated
uuid: 13a426bc-7c34-49e5-ac8e-26d830845f28
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: 1563db7c-ccb6-46b3-9299-67ec0aedaca0
translation-type: tm+mt
source-git-commit: b447e316bed8e0e87d608679c147e6bd7b0815eb
workflow-type: tm+mt
source-wordcount: '1008'
ht-degree: 1%

---


# Connessione tramite LDAP{#connecting-through-ldap}

## Configurazione di Campaign e LDAP {#configuring-campaign-and-ldap}

>[!NOTE]
>
>La configurazione LDAP è possibile solo per le installazioni locali o ibride.

La configurazione LDAP viene eseguita nella procedura guidata di distribuzione. L&#39; **[!UICONTROL LDAP integration]** opzione deve essere selezionata durante il primo passaggio di configurazione. Fare riferimento alla procedura guidata [di distribuzione](../../installation/using/deploying-an-instance.md#deployment-wizard).

La finestra consente di configurare l’identificazione di  utenti Adobe Campaign tramite la directory LDAP specificata.

![](assets/s_ncs_install_deployment_wiz_ldap_01.png)

* Specificate l’indirizzo del server LDAP nel **[!UICONTROL LDAP server]** campo. Potete aggiungere il numero della porta. Per impostazione predefinita, la porta utilizzata è 389.
* Nell&#39;elenco a discesa, selezionate il metodo di autenticazione per gli utenti:

   * Password crittografata (**md5**)

      modalità predefinita.

   * Password di testo normale + SSL (**TLS**)

      L&#39;intera procedura di autenticazione (password inclusa) è crittografata. La porta sicura 636 non deve essere utilizzata in questa modalità:  Adobe Campaign passa automaticamente alla modalità protetta.

      Quando utilizzate questa modalità di autenticazione, in Linux il certificato viene verificato da una libreria client openLDAP. È consigliabile utilizzare un certificato SSL valido in modo che la procedura di autenticazione sia crittografata. In caso contrario, le informazioni saranno in testo normale.

      Il certificato viene verificato anche in Windows.

   * Windows NT LAN Manager (**NTLM**)

      Autenticazione Windows proprietaria. Viene **[!UICONTROL Unique identifier]** utilizzato solo per il nome di dominio.

   * Autenticazione con password distribuita (**DPA**)

      Autenticazione Windows proprietaria. Viene **[!UICONTROL Unique identifier]** utilizzato solo per il nome di dominio (domain.com).

   * Password testo normale

      Nessuna crittografia (solo per le fasi di prova).

* Selezionate la modalità di autenticazione utente: **[!UICONTROL Automatically compute the unique user identifier]** (vedere il calcolo [del nome](#distinguished-name-calculation)distintivo passaggio) o **[!UICONTROL Search the unique user identifier in the directory]** (vedere [Ricerca di identificatori](#searching-for-identifiers)passo).

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

## Calcolo Nome distinto {#distinguished-name-calculation}

Se si desidera calcolare gli identificatori Nome distintivo (DN), il passaggio successivo della procedura guidata di distribuzione consente di configurare la modalità di calcolo.

![](assets/s_ncs_install_deployment_wiz_ldap_02.png)

* Specificate l&#39;identificatore univoco dell&#39;utente nella directory (Nome distinto - DN) del **[!UICONTROL Distinguished Name]** campo.

   **[!UICONTROL (login)]** viene sostituito con l&#39;identificatore dell&#39;operatore Adobe Campaign .

   >[!CAUTION]
   >
   >L&#39; **[!UICONTROL dc]** impostazione deve essere in lettere minuscole.

* Selezionate l’opzione **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** per sincronizzare le associazioni di gruppi e utenti nella directory LDAP e le associazioni di gruppi e utenti in  Adobe Campaign.

   Quando selezionate questa opzione, le **[!UICONTROL Application level DN used for the search]** e **[!UICONTROL Password of the application login]** sono abilitate.

   Se compilate questi due campi,  Adobe Campaign si connetterà al server LDAP con login e password personalizzati. Se sono vuoti,  Adobe Campaign si connetterà al server in modo anonimo.

## Ricerca di identificatori {#searching-for-identifiers}

Se scegliete di cercare un identificatore, la procedura guidata di distribuzione consente di configurare la ricerca.

* Nei campi **[!UICONTROL Application level DN used for the search]** e **[!UICONTROL Password of the application login]** , fornite l&#39;identificatore e la password con cui  Adobe Campaign si connetterà alla ricerca dell&#39;identificatore. Se sono vuoti,  Adobe Campaign si connetterà al server in modo anonimo.
* Specificate i campi **[!UICONTROL Base identifier]** e **[!UICONTROL Search scope]** per determinare un sottoinsieme della directory LDAP da cui avviare la ricerca.

   Selezionate la modalità desiderata nell’elenco a discesa:

   ![](assets/s_ncs_install_deployment_wiz_ldap_03.png)

   1. **[!UICONTROL Recursive (default mode)]**.

      La ricerca completa della directory LDAP inizia da un determinato livello.

   1. **[!UICONTROL Limited to the base]**.

      Tutti gli attributi sono inclusi nella ricerca.

   1. **[!UICONTROL Limited to the first sub-level of the base]**.

      La ricerca viene eseguita su tutti gli attributi della directory e a partire dal primo livello dell&#39;attributo.

* Il **[!UICONTROL Filter]** campo consente di specificare un elemento per definire meglio l’ambito della ricerca.

## Configurazione delle autorizzazioni LDAP {#configuring-ldap-authorizations}

Questa finestra viene visualizzata quando selezionate l’ **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** opzione.

![](assets/s_ncs_install_deployment_wiz_ldap_04.png)

È necessario specificare diversi parametri per individuare il gruppo o i gruppi a cui l’utente appartiene e i diritti corrispondenti, ad esempio:

* il **[!UICONTROL Database identifier]** campo,
* il **[!UICONTROL Search scope]** campo,

   >[!NOTE]
   >
   >Se avete scelto di cercare il DN, potete selezionare **[!UICONTROL Reuse the DN search parameters]** per riportare i valori selezionati per il DN e l&#39;ambito di ricerca dalla schermata precedente.

* il **[!UICONTROL Rights search filter]** campo, in base al login e al nome distintivo dell&#39;utente,
* il **[!UICONTROL Attribute containing the group or authorization name]** campo relativo all’utente,
* il **[!UICONTROL Association mask]** campo che consente di estrarre il nome del gruppo in  Adobe Campaign e i relativi diritti associati. Potete usare espressioni regolari per cercare il nome.
* Selezionate **[!UICONTROL Enable the connection of users declared in the LDAP directory if the operator is not declared in Adobe Campaign]** in modo che all&#39;utente vengano automaticamente concessi i diritti di accesso alla connessione.

Fare clic **[!UICONTROL Save]** per completare la configurazione dell&#39;istanza.

## Gestione degli operatori {#managing-operators}

Una volta confermata la configurazione, è necessario definire  operatori Adobe Campaign gestiti tramite la directory LDAP.

Per utilizzare la directory LDAP per l’autenticazione di un operatore, modificate il profilo corrispondente e fate clic sul **[!UICONTROL Edit the access parameters]** collegamento. Selezionate l’ **[!UICONTROL Use LDAP for authentication]** opzione: Il **[!UICONTROL Password]** campo è disabilitato per questo operatore.

![](assets/s_ncs_install_operator_in_ldap.png)

## Casi d’uso {#use-cases}

Questa sezione fornisce alcuni casi d’uso semplici per aiutarti a ottenere le configurazioni più appropriate in base alle tue esigenze.

1. Un utente è stato creato nella directory LDAP ma non in  Adobe Campaign.

    Adobe Campaign può essere configurato in modo che l&#39;utente possa accedere alla piattaforma tramite la propria autenticazione LDAP.  Adobe Campaign deve essere in grado di controllare la validità della combinazione di ID/password nella directory LDAP, in modo che l’operatore possa essere creato al volo in  Adobe Campaign. Per eseguire questa operazione, selezionare l&#39; **[!UICONTROL Enable the connection of users declared in the LDAP directory if the operator is not declared in Adobe Campaign]** opzione. In questo caso, è necessario configurare anche la sincronizzazione dei gruppi: l&#39; **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** opzione deve essere selezionata.

1. L’utente è stato creato in  Adobe Campaign ma non nella directory LDAP.

   Non potranno accedere a  Adobe Campaign.

1. Nella directory LDAP è presente un gruppo che non esiste in  Adobe Campaign.

   Questo gruppo non verrà creato in  Adobe Campaign. È necessario creare il gruppo e sincronizzare i gruppi per abilitare una corrispondenza tramite l&#39; **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** opzione.

1. I gruppi esistono in  Adobe Campaign e la directory LDAP viene attivata dopo l’evento: i gruppi di utenti in  Adobe Campaign non vengono sostituiti automaticamente con il contenuto dei gruppi LDAP. Allo stesso modo, se un gruppo esiste solo in  Adobe Campaign, nessun utente LDAP può aggiungervi altri utenti fino a quando il gruppo non è stato creato e sincronizzato in LDAP.

   I gruppi non vengono mai creati al momento, sia  Adobe Campaign che mediante LDAP. Devono essere creati singolarmente, sia in  Adobe Campaign che nella directory LDAP.

   I nomi dei gruppi nella directory LDAP devono coincidere con i nomi  gruppi Adobe Campaign. La relativa maschera di associazione è definita nell’ultima fase di configurazione della procedura guidata di distribuzione:  Adobe Campaign_(.*), ad esempio.

