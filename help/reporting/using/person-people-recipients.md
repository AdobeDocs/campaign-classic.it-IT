---
product: campaign
title: Persona, persone e destinatari
description: Persona, persone e destinatari
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Reporting, Monitoring
exl-id: 69b810f3-aa8b-4ab5-95c1-831257d7fcb9
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 9%

---

# Persone e destinatari {#person-people-and-recipients}



Questo esempio ti aiuterà a comprendere la differenza tra una persona/una persona e un destinatario in Adobe Campaign. Invieremo una consegna a diverse persone per evidenziare la differenza tra persone e destinatari e specificare il metodo di calcolo per i seguenti indicatori:

* **[!UICONTROL Clicks]**
* **[!UICONTROL Distinct clicks for the population reached]**
* **[!UICONTROL Distinct opens for the population reached]**
* **[!UICONTROL Estimation of forwards]**
* **[!UICONTROL Raw reactivity]**

>[!NOTE]
>
>Questi indicatori vengono utilizzati nel report **[!UICONTROL Tracking indicators]**. Per ulteriori informazioni, consulta [Indicatori di tracciamento](../../reporting/using/delivery-reports.md#tracking-indicators).

A una consegna vengono aggiunti tre collegamenti. Viene inviato a 4 destinatari:

![](assets/s_ncs_user_indicators_example_1.png)

* **[!UICONTROL John Davis]** : questo destinatario non apre l&#39;e-mail (e quindi non fa clic su alcun collegamento).
* **[!UICONTROL Marie Stuart]** : apre l&#39;e-mail ma non fa clic su alcun collegamento.
* **[!UICONTROL Florian David]** : apre l&#39;e-mail e fa clic sui collegamenti 9 volte. Inoltre, inoltra l’e-mail a qualcuno che la apre e fa clic due volte.
* **[!UICONTROL Henry Macdonald]** : questo destinatario ha configurato il browser Internet per rifiutare i cookie. Apre l’e-mail e fa clic sui collegamenti 4 volte.

Vengono restituiti i seguenti registri di tracciamento:

![](assets/s_ncs_user_indicators_example_2.png)

Per avere un’idea più chiara del conteggio delle persone e dei destinatari, analizzeremo i registri di ciascun profilo.

## Passaggio 1: John {#step-1--john}

**[!UICONTROL John Davis]** non apre l&#39;e-mail (e quindi non fa clic su alcun collegamento).

![](assets/s_ncs_user_indicators_example_8.png)

Poiché John non ha aperto né fatto clic nell’e-mail, non viene visualizzato nei registri.

**Calcolo intermedio:**

|   | Destinatari che hanno fatto clic | Persone che hanno fatto clic | Destinatari che hanno aperto |
|---|---|---|---|
| John | - | - | - |
| Totale intermedio | 0 | 0 | 0 |

## Passaggio 2: Marie {#step-2--marie}

**[!UICONTROL Marie Stuart]** apre l&#39;e-mail ma non fa clic su alcun collegamento.

![](assets/s_ncs_user_indicators_example_7.png)

L&#39;apertura di Marie viene visualizzata nel seguente registro:

![](assets/s_ncs_user_indicators_example_4bis.png)

L&#39;apertura viene assegnata a un destinatario: Marie. Adobe Campaign aggiunge quindi un nuovo destinatario al conteggio.

**Calcolo intermedio:**

|   | Destinatari che hanno fatto clic | Persone che hanno fatto clic | Destinatari che hanno aperto |
|---|---|---|---|
| John | - | - | - |
| Marie | - | - | +1 |
| Totale intermedio | 0 | 0 | 1 |

## Passaggio 3: Florian {#step-3--florian}

**[!UICONTROL Florian David]** apre l&#39;e-mail e fa clic sui collegamenti 9 volte. Inoltre, inoltra l’e-mail a qualcuno che la apre e fa clic due volte.

![](assets/s_ncs_user_indicators_example_9.png)

Le azioni di Florian (un clic aperto e 9 clic) vengono visualizzate nei seguenti registri:

![](assets/s_ncs_user_indicators_example_3bis.png)

**Destinatari**: l&#39;apertura e i clic vengono assegnati allo stesso destinatario (Florian). Poiché questo destinatario è diverso dal precedente (Marie), Adobe Campaign aggiunge al conteggio un nuovo destinatario.

Persone: poiché il browser di questo destinatario accetta i cookie, lo stesso identificatore (UUID) viene assegnato a tutti i registri di clic: **`fe37a503 [...]`**. Adobe Campaign identifica correttamente questi clic come appartenenti alla stessa persona. Al conteggio viene aggiunta una nuova persona.

**Calcolo intermedio:**

|   | Destinatari che hanno fatto clic | Persone che hanno fatto clic | Destinatari che hanno aperto |
|---|---|---|---|
| John | - | - | - |
| Marie | - | - | +1 |
| Florian | +1 | +1 | +1 |
| Totale intermedio | 1 | 1 | 2 |

I seguenti registri coincidono con l’apertura e i due clic effettuati dalla persona a cui Florian ha inoltrato l’e-mail:

![](assets/s_ncs_user_indicators_example_6bis.png)

**Destinatari**: i relativi clic e messaggi aperti vengono assegnati al destinatario che ha inoltrato l&#39;e-mail (Florian). Poiché questo destinatario è già stato conteggiato, il conteggio dei destinatari rimane lo stesso.

![](assets/s_ncs_user_indicators_example_12.png)

**Persone**: per quanto riguarda i clic, lo stesso identificatore (UUID) è assegnato a tutti i registri: **`9ab648f9 [...]`**. Questo identificatore non è ancora stato conteggiato. Una nuova persona viene quindi aggiunta al conteggio.

![](assets/s_ncs_user_indicators_example_13.png)

**Calcolo intermedio:**

|   | Destinatari che hanno fatto clic | Persone che hanno fatto clic | Destinatari che hanno aperto |
|---|---|---|---|
| John | - | - | - |
| Marie | - | - | +1 |
| Florian | +1 | +1 | +1 |
| Persona sconosciuta | - | +1 | - |
| Totale intermedio | 1 | 2 | 2 |

## Passaggio 4: Henry {#step-4--henry}

**[!UICONTROL Henry Macdonald]** ha configurato il browser Internet per rifiutare i cookie. Apre l’e-mail e fa clic sui collegamenti 4 volte.

![](assets/s_ncs_user_indicators_example_10.png)

I clic aperti e i 4 clic eseguiti da Henry vengono visualizzati nei seguenti registri:

![](assets/s_ncs_user_indicators_example_5bis.png)

**Destinatari**: i clic e i messaggi aperti vengono assegnati allo stesso destinatario (Henry). Poiché questo destinatario non è ancora stato conteggiato, Adobe Campaign aggiunge un destinatario al conteggio.

**Persone**: poiché il browser di Henry non accetta i cookie, viene generato un nuovo identificatore (UUID) per ogni clic. Ciascuno dei 4 clic viene interpretato come proveniente da una persona diversa. Poiché questi identificatori non sono ancora stati conteggiati, vengono aggiunti al conteggio.

**Calcolo intermedio:**

|   | Destinatari che hanno fatto clic | Persone che hanno fatto clic | Destinatari che hanno aperto |
|---|---|---|---|
| John | - | - | - |
| Marie | - | - | +1 |
| Florian | +1 | +1 | +1 |
| Persona sconosciuta | - | +1 | - |
| Henry | +1 | +4 | +1 |
| Totale intermedio | 2 | 6 | 3 |

## Riepilogo {#summary}

A livello di consegna, si ottengono i seguenti risultati:

![](assets/s_ncs_user_indicators_example.png)

* **[!UICONTROL Clicks]** (destinatari che hanno fatto clic): 2
* **[!UICONTROL Distinct clicks for the population reached]** (persone che hanno fatto clic): 6
* **[!UICONTROL Distinct opens for the population reached]** (destinatari che hanno aperto): 3

La reattività grezza e la stima dei forward sono calcolate come segue:

![](assets/s_ncs_user_indicators_example11.png)

* **[!UICONTROL Estimation of forwards]** = **B - A** (quindi 6 - 2 = 4)
* **[!UICONTROL Raw reactivity]** = **A / C** (quindi 2 / 3 = 66,67%)

>[!NOTE]
>
>Nelle seguenti formule:
>
>* Un rappresenta l&#39;indicatore **[!UICONTROL Clicks]** (destinatari che hanno fatto clic).
>* B rappresenta l&#39;indicatore **[!UICONTROL Distinct clicks for the population reached]** (persone che hanno fatto clic).
>* C rappresenta l&#39;indicatore **[!UICONTROL Distinct opens for the population reached]** (destinatari che hanno aperto).
