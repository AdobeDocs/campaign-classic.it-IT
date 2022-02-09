---
product: campaign
title: Persona, persone e destinatari
description: Persona, persone e destinatari
exl-id: 69b810f3-aa8b-4ab5-95c1-831257d7fcb9
source-git-commit: 81716a30a57d3ed8542b329d5fb9b0443fd4bf31
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Persone e destinatari {#person-people-and-recipients}

![](../../assets/common.svg)

Questo esempio ti aiuterà a comprendere la differenza tra una persona/a e un destinatario in Adobe Campaign. Invieremo una consegna a più persone per evidenziare la differenza tra persone e destinatari, specificando al tempo stesso il metodo di calcolo per i seguenti indicatori:

* **[!UICONTROL Clicks]**
* **[!UICONTROL Distinct clicks for the population reached]**
* **[!UICONTROL Distinct opens for the population reached]**
* **[!UICONTROL Estimation of forwards]**
* **[!UICONTROL Raw reactivity]**

>[!NOTE]
>
>Questi indicatori sono utilizzati nella **[!UICONTROL Tracking indicators]** rapporto. Per ulteriori informazioni, consulta [Indicatori di tracciamento](../../reporting/using/delivery-reports.md#tracking-indicators).

A una consegna vengono aggiunti tre collegamenti. Viene inviato a 4 destinatari:

![](assets/s_ncs_user_indicators_example_1.png)

* **[!UICONTROL John Davis]** : il destinatario non apre l’e-mail (e quindi non fa clic su alcun collegamento).
* **[!UICONTROL Marie Stuart]** : apre l’e-mail ma non fa clic su alcun collegamento.
* **[!UICONTROL Florian David]** : apre l’e-mail e fa clic sui collegamenti 9 volte. Inoltra anche l’e-mail a qualcuno che l’apre e fa clic due volte.
* **[!UICONTROL Henry Macdonald]** : il destinatario ha configurato il proprio browser Internet per rifiutare i cookie. Apre l&#39;e-mail e fa clic sui collegamenti 4 volte.

Vengono restituiti i seguenti registri di tracciamento:

![](assets/s_ncs_user_indicators_example_2.png)

Per avere un’idea più chiara del conteggio delle persone e dei destinatari, analizzeremo i registri di ciascun profilo.

## Passaggio 1: John {#step-1--john}

**[!UICONTROL John Davis]** non apre l’e-mail (e quindi non fa clic su alcun collegamento).

![](assets/s_ncs_user_indicators_example_8.png)

Poiché John non ha aperto né cliccato nell&#39;e-mail, non appare nei log.

**Calcolo intermedio:**

|  | Destinatari che hanno fatto clic su | Persone che hanno fatto clic su | Destinatari che hanno aperto |
|---|---|---|---|
| John | - | - | - |
| Totale intermedio | 0 | 0 | 0 |

## Passaggio 2: Marie {#step-2--marie}

**[!UICONTROL Marie Stuart]** apre l’e-mail ma non fa clic su alcun collegamento.

![](assets/s_ncs_user_indicators_example_7.png)

L&#39;apertura di Marie viene visualizzata nel seguente registro:

![](assets/s_ncs_user_indicators_example_4bis.png)

L’apertura viene assegnata a un destinatario: Marie. Pertanto, Adobe Campaign aggiunge un nuovo destinatario al conteggio.

**Calcolo intermedio:**

|  | Destinatari che hanno fatto clic su | Persone che hanno fatto clic su | Destinatari che hanno aperto |
|---|---|---|---|
| John | - | - | - |
| Marie | - | - | +1 |
| Totale intermedio | 0 | 0 | 1 |

## Passaggio 3: Florian {#step-3--florian}

**[!UICONTROL Florian David]** apre l’e-mail e fa clic sui collegamenti 9 volte. Inoltra anche l’e-mail a qualcuno che l’apre e fa clic due volte.

![](assets/s_ncs_user_indicators_example_9.png)

Le azioni di Florian (uno aperto e 9 clic) vengono visualizzate nei seguenti registri:

![](assets/s_ncs_user_indicators_example_3bis.png)

**Destinatari**: gli open e i clic vengono assegnati allo stesso destinatario (Florian). Poiché questo destinatario è diverso da quello precedente (Marie), Adobe Campaign aggiunge al conteggio un nuovo destinatario.

Persone: Poiché il browser di questo destinatario accetta i cookie, lo stesso identificatore (UUID) viene assegnato a tutti i registri di clic: **`fe37a503 [...]`**. Adobe Campaign identifica correttamente questi clic come appartenenti alla stessa persona. Al conteggio viene aggiunta una nuova persona.

**Calcolo intermedio:**

|  | Destinatari che hanno fatto clic su | Persone che hanno fatto clic su | Destinatari che hanno aperto |
|---|---|---|---|
| John | - | - | - |
| Marie | - | - | +1 |
| Florian | +1 | +1 | +1 |
| Totale intermedio | 1 | 1 | 2 |

I registri seguenti coincidono con i due clic aperti effettuati dalla persona a cui Florian ha inoltrato l’e-mail a:

![](assets/s_ncs_user_indicators_example_6bis.png)

**Destinatari**: i relativi clic e aperti vengono assegnati al destinatario che ha inoltrato l’e-mail (Florian). Poiché questo destinatario è già stato conteggiato, il conteggio dei destinatari rimane lo stesso.

![](assets/s_ncs_user_indicators_example_12.png)

**Persone**: per quanto riguarda i clic, lo stesso identificatore (UUID) viene assegnato a tutti i log: **`9ab648f9 [...]`**. Questo identificatore non è ancora stato conteggiato. Viene quindi aggiunta una nuova persona al conteggio.

![](assets/s_ncs_user_indicators_example_13.png)

**Calcolo intermedio:**

|  | Destinatari che hanno fatto clic su | Persone che hanno fatto clic su | Destinatari che hanno aperto |
|---|---|---|---|
| John | - | - | - |
| Marie | - | - | +1 |
| Florian | +1 | +1 | +1 |
| Persona sconosciuta | - | +1 | - |
| Totale intermedio | 1 | 2 | 2 |

## Passaggio 4: Henry {#step-4--henry}

**[!UICONTROL Henry Macdonald]** ha configurato il browser Internet per rifiutare i cookie. Apre l&#39;e-mail e fa clic sui collegamenti 4 volte.

![](assets/s_ncs_user_indicators_example_10.png)

I 4 clic aperti e quelli effettuati da Henry compaiono nei seguenti registri:

![](assets/s_ncs_user_indicators_example_5bis.png)

**Destinatari**: i clic aperti e vengono assegnati allo stesso destinatario (Henry). Poiché questo destinatario non è ancora stato conteggiato, Adobe Campaign aggiunge un destinatario al conteggio.

**Persone**: Poiché il browser di Henry non accetta i cookie, per ogni clic viene generato un nuovo identificatore (UUID). Ognuno dei 4 clic viene interpretato come proveniente da una persona diversa. Poiché questi identificatori non sono ancora stati conteggiati, vengono aggiunti al conteggio.

**Calcolo intermedio:**

|  | Destinatari che hanno fatto clic su | Persone che hanno fatto clic su | Destinatari che hanno aperto |
|---|---|---|---|
| John | - | - | - |
| Marie | - | - | +1 |
| Florian | +1 | +1 | +1 |
| Persona sconosciuta | - | +1 | - |
| Henry | +1 | +4 | +1 |
| Totale intermedio | 2 | 6 | 3 |

## Riepilogo {#summary}

A livello di consegna, otteniamo i seguenti risultati:

![](assets/s_ncs_user_indicators_example.png)

* **[!UICONTROL Clicks]** (destinatari che hanno fatto clic su): 2
* **[!UICONTROL Distinct clicks for the population reached]** (persone che hanno fatto clic su): 6
* **[!UICONTROL Distinct opens for the population reached]** (destinatari che hanno aperto): 3

La reattività grezza e la stima dei contratti a termine sono calcolate come segue:

![](assets/s_ncs_user_indicators_example11.png)

* **[!UICONTROL Estimation of forwards]** = **B - A** (quindi 6 - 2 = 4)
* **[!UICONTROL Raw reactivity]** = **A/C** (quindi 2 / 3 = 66,67%)

>[!NOTE]
>
>Nelle seguenti formule:
>
>* A rappresenta **[!UICONTROL Clicks]** (destinatari che hanno fatto clic su).
>* B rappresenta **[!UICONTROL Distinct clicks for the population reached]** (persone che hanno fatto clic su).
>* C rappresenta **[!UICONTROL Distinct opens for the population reached]** (destinatari che hanno aperto).

