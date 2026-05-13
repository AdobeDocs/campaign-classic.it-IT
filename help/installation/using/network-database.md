---
product: campaign
title: Rete, database e SSL/TLS
description: Ulteriori informazioni sulle best practice per la configurazione di reti, database e SSL/TLS
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 2a66dfaa-7fff-48de-bdd4-62f3ebfbab19
TQID: https://experienceleague.adobe.com/PLGVcm4QYeU0A1uEhlDEfweZ275xpxtxo91r4aidr1I
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 138
ht-degree: 9%

---

# Rete, database e SSL/TLS {#network-database}

## Configurazione della rete

Una cosa molto importante da controllare durante la distribuzione di un tipo di architettura on-premise è la [configurazione di rete](../../installation/using/network-configuration.md). Verificare che il server Tomcat NON sia direttamente accessibile all&#39;esterno del server:

* Chiudi la porta Tomcat (8080) sugli IP esterni (deve funzionare su localhost)
* Non mappare la porta HTTP standard (80) su Tomcat 1 (8080)

Quando è possibile, utilizza un canale sicuro: POP3S invece di POP3 (o POP3 su TLS).

## Database

È necessario applicare le procedure consigliate per la protezione del motore di database.

## Configurazione SSL/TLS

Per verificare il certificato, puoi utilizzare openssl. Per controllare le crittografie attive, puoi utilizzare nmap:

```
#!/bin/sh
#
# usage: testSSL.sh remote.host.name [port]
#
REMHOST=$1
REMPORT=${2:-443}
 
echo |\
openssl s_client -connect ${REMHOST}:${REMPORT} -servername ${REMHOST} 2>&1 |\
sed -ne '/-BEGIN CERTIFICATE-/,/-END CERTIFICATE-/p' |\
openssl x509 -noout -subject -dates
   
nmap --script ssl-enum-ciphers -p ${REMPORT} ${REMHOST}
```

È inoltre possibile utilizzare uno script python [sslyze](https://github.com/nabla-c0d3/sslyze/releases) che esegue entrambe le operazioni.

```
python sslyze.py --sslv2 --sslv3 --tlsv1 --reneg --resum --certinfo=basic --hide_rejected_ciphers --sni=SNI myserver.com
```
