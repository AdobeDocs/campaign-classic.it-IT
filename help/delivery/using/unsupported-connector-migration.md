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

* **[!UICONTROL Generic SMPP]** (SMPP versione 3.4 che supporta la modalità binaria)
* **[!UICONTROL Sybase365]** (SAP SMS 365)
* **[!UICONTROL CLX Communications]**
* **[!UICONTROL Tele2]**
* **[!UICONTROL O2]**
* **[!UICONTROL iOS]**

Le funzionalità obsolete sono ancora disponibili e supportate, ma non verranno ulteriormente migliorate. È consigliabile utilizzare il connettore **[!UICONTROL Extended generic SMPP]**.

Per ulteriori informazioni sulle funzionalità obsolete e rimosse, consulta questa [pagina](../../rn/using/deprecated-features.md).

I vecchi connettori SMS utilizzano il connettore Java SMS che sovraccarica il processo web. La migrazione al nuovo connettore **[!UICONTROL Extended Generic SMPP]** sposterà questo carico nell&#39;MTA che potrà supportarlo.

## Migrazione al connettore SMPP generico esteso {#migrating-extended-generic-smpp}

>[!CAUTION]
>
>Anche se è possibile trasporre i parametri, la configurazione del connettore **[!UICONTROL Extended Generic SMPP]** richiede di parlare con il provider che fornirà le informazioni necessarie per compilare il resto dei parametri. Per ulteriori informazioni, consulta questa [pagina](sms-protocol.md).

Innanzitutto, sarà necessario creare un nuovo account esterno **[!UICONTROL Extended Generic SMPP]** e quindi potrebbe essere possibile trasporre alcuni parametri. Puoi trovare i passaggi dettagliati in questa [pagina](sms-set-up.md#creating-an-smpp-external-account).

È ora necessario compilare i parametri dalla scheda **[!UICONTROL Mobile]** dell&#39;account esterno **[!UICONTROL Extended Generic SMPP]** appena creato a seconda del connettore precedente.

### Dal connettore generico {#from-generic-connector}

Quando si sceglie il connettore **[!UICONTROL Generic]**, è necessario disporre di un connettore JavaScript personalizzato che si adatterà a ogni situazione.

Se si è certi che il connettore sta già utilizzando il protocollo SMPP, è possibile eseguire la migrazione al connettore **[!UICONTROL Extended Generic SMPP]**. In caso contrario, verifica con il provider se supporta il protocollo SMPP e configura un nuovo connettore con l’aiuto di un consulente.

Dal connettore **[!UICONTROL Generic]**, puoi trasporre nel tuo account **[!UICONTROL Extended SMPP]** appena creato:

![](assets/smpp_generic.png)

Nella scheda **[!UICONTROL Connection Settings]**:

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**

### Dal connettore SMPP generico {#from-generic-smpp-connector}

Dal connettore **[!UICONTROL Generic SMPP]**, puoi trasporre nel tuo account **[!UICONTROL Extended SMPP]** appena creato:

![](assets/smpp_generic_2.png)

Nella scheda **[!UICONTROL Connection Settings]**:

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

Nella scheda **[!UICONTROL SMPP Channel Settings]**:

* **[!UICONTROL Source number]**
* **[!UICONTROL Source NPI]**
* **[!UICONTROL Destination NPI]**
* **[!UICONTROL Source TON]**
* **[!UICONTROL Destination TON]**

Nella scheda **[!UICONTROL Mapping of Encoding]**:

* **[!UICONTROL Outbound SMS coding]**

Nella scheda **[!UICONTROL SMSC specificities]**:

* **[!UICONTROL Coding when sending]** corrisponde a **[!UICONTROL ID Format in MT acknowledgement]**
* **[!UICONTROL Coding when receiving]** corrisponde a **[!UICONTROL ID Format in the SR]**

### Dal connettore Sybase365 {#from-sybase}

Dal connettore **[!UICONTROL Sybase365]**, puoi trasporre nel tuo account **[!UICONTROL Extended SMPP]** appena creato:

![](assets/smpp_3.png)

Nella scheda **[!UICONTROL Connection Settings]**:

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

### Da connettore CLX {#from-clx}

Dal connettore **[!UICONTROL CLX]**, puoi trasporre nel tuo account **[!UICONTROL Extended SMPP]** appena creato:

![](assets/smpp_4.png)

Nella scheda **[!UICONTROL Connection Settings]**:

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

Nella scheda **[!UICONTROL SMPP Channel Settings]**:

* **[!UICONTROL Source number]**

Nella scheda **[!UICONTROL SMSC specificities]**:

* **[!UICONTROL Coding when sending]** corrisponde a **[!UICONTROL ID Format in MT acknowledgement]**
* **[!UICONTROL Coding when receiving]** corrisponde a **[!UICONTROL ID Format in the SR]**

### Dal connettore Tele2 {#from-tele2}

Dal connettore **[!UICONTROL Tele2]**, puoi trasporre nel tuo account **[!UICONTROL Extended SMPP]** appena creato:

![](assets/smpp_6.png)

Nella scheda **[!UICONTROL Connection Settings]**:

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

Nella scheda **[!UICONTROL SMPP Channel Settings]**:

* **[!UICONTROL Source number]**
* **[!UICONTROL Source NPI]**
* **[!UICONTROL Destination NPI]**
* **[!UICONTROL Source TON]**

Nella scheda **[!UICONTROL Mapping of Encoding]**:

* **[!UICONTROL Outbound SMS coding]**

### Dal connettore O2 {#from-O2}

Dal connettore **[!UICONTROL O2]**, puoi trasporre nel tuo account **[!UICONTROL Extended SMPP]** appena creato:

![](assets/smpp_5.png)

Nella scheda **[!UICONTROL Connection Settings]**:

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

Nella scheda **[!UICONTROL SMPP Channel Settings]**:

* **[!UICONTROL Source number]**
* **[!UICONTROL Source NPI]**
* **[!UICONTROL Destination NPI]**
* **[!UICONTROL Source TON]**
* **[!UICONTROL Destination TON]**
