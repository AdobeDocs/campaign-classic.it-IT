---
product: campaign
title: Integrazione con Adobe Target
description: Integrazione con Adobe Target
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: 2e29d090-b87b-4cff-a703-58e1da082f04
source-git-commit: b6e24c63ece12f25b7dafe3fede9e38b3aab2427
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---

# Integrazione con Adobe Target{#integrating-with-adobe-target}

![](../../assets/common.svg)

Utilizza Adobe Campaign con Adobe Target per ottimizzare il contenuto delle e-mail.

Per ottimizzare il contenuto delle e-mail, puoi creare un’offerta di reindirizzamento in Adobe Target, quindi utilizzare Adobe Campaign per gestire le offerte e-mail. Ad esempio, puoi visualizzare offerte diverse per i destinatari di sesso maschile e femminile.

L’integrazione avviene all’apertura dell’e-mail. Quando il cliente apre l’e-mail, viene effettuata una chiamata a Target e viene visualizzata una versione dinamica del contenuto. Il contenuto è costituito da un’immagine statica supportata da tutti i browser. Target tiene traccia della reazione all’offerta a livello di pubblico o di sessione e tali dati sono disponibili nei rapporti di Target. [Ulteriori informazioni nella documentazione di Adobe Target](https://experienceleague.adobe.com/docs/target/using/integrate/campaign-and-target.html).


>[!NOTE]
>
>L’integrazione supporta solo immagini statiche. Il resto del contenuto non può essere personalizzato.

Adobe Target può utilizzare diversi tipi di dati:

* Dati dal data mart di Adobe Campaign
* Segmenti collegati all’ID visitatore in Adobe Target, se i dati utilizzati non sono soggetti a limitazioni legali
* Dati Adobe Target: agente utente, indirizzo IP, dati di geolocalizzazione
