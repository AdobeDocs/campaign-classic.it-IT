---
product: campaign
title: Utilizzare Adobe Campaign e Adobe Target
description: Scopri come integrare Adobe Campaign con Adobe Target
feature: Target Integration
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: 2e29d090-b87b-4cff-a703-58e1da082f04
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---

# Utilizzare Campaign e Target{#integrating-with-adobe-target}



Utilizza Adobe Campaign con Adobe Target per ottimizzare il contenuto delle e-mail.

Per ottimizzare il contenuto delle e-mail, puoi creare un’offerta di reindirizzamento in Adobe Target, quindi utilizzare Adobe Campaign per gestire le offerte e-mail. Ad esempio, puoi visualizzare offerte diverse per destinatari di sesso maschile e femminile.

L’integrazione avviene all’apertura dell’e-mail. Quando il cliente apre l’e-mail, viene effettuata una chiamata a Target e viene visualizzata una versione dinamica del contenuto. Il contenuto è costituito da un’immagine statica supportata da tutti i browser. Target tiene traccia della reazione all’offerta a livello di pubblico o di sessione e i dati sono disponibili nei rapporti di Target. [Ulteriori informazioni nella documentazione di Adobe Target](https://experienceleague.adobe.com/docs/target/using/integrate/campaign-and-target.html).


>[!NOTE]
>
>L’integrazione supporta solo immagini statiche. Impossibile personalizzare il resto del contenuto.

Adobe Target può utilizzare diversi tipi di dati:

* Dati dal data mart di Adobe Campaign
* Segmenti collegati all’ID visitatore in Adobe Target, se i dati utilizzati non sono soggetti a limitazioni legali
* Dati Adobe Target: agente utente, indirizzo IP, dati di geolocalizzazione
