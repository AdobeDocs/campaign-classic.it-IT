---
product: campaign
title: Migrazione del connettore SMS non supportata
description: Migrare il connettore SMS non supportato al connettore SMPP generico esteso
feature: SMS, Upgrade
hidefromtoc: true
exl-id: 60acf80c-8506-410b-ab2c-4f67a5677b43
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 1%

---

# Migrare il connettore SMS non supportato al connettore SMPP generico esteso{#unsupported-connector-migration}



A partire dalla versione 20.2, i connettori legacy sono diventati obsoleti. Questo documento ti aiuterà a migrare i connettori ancora in esecuzione sul vecchio sistema al connettore SMPP consigliato.

>[!CAUTION]
>
>Questa migrazione non è obbligatoria ma consigliata da Adobe e garantisce l’esecuzione sull’ultima versione supportata del software.

## Informazioni sui connettori SMS {#about-sms-connectors}

I seguenti connettori sono obsoleti a partire dalla versione 20.2:

* **[!UICONTROL Generic SMPP]** (SMPP versione 3.4 supporta la modalità binaria)
* **[!UICONTROL Sybase365]** (SAP SMS 365)
* **[!UICONTROL CLX Communications]**
* **[!UICONTROL Tele2]**
* **[!UICONTROL O2]**
* **[!UICONTROL iOS]**

Le funzionalità obsolete sono ancora disponibili e supportate, ma non verranno ulteriormente migliorate. È consigliabile utilizzare **[!UICONTROL Extended generic SMPP]** connettore.

Per ulteriori informazioni sulle funzioni obsolete e rimosse, consulta questa [pagina](../../rn/using/deprecated-features.md).

I vecchi connettori SMS utilizzano il connettore Java SMS che sovraccarica il processo web. Migrazione al nuovo **[!UICONTROL Extended Generic SMPP]** Il connettore sposterà questo carico nell’MTA che potrà supportarlo.

## Migrazione al connettore SMPP generico esteso {#migrating-extended-generic-smpp}

>[!CAUTION]
>
>Anche se è possibile trasporre i parametri, la configurazione **[!UICONTROL Extended Generic SMPP]** il connettore richiede di parlare con il provider che ti fornirà le informazioni necessarie per compilare il resto dei parametri. Per ulteriori informazioni, consulta questa [pagina](sms-protocol.md).

Innanzitutto, devi creare un nuovo **[!UICONTROL Extended Generic SMPP]** account esterno e potresti essere in grado di recepire alcuni parametri. Puoi trovare i passaggi dettagliati in questo [pagina](sms-set-up.md#creating-an-smpp-external-account).

Ora devi compilare i parametri della **[!UICONTROL Mobile]** della nuova scheda **[!UICONTROL Extended Generic SMPP]** account esterno a seconda del connettore precedente.

### Dal connettore generico {#from-generic-connector}

Quando si sceglie **[!UICONTROL Generic]** connettore, è necessario disporre di un connettore JavaScript personalizzato che si adatterà a ogni situazione.

Se sai che il connettore sta già utilizzando il protocollo SMPP, puoi migrare al **[!UICONTROL Extended Generic SMPP]** connettore. In caso contrario, verifica con il provider se supporta il protocollo SMPP e configura un nuovo connettore con l’aiuto di un consulente.

Dal tuo **[!UICONTROL Generic]** connettore, è possibile trasporre nel nuovo **[!UICONTROL Extended SMPP]** account:

![](assets/smpp_generic.png)

In **[!UICONTROL Connection Settings]** scheda:

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**

### Dal connettore SMPP generico {#from-generic-smpp-connector}

Dal tuo **[!UICONTROL Generic SMPP]** connettore, è possibile trasporre nel nuovo **[!UICONTROL Extended SMPP]** account:

![](assets/smpp_generic_2.png)

In **[!UICONTROL Connection Settings]** scheda:

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

In **[!UICONTROL SMPP Channel Settings]** scheda:

* **[!UICONTROL Source number]**
* **[!UICONTROL Source NPI]**
* **[!UICONTROL Destination NPI]**
* **[!UICONTROL Source TON]**
* **[!UICONTROL Destination TON]**

In **[!UICONTROL Mapping of Encoding]** scheda:

* **[!UICONTROL Outbound SMS coding]**

In **[!UICONTROL SMSC specificities]** scheda:

* **[!UICONTROL Coding when sending]** corrisponde a **[!UICONTROL ID Format in MT acknowledgement]**
* **[!UICONTROL Coding when receiving]** corrisponde a **[!UICONTROL ID Format in the SR]**

### Dal connettore Sybase365 {#from-sybase}

Dal tuo **[!UICONTROL Sybase365]** connettore, è possibile trasporre nel nuovo **[!UICONTROL Extended SMPP]** account:

![](assets/smpp_3.png)

In **[!UICONTROL Connection Settings]** scheda:

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

### Da connettore CLX {#from-clx}

Dal tuo **[!UICONTROL CLX]** connettore, è possibile trasporre nel nuovo **[!UICONTROL Extended SMPP]** account:

![](assets/smpp_4.png)

In **[!UICONTROL Connection Settings]** scheda:

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

In **[!UICONTROL SMPP Channel Settings]** scheda:

* **[!UICONTROL Source number]**

In **[!UICONTROL SMSC specificities]** scheda:

* **[!UICONTROL Coding when sending]** corrisponde a **[!UICONTROL ID Format in MT acknowledgement]**
* **[!UICONTROL Coding when receiving]** corrisponde a **[!UICONTROL ID Format in the SR]**

### Dal connettore Tele2 {#from-tele2}

Dal tuo **[!UICONTROL Tele2]** connettore, è possibile trasporre nel nuovo **[!UICONTROL Extended SMPP]** account:

![](assets/smpp_6.png)

In **[!UICONTROL Connection Settings]** scheda:

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

In **[!UICONTROL SMPP Channel Settings]** scheda:

* **[!UICONTROL Source number]**
* **[!UICONTROL Source NPI]**
* **[!UICONTROL Destination NPI]**
* **[!UICONTROL Source TON]**

In **[!UICONTROL Mapping of Encoding]** scheda:

* **[!UICONTROL Outbound SMS coding]**

### Dal connettore O2 {#from-O2}

Dal tuo **[!UICONTROL O2]** connettore, è possibile trasporre nel nuovo **[!UICONTROL Extended SMPP]** account:

![](assets/smpp_5.png)

In **[!UICONTROL Connection Settings]** scheda:

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

In **[!UICONTROL SMPP Channel Settings]** scheda:

* **[!UICONTROL Source number]**
* **[!UICONTROL Source NPI]**
* **[!UICONTROL Destination NPI]**
* **[!UICONTROL Source TON]**
* **[!UICONTROL Destination TON]**
