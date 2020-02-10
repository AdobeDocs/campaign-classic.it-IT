---
title: Architettura generale
seo-title: Architettura generale
description: Architettura generale
seo-description: null
page-status-flag: never-activated
uuid: a565a10c-cbef-455a-aa1d-9be9cd207c7a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: introduction
discoiquuid: f4879774-afe5-4556-ab60-9297cabbca2c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Architettura generale{#general-architecture}

## Architettura minima {#minimum-architecture}

Con una configurazione minima, Adobe Campaign funziona con:

* il server dell’applicazione Adobe Campaign,
* il database.

   ![](assets/formation_exploitation.png)

Questo diagramma mostra che l&#39;unico traffico coinvolto nel contesto di un&#39;architettura minima è:

1. traffico del protocollo HTTP verso il server Adobe Campaign tramite Internet,
1. Traffico del protocollo SMTP da e verso il server Adobe Campaign tramite Internet.

## Architettura distribuita {#distributed-architecture}

Adobe Campaign è costituito da più moduli che possono essere suddivisi su più computer. Questa modalità operativa presenta diversi vantaggi:

* bilanciamento del carico,
* l&#39;impostazione della ridondanza del modulo,
* creazione di un&#39;architettura suddivisa in più fornitori di servizi (segmentazione dei servizi forniti).

![](assets/architecturerepartie.png)

La distribuzione dei moduli su diverse macchine offre una grande flessibilità d&#39;uso e una migliore adattabilità.

>[!NOTE]
>
>Per ulteriori informazioni sulle diverse architetture, consulta [questa sezione](../../installation/using/general-architecture.md).

## Elenco delle porte aperte {#list-of-open-ports}

| Numero porta | Modulo o applicazione Adobe Campaign interessati | Configurabile |
|---|---|---|
| 443/tcp o 80/tcp | Server Web (Apache/IIS) | SÌ |
| 6666/udp (locale) | Adobe Campaign: Syslogd | SÌ |
| 8005/tcp (locale) | Adobe Campaign: modulo web | SÌ |
| 8080/tcp | Adobe Campaign: modulo web (tomcat) | SÌ |
| 7777 | Server delle statistiche (server di stato) | SÌ |

