---
product: campaign
title: Nuove funzioni basate su GCM
description: Nuove funzioni basate su GCM
feature: Technote
exl-id: 154dee7a-a1e9-40a2-bfa5-3641382d0574
source-git-commit: b6d64f66d287dba79be5eddec48ee852c2c7740c
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 2%

---

# Funzioni basate su GCM {#new-functions}

Per migliorare la sicurezza, è stato reso obsoleto l’utilizzo dell’algoritmo AES (Advanced Encryption Standard) con modalità CBC (Cipher Block Chaining) per le operazioni di crittografia. Sono state introdotte nuove funzioni di crittografia. Queste funzioni utilizzano AES con modalità Galois/Counter (AES-GCM), fornendo un&#39;alternativa più sicura. Queste funzioni sono disponibili in JavaScript, JSP, API SOAP e schemi XML, consentendo ai clienti di passare da CBC a GCM per la crittografia e la decrittografia.

In questa documentazione sono elencate le nuove funzioni AES-GCM introdotte e le funzioni basate su CBC che verranno dichiarate obsolete.

Nuove funzioni:

* [Funzione API EncryptString](#encryptString-api-xtk)
* [Funzione API EncryptStringWithServerPassword](#EncryptStringWithServerPassword-api-xtk)
* [funzione javascript encryptString](#encryptString-javascript)

Funzioni legacy utilizzabili per GCM:

* [Funzione JavaScript DecryptString](#decryptString-javascript)
* [Funzione JavaScript DecryptPassword](#decryptPassword-javascript)

[Funzioni obsolete](#depracated-functions)

## Funzioni API

### EncryptString {#encryptString-api-xtk}

Crittografa la stringa di caratteri con la chiave dell’istanza utilizzando l’algoritmo AES con modalità GCM.

```
            String 
            encrypted = EncryptString (
            String       
            decrypted
            

      )
         
```

**Parametri**: testo decrittografato

**Valore/i restituito/i**: crittografato

**Schema**: xtk:session

**Statico**: Sì

## EncryptStringWithServerPassword {#EncryptStringWithServerPassword-api-xtk}

Crittografa la stringa di caratteri con la chiave del server utilizzando l’algoritmo AES con modalità GCM.


```
            String 
            encrypted = EncryptStringWithServerPassword (
            String       
            decrypted
            

      )
         
```

**Parametri**: decrittografati

**Valore/i restituito/i**: crittografato

**Schema**: xtk:session

**Statico**: Sì

## Funzioni JavaScript

### encryptString() {#encryptString-javascript}

Crittografa una stringa di caratteri con la chiave dell’istanza o di qualsiasi altra chiave.

```
            encryptString (str [, key
      ] [, useSalt ])
         
```

**Parametri**:

* str: stringa di caratteri da crittografare.
* chiave: la chiave di crittografia AES è codificata in base 64: 256 bit se la lunghezza della chiave è 32; 192 bit se la lunghezza della chiave è 24; 128 bit se la lunghezza della chiave è 16 o se non è specificata alcuna chiave.
* useSalt: utilizza un sale dei dati per crittografare. True per impostazione predefinita.

**Valore restituito**: restituisce la stringa di caratteri crittografati.

**Note**

La cifratura avviene secondo il seguente metodo:

* La stringa di caratteri Unicode viene trasformata in una stringa UTF-8.
* Alla fine viene aggiunto un carattere di spunta nel testo crittografato.
* Questa stringa viene crittografata utilizzando l’algoritmo AES in modalità Galois/Counter Mode (GCM) utilizzando salt con un vettore di inizializzazione di 12 byte e un tag di 16 byte. Se come parametro non viene fornita alcuna chiave, viene utilizzata la chiave di istanza.
* Il testo crittografato conterrà il tag e il vettore di inizializzazione.
* Il blocco crittografato viene quindi convertito in base 64.

La decrittografia viene eseguita utilizzando la funzione decryptString.

**Caratteristiche**

Disponibile in:

* Gestione dei contenuti
* Proprietà di consegna
* Messaggio di consegna
* Regola di tipologia
* Importazione
* JSSP
* Metodo SOAP
* WebApp
* Flusso di lavoro

### decryptString() {#decryptString-javascript}

Decritta una stringa di caratteri con la chiave dell’istanza o di qualsiasi altra chiave. Questa funzione legacy può essere utilizzata con GCM. È obsoleto per la decrittografia del testo crittografato crittografato utilizzando la modalità AES-CBC.

```
            decryptString (str [, key
      ] [, useSalt ])
         
```

**Parametri**:

* str: stringa di caratteri da decrittografare.
* chiave: la chiave di crittografia AES è codificata in base 64: 256 bit se la lunghezza della chiave è 32; 192 bit se la lunghezza della chiave è 24; 128 bit se la lunghezza della chiave è 16 o se non è specificata alcuna chiave.
* useSalt: utilizza un sale dei dati per decrittografare. True per impostazione predefinita.

**Valore restituito**: restituisce la stringa di caratteri decrittografata.

**Avviso**: le password archiviate nel database (opzioni/account esterni) non possono più essere decrittografate utilizzando questo metodo. Per questo, utilizza [decryptPassword](#decryptPassword-javascript).

### decryptPassword() {#decryptPassword-javascript}

Decritta una password archiviata in un account esterno. Questa funzione legacy può essere utilizzata con GCM. È obsoleto per la decrittografia del testo crittografato crittografato utilizzando la modalità AES-CBC.

```
            decryptPassword (str)
         
```

**Parametri**:

* str: stringa di caratteri da decrittografare.

**Valore restituito**: restituisce la password in formato testo normale.

**Note**

Questa funzione non può essere chiamata nei flussi di lavoro, nelle applicazioni web, nei rapporti o nelle consegne. Può essere chiamato nelle implementazioni di chiamate JSSP o SOAP. Esempio:

```
        function nms_extAccount_LogonToRemoteInstance(remoteInstanceUrl, login, encryptedPassword) {
        var cnx = null, sessionService = null;
        try
            {
                var cnx = new HttpSoapConnection(remoteInstanceUrl + '/nl/jsp/soaprouter.jsp', 'utf-8', 0);
                sessionService = new SoapService(cnx, 'xtk:session');
                sessionService.addMethod("Logon", "xtk:session#Logon",
                    ["token", "string", "login", "string", "password", "string", "parameters", "NLElement"],
                    ["sessionToken", "string", "sessionInfo", "NLElement", "securityToken", "string"]);
                return sessionService.Logon("", login, decryptPassword(encryptedPassword), <parameters/>);
            }
        catch( e ) {
        logError(e);
        }
        finally {
        if( sessionService ) sessionService.dispose();
        if( cnx ) cnx.dispose();
        }
        })
      
```

## Funzioni obsolete {#depracated-functions}

Le seguenti funzioni sono completamente obsolete:

* cryptString
* Crittografa
* CrittografaPasswordServer
