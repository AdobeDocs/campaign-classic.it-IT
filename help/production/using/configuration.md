---
title: Configurazione
seo-title: Configurazione
description: Configurazione
seo-description: null
page-status-flag: never-activated
uuid: 4316d4b2-0964-4e25-9e4f-f2378f044c85
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: 12f13b8d-afc3-4b55-a31b-080d31f84fc9
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 2%

---


# Configurazione{#configuration}

## Modifica della porta di ascolto syslogd {#changing-the-syslogd-listening-port}

Per impostazione predefinita, la porta di ascolto **syslogd** è 666 (udp). Se necessario, potete modificarlo utilizzando una variabile di ambiente.

Una volta configurata, questa variabile viene presa in considerazione da tutti  moduli Adobe Campaign.

### In Linux {#in-linux}

Modificate il file **customer.sh** e aggiungete la seguente riga:

```
export TRACE_ADDR=localhost:<listening port>
```

### In Windows {#in-windows}

È necessario creare la variabile di ambiente **TRACE_ADDR.** con il valore **localhost** : **`<listening port="" />`**.

>[!CAUTION]
>
>È consigliabile eseguire alcuni test per verificare che la piattaforma funzioni correttamente dopo la creazione di questa variabile di ambiente.

## Configurazione delle aree di protezione {#configuring-security-zones}

Ogni operatore deve essere collegato a una zona per accedere a un&#39;istanza e l&#39;IP dell&#39;operatore deve essere incluso negli indirizzi o nei set di indirizzi definiti nella zona di sicurezza. La configurazione della zona tecnica viene eseguita nel file di configurazione del server Adobe Campaign . Il collegamento di un operatore a un&#39;area di protezione deve essere definito nella console ( **[!UICONTROL Administration > Access management > Operators]** nodo).

>[!NOTE]
>
>Per ulteriori informazioni sulla configurazione delle aree di protezione, consultare [questa sezione](../../installation/using/configuring-campaign-server.md#defining-security-zones).

