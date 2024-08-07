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
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 4%

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
