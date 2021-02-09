---
solution: Campaign Classic
product: campaign
title: File temporanei
description: File temporanei
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 1fdee02e98ce66ec184d8587d0838557f027cf75
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 4%

---


# File temporanei{#temporary-files}

I messaggi di errore come i seguenti potrebbero essere visualizzati (in particolare nei registri di consegna) quando il sistema viene messo in produzione:

*Impossibile rinominare il file &quot;/tmp/tmp0000.tmp&quot; in /usr/local/neolane/nl6/bin/..//var/XXX/mta/86510470.xml ;(errno=18, collegamento cross-device non valido) (iRc=-52)*

La causa è la seguente:

 Adobe Campaign genera file temporanei in **/tmp**, quindi li rinomina per spostarli in **/usr/local/neolane/nl6/var**. Questo errore si verifica quando entrambe le cartelle (**/tmp** e **/usr/local/neolane/nl6/var**, che in realtà è un collegamento simbolico a **/var/nl6**) corrispondono a diversi dispositivi. Per la verifica viene utilizzato il comando **df**.

Per risolvere il problema, i file temporanei devono essere generati nello stesso dispositivo della destinazione.

Ad esempio, eseguire quanto segue:

```
$ cd ~/nl6/var
$ mkdir tmp
$ vi ~/nl6/customer.sh
```

Quindi aggiungete:

```
export TMPDIR=/usr/local/neolane/nl6/var/tmp 
```
