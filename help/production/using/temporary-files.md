---
product: campaign
title: File temporanei
description: File temporanei
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: e77800f5-c0ae-446d-8ff3-bc8a18c97dbd
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 4%

---

# File temporanei{#temporary-files}



Messaggi di errore come i seguenti possono essere visualizzati (in particolare nei registri di consegna) quando il sistema viene messo in produzione:

*Impossibile rinominare il file /tmp/tmp0000.tmp in /usr/local/neolane/nl6/bin/..//var/XXX/mta/86510470.xml ;(errno=18, collegamento tra dispositivi non valido) (iRc=-52)*

La causa è la seguente:

Adobe Campaign genera file temporanei in **/tmp**, quindi li rinomina per spostarli in **/usr/local/neolane/nl6/var**. Questo errore si verifica quando entrambe le cartelle (**/tmp** e **/usr/local/neolane/nl6/var**, che è in realtà un collegamento simbolico a **/var/nl6**) corrispondono a dispositivi diversi. Il **df** per la verifica.

Per risolvere il problema, i file temporanei devono essere generati nello stesso dispositivo della destinazione.

Ad esempio, esegui quanto segue:

```
$ cd ~/nl6/var
$ mkdir tmp
$ vi ~/nl6/customer.sh
```

Quindi aggiungi:

```
export TMPDIR=/usr/local/neolane/nl6/var/tmp 
```
