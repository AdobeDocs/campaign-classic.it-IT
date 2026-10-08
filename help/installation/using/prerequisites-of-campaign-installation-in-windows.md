---
product: campaign
title: Prerequisiti per l’installazione di Campaign in Windows
description: Prerequisiti per l’installazione di Campaign in Windows
feature: Installation, Instance Settings
badge-v7-prem: label="On-premise/hybrid only" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: a7cf59cc-9260-4109-af4c-b2e2a9c999da
TQID: 'https://experienceleague.adobe.com/vECxz7-bt6DMteRM-N4BtD6Uo5qonHrkgQQeEOkTSt0'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 7f0a1ee5-eeb8-5478-a9cd-b1896f033118
    internal-label: Instance Settings
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: e656c701-3899-4db3-989c-de0980ddfffa
    internal-label: Installation
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 11%
---
# Introduzione all’installazione di Campaign su Windows {#prerequisites-of-campaign-installation-in-windows}



La configurazione tecnica e il software necessari per installare Adobe Campaign sono presentati nella [Matrice di compatibilità](../../rn/using/compatibility-matrix.md).

Il processo di installazione del server Adobe Campaign per l&#39;utilizzo di più istanze è descritto di seguito in [Installazione del server](../../installation/using/installing-the-server.md).

Le fasi principali sono le seguenti:

1. Installare il server applicazioni, consultare [Esecuzione del programma di installazione](../../installation/using/installing-the-server.md#executing-the-installation-program).
1. Integrare con un server Web (facoltativo, a seconda dei componenti distribuiti), vedere [Configurazione del server Web IIS](../../installation/using/integration-into-a-web-server-for-windows.md#configuring-the-iis-web-server).

Una volta completati i passaggi di installazione, è necessario configurare le istanze, il database e il server. Per ulteriori informazioni, consulta [Informazioni sulla configurazione iniziale](../../installation/using/about-initial-configuration.md).

>[!NOTE]
>
>Quando Adobe Campaign viene distribuito in un ambiente Windows, gli utenti con i diritti di accesso necessari possono utilizzare la sintassi UNC (Universal.Uniform Naming Convention) per i percorsi di accesso durante la manipolazione dei file in rete.
