---
product: campaign
title: Disinstallazione di Campaign
description: Scopri come disinstallare Campaign
feature: Installation
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
audience: installation
content-type: reference
topic-tags: appendices
exl-id: e2b026ba-aaf3-443d-8c36-c908288a14fd
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '43'
ht-degree: 18%

---

# Disinstallazione di Campaign{#uninstalling-campaign}



>[!CAUTION]
>
>Queste procedure disinstalleranno definitivamente Adobe Campaign. Tutti i dati andranno persi.

**RHEL**

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

Fai riferimento a questo [pagina](../../migration/using/migrating-in-windows-for-adobe-campaign-7.md#deleting-and-cleansing-adobe-campaign-previous-version). Non dimenticare di rimuovere la cartella di installazione di Campaign.
