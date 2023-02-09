---
product: campaign
title: Architettura generale
description: Architettura generale
audience: production
content-type: reference
topic-tags: introduction
exl-id: 3bfb5448-6996-4080-bf9a-434f1207637e
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 4%

---

# Architettura generale{#general-architecture}

![](../../assets/v7-only.svg)

## Architettura minima {#minimum-architecture}

In una configurazione minima, Adobe Campaign funziona con:

* il server dell’applicazione Adobe Campaign,
* il database.

   ![](assets/formation_exploitation.png)

Questo diagramma mostra che l’unico traffico coinvolto nel contesto di un’architettura minima è:

1. traffico del protocollo HTTP verso il server Adobe Campaign tramite Internet,
1. Traffico del protocollo SMTP da e verso il server Adobe Campaign tramite Internet.

## Architettura distribuita {#distributed-architecture}

Adobe Campaign è costituito da più moduli che possono essere suddivisi su più macchine. Questa modalità operativa presenta diversi vantaggi:

* bilanciamento del carico,
* l&#39;impostazione della ridondanza dei moduli,
* creazione di un’architettura suddivisa per diversi fornitori di servizi (segmentazione dei servizi forniti).

![](assets/architecturerepartie.png)

La distribuzione dei moduli su diverse macchine offre una grande flessibilità d&#39;uso e una migliore adattabilità.

>[!NOTE]
>
>Per ulteriori informazioni sulle varie architetture, consulta [questa sezione](../../installation/using/general-architecture.md).

## Elenco delle porte aperte {#list-of-open-ports}

| Numero della porta | Modulo o applicazione Adobe Campaign interessati | Configurabile |
|---|---|---|
| 443/tcp o 80/tcp | Server web (Apache/IIS) | SÌ |
| 6666/udp (locale) | Adobe Campaign: Slogd | SÌ |
| 8005/tcp (locale) | Adobe Campaign: modulo web | SÌ |
| 8080/tcp | Adobe Campaign: modulo web (tomcat) | SÌ |
| 7777 | Server statistiche (server stat) | SÌ |
