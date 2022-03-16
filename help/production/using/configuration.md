---
product: campaign
title: Configurazione aggiuntiva
description: Configurazione
exl-id: 80d388fd-873c-4a08-b8b6-697988f2a18c
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 1%

---

# Configurazione{#configuration}

![](../../assets/v7-only.svg)

## Modifica della porta di ascolto syslogd {#changing-the-syslogd-listening-port}

Per impostazione predefinita, la **syslogd** la porta di ascolto è 666 (udp). Se necessario, puoi modificarlo utilizzando una variabile di ambiente.

Una volta configurata, questa variabile viene presa in considerazione da tutti i moduli Adobe Campaign.

### In Linux {#in-linux}

Modifica le **customer.sh** e aggiungi la seguente riga:

```
export TRACE_ADDR=localhost:<listening port>
```

### In Windows {#in-windows}

È necessario creare il **TRACE_ADDR** variabile di ambiente con **localhost** valore: **`<listening port="" />`**.

>[!IMPORTANT]
>
>È consigliabile eseguire alcuni test per assicurarsi che la piattaforma funzioni dopo la creazione di questa variabile di ambiente.

## Configurazione delle aree di protezione {#configuring-security-zones}

Ogni operatore deve essere collegato a una zona per accedere a un’istanza e l’IP dell’operatore deve essere incluso negli indirizzi o nei set di indirizzi definiti nella zona di sicurezza. La configurazione della zona tecnica viene eseguita nel file di configurazione del server Adobe Campaign. Il collegamento di un operatore a un’area di sicurezza deve essere definito nella console ( **[!UICONTROL Administration > Access management > Operators]** node).

>[!NOTE]
>
>Per ulteriori informazioni sulla configurazione delle aree di protezione, consulta [questa sezione](../../installation/using/security-zones.md).
