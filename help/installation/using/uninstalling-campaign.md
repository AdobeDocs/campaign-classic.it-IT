---
solution: Campaign Classic
product: campaign
title: Disinstallazione di Campaign
description: Scopri come disinstallare Campaign
audience: installation
content-type: reference
topic-tags: appendices
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '36'
ht-degree: 19%

---


# Disinstallazione di Campaign{#uninstalling-campaign}

>[!CAUTION]
>
>Queste procedure verranno disinstallate in modo permanente  Adobe Campaign. Tutti i dati andranno persi.

**RHEL:**

```
rpm -e nlserver6-v7
userdel -r neolane
groupdel neolane
rm -rf /user/local/neolane
```

**Debian:**

```
apt purge nlserver6-v7
userdel -r neolane
groupdel neolane
rm -rf /user/local/neolane
```

**Windows:**

Fare riferimento a questa [pagina](../../migration/using/migrating-in-windows-for-adobe-campaign-7.md#deleting-and-cleansing-adobe-campaign-previous-version). Non dimenticare di rimuovere la cartella di installazione di Campaign.
