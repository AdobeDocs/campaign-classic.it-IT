---
product: campaign
title: Nota tecnica - Aggiornamenti dei sistemi Adobe Campaign
description: Aggiornamento del sistema Adobe Campaign
feature: Technote, Upgrade
exl-id: 78949d94-60b3-44f1-8e5a-d61b5b723e87
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 4%

---

# Aggiornamenti dell’ambiente Adobe Campaign 2023 {#ac-system-upgrade}

L’infrastruttura di Campaign si basa su sistemi di terze parti che devono essere regolarmente aggiornati con le versioni e le correzioni più recenti. Questi aggiornamenti sono obbligatori per garantire la continuità del servizio e la protezione degli ambienti Campaign dai rischi di sicurezza. Inoltre, è necessario un aggiornamento di Campaign per garantire la compatibilità con modifiche al sistema di terze parti.

As a **Cliente di Cloud Service in hosting o gestiti**, Adobe fornisce informazioni su questi aggiornamenti quando sono necessari. Sarà necessario aggiornare gli ambienti in conformità con le raccomandazioni per garantire la conformità.

Come un **Cliente on-premise o ibrido**, Adobe consiglia vivamente di aggiornare le versioni di sistema e Campaign in base allo stesso calendario.

Per motivi di sicurezza, è necessario [installare la build Campaign più recente](#ac-upgrade), quindi aggiornare il [sistema operativo](#os-upgrade) e/o [Sistema di gestione del database relazionale (RDBMS)](#pg-upgrade).

>[!NOTE]
>
>Per qualsiasi domanda su queste modifiche, contatta [Assistenza clienti Adobe](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). Consulta anche [Domande frequenti sull’aggiornamento della build](../../platform/using/faq-build-upgrade.md).
>

## Aggiornamento della build di Campaign {#ac-upgrade}

**Sei interessato da questo problema?**

Se è interessato da [aggiornamento del sistema operativo](#os-upgrade) e/o [aggiornamento del sistema del database](#pg-upgrade) descritto di seguito, devi aggiornare gli ambienti Campaign a [ultima versione 7.3.2](../../rn/using/latest-release.md#release-7-3-2), compatibile con questi sistemi.

**Come si esegue l’aggiornamento?**

* In qualità di cliente di Cloud Service in hosting o gestiti, Adobe ti contatterà e aggiornerà la tua versione di Campaign.
* In qualità di cliente ibrido, Adobe ti informerà sulle date pianificate per l’aggiornamento della build per l’ambiente di mid-sourcing. Devi anche aggiornare l’ambiente di marketing alla stessa versione.
* In qualità di cliente on-premise, ti viene richiesto di aggiornare gli ambienti Campaign alla build 7.3.2 più recente.


## Aggiornamento del sistema operativo {#os-upgrade}

**Sei interessato da questo problema?**

Se esegui Campaign su un sistema operativo Debian, per beneficiare degli ultimi aggiornamenti di sicurezza Debian, devi spostare l’infrastruttura Campaign in **Debian 11**. Tieni presente che il supporto per la sicurezza di Debian 9 sarà disponibile fino al 30 giugno 2023.

**Come si esegue l’aggiornamento?**

* In qualità di cliente di Cloud Service in hosting o gestiti, Adobe ti contatterà e aggiornerà il tuo ambiente.
* In qualità di cliente ibrido, Adobe ti informerà sulle date di aggiornamento pianificate per l’ambiente di mid-sourcing. Se il tuo ambiente di marketing è in esecuzione anche su Debian, devi aggiornarlo a Debian 11 troppo.
* In qualità di cliente on-premise, ti viene richiesto di aggiornare i tuoi ambienti a Debian 11.

## Aggiornamento del sistema del database {#pg-upgrade}

**Sei interessato da questo problema?**

Se il sistema di database per Campaign è PostgreSQL, per beneficiare delle ultime innovazioni PostgreSQL e degli aggiornamenti di sicurezza, è necessario eseguire l’aggiornamento a **PostgreSQL 14**. Il 9 novembre 2023 PostgreSQL 11 raggiungerà la fine del ciclo di vita.

**Come si esegue l’aggiornamento?**

* In qualità di cliente di Cloud Service in hosting o gestiti, Adobe contatterà l&#39;utente e aggiornerà il sistema di database da PostgreSQL 11 a PostgreSQL 14.
* In qualità di cliente ibrido, se il sistema del database di marketing è PostgreSQL, è necessario aggiornarlo a PostgreSQL 14.
* In qualità di cliente on-premise, ti viene richiesto di aggiornare il sistema di database a PostgreSQL 14.


## Collegamenti utili

* [Aggiornare l’ambiente](../../production/using/build-upgrade.md)
* [Domande frequenti sull’aggiornamento della build](../../platform/using/faq-build-upgrade.md)
* [Scarica la build Campaign Classic più recente](https://experience.adobe.com/#/downloads/content/software-distribution/it/campaign.html)
* [Rendi la nuova Client Console disponibile agli utenti](../../installation/using/client-console-availability-for-windows.md)
