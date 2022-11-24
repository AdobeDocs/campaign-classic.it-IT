---
product: campaign
title: Nota tecnica - Aggiornamenti del sistema Adobe Campaign
description: Aggiornamento del sistema Adobe Campaign
hide: true
hidefromtoc: true
exl-id: 78949d94-60b3-44f1-8e5a-d61b5b723e87
source-git-commit: 1b7b216c22d48159a1590603de220714c1d7cf32
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 8%

---

# Aggiornamenti dell’ambiente Adobe Campaign 2023 {#ac-system-upgrade}

L’infrastruttura Campaign si basa su sistemi di terze parti che devono essere aggiornati regolarmente con le versioni e le correzioni più recenti. Questi aggiornamenti sono obbligatori per garantire la continuità del servizio e proteggere gli ambienti Campaign dai rischi per la sicurezza. Inoltre, è necessario un aggiornamento di Campaign per garantire la compatibilità con le modifiche del sistema di terze parti.

Come **Cliente Cloud Services ospitati o gestiti**, l’Adobe ti informa di questi aggiornamenti quando sono necessari. Sarà necessario aggiornare gli ambienti in conformità alle raccomandazioni per garantire la conformità.

Come **Clienti on-premise o ibridi**, l’Adobe consiglia vivamente di aggiornare le versioni di sistema e Campaign in base allo stesso calendario.

Per motivi di sicurezza, devi [installa la build Campaign più recente](#ac-upgrade)e quindi aggiorna il [sistema operativo](#os-upgrade) e/o [Sistema di gestione del database delle relazioni (RDBMS)](#pg-upgrade).

>[!NOTE]
>
>Per qualsiasi domanda su queste modifiche, contatta [Adobe Customer Care](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). Vedi anche [Domande frequenti sull’aggiornamento della build](../../platform/using/faq-build-upgrade.md).

## Aggiornamento della build di Campaign {#ac-upgrade}

**Sei interessato da questo problema?**

Se sei interessato dal [aggiornamento del sistema operativo](#os-upgrade) e/o [aggiornamento del sistema di database](#pg-upgrade) di seguito, è necessario aggiornare gli ambienti Campaign a [la versione più recente della versione 7.3.2](../../rn/using/latest-release.m#release-7-3-2), compatibile con tali sistemi.

**Come si esegue l’aggiornamento?**

* In qualità di cliente in hosting o di Cloud Services gestiti, Adobe ti contatterà e aggiornerà la versione Campaign.
* In qualità di cliente ibrido, Adobe ti informerà delle date di aggiornamento della build pianificate per l’ambiente di mid-sourcing. Devi anche aggiornare l’ambiente di marketing alla stessa versione.
* In qualità di cliente on-premise, ti viene richiesto di aggiornare gli ambienti Campaign alla build 7.3.2 più recente.


## Aggiornamento del sistema operativo {#os-upgrade}

**Sei interessato da questo problema?**

Se utilizzi Campaign su un sistema operativo Debian, per usufruire degli ultimi aggiornamenti sulla sicurezza Debian, devi spostare l’infrastruttura Campaign in **Debian 11**. Debian 9 ha raggiunto la fine del ciclo di vita il 30 giugno 2022 e non fornisce più correzioni di sicurezza.

**Come si esegue l’aggiornamento?**

* In qualità di cliente di Cloud Services ospitati o gestiti, Adobe ti contatterà e aggiornerà l’ambiente.
* In qualità di cliente ibrido, Adobe ti informerà delle date di aggiornamento pianificate per l’ambiente di mid-sourcing. Se anche il tuo ambiente di marketing è in esecuzione su Debian, devi aggiornarlo anche a Debian 11.
* In qualità di cliente on-premise, ti viene richiesto di aggiornare i tuoi ambienti a Debian 11.

## Aggiornamento del sistema del database {#pg-upgrade}

**Sei interessato da questo problema?**

Se il sistema di database per Campaign è PostgreSQL, per usufruire delle ultime innovazioni e degli aggiornamenti di sicurezza PostgreSQL, è necessario eseguire l’aggiornamento a **PostgreSQL 14**. PostreSQL 11 raggiungerà la fine del ciclo di vita il 30 novembre 2022.

**Come si esegue l’aggiornamento?**

* In qualità di cliente di Cloud Services ospitati o gestiti, Adobe ti contatterà e aggiornerà il tuo sistema di database da PostgreSQL 11 a PostgreSQL 14.
* In qualità di cliente ibrido, se il sistema di database di marketing è PostgreSQL, è necessario aggiornarlo a PostgreSQL 14.
* In qualità di cliente on-premise, ti viene richiesto di aggiornare il sistema di database a PostgreSQL 14.


## Collegamenti utili

* [Aggiornare l’ambiente](../../production/using/build-upgrade.md)
* [Domande frequenti sull’aggiornamento della build](../../platform/using/faq-build-upgrade.md)
* [Scarica la build più recente di Campaign Classic](https://experience.adobe.com/#/downloads/content/software-distribution/it/campaign.html)
* [Rendere la nuova console client disponibile agli utenti](../../installation/using/client-console-availability-for-windows.md)
