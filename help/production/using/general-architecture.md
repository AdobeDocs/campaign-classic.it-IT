---
solution: Campaign Classic
product: campaign
title: Architettura generale
description: Architettura generale
audience: production
content-type: reference
topic-tags: introduction
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 4%

---


# Architettura generale{#general-architecture}

## Architettura minima {#minimum-architecture}

In una configurazione minima,  Adobe Campaign funziona con:

*  server applicazioni Adobe Campaign,
* il database.

   ![](assets/formation_exploitation.png)

Questo diagramma mostra che l&#39;unico traffico coinvolto nel contesto di un&#39;architettura minima è:

1. traffico del protocollo HTTP verso il server Adobe Campaign  tramite Internet,
1. Traffico del protocollo SMTP da e verso il server Adobe Campaign  tramite Internet.

## Architettura distribuita {#distributed-architecture}

 Adobe Campaign è costituito da moduli multipli che possono essere suddivisi su più computer. Questa modalità operativa presenta diversi vantaggi:

* bilanciamento del carico,
* l&#39;impostazione della ridondanza del modulo,
* creazione di un&#39;architettura suddivisa in più fornitori di servizi (segmentazione dei servizi forniti).

![](assets/architecturerepartie.png)

La distribuzione dei moduli su diverse macchine offre una grande flessibilità d&#39;uso e una migliore adattabilità.

>[!NOTE]
>
>For more on the various architectures, refer to [this section](../../installation/using/general-architecture.md).

## Elenco delle porte aperte {#list-of-open-ports}

| Numero della porta | Modulo o applicazione Adobe Campaign interessati  | Configurabile |
|---|---|---|
| 443/tcp o 80/tcp | Server Web (Apache/IIS) | SÌ |
| 6666/udp (locale) |  Adobe Campaign: Syslogd | SÌ |
| 8005/tcp (locale) |  Adobe Campaign: modulo web | SÌ |
| 8080/tcp |  Adobe Campaign: modulo web (tomcat) | SÌ |
| 7777 | Server delle statistiche (server di stato) | SÌ |

