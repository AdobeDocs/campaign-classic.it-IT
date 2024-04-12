---
product: campaign
title: Risoluzione dei problemi di IMS
description: Risoluzione dei problemi di IMS
feature: Configuration
badge-v7-prem: label="Solo on-premise/ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: 1ce89c3a-1fe6-4ed6-9547-2eb9713a0ec3
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 1%

---

# Risoluzione dei problemi di IMS{#ims-troubleshooting}


Di seguito sono riportati alcuni suggerimenti utili per la risoluzione dei problemi **on-premise** e **ibrido** I clienti di risolvono i problemi più comuni che si verificano durante l’utilizzo dell’integrazione IMS. Per **in hosting** clienti, contatta l’Adobe.

**Account esterno**

Ci dovrebbe essere solo **uno** account esterno con le seguenti impostazioni:

* **Nome interno**: Adobe_Marketing_Cloud
* **Tipo**: ADOBE MARKETING CLOUD

Elimina eventuali account esterni duplicati con le stesse impostazioni.

**Contesto del prodotto**

Se l’account esterno ha **Contesto del prodotto** , verifica che il relativo valore sia impostato su: **dma_campaign_classic**

Assicurati che il contesto del prodotto sia lo stesso per Campaign e Experience Cloud.

Ad esempio, se **Contesto del prodotto** non viene visualizzato, il contesto di prodotto predefinito deve essere **dma_campaign** sia in Campaign che in Experience Cloud. Se il **Contesto del prodotto** viene visualizzato, il contesto di prodotto predefinito deve essere **dma_campaign_classic** sia in Campaign che in Experience Cloud.

**[!UICONTROL IMS Server URL]**

Nella campagna **Adobe Marketing Cloud** account esterno, verifica che **[!UICONTROL IMS Server URL]** è `adobeid-na1.services.adobe.com` o `ims-na1.adobelogin.com`. Assicurati che le istanze di stage e produzione puntino allo stesso endpoint di produzione IMS.

**Maschera di associazione**

* Verifica che l’utente che tenta di accedere faccia parte di un gruppo di operatori nel dashboard di Enterprise.
* Verifica che la **[!UICONTROL Association Mask]** è un prefisso del nome del gruppo di operatori dell&#39;utente nel dashboard di Enterprise.
* Verificare che non siano presenti spazi bianchi e errori di ortografia.
* Verifica che i nomi dei gruppi di operatori in Campaign non siano stati modificati e rispetta la seguente sintassi:

```
<Association Mask> + <Operator Group Name in Campaign> = Complete name of the operator group in Enterprise Dashboard
```

**Ambito**

Gli ambiti definiti nell’account esterno Campaign devono essere un sottoinsieme di quelli per i quali è stato eseguito il provisioning da IMS.

**URL callback**

Il **URL callback** devono essere aggiunte al inserisco nell&#39;elenco Consentiti di e iniziare con &quot;https://&quot;. Verifica che la **URL callback** è collegato all’istanza corrispondente. Ad esempio, l’istanza di produzione deve reindirizzare all’URL di produzione.

**ID client e segreto**

L’ID client corrisponde tra l’account esterno di Campaign e quello fornito da IMS.

Verifica che il segreto client immesso sia corretto.

**Riavvia il server**

Riavvia il server se vengono apportate modifiche alle impostazioni precedenti nell’account esterno di Campaign

**Tipi comuni di errori e possibili soluzioni**

* L&#39;utente viene reindirizzato alla pagina adobe.com:

  Si è verificato un problema con **[!UICONTROL Callback URL]**. Consulta i passaggi precedenti per verificare **[!UICONTROL Callback URL]** configurazione.

* Messaggio &quot;L’accesso non dispone di diritti corrispondenti all’espressione&quot;:

  Consulta i passaggi precedenti per verificare **[!UICONTROL Association Mask]** e la configurazione dei gruppi di operatori.

* L’utente non è in grado di accedere alla pagina di accesso di Adobe ID:

  Per verificare la configurazione dell’ambito, consulta i passaggi precedenti.
