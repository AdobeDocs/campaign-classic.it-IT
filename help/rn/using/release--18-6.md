---
title: Versione 18.6
seo-title: Versione 18.6
description: Versione 18.6
seo-description: null
page-status-flag: never-activated
uuid: 72941f8f-0b84-4868-a768-8aa972459ef2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rn
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 79a6d3cf-2425-49b9-9b92-b56be26438bf
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '813'
ht-degree: 8%

---


# Versione 18.6{#release-18-6}

## Versione 18.6.2 - Build 8949{#release-18-6-3-build-8949}

22 agosto 2018

>[!CAUTION]
>
>Questa costruzione è stata richiamata. Effettuare l&#39; [aggiornamento alla build](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) più recente o contattare il supporto [](https://support.neolane.net/)tecnico.

**Novità?**

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
   <td> <p>Quando più utenti di Campaign si connettono allo stesso account esterno FDA Teradata, ora puoi passare una banda di query (coppie chiave/valore) specifica per ciascun utente. Ogni volta che un utente di Campaign esegue una query sul database Teradata,  Adobe Campaign è ora in grado di inviare i metadati associati all'utente. Tali dati, composti da un elenco di chiavi e valori, possono essere utilizzati dagli amministratori Teradata a scopo di audit o per gestire, ad esempio, i diritti di accesso.</p><p>Per ulteriori informazioni, consulta la <a href="https://docs.campaign.adobe.com/doc/AC/en/PTF_Administration_basics_External_accounts.html#Teradata_external_account">documentazione dettagliata</a>.</p> </td>
  </tr> 
 </tbody> 
</table>

**Miglioramenti**

* I registri di archiviazione delle e-mail sono stati migliorati, il che rende più semplice e chiaro verificare quali e-mail sono state distribuite correttamente o hanno avuto esito negativo attraverso l&#39;archiviazione CCN. (NEO-10675)
* È stato risolto un problema che causava la visualizzazione degli IP del sistema di bilanciamento del carico al posto degli IP dei clienti nei log di monitoraggio. (NEO-11295)
* È stato risolto un problema casuale che causava la sovrascrittura errata delle proprietà di una consegna. (NEO-11015)
* È stato corretto un errore di sintassi durante l&#39;ordinamento dei risultati dell&#39;attività di arricchimento. (NEO-11394)
* È stato risolto un problema che si verificava durante l&#39;utilizzo di campi calcolati in un&#39;attività di **[!UICONTROL Survey answers]** flusso di lavoro. (NEO-11382)
* Tomcat è stato aggiornato per prevenire lo sfruttamento delle vulnerabilità. (NEO-11503)
* È stato corretto un errore con codifica LATIN1 quando si utilizzava una connessione FDA a un database PostgreSQL. (NEO-11299)
* È stato risolto un problema che si verificava durante l&#39;utilizzo dell&#39;opzione di **[!UICONTROL Prepare the personalization data with a workflow]** consegna. (NEO-11047)
* È stato risolto un problema di post-aggiornamento che impediva l&#39;invio di SMS quando si utilizzava un connettore esteso.
* Importazione/esportazione del pacchetto migliorata (registro e regione aggiunti nell’interfaccia).
* È stato risolto un problema che causava errori inutili nel registro post-aggiornamento quando un&#39;attività del **[!UICONTROL Survey answers]** flusso di lavoro non era completamente configurata.

**Evoluzioni tecniche**

Banda query

Una chiave specifica (PROXYUSER o PROXYROLE) viene utilizzata per associare un utente Teradata o un ruolo a un utente Campaign. È stata aggiunta una nuova autorizzazione per utilizzare questo utente/ruolo proxy. È necessario aggiungere il diritto di accesso GRANT CONNECT THROUGH all&#39;account del database (quello definito nell&#39;account esterno di Teradata).

È stata aggiunta una nuova scheda nei conti esterni Teradata. La **[!UICONTROL Query banding]** scheda include le seguenti opzioni:

