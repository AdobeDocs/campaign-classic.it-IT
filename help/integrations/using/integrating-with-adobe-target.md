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
TQID: https://experienceleague.adobe.com/f58vs0ePAH-7bcfJ8u1GKLzcz0-fHnrwFyOVUWOFW-o
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2:
  - id: b1fd1501-3105-4d6b-b4d4-9af53126df75
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 209
ht-degree: 0%

---

# Utilizzare Campaign e Target{#integrating-with-adobe-target}



Utilizza Adobe Campaign con Adobe Target per ottimizzare il contenuto delle e-mail.

Per ottimizzare il contenuto delle e-mail, puoi creare un’offerta di reindirizzamento in Adobe Target, quindi utilizzare Adobe Campaign per gestire le offerte e-mail. Ad esempio, puoi visualizzare offerte diverse per destinatari di sesso maschile e femminile.

L’integrazione avviene all’apertura dell’e-mail. Quando il cliente apre l’e-mail, viene effettuata una chiamata a Target e viene visualizzata una versione dinamica del contenuto. Il contenuto è costituito da un’immagine statica supportata da tutti i browser. Target tiene traccia della reazione all’offerta a livello di pubblico o di sessione e i dati sono disponibili nei rapporti di Target. [Ulteriori informazioni nella documentazione di Adobe Target](https://experienceleague.adobe.com/docs/target/using/integrate/campaign-and-target.html?lang=it).


>[!NOTE]
>
>L’integrazione supporta solo immagini statiche. Impossibile personalizzare il resto del contenuto.

Adobe Target può utilizzare diversi tipi di dati:

* Dati dal data mart di Adobe Campaign
* Segmenti collegati all’ID visitatore in Adobe Target, se i dati utilizzati non sono soggetti a limitazioni legali
* Dati Adobe Target: agente utente, indirizzo IP, dati di geolocalizzazione
