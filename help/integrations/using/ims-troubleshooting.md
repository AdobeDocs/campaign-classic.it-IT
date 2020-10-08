---
title: Risoluzione dei problemi di IMS
seo-title: Risoluzione dei problemi di IMS
description: Risoluzione dei problemi di IMS
seo-description: null
page-status-flag: never-activated
uuid: 5db95afc-8cbf-4ec3-b58f-504486fe4a40
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
discoiquuid: e31db11a-ad8e-4fd0-bab7-0df1079231c9
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 2%

---


# Risoluzione dei problemi di IMS{#ims-troubleshooting}

I seguenti suggerimenti per la risoluzione dei problemi aiuteranno i clienti **interni** a risolvere i problemi più comuni che si verificano quando si utilizza l&#39;integrazione IMS. Per i clienti **ospitati** , contattate  Adobe.

**Account esterno**

Deve essere presente **un solo** account esterno con le seguenti impostazioni:

* **Nome** interno:  Adobe_Marketing_Cloud
* **Tipo**: Adobe Marketing Cloud

Eliminate eventuali account esterni duplicati con le stesse impostazioni.

**Contesto prodotto**

Se l&#39;account esterno dispone di un campo Contesto **** prodotto, verificate che il relativo valore sia impostato su: **dma_campaign_classic**

Assicurati che il contesto del prodotto sia lo stesso per Campaign e  Experience Cloud.

Ad esempio, se il Contesto **** prodotto non viene visualizzato, il contesto prodotto predefinito deve essere **dma_campaign** sia nel Experience Cloud Campaign che . Se viene visualizzato il campo Contesto **** prodotto, il contesto predefinito del prodotto deve essere **dma_campaign_classic** sia nel Experience Cloud Campaign che .

**[!UICONTROL IMS Server URL]**

Nell&#39;account esterno di Campaign **Adobe Marketing Cloud** , verifica che **[!UICONTROL IMS Server URL]** sia [adobeid-na1.services.adobe.com](https://adobeid-na1.services.adobe.com/) o [ims-na1.adobelogin.com](http://ims-na1.adobelogin.com/). Accertatevi che le istanze di fase e produzione puntino allo stesso punto finale di produzione IMS.

**Maschera di associazione**

* Verificate che l&#39;utente che sta tentando di accedere faccia parte di un gruppo di operatori nella dashboard di Enterprise.
* Verificate che il prefisso **[!UICONTROL Association Mask]** sia il nome del gruppo di operatori dell&#39;utente nella dashboard di Enterprise.
* Assicuratevi che non vi siano spazi bianchi e errori di ortografia.
* Verifica che i nomi dei gruppi di operatori in Campaign non siano stati modificati e rispetta la sintassi seguente:

```
<Association Mask> + <Operator Group Name in Campaign> = Complete name of the operator group in Enterprise Dashboard
```

**Scopo**

Gli ambiti definiti nell&#39;account esterno della campagna devono essere un sottoinsieme di quelli predisposti da IMS.

**URL richiamata**

L’URL **di** callback deve essere aggiunto all’elenco consentiti  e iniziare con &quot;https://&quot;. Verificate che l’URL **di** callback sia collegato all’istanza corrispondente. Ad esempio, l&#39;istanza di produzione deve reindirizzare all&#39;URL di produzione.

**ID client e segreto**

L&#39;ID client corrisponde all&#39;account esterno della campagna e a quello fornito da IMS.

Verificate che il segreto cliente immesso sia corretto.

**Riavviare il server**

Riavvia il server se vengono apportate modifiche alle impostazioni precedenti nell&#39;account esterno di Campaign

**Tipi comuni di errori e possibili soluzioni**

* L&#39;utente viene reindirizzato alla pagina adobe.com:

   C&#39;è un problema con il **[!UICONTROL Callback URL]**. Fare riferimento ai passaggi precedenti per verificare la **[!UICONTROL Callback URL]** configurazione.

* Messaggio &quot;Login non ha alcun diritto corrispondente all&#39;espressione&quot;:

   Fare riferimento ai passaggi precedenti per verificare la configurazione dei gruppi **[!UICONTROL Association Mask]** e degli operatori.

* L&#39;utente non è in grado di accedere alla  pagina di accesso di Adobe ID:

   Fare riferimento ai passaggi precedenti per controllare la configurazione dell&#39;ambito.

