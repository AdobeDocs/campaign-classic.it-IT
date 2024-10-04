---
product: campaign
title: Introduzione agli aggiornamenti
description: Ulteriori informazioni sugli aggiornamenti di Campaign Classic
feature: Release Notes
role: User
level: Beginner
exl-id: 7a05fdff-8f9d-4e8d-812e-0f1509db5499
source-git-commit: 7b71cac6f4c2fc2e8d30683130adb27eff757b73
workflow-type: tm+mt
source-wordcount: '903'
ht-degree: 100%

---

# Aggiornamenti della versione {#rn-overview}

Per Adobe Campaign Classic vengono rilasciati periodicamente aggiornamenti di prodotto con nuove funzionalità, correzioni di bug e miglioramenti delle a livello di prestazioni, sicurezza e usabilità. Questi aggiornamenti vengono rilasciati come **build del prodotto**. Informazioni dettagliate su ogni nuova build sono disponibili nella sezione [Note sulla versione](latest-release.md).

<!--
## Product versions

For Campaign, the version naming is the following:

1. Campaign Major version are v7 and v8.
1. A Minor version is a sub-version of a Major version. For example: v7.3, v7.4.
1. A Patch version is a post-release fix. For example: v7.3.2, v7.3.3.


Aligned with this naming, Campaign has 3 types of upgrades:

1. Major Upgrades - A major upgrade is an upgrade to a new version of Adobe Campaign (ex: v7 to v8)
1. Minor Upgrades - A minor upgrade brings new features, enhancements and fixes (ex: 7.4.X to 7.5.X)
1. Patch Upgrades - A patch upgrade includes fixes only (ex: 8.5.1 to 8.5.2)
-->

## Stato delle versioni {#rn-statuses}

A ogni nuova versione è associato uno stato identificato da un colore nelle [Note sulla versione](latest-release.md).

| Stato | Descrizione |
|---|---|
| [!BADGE Disponibilità generale]{type=Positive} | La più recente build stabile, convalidata in produzione e raccomandata da Adobe. |
| [!BADGE Disponibilità limitata]{type=Informative} | Solo per implementazione su richiesta. |
| [!BADGE Obsoleto]{type=negative} | Nessuna distribuzione. Nessun bug fix. Le implementazioni esistenti devono essere aggiornate. |

## Ciclo di rilascio {#rn-cycle}

Adobe Campaign viene aggiornato regolarmente. La frequenza regolare degli aggiornamenti è volta a far ottenere agli utenti il prodotto migliore e più recente, mantenendo l’ambiente sicuro e migliorando l’esperienza di utilizzo.

Per questo motivo è fondamentale **eseguire la build stabile più recente** di Adobe Campaign. In questo modo sarà possibile ottenere un’esperienza di supporto migliore, poiché identificare, riprodurre e risolvere un problema in una build recente è generalmente molto più rapido. Inoltre, molti problemi che gli utenti potrebbero incontrare sono già stati risolti nelle build più recenti.

