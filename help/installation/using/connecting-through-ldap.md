---
product: campaign
title: Connessione tramite LDAP
description: 'Scopri come utilizzare LDAP per accedere a Campaign '
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 0533cd50-3aa4-4160-9152-e916e149e77f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1008'
ht-degree: 1%

---

# Connessione tramite LDAP{#connecting-through-ldap}

![](../../assets/v7-only.svg)

## Configurazione di Campaign e LDAP {#configuring-campaign-and-ldap}

>[!NOTE]
>
>La configurazione LDAP è possibile solo per installazioni on-premise o ibride.

La configurazione LDAP viene eseguita nella procedura guidata di distribuzione. La **[!UICONTROL LDAP integration]** deve essere selezionata durante il primo passaggio di configurazione. Fai riferimento a [Procedura guidata di distribuzione](../../installation/using/deploying-an-instance.md#deployment-wizard).

La finestra ti consente di configurare l&#39;identificazione degli utenti Adobe Campaign tramite la directory LDAP specificata.

![](assets/s_ncs_install_deployment_wiz_ldap_01.png)

* Specifica l&#39;indirizzo del server LDAP nel **[!UICONTROL LDAP server]** campo . È possibile aggiungere il numero di porta. Per impostazione predefinita, la porta utilizzata è 389.
* Nell’elenco a discesa , seleziona il metodo di autenticazione per gli utenti:

   * Password crittografata (**md5**)

      modalità predefinita.

   * Password testo normale + SSL (**TLS**)

      L&#39;intera procedura di autenticazione (password inclusa) è crittografata. La porta sicura 636 non deve essere utilizzata in questa modalità: Adobe Campaign passa automaticamente alla modalità protetta.

      Quando utilizzi questa modalità di autenticazione, in Linux, il certificato viene verificato da una libreria client openLDAP. È consigliabile utilizzare un certificato SSL valido in modo che la procedura di autenticazione sia crittografata. In caso contrario, le informazioni saranno in testo normale.

      Il certificato viene verificato anche in Windows.

   * Gestione LAN Windows NT (**NTLM**)

      Autenticazione Windows proprietaria. La **[!UICONTROL Unique identifier]** viene utilizzato solo per il nome di dominio.

   * Autenticazione con password distribuita (**DPA**)

      Autenticazione Windows proprietaria. La **[!UICONTROL Unique identifier]** viene utilizzato solo per il nome di dominio (domain.com).

   * Password testo normale

      Nessuna crittografia (solo per le fasi di prova).

* Seleziona la modalità di autenticazione utente: **[!UICONTROL Automatically compute the unique user identifier]** (vedi passaggio [Calcolo del nome distinto](#distinguished-name-calculation)) o **[!UICONTROL Search the unique user identifier in the directory]** (vedi passaggio [Ricerca di identificatori](#searching-for-identifiers)).

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

* Specifica l’identificatore univoco dell’utente nella directory (Nome distinto - DN) nel **[!UICONTROL Distinguished Name]** campo .

   **[!UICONTROL (login)]** viene sostituito con l’identificatore dell’operatore Adobe Campaign.

   >[!CAUTION]
   >
   >La **[!UICONTROL dc]** L&#39;impostazione deve essere in minuscolo.

* Seleziona l’opzione **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** per sincronizzare il gruppo e le associazioni di utenti nella directory LDAP e le associazioni di gruppi e utenti in Adobe Campaign.

   Quando selezioni questa opzione, la **[!UICONTROL Application level DN used for the search]** e **[!UICONTROL Password of the application login]** sono abilitati.

   Se si compilano questi due campi, Adobe Campaign si connetterà al server LDAP con il proprio login e password. Se sono vuoti, Adobe Campaign si connetterà al server in modo anonimo.

## Ricerca di identificatori {#searching-for-identifiers}

Se scegli di cercare un identificatore, la procedura guidata di distribuzione ti consente di configurare la ricerca.

* In **[!UICONTROL Application level DN used for the search]** e **[!UICONTROL Password of the application login]** , fornisci l’identificatore e la password con cui Adobe Campaign si connetterà alla ricerca dell’identificatore. Se sono vuoti, Adobe Campaign si connetterà al server in modo anonimo.
* Specifica la **[!UICONTROL Base identifier]** e **[!UICONTROL Search scope]** campi per determinare un sottoinsieme della directory LDAP da cui avviare la ricerca.

   Seleziona la modalità desiderata nell’elenco a discesa:

   ![](assets/s_ncs_install_deployment_wiz_ldap_03.png)

   1. **[!UICONTROL Recursive (default mode)]**.

      La directory LDAP viene cercata completamente, a partire da un determinato livello.

   1. **[!UICONTROL Limited to the base]**.

      Tutti gli attributi sono inclusi nella ricerca.

   1. **[!UICONTROL Limited to the first sub-level of the base]**.

      La ricerca viene eseguita su tutti gli attributi della directory a partire dal primo livello dell&#39;attributo.

* La **[!UICONTROL Filter]** consente di specificare un elemento per perfezionare l’ambito della ricerca.

## Configurazione delle autorizzazioni LDAP {#configuring-ldap-authorizations}

Questa finestra viene visualizzata quando si seleziona la **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** opzione .

![](assets/s_ncs_install_deployment_wiz_ldap_04.png)

È necessario specificare diversi parametri per trovare il gruppo o i gruppi a cui appartiene l’utente e i relativi diritti, ovvero:

* la **[!UICONTROL Database identifier]** campo,
* la **[!UICONTROL Search scope]** campo,

   >[!NOTE]
   >
   >Se hai scelto di cercare il DN, puoi selezionare **[!UICONTROL Reuse the DN search parameters]** per riportare i valori selezionati per il DN e l&#39;ambito di ricerca dalla schermata precedente.

* la **[!UICONTROL Rights search filter]** in base al login e al nome distinto dell&#39;utente,
* la **[!UICONTROL Attribute containing the group or authorization name]** campo relativo all&#39;utente,
* la **[!UICONTROL Association mask]** campo che abilita l’estrazione del nome del gruppo in Adobe Campaign e dei relativi diritti associati. È possibile utilizzare espressioni regolari per cercare il nome.
* Seleziona **[!UICONTROL Enable the connection of users declared in the LDAP directory if the operator is not declared in Adobe Campaign]** in modo che all&#39;utente vengano automaticamente concessi diritti di accesso alla connessione.

Fai clic su **[!UICONTROL Save]** per completare la configurazione dell’istanza.

## Gestione degli operatori {#managing-operators}

Una volta confermata la configurazione, è necessario definire gli operatori Adobe Campaign gestiti tramite la directory LDAP.

Per utilizzare la directory LDAP per autenticare un operatore, modifica il profilo corrispondente e fai clic sul **[!UICONTROL Edit the access parameters]** link. Seleziona la **[!UICONTROL Use LDAP for authentication]** opzione: La **[!UICONTROL Password]** campo disabilitato per questo operatore.

![](assets/s_ncs_install_operator_in_ldap.png)

## Casi d’uso {#use-cases}

Questa sezione fornisce alcuni semplici casi d’uso per aiutarti a raggiungere le configurazioni più appropriate in base alle tue esigenze.

1. Un utente è stato creato nella directory LDAP ma non in Adobe Campaign.

   Adobe Campaign può essere configurato in modo che l&#39;utente possa accedere alla piattaforma tramite la propria autenticazione LDAP. Adobe Campaign deve essere in grado di controllare la validità della combinazione di ID/password nella directory LDAP, in modo che l&#39;operatore possa essere creato on-the-fly in Adobe Campaign. Per eseguire questa operazione, controlla il **[!UICONTROL Enable the connection of users declared in the LDAP directory if the operator is not declared in Adobe Campaign]** opzione . In questo caso, anche la sincronizzazione dei gruppi deve essere configurata: la **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** deve essere selezionata.

1. L&#39;utente è stato creato in Adobe Campaign ma non nella directory LDAP.

   Non saranno in grado di accedere ad Adobe Campaign.

1. Nella directory LDAP è presente un gruppo che non esiste in Adobe Campaign.

   Questo gruppo non verrà creato in Adobe Campaign. È necessario creare il gruppo e sincronizzare i gruppi per abilitare una corrispondenza tramite il **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** opzione .

1. I gruppi esistono in Adobe Campaign e la directory LDAP viene attivata dopo l&#39;evento: i gruppi di utenti in Adobe Campaign non vengono sostituiti automaticamente con il contenuto dei gruppi LDAP. Allo stesso modo, se un gruppo esiste solo in Adobe Campaign, nessun utente LDAP può essere aggiunto ad esso fino a quando il gruppo non è stato creato e sincronizzato in LDAP.

   I gruppi non vengono mai creati al volo, sia da Adobe Campaign che da LDAP. Devono essere create singolarmente, sia in Adobe Campaign che nella directory LDAP.

   I nomi dei gruppi nella directory LDAP devono coincidere con i nomi dei gruppi Adobe Campaign. La relativa maschera di associazione è definita nell’ultima fase di configurazione della procedura guidata di distribuzione: Adobe Campaign_(.*), ad esempio.
