---
product: campaign
title: Risoluzione dei problemi di IMS
description: Risoluzione dei problemi di IMS
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: 1ce89c3a-1fe6-4ed6-9547-2eb9713a0ec3
source-git-commit: f4513834cf721f6d962c7c02c6c64b2171059352
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 2%

---

# Risoluzione dei problemi di IMS{#ims-troubleshooting}

![](../../assets/common.svg)

I seguenti suggerimenti per la risoluzione dei problemi sono utili **on-premise** i clienti risolvono i problemi più comuni che si verificano quando utilizzano l’integrazione IMS. Per **ospitato** clienti, contattare l&#39;Adobe.

**Account esterno**

Ci dovrebbe essere solo **uno** account esterno con le seguenti impostazioni:

* **Nome interno**: Adobe_Marketing_Cloud
* **Tipo**: Adobe Marketing Cloud

Elimina tutti gli account esterni duplicati con le stesse impostazioni.

**Contesto del prodotto**

Se l’account esterno ha una **Contesto del prodotto** controlla che il relativo valore sia impostato su: **dma_campaign_classic**

Assicurati che il contesto del prodotto sia lo stesso per Campaign ed Experience Cloud.

Ad esempio, se **Contesto del prodotto** non viene visualizzato, il contesto di prodotto predefinito deve essere **dma_campaign** sia in Campaign che in Experience Cloud. Se la **Contesto del prodotto** viene visualizzato il campo , il contesto di prodotto predefinito deve essere **dma_campaign_classic** sia in Campaign che in Experience Cloud.

**[!UICONTROL IMS Server URL]**

Nella campagna **Adobe Marketing Cloud** account esterno, controlla che il **[!UICONTROL IMS Server URL]** è `adobeid-na1.services.adobe.com` o `ims-na1.adobelogin.com`. Assicurati che entrambe le istanze di stage e produzione puntino allo stesso punto finale di produzione IMS.

**Maschera di associazione**

* Controlla che l&#39;utente che sta tentando di accedere faccia parte di un gruppo di operatori nella dashboard di Enterprise.
* Controlla che la **[!UICONTROL Association Mask]** è un prefisso del nome del gruppo di operatori dell’utente nella dashboard di Enterprise.
* Assicurati che non ci siano spazi bianchi e errori di ortografia.
* Verifica che i nomi dei gruppi di operatori in Campaign non siano stati modificati e rispetta la seguente sintassi:

```
<Association Mask> + <Operator Group Name in Campaign> = Complete name of the operator group in Enterprise Dashboard
```

**Scopo**

Gli ambiti definiti nell’account esterno Campaign devono essere un sottoinsieme di quelli forniti da IMS.

**URL di callback**

La **URL di callback** devono essere aggiunti all&#39;inserire nell&#39;elenco Consentiti e iniziare con &quot;https://&quot;. Controlla che la **URL di callback** è collegato all’istanza corrispondente. Ad esempio, l’istanza di produzione deve reindirizzare all’URL di produzione.

**ID client e segreto**

L’ID client corrisponde tra l’account esterno Campaign e quello fornito da IMS.

Verifica che il segreto client immesso sia corretto.

**Riavvia il server**

Riavvia il server se vengono apportate modifiche alle impostazioni di cui sopra nell’account esterno di Campaign

**Tipi comuni di errori e possibili soluzioni**

* L&#39;utente viene reindirizzato alla pagina adobe.com:

   C&#39;è un problema con il **[!UICONTROL Callback URL]**. Fai riferimento ai passaggi precedenti per controllare il **[!UICONTROL Callback URL]** configurazione.

* Messaggio &quot;Il login non ha alcun diritto corrispondente all’espressione&quot;:

   Fai riferimento ai passaggi precedenti per controllare il **[!UICONTROL Association Mask]** e la configurazione dei gruppi di operatori.

* L’utente non è in grado di accedere alla pagina di accesso di Adobe ID:

   Fai riferimento ai passaggi precedenti per controllare la configurazione dell’ambito.
