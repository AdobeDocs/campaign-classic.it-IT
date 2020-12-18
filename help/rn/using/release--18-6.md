---
solution: Campaign Classic
product: campaign
title: Versione 18.6
description: Versione 18.6
audience: rn
content-type: reference
topic-tags: latest-release-notes
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '794'
ht-degree: 6%

---


# Versione 18.6{#release-18-6}

## Versione 18.6.2 - Build 8949{#release-18-6-3-build-8949}

22 agosto 2018

>[!CAUTION]
>
>Questa costruzione è stata richiamata. [effettuare l&#39;aggiornamento alla build più recente](../../production/using/build-upgrade.md) o contattare l&#39;Assistenza clienti  Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).[

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
   <td> Banda query<br /> </td> 
   <td> <p>Quando più utenti di Campaign si connettono allo stesso account esterno di FDA Teradata, ora puoi passare una banda di query (coppie chiave/valore) specifica per ciascun utente. Ogni volta che un utente di Campaign esegue una query sul database Teradata,  Adobe Campaign è ora in grado di inviare i metadati associati all'utente. Tali dati, composti da un elenco di chiavi e valori, possono essere utilizzati dagli amministratori Teradata a scopo di controllo o per gestire, ad esempio, i diritti di accesso.</p><p>Per ulteriori informazioni, consulta la <a href="../../installation/using/external-accounts.md">documentazione dettagliata</a>.</p> </td>
  </tr> 
 </tbody> 
</table>

**Miglioramenti**

* I registri di archiviazione delle e-mail sono stati migliorati, il che rende più semplice e chiaro verificare quali e-mail sono state distribuite correttamente o hanno avuto esito negativo attraverso l&#39;archiviazione CCN. (NEO-10675)
* È stato risolto un problema che causava la visualizzazione degli IP del sistema di bilanciamento del carico al posto degli IP dei clienti nei log di monitoraggio. (NEO-11295)
* È stato risolto un problema casuale che causava la sovrascrittura errata delle proprietà di una consegna. (NEO-11015)
* È stato corretto un errore di sintassi durante l&#39;ordinamento dei risultati dell&#39;attività di arricchimento. (NEO-11394)
* È stato risolto un problema che si verificava durante l&#39;utilizzo di campi calcolati in un&#39;attività del flusso di lavoro **[!UICONTROL Survey answers]**. (NEO-11382)
* Tomcat è stato aggiornato per prevenire lo sfruttamento delle vulnerabilità. (NEO-11503)
* È stato corretto un errore con codifica LATIN1 quando si utilizzava una connessione FDA a un database PostgreSQL. (NEO-11299)
* È stato risolto un problema che si verificava durante l&#39;utilizzo dell&#39;opzione di consegna **[!UICONTROL Prepare the personalization data with a workflow]**. (NEO-11047)
* È stato risolto un problema di post-aggiornamento che impediva l&#39;invio di SMS quando si utilizzava un connettore esteso.
* Importazione/esportazione del pacchetto migliorata (registro e regione aggiunti nell’interfaccia).
* È stato risolto un problema che causava errori inutili nel registro post-aggiornamento quando un&#39;attività del flusso di lavoro **[!UICONTROL Survey answers]** non era completamente configurata.

**Evoluzioni tecniche**

Banda query

Una chiave specifica (PROXYUSER o PROXYROLE) viene utilizzata per associare un utente Teradata o un ruolo a un utente di Campaign. È stata aggiunta una nuova autorizzazione per utilizzare questo utente/ruolo proxy. È necessario aggiungere il diritto di accesso GRANT CONNECT THROUGH all&#39;account del database (quello definito nell&#39;account esterno di Teradata).

È stata aggiunta una nuova scheda agli account esterni di Teradata. La scheda **[!UICONTROL Query banding]** include le seguenti opzioni:

* **[!UICONTROL Active]**: selezionare questa casella per attivare la funzione.
* **[!UICONTROL Default]**: immettete un banding di query predefinito che verrà utilizzato se un utente non dispone di bande di query associate. Se non è stata definita alcuna bande di query predefinita, gli utenti che non dispongono di bande di query associate non potranno utilizzare Teradata.
* **[!UICONTROL Users]**: per ogni utente, specificate una bendatura di query. È possibile aggiungere tutte le coppie chiave/valore necessarie. Ad esempio: &quot;priorità=1;carico di lavoro=alto;&quot;

Per ulteriori informazioni sulla bendatura delle query, fare riferimento ai seguenti articoli:

* [https://docs.teradata.com/reader/cY5~BoeEUFWjgN2kBnH3Vw/a5G1~izve68yTMa24kVjVw](https://docs.teradata.com/reader/cY5B%7EoeEUFWjgN2kBnH3Vw/a5G1iz%7Eve68yTMa24kVjVw)
* [https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ)

## Versione 18.6 - Build 8947{#release-18-6-build-8947}

25 giugno 2018

>[!CAUTION]
>
>Questa costruzione è stata richiamata. [eseguire l&#39;aggiornamento alla build più recente](../../production/using/build-upgrade.md) o contattare il supporto tecnico [supporto](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

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
   <td> Miglioramenti alla sicurezza<br /> </td> 
   <td> Una serie di miglioramenti alla sicurezza è stata aggiunta al Campaign Classic. Miglioramenti e correzioni sono elencati di seguito.<br /> </td> 
  </tr> 
  <tr> 
   <td> Supporto di Windows Server 2016<br /> </td> 
   <td>  Adobe Campaign è ora compatibile con Windows Server 2016. Fare riferimento a <a href="https://helpx.adobe.com/campaign/kb/compatibility-matrix.html">Matrice di compatibilità Campaign Classic</a>.<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Miglioramenti della sicurezza**

decryptString

La funzione **decryptString** è obsoleta. Fare riferimento all&#39;articolo [Funzioni obsolete e rimosse](https://helpx.adobe.com/it/campaign/kb/deprecated-and-removed-features.html).

Per i nuovi clienti, questa funzione è ora utilizzata solo per decifrare l&#39;ID crittografato del destinatario nelle pagine di destinazione. Per decifrare le password memorizzate in un account esterno, utilizzare la nuova funzione **decrittografarePassword**.

Per i clienti esistenti, il comportamento di questa funzione non viene modificato, ma si consiglia di utilizzare **decrittografarePassword** invece di **decrittareString**. L&#39;opzione di compatibilità **XtkSecurity_Unsafe_DecryptString** viene aggiunta dall&#39;aggiornamento successivo e attivata per impostazione predefinita, consentendo di continuare a utilizzare la funzione. Per disattivare **deryptString**, disattivate l&#39;opzione.

decryptPassword

È stata aggiunta la funzione **deryptPassword**. Consente di decrittografare una password memorizzata in un account esterno. Per ulteriori informazioni, fare riferimento alla documentazione [JSAPI](https://helpx.adobe.com/it/campaign/kb/compatibility-matrix.html).

API dei file

Per le nuove installazioni, l&#39;accesso alle cartelle tramite le API dei file è limitato alle **var**, **sftp** e alle cartelle temporanee di  Adobe Campaign.

Per i clienti esistenti, le API dei file non possono più accedere alla cartella **conf** di  Adobe Campaign. L&#39;opzione di compatibilità **XtkSecurity_Disable_JSFileSandboxing** viene aggiunta dal postaggiornamento e attivata per impostazione predefinita, consentendo di continuare ad accedere alle altre cartelle. Per limitare l&#39;accesso alle **var**, **sftp** e alle cartelle temporanee di  Adobe Campaign, disattivate l&#39;opzione.

**Patch**

* È stato risolto un problema che poteva influire sulle prestazioni dei messaggi transazionali SMS. (NEO-9812)
