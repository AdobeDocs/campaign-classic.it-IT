---
product: campaign
title: Integrazione con Adobe Target
description: Integrazione con Adobe Target
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: 2e29d090-b87b-4cff-a703-58e1da082f04
source-git-commit: b458ac67733a2f0e508df729add37d9a78dbcbd8
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---

# Integrazione con Adobe Target{#integrating-with-adobe-target}

![](../../assets/v7-only.svg)

L’integrazione tra Adobe Campaign e Adobe Target (Classic e Standard) in Adobe Experience Cloud consente di includere un’offerta da Adobe Target in una consegna e-mail Adobe Campaign.

Il principio di funzionamento è il seguente: quando un destinatario apre un’e-mail inviata tramite Adobe Campaign, una chiamata ad Adobe Target ti consente di visualizzare una versione dinamica del contenuto. Questa versione dinamica viene calcolata a seconda delle regole precedentemente specificate durante la creazione dell’e-mail.

Ulteriori informazioni sull&#39;integrazione di Adobe Campaign e Adobe Target con [questi quattro suggerimenti e trucchi](https://www.adobe.com/content/dam/www/us/en/marketing/campaign/pdfs/Adobe_Campaign_for_Target_Tips_and_Tricks.pdf).
>[!NOTE]
>
>L’integrazione supporta solo immagini statiche. Il resto del contenuto non può essere personalizzato.

Adobe Target può utilizzare diversi tipi di dati:

* Dati dal data mart di Adobe Campaign
* Segmenti collegati all’ID visitatore in Adobe Target, se i dati utilizzati non sono soggetti a limitazioni legali
* Dati Adobe Target: agente utente, indirizzo IP, dati di geolocalizzazione

>[!NOTE]
>
>Puoi anche trovare informazioni sull&#39;integrazione tra Adobe Campaign e Adobe Target nelle [pagine della guida di Adobe Target](https://experienceleague.adobe.com/docs/target/using/integrate/campaign-and-target.html).
