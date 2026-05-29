---
product: campaign
title: File temporanei
description: File temporanei
feature: Monitoring
badge-v7-prem: label="Solo on-premise/ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: e77800f5-c0ae-446d-8ff3-bc8a18c97dbd
TQID: https://experienceleague.adobe.com/eZnGm-WK-etrLLbJ-aeuSqakYAfPNBQd2q3JlEd4rE8
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
feature_v2: []
subfeature_v2: id: c03a11ff-bdf9-4e5b-b279-f468b4293464id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 164
ht-degree: 14%

---

# File temporanei{#temporary-files}



Messaggi di errore come i seguenti possono essere visualizzati (in particolare nei registri di consegna) quando il sistema viene messo in produzione:

*Impossibile rinominare il file &#39;/tmp/tmp0000.tmp&#39; in /usr/local/neolane/nl6/bin/..//var/XXX/mta/86510470.xml ;(errno=18, collegamento tra dispositivi non valido) (iRc=-52)*

La causa è la seguente:

Adobe Campaign genera file temporanei in **/tmp** e li rinomina per spostarli in **/usr/local/neolane/nl6/var**. Questo errore si verifica quando entrambe le cartelle (**/tmp** e **/usr/local/neolane/nl6/var**, che è in realtà un collegamento simbolico a **/var/nl6**) corrispondono a dispositivi diversi. Comando **df** utilizzato per la verifica.

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
