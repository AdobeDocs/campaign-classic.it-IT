---
solution: Campaign Classic
product: campaign
title: Configurazione
description: Configurazione
audience: production
content-type: reference
topic-tags: production-procedures
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 1%

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

>[!IMPORTANT]
>
>È consigliabile eseguire alcuni test per verificare che la piattaforma funzioni correttamente dopo la creazione di questa variabile di ambiente.

## Configurazione delle aree di protezione {#configuring-security-zones}

Ogni operatore deve essere collegato a una zona per accedere a un&#39;istanza e l&#39;IP dell&#39;operatore deve essere incluso negli indirizzi o nei set di indirizzi definiti nella zona di sicurezza. La configurazione della zona tecnica viene eseguita nel file di configurazione del server Adobe Campaign . Il collegamento di un operatore a un&#39;area di protezione deve essere definito nella console ( **[!UICONTROL Administration > Access management > Operators]** nodo).

>[!NOTE]
>
>Per ulteriori informazioni sulla configurazione delle aree di protezione, consultare [questa sezione](../../installation/using/configuring-campaign-server.md#defining-security-zones).
