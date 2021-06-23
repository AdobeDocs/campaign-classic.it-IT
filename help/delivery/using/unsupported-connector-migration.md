---
product: campaign
title: Migrazione del connettore SMS non supportata
description: Migrare un connettore SMS non supportato al connettore SMPP generico esteso
audience: delivery
content-type: reference
topic-tags: sending-messages-on-mobiles
hidefromtoc: true
exl-id: 60acf80c-8506-410b-ab2c-4f67a5677b43
source-git-commit: a129f49d4f045433899fd7fdbd057fb16d0ed36a
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 1%

---

# Migrare un connettore SMS non supportato al connettore SMPP generico esteso{#unsupported-connector-migration}

A partire dalla versione 20.2, i connettori legacy sono diventati obsoleti. Questo documento ti aiuterà a migrare i connettori ancora in esecuzione sul vecchio sistema al connettore SMPP consigliato.

>[!CAUTION]
>
>Questa migrazione non è obbligatoria ma consigliata dall’Adobe e assicurerà di essere in esecuzione sull’ultima versione supportata del software.

## Informazioni sui connettori SMS {#about-sms-connectors}

I seguenti connettori sono obsoleti a partire dalla versione 20.2:

* **[!UICONTROL Generic SMPP]** (SMPP versione 3.4 che supporta la modalità binaria)
* **[!UICONTROL Sybase365]** (SAP SMS 365)
* **[!UICONTROL CLX Communications]**
* **[!UICONTROL Tele2]**
* **[!UICONTROL O2]**
* **[!UICONTROL iOS]**

Le funzionalità obsolete sono ancora disponibili e supportate, ma non saranno ulteriormente migliorate. È consigliabile utilizzare il connettore **[!UICONTROL Extended generic SMPP]**.

Per ulteriori informazioni sulle funzioni obsolete e rimosse, consulta questa [pagina](../../rn/using/deprecated-features.md).

I vecchi connettori SMS utilizzano il connettore SMS Java che sovraccarica il processo web. La migrazione al nuovo connettore **[!UICONTROL Extended Generic SMPP]** sposterà questo carico nell’MTA che può supportarlo.

## Migrazione al connettore SMPP generico esteso {#migrating-extended-generic-smpp}

>[!CAUTION]
>
>Anche se è possibile trasporre i parametri, la configurazione del connettore **[!UICONTROL Extended Generic SMPP]** richiede di parlare con il provider che ti fornirà le informazioni necessarie per compilare il resto dei parametri. Per ulteriori informazioni, consulta questa [pagina](sms-protocol.md).

Innanzitutto, dovrai creare un nuovo account esterno **[!UICONTROL Extended Generic SMPP]** e quindi potresti essere in grado di trasporre alcuni dei parametri. Puoi trovare i passaggi dettagliati in questa [pagina](sms-set-up.md#creating-an-smpp-external-account).

È ora necessario compilare i parametri dalla scheda **[!UICONTROL Mobile]** dell’account esterno appena creato **[!UICONTROL Extended Generic SMPP]** a seconda del connettore precedente.

### Dal connettore generico {#from-generic-connector}

Quando scegli il connettore **[!UICONTROL Generic]**, devi disporre di un connettore JavaScript personalizzato che si adatta a ogni situazione.

Se sai che questo connettore sta già utilizzando il protocollo SMPP, puoi effettuare la migrazione al connettore **[!UICONTROL Extended Generic SMPP]**. In caso contrario, verifica con il tuo provider se supporta il protocollo SMPP e configura un nuovo connettore con l’aiuto di un consulente.

Dal connettore **[!UICONTROL Generic]** puoi trasporre all&#39;account **[!UICONTROL Extended SMPP]** appena creato:

![](assets/smpp_generic.png)

Nella scheda **[!UICONTROL Connection Settings]** :

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**

### Dal connettore SMPP generico {#from-generic-smpp-connector}

Dal connettore **[!UICONTROL Generic SMPP]** puoi trasporre all&#39;account **[!UICONTROL Extended SMPP]** appena creato:

![](assets/smpp_generic_2.png)

Nella scheda **[!UICONTROL Connection Settings]** :

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

Nella scheda **[!UICONTROL SMPP Channel Settings]** :

* **[!UICONTROL Source number]**
* **[!UICONTROL Source NPI]**
* **[!UICONTROL Destination NPI]**
* **[!UICONTROL Source TON]**
* **[!UICONTROL Destination TON]**

Nella scheda **[!UICONTROL Mapping of Encoding]** :

* **[!UICONTROL Outbound SMS coding]**

Nella scheda **[!UICONTROL SMSC specificities]** :

* **[!UICONTROL Coding when sending]** corrisponde a  **[!UICONTROL ID Format in MT acknowledgement]**
* **[!UICONTROL Coding when receiving]** corrisponde a  **[!UICONTROL ID Format in the SR]**

### Dal connettore Sybase365 {#from-sybase}

Dal connettore **[!UICONTROL Sybase365]** puoi trasporre all&#39;account **[!UICONTROL Extended SMPP]** appena creato:

![](assets/smpp_3.png)

Nella scheda **[!UICONTROL Connection Settings]** :

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

### Da connettore CLX {#from-clx}

Dal connettore **[!UICONTROL CLX]** puoi trasporre all&#39;account **[!UICONTROL Extended SMPP]** appena creato:

![](assets/smpp_4.png)

Nella scheda **[!UICONTROL Connection Settings]** :

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

Nella scheda **[!UICONTROL SMPP Channel Settings]** :

* **[!UICONTROL Source number]**

Nella scheda **[!UICONTROL SMSC specificities]** :

* **[!UICONTROL Coding when sending]** corrisponde a  **[!UICONTROL ID Format in MT acknowledgement]**
* **[!UICONTROL Coding when receiving]** corrisponde a  **[!UICONTROL ID Format in the SR]**

### Dal connettore Tele2 {#from-tele2}

Dal connettore **[!UICONTROL Tele2]** puoi trasporre all&#39;account **[!UICONTROL Extended SMPP]** appena creato:

![](assets/smpp_6.png)

Nella scheda **[!UICONTROL Connection Settings]** :

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

Nella scheda **[!UICONTROL SMPP Channel Settings]** :

* **[!UICONTROL Source number]**
* **[!UICONTROL Source NPI]**
* **[!UICONTROL Destination NPI]**
* **[!UICONTROL Source TON]**

Nella scheda **[!UICONTROL Mapping of Encoding]** :

* **[!UICONTROL Outbound SMS coding]**

### Dal connettore O2 {#from-O2}

Dal connettore **[!UICONTROL O2]** puoi trasporre all&#39;account **[!UICONTROL Extended SMPP]** appena creato:

![](assets/smpp_5.png)

Nella scheda **[!UICONTROL Connection Settings]** :

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

Nella scheda **[!UICONTROL SMPP Channel Settings]** :

* **[!UICONTROL Source number]**
* **[!UICONTROL Source NPI]**
* **[!UICONTROL Destination NPI]**
* **[!UICONTROL Source TON]**
* **[!UICONTROL Destination TON]**
