---
product: campaign
title: Disinstallazione di Campaign
description: Scopri come disinstallare Campaign
audience: installation
content-type: reference
topic-tags: appendices
exl-id: e2b026ba-aaf3-443d-8c36-c908288a14fd
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '36'
ht-degree: 19%

---

# Disinstallazione di Campaign{#uninstalling-campaign}

>[!CAUTION]
>
>Queste procedure disinstalleranno definitivamente Adobe Campaign. Tutti i dati andranno persi.

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

Fai riferimento a questa [pagina](../../migration/using/migrating-in-windows-for-adobe-campaign-7.md#deleting-and-cleansing-adobe-campaign-previous-version). Non dimenticare di rimuovere la cartella di installazione di Campaign.
