---
product: campaign
title: Rete, database e SSL/TLS
description: Ulteriori informazioni sulle best practice per la configurazione di reti, database e SSL/TLS
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 2a66dfaa-7fff-48de-bdd4-62f3ebfbab19
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 14%

---

# Rete, database e SSL/TLS {#network-database}



## Configurazione della rete

Una cosa molto importante da verificare durante la distribuzione di un tipo di architettura on-premise è la [configurazione di rete](../../installation/using/network-configuration.md). Verificare che il server Tomcat NON sia direttamente accessibile all&#39;esterno del server:

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

È inoltre possibile utilizzare un’ [dimensioni](https://github.com/nabla-c0d3/sslyze/releases) script python che esegue entrambe le operazioni.

```
python sslyze.py --sslv2 --sslv3 --tlsv1 --reneg --resum --certinfo=basic --hide_rejected_ciphers --sni=SNI myserver.com
```