* **[!UICONTROL Active]**: selezionare questa casella per attivare la funzione.
* **[!UICONTROL Default]**: immettete un banding di query predefinito che verrà utilizzato se un utente non dispone di bande di query associate. Se non è definita alcuna banding di query predefinita, gli utenti che non dispongono di bande di query associate non potranno utilizzare Teradata.
* **[!UICONTROL Users]**: per ogni utente, specificate una bendatura di query. È possibile aggiungere tutte le coppie chiave/valore necessarie. Ad esempio: &quot;priorità=1;carico di lavoro=alto;&quot;

Per ulteriori informazioni sulla bendatura delle query, fare riferimento ai seguenti articoli:

* [https://docs.teradata.com/reader/cY5~BoeEUFWjgN2kBnH3Vw/a5G1~izve68yTMa24kVjVw](https://docs.teradata.com/reader/cY5B%7EoeEUFWjgN2kBnH3Vw/a5G1iz%7Eve68yTMa24kVjVw)
* [https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ)

## Versione 18.6 - Build 8947{#release-18-6-build-8947}

25 giugno 2018

>[!CAUTION]
>
>Questa costruzione è stata richiamata. Effettuare l&#39; [aggiornamento alla build](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) più recente o contattare il supporto [](https://support.neolane.net/)tecnico.

**Novità?**

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
   <td> Una serie di miglioramenti alla sicurezza è stata aggiunta al Campaign Classic. I miglioramenti e le correzioni sono elencati di seguito.<br /> </td> 
  </tr> 
  <tr> 
   <td> Supporto di Windows Server 2016<br /> </td> 
   <td>  Adobe Campaign è ora compatibile con Windows Server 2016. Fare riferimento alla matrice <a href="https://helpx.adobe.com/it/campaign/kb/compatibility-matrix.html">di compatibilità</a>Campaign Classic.<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Miglioramenti della sicurezza**

decryptString

La funzione **deryptString** è obsoleta. Consultate l&#39;articolo [Funzioni](https://helpx.adobe.com/it/campaign/kb/deprecated-and-removed-features.html) obsolete e rimosse.

Per i nuovi clienti, questa funzione è ora utilizzata solo per decifrare l&#39;ID crittografato del destinatario nelle pagine di destinazione. Per decifrare le password memorizzate in un account esterno, utilizzare la nuova funzione **decryptPassword** .

Per i clienti esistenti, il comportamento di questa funzione non viene modificato, ma si consiglia di utilizzare **decryptPassword** invece di **decryptString**. L&#39;opzione di compatibilità **XtkSecurity_Unsafe_DecryptString** viene aggiunta dall&#39;aggiornamento successivo e attivata per impostazione predefinita, consentendo di continuare a utilizzare la funzione. Per disattivare **deryptString**, disattivate l’opzione.

decryptPassword

È stata aggiunta la funzione **deryptPassword** . Consente di decrittografare una password memorizzata in un account esterno. Per ulteriori informazioni, consulta la documentazione [JSAPI](https://helpx.adobe.com/it/campaign/kb/compatibility-matrix.html) .

API dei file

Per le nuove installazioni, l&#39;accesso alle cartelle tramite le API dei file è limitato alle cartelle **var**, **sftp** e temporanee di  Adobe Campaign.

Per i clienti esistenti, le API dei file non possono più accedere alla cartella **conf** di  Adobe Campaign. L&#39;opzione di compatibilità **XtkSecurity_Disable_JSFileSandboxing** viene aggiunta dall&#39;aggiornamento successivo e attivata per impostazione predefinita, consentendo di continuare ad accedere alle altre cartelle. Per limitare l&#39;accesso alle cartelle **var**, **sftp** e temporanee di  Adobe Campaign, disattivate l&#39;opzione.

**Patch**

* È stato risolto un problema che poteva influire sulle prestazioni dei messaggi transazionali SMS. (NEO-9812)
