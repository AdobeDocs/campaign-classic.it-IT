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


I seguenti suggerimenti per la risoluzione dei problemi aiuteranno i clienti **on-premise** e **hybrid** a risolvere i problemi più comuni che si verificano quando si utilizza l&#39;integrazione IMS. Per i clienti **hosted**, contatta l&#39;Adobe.

**Account esterno**

Deve essere presente solo **un** account esterno con le seguenti impostazioni:

* **Nome Interno**: Adobe_Marketing_Cloud
* **Tipo**: Adobe Marketing Cloud

Elimina eventuali account esterni duplicati con le stesse impostazioni.

**Contesto prodotto**

Se l&#39;account esterno dispone di un campo **Contesto prodotto**, verificare che il relativo valore sia impostato su: **dma_campaign_classic**

Assicurati che il contesto del prodotto sia lo stesso per Campaign e Experience Cloud.

Se ad esempio il **contesto di prodotto** non viene visualizzato, il contesto di prodotto predefinito deve essere **dma_campaign** sia in Campaign che in Experience Cloud. Se viene visualizzato il campo **Contesto prodotto**, il contesto di prodotto predefinito deve essere **dma_campaign_classic** sia in Campaign che in Experience Cloud.

**[!UICONTROL IMS Server URL]**

Nell&#39;account esterno **Adobe Marketing Cloud** della campagna, verificare che **[!UICONTROL IMS Server URL]** sia `adobeid-na1.services.adobe.com` o `ims-na1.adobelogin.com`. Assicurati che le istanze di stage e produzione puntino allo stesso endpoint di produzione IMS.

**Maschera di associazione**

* Verifica che l’utente che tenta di accedere faccia parte di un gruppo di operatori nel dashboard di Enterprise.
* Verificare che **[!UICONTROL Association Mask]** sia un prefisso del nome del gruppo di operatori dell&#39;utente nel dashboard di Enterprise.
* Verificare che non siano presenti spazi bianchi e errori di ortografia.
* Verifica che i nomi dei gruppi di operatori in Campaign non siano stati modificati e rispetta la seguente sintassi:

```
<Association Mask> + <Operator Group Name in Campaign> = Complete name of the operator group in Enterprise Dashboard
```

**Ambito**

Gli ambiti definiti nell’account esterno Campaign devono essere un sottoinsieme di quelli per i quali è stato eseguito il provisioning da IMS.

**URL richiamata**

L&#39;**URL callback** deve essere aggiunto al inserisco nell&#39;elenco Consentiti di e iniziare con &quot;https://&quot;. Verificare che l&#39;**URL callback** sia collegato all&#39;istanza corrispondente. Ad esempio, l’istanza di produzione deve reindirizzare all’URL di produzione.

**ID client e segreto**

L’ID client corrisponde tra l’account esterno di Campaign e quello fornito da IMS.

Verifica che il segreto client immesso sia corretto.

**Riavvia il server**

Riavvia il server se vengono apportate modifiche alle impostazioni precedenti nell’account esterno di Campaign

**Tipi comuni di errori e possibili soluzioni**

* L&#39;utente viene reindirizzato alla pagina adobe.com:

  Problema con **[!UICONTROL Callback URL]**. Fare riferimento ai passaggi precedenti per verificare la configurazione di **[!UICONTROL Callback URL]**.

* Messaggio &quot;L’accesso non dispone di diritti corrispondenti all’espressione&quot;:

  Fare riferimento ai passaggi precedenti per verificare la configurazione di **[!UICONTROL Association Mask]** e gruppi di operatori.

* L’utente non è in grado di accedere alla pagina di accesso di Adobe ID:

  Per verificare la configurazione dell’ambito, consulta i passaggi precedenti.
