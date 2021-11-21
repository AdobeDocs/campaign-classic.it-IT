---
product: campaign
title: Note sulla versione 18.6 di Campaign
description: Note sulla versione di Campaign 18.6
audience: rn
content-type: reference
topic-tags: latest-release-notes
feature: Overview
role: User
level: Beginner
exl-id: a849ce10-0972-4c42-b10e-67a81c79bc65
source-git-commit: c281d437907efb4d514bec7cacc698c383f3fe53
workflow-type: tm+mt
source-wordcount: '794'
ht-degree: 7%

---

# Versione 18.6{#release-18-6}

![](../../assets/v7-only.svg)

## Versione 18.6.2 - Build 8949{#release-18-6-3-build-8949}

22 agosto 2018

>[!CAUTION]
>
>Questa build è stata richiamata. Per favore [aggiornamento alla build più recente](../../production/using/build-upgrade.md) o contatti [Adobe Customer Care](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**Novità**

<table> 
 <thead> 
  <tr> 
   <th> Funzionalità<br /> </th> 
   <th> Descrizione<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Proiezione query<br /> </td> 
   <td> <p>Quando più utenti di Campaign si collegano allo stesso account esterno della Teradata FDA, ora puoi passare una banda di query (coppie chiave/valore) specifica per ogni utente. Ogni volta che un utente di Campaign esegue una query sul database di Teradata, Adobe Campaign è ora in grado di inviare i metadati associati all’utente. Questi dati, costituiti da un elenco di chiavi e valori, possono quindi essere utilizzati dagli amministratori di Teradata a scopo di controllo o per gestire i diritti di accesso, ad esempio.</p><p>Per ulteriori informazioni, consulta la <a href="../../installation/using/external-accounts.md">documentazione dettagliata</a>.</p> </td>
  </tr> 
 </tbody> 
</table>

**Miglioramenti**

* I registri di archiviazione delle e-mail sono stati migliorati, il che rende più semplice e chiaro il controllo delle e-mail consegnate correttamente o non riuscite tramite l’archiviazione CCN. (NEO-10675)
* È stato risolto un problema che causava la visualizzazione degli IP del load balancer invece degli IP dei clienti nei log di monitoraggio dei broadcaster. (NEO-11295)
* È stato risolto un problema casuale che causava la sovrascrittura errata delle proprietà di una consegna. (NEO-11015)
* È stato corretto un errore di sintassi durante l’ordinamento dei risultati dell’attività di arricchimento. (NEO-11394)
* È stato risolto un problema che si verificava durante l’utilizzo dei campi calcolati in una **[!UICONTROL Survey answers]** attività del flusso di lavoro. (NEO-11382)
* Tomcat è stato aggiornato per prevenire lo sfruttamento delle vulnerabilità. (NEO-11503)
* È stato corretto un errore di codifica LATIN1 durante l’utilizzo di una connessione FDA a un database PostgreSQL. (NEO-11299)
* È stato risolto un problema che si verificava durante l&#39;utilizzo del **[!UICONTROL Prepare the personalization data with a workflow]** opzione di consegna. (NEO-11047)
* È stato risolto un problema relativo al post aggiornamento che impediva l’invio di SMS quando si utilizzava un connettore esteso.
* Importazione/esportazione del pacchetto migliorata (registro e area geografica aggiunti nell’interfaccia).
* È stato risolto un problema che mostrava errori inutili nel registro post-aggiornamento quando un **[!UICONTROL Survey answers]** attività del flusso di lavoro non configurata completamente.

**Evoluzioni tecniche**

Proiezione query

Una chiave specifica (PROXYUSER o PROXYROLE) viene utilizzata per associare un utente o un ruolo di Teradata a un utente di Campaign. È stata aggiunta una nuova autorizzazione per utilizzare questo utente/ruolo proxy. È necessario aggiungere il diritto di accesso GRANT CONNECT THROUGH all’account del database (quello definito nell’account esterno Teradata).

È stata aggiunta una nuova scheda negli account esterni Teradata. La **[!UICONTROL Query banding]** La scheda include le seguenti opzioni:

* **[!UICONTROL Active]**: selezionare questa casella per attivare la funzione.
* **[!UICONTROL Default]**: immetti un binding di query predefinito che verrà utilizzato se un utente non dispone di un binding di query associato. Se non è definito alcun banding di query predefinito, gli utenti che non dispongono di un binding di query associato non saranno in grado di utilizzare Teradate.
* **[!UICONTROL Users]**: per ogni utente, specificare una banda di query. Puoi aggiungere tutte le coppie chiave/valore necessarie. Ad esempio: &quot;priority=1;carico di lavoro=alto;&quot;

Per ulteriori informazioni sul binding delle query, consulta questi articoli:

* [https://docs.teradata.com/reader/cY5B~oeEUFWjgN2kBnH3Vw/a5G1iz~ve68yTMa24kVjVw](https://docs.teradata.com/reader/cY5B%7EoeEUFWjgN2kBnH3Vw/a5G1iz%7Eve68yTMa24kVjVw)
* [https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ)

## Versione 18.6 - Build 8947{#release-18-6-build-8947}

25 giugno 2018

>[!CAUTION]
>
>Questa build è stata richiamata. Per favore [aggiornamento alla build più recente](../../production/using/build-upgrade.md) o contatti [supporto tecnico](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**Novità**

<table> 
 <thead> 
  <tr> 
   <th> Funzionalità<br /> </th> 
   <th> Descrizione<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Miglioramenti della sicurezza<br /> </td> 
   <td> In Campaign Classic è stata aggiunta una serie di miglioramenti a livello di sicurezza. I miglioramenti e le correzioni sono elencati di seguito.<br /> </td> 
  </tr> 
  <tr> 
   <td> Supporto di Windows Server 2016<br /> </td> 
   <td> Adobe Campaign è ora compatibile con Windows Server 2016. Fai riferimento a <a href="https://helpx.adobe.com/campaign/kb/compatibility-matrix.html">Matrice di compatibilità di Campaign Classic</a>.<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Miglioramenti di sicurezza**

decryptString

La **decryptString** è obsoleta. Fai riferimento a [Funzioni obsolete e rimosse](deprecated-features.md) articolo.

Per i nuovi clienti, questa funzione ora viene utilizzata solo per decifrare l’ID crittografato del destinatario nelle pagine di destinazione. Per decrittografare le password memorizzate in un account esterno, utilizza il nuovo **decryptPassword** funzione .

Per i clienti esistenti, il comportamento di questa funzione non viene modificato, ma ti consigliamo di utilizzare **decryptPassword** anziché **decryptString**. La **XtkSecurity_Unsafe_DecryptString** l’opzione di compatibilità viene aggiunta dall’aggiornamento successivo e attivata per impostazione predefinita, consentendo di continuare a utilizzare la funzione . Per disattivare **decryptString**, disattiva l’opzione .

decryptPassword

La **decryptPassword** è stata aggiunta la funzione . Consente di decrittografare una password memorizzata in un account esterno. Fai riferimento a [JSAPI](https://helpx.adobe.com/it/campaign/kb/compatibility-matrix.html) documentazione per ulteriori informazioni.

API file

Per le nuove installazioni, l’accesso alle cartelle tramite API di file è limitato alla **var**, **sftp** e cartelle temporanee di Adobe Campaign.

Per i clienti esistenti, le API dei file non possono più accedere al **conf** cartella di Adobe Campaign. La **XtkSecurity_Disable_JSFileSandboxing** l’opzione di compatibilità viene aggiunta dall’aggiornamento successivo e attivata per impostazione predefinita, consentendo di continuare ad accedere alle altre cartelle. Se desideri limitare l’accesso al **var**, **sftp** e cartelle temporanee di Adobe Campaign, disattiva l’opzione .

**Patch**

* È stato risolto un problema che poteva influire sulle prestazioni dei messaggi transazionali SMS. (NEO-9812)
