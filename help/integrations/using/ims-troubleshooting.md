---
product: campaign
title: Risoluzione dei problemi di IMS
description: Risoluzione dei problemi di IMS
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: 1ce89c3a-1fe6-4ed6-9547-2eb9713a0ec3
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 1%

---

# Risoluzione dei problemi di IMS{#ims-troubleshooting}

![](../../assets/common.svg)

I seguenti suggerimenti per la risoluzione dei problemi aiuteranno i clienti **on-premise** a risolvere i problemi più comuni che si verificano durante l’utilizzo dell’integrazione IMS. Per i clienti **in hosting**, contatta l&#39;Adobe.

**Account esterno**

Dovrebbe essere disponibile solo un account esterno **uno** con le seguenti impostazioni:

* **Nome** interno: Adobe_Marketing_Cloud
* **Tipo**: Adobe Marketing Cloud

Elimina tutti gli account esterni duplicati con le stesse impostazioni.

**Contesto del prodotto**

Se l&#39;account esterno dispone di un campo **Contesto prodotto**, verifica che il relativo valore sia impostato su: **dma_campaign_classic**

Assicurati che il contesto del prodotto sia lo stesso per Campaign ed Experience Cloud.

Ad esempio, se il **Contesto prodotto** non viene visualizzato, il contesto di prodotto predefinito deve essere **dma_campaign** sia in Campaign che in Experience Cloud. Se viene visualizzato il campo **Contesto prodotto** , il contesto di prodotto predefinito deve essere **dma_campaign_classic** sia in Campaign che in Experience Cloud.

**[!UICONTROL IMS Server URL]**

Nell’account esterno Campaign **Adobe Marketing Cloud**, verifica che il **[!UICONTROL IMS Server URL]** sia [adobeid-na1.services.adobe.com](https://adobeid-na1.services.adobe.com/) o [ims-na1.adobelogin.com](http://ims-na1.adobelogin.com/). Assicurati che entrambe le istanze di stage e produzione puntino allo stesso punto finale di produzione IMS.

**Maschera di associazione**

* Controlla che l&#39;utente che sta tentando di accedere faccia parte di un gruppo di operatori nella dashboard di Enterprise.
* Controlla che il **[!UICONTROL Association Mask]** sia un prefisso del nome del gruppo di operatori dell’utente nella dashboard di Enterprise.
* Assicurati che non ci siano spazi bianchi e errori di ortografia.
* Verifica che i nomi dei gruppi di operatori in Campaign non siano stati modificati e rispetta la seguente sintassi:

```
<Association Mask> + <Operator Group Name in Campaign> = Complete name of the operator group in Enterprise Dashboard
```

**Scopo**

Gli ambiti definiti nell’account esterno Campaign devono essere un sottoinsieme di quelli forniti da IMS.

**URL di callback**

L’ **URL di callback** deve essere aggiunto all’inserire nell&#39;elenco Consentiti e iniziare con &quot;https://&quot;. Verifica che l&#39; **URL di callback** sia collegato all&#39;istanza corrispondente. Ad esempio, l’istanza di produzione deve reindirizzare all’URL di produzione.

**ID client e segreto**

L’ID client corrisponde tra l’account esterno Campaign e quello fornito da IMS.

Verifica che il segreto client immesso sia corretto.

**Riavvia il server**

Riavvia il server se vengono apportate modifiche alle impostazioni di cui sopra nell’account esterno di Campaign

**Tipi comuni di errori e possibili soluzioni**

* L&#39;utente viene reindirizzato alla pagina adobe.com:

   Si è verificato un problema con **[!UICONTROL Callback URL]**. Fai riferimento ai passaggi precedenti per controllare la configurazione **[!UICONTROL Callback URL]**.

* Messaggio &quot;Il login non ha alcun diritto corrispondente all’espressione&quot;:

   Fai riferimento ai passaggi precedenti per controllare la configurazione dei gruppi di operatori e **[!UICONTROL Association Mask]** .

* L’utente non è in grado di accedere alla pagina di accesso di Adobe ID:

   Fai riferimento ai passaggi precedenti per controllare la configurazione dell’ambito.
