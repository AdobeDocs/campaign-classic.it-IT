---
product: campaign
title: File temporanei
description: File temporanei
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: e77800f5-c0ae-446d-8ff3-bc8a18c97dbd
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 4%

---

# File temporanei{#temporary-files}

![](../../assets/v7-only.svg)

Possono essere visualizzati messaggi di errore come i seguenti (in particolare nei registri di consegna) quando il sistema viene messo in produzione:

*Impossibile rinominare il file &quot;/tmp/tmp0000.tmp&quot; in /usr/local/neolane/nl6/bin/..//var/XXX/mta/86510470.xml ;(errno=18, collegamento cross-device non valido) (iRc=-52)*

La causa è la seguente:

Adobe Campaign genera file temporanei sotto **/tmp**, quindi li rinomina per spostarli in **/usr/local/neolane/nl6/var**. Questo errore si verifica quando entrambe le cartelle (**/tmp** e **/usr/local/neolane/nl6/var**, che è in realtà un collegamento simbolico a **/var/nl6**) corrispondono a diversi dispositivi. Il comando **df** viene utilizzato per la verifica.

Per risolvere questo problema, i file temporanei devono essere generati nello stesso dispositivo della destinazione.

Ad esempio, eseguire quanto segue:

```
$ cd ~/nl6/var
$ mkdir tmp
$ vi ~/nl6/customer.sh
```

Quindi aggiungi:

```
export TMPDIR=/usr/local/neolane/nl6/var/tmp 
```
