---
solution: Campaign Classic
product: campaign
title: Rete, database e SSL/TLS
description: Ulteriori informazioni sulle best practice per la configurazione di rete, database e SSL/TLS.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: 63b2e6b95812f1649e636580984a1f0dcc9c5c53
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 2%

---


# Rete, database e SSL/TLS {#network-database}

## Configurazione di rete

Una cosa molto importante da verificare quando si distribuisce un tipo di architettura on-premise è la [configurazione di rete](../../installation/using/network-configuration.md). Assicurati che il server Tomcat NON sia direttamente accessibile all&#39;esterno del server:

* Chiudi la porta Tomcat (8080) su IP esterni (deve funzionare su localhost)
* Non mappare la porta HTTP standard (80) su quella Tomcat (8080)

Quando è possibile, utilizza un canale sicuro: POP3S invece POP3 (o POP3 su TLS).

## Database

È necessario applicare le best practice relative alla sicurezza del motore di database.

## Configurazione SSL/TLS

Per controllare il certificato, puoi utilizzare openssl. Per controllare i caratteri attivi, puoi utilizzare nmap:

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

È inoltre possibile utilizzare uno script [ridimensiona](https://github.com/nabla-c0d3/sslyze/releases) python che esegue entrambe le operazioni.

```
python sslyze.py --sslv2 --sslv3 --tlsv1 --reneg --resum --certinfo=basic --hide_rejected_ciphers --sni=SNI myserver.com
```
