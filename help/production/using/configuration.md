---
product: campaign
title: Configurazione aggiuntiva
description: Configurazione
feature: Monitoring, Configuration
badge-v7-prem: label="Solo on-premise/ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
exl-id: 80d388fd-873c-4a08-b8b6-697988f2a18c
TQID: https://experienceleague.adobe.com/gzcQquM9q71NIOt8mScgRpLtwffxvopslrrpLxxIang
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
subfeature_v2: id: efa38731-2723-4334-8d8b-a778af834835id: c03a11ff-bdf9-4e5b-b279-f468b4293464id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080bid: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 194
ht-degree: 11%

---

# Configurazione{#configuration}



## Modifica della porta di ascolto syslogd {#changing-the-syslogd-listening-port}

Per impostazione predefinita, la porta di ascolto **syslogd** è 666 (udp). Se necessario, puoi modificarla utilizzando una variabile di ambiente.

Una volta configurata, questa variabile viene presa in considerazione da tutti i moduli di Adobe Campaign.

### In Linux {#in-linux}

Modifica il file **customer.sh** e aggiungi la seguente riga:

```sql
export TRACE_ADDR=localhost:<listening port>
```

### In Windows {#in-windows}

È necessario creare la variabile di ambiente **TRACE_ADDR** con il valore **localhost**: **`<listening port="" />`**.

>[!IMPORTANT]
>
>È consigliabile eseguire alcuni test per verificare che la piattaforma funzioni dopo aver creato questa variabile di ambiente.

## Configurazione delle aree di protezione {#configuring-security-zones}

Ogni operatore deve essere collegato a una zona per accedere a un&#39;istanza e l&#39;IP dell&#39;operatore deve essere incluso negli indirizzi o nei set di indirizzi definiti nell&#39;area di sicurezza. La configurazione della zona tecnica viene eseguita nel file di configurazione del server Adobe Campaign. Il collegamento di un operatore a un&#39;area di sicurezza deve essere definito nella console (nodo **[!UICONTROL Administration > Access management > Operators]**).

>[!NOTE]
>
>Per ulteriori informazioni sulla configurazione delle aree di protezione, consulta [questa sezione](../../installation/using/security-zones.md).
