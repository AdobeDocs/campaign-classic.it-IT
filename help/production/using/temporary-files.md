---
title: File temporanei
seo-title: File temporanei
description: File temporanei
seo-description: null
page-status-flag: never-activated
uuid: ae7ec619-e93f-41fb-ba7c-fcbcf4cba84f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: f18237b0-ef54-46a6-9c14-34b038f9de18
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 6%

---


# File temporanei{#temporary-files}

Se compaiono messaggi di errore come i seguenti (in particolare nei registri di consegna) quando il sistema viene messo in produzione:

**Impossibile rinominare il file &quot;/tmp/tmp0000.tmp&quot; in /usr/local/neolane/nl6/bin/..//var/XXX/mta/86510470.xml ;(errno=18, collegamento cross-device non valido) (iRc=-52)**

La causa è la seguente:

 Adobe Campaign genera file temporanei sotto **/tmp**, quindi li rinomina per spostarli in **/usr/local/neolane/nl6/var**. Questo errore si verifica quando entrambe le cartelle (**/tmp** e **/usr/local/neolane/nl6/var**, che è in realtà un collegamento simbolico a **/var/nl6**) corrispondono a diversi dispositivi. Il comando **df** viene utilizzato per la verifica.

Per risolvere il problema, i file temporanei devono essere generati nello stesso dispositivo della destinazione. Ad esempio, eseguendo:

```
$ cd ~/nl6/var
$ mkdir tmp
$ vi ~/nl6/customer.sh
```

e quindi aggiungere:

```
export TMPDIR=/usr/local/neolane/nl6/var/tmp 
```