In qualità di cliente in hosting, puoi beneficiare automaticamente, senza alcun intervento da parte tua, dell’aggiornamento alla build stabile più recente. Ulteriori informazioni nella [sezione Aggiornamento annuale](#yearly-upgrade). Se effettui la migrazione da una build precedente, Adobe consiglia di eseguire prima l’aggiornamento a questa build.

## Raccomandazioni {#rn-recommendations}

Per garantire una configurazione stabile, si consiglia di installare **la stessa build** su tutti i server in esecuzione sulla stessa configurazione client.

Inoltre, salvo diversa indicazione nelle [Note sulla versione](latest-release.md), la console client e l’istanza del server devono avere la **stessa build**.

Per mantenere aggiornata l’implementazione, per ogni nuova versione leggi le pagine [Funzioni obsolete e rimosse](../../rn/using/deprecated-features.md) e [Matrice di compatibilità](../../rn/using/compatibility-matrix.md).

## Processo di aggiornamento{#process-upgrade}

In qualità di cliente in hosting, Managed Services o ibrido, contatta l’Assistenza clienti di Adobe per aggiornare l’ambiente.

In qualità di cliente on-premise, puoi eseguire l’aggiornamento. A tal fine, è necessario [scaricare la build stabile più recente (GA)](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) e aggiornare tutti gli ambienti.

Per ulteriori informazioni, consulta l’articolo sul [processo di aggiornamento](../../production/using/build-upgrade.md) e le [domande frequenti sull’aggiornamento della build](../../platform/using/faq-build-upgrade.md).

## Aggiornamento annuale {#yearly-upgrade}

Adobe si impegna a fornire la migliore esperienza e il maggior valore tramite soluzioni software. Ci impegniamo a garantire l’accesso alle versioni più recenti delle tecnologie correlate con cui interagiscono le nostre soluzioni al fine di eseguire le proprie attività.

Adobe Campaign Classic, in particolare, utilizza una gamma di tecnologie per fornire valore. Questa combinazione di tecnologie richiede l’aggiornamento regolare delle istanze di Campaign Classic, così da assicurarti di utilizzare le versioni più aggiornate al fine di garantire la massima protezione, stabilità e prestazioni.

In qualità di utente in hosting, potrai beneficiare automaticamente, senza alcun intervento da parte tua, dell’aggiornamento alla più recente build con disponibilità generale (GA). Ulteriori informazioni sono disponibili nelle domande frequenti riportate di seguito.

### Perché la mia organizzazione ha bisogno di questo aggiornamento?

In qualità di cliente in hosting, se il tuo account necessita l’aggiornamento di una o più tecnologie correlate a Campaign Classic ed è necessario aggiornare l’infrastruttura alla build (ad esempio dalla v7.2.1 alla v7.3.3) e/o alla versione (ad esempio dalla v7 alla v8) corrente, riceverai una notifica direttamente da Adobe.

In qualità di cliente on-premise o ibrido che utilizza una build precedente, Adobe ti consiglia di passare all’ultima build stabile (GA).

In questo modo il tuo account sarà protetto da eventuali vulnerabilità e potrà sfruttare le prestazioni fornite dalle tecnologie aggiornate. Questo aggiornamento consentirà anche al tuo account di usufruire di aggiornamenti più semplici, regolari e meno laboriosi.

### Quali sono il processo e tempistica di questo aggiornamento?

Il team Adobe guiderà la tua organizzazione attraverso questo percorso.

Abbiamo organizzato un team di responsabili dell’Assistenza clienti, Product Manager, tecnici, specialisti TechOps e consulenti di prodotto che potrà assisterti e garantire un’esperienza fluida.

### Vantaggi

<tr>
  <td>
      <img alt="Sicurezza" src="assets/do-not-localize/security.png"/>
    <div>
    <strong>Maggiore sicurezza</strong>
    </div>
    <ul>
    <li>Diverse tecnologie utilizzate per alimentare Adobe Campaign Classic funzionano congiuntamente per offrire valore.</li>
    <li>Tutte le istanze devono essere aggiornate per garantire la sicurezza.</li>
    <li>La sicurezza richiede attenzione costante e manutenzione proattiva.</li>
    <li>I rischi di sicurezza sono onnipresenti e non possono essere ignorati: ogni aggiornamento di Campaign Classic migliora la sicurezza.</li>
    </ul>
  </td>

<td>
      <img alt="Assistenza" src="assets/do-not-localize/support.png" />
    <div>
    <strong>Supporto migliorato</strong>
    </div>
    <ul>
    <li>La maggior parte dei problemi critici in realtà vengono risolti con gli aggiornamenti e possono essere evitati.</li>
    <li>Gli aggiornamenti regolari contribuiscono a ridurre ed eliminare le difficoltà e di conseguenza aumentano l’efficienza.</li>
    <li>La riduzione nel volume di richieste di assistenza determina risoluzioni più rapide e maggiore attenzione ai problemi che non sono correlati agli aggiornamenti.</li>
    </ul>
  </td>
</tr>

<tr>
  <td>
      <img alt="Manutenzione" src="assets/do-not-localize/maintenance.png"/>
    <div>
    <strong>Manutenzione e stabilità migliorate</strong>
    </div>
    <ul>
    <li>Nel tempo, il team Adobe Campaign individua modi efficaci per migliorare la stabilità e le prestazioni del prodotto e per risolvere i problemi noti.</li>
    <li>L’aggiornamento permette di usufruire di tali miglioramenti ed elimina le problematiche comuni riscontrate dalle organizzazioni che registrano una rapida crescita e/o complessità all’interno delle proprie istanze di Campaign Classic.</li>
    <li>I team di marketing e IT dell’organizzazione coglieranno subito i miglioramenti implementati nello stack tecnologico di Campaign Classic.</li>
    </ul>
  </td>

<td>
      <img alt="Aggiornamento della build" src="assets/do-not-localize/upgrades.png" />
    <div>
    <strong>Aggiornamenti più semplici</strong>
    </a>
    </div>
    <ul>
    <li>L’aggiornamento dell’istanza di Campaign Classic risulta più complesso e laborioso se si saltano una o più versioni.</li>
    <li>Più si rimanda l’aggiornamento, più questo diventa complesso (e più ci si espone a vulnerabilità).</li>
    <li>Con aggiornamenti regolari si riducono sia i tempi di inattività associati alla procedura di aggiornamento, sia il rischio di regressione.</li>
    </ul>
  </td>
</tr>
</table>

## Risorse aggiuntive{#support}

* [Trova la versione Campaign](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).
* [Guida e supporto](../../support.md)
* [Versioni del Pannello di controllo](https://experienceleague.adobe.com/docs/control-panel/using/release-notes.html?lang=it)
* [Ultimi aggiornamenti della documentazione](../../rn/using/documentation-updates.md)
* [Funzioni obsolete e rimosse](../../rn/using/deprecated-features.md)
* [Domande frequenti sull’aggiornamento della build](../../platform/using/faq-build-upgrade.md)

Per ricevere informazioni sulle nuove versioni della soluzione Experience Cloud, abbonati ad [Adobe Priority Product Update](https://www.adobe.com/it/subscription/priority-product-update.html).
