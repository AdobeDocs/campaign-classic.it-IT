---
product: campaign
title: Disponibilità della console client per Windows
description: Disponibilità della console client per Windows
feature: Installation, Upgrade
badge-v7-prem: label="on-premise e ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 57845eae-1f1a-42f4-b2ba-46d454677ae0
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 4%

---

# Disponibilità della console client per Windows{#client-console-availability-for-windows}



Per poter accedere all’istanza creata e configurata, gli utenti di Adobe Campaign devono utilizzare la console client.

## Rendi disponibile la console client

Quando il computer utilizzato per avviare un server applicazioni Adobe Campaign (**nlserver web**) riceve connessioni utente dalla console client, è possibile configurarla per rendere disponibile il programma di configurazione per Adobe Campaign rich client tramite un&#39;interfaccia HTML. Ogni volta che è disponibile una nuova versione della console client, gli utenti vengono invitati a scaricarla all’avvio della console client.

A questo scopo, devi:

1. Selezionare il pacchetto contenente il programma di installazione della console.

   Questo file è denominato `setup-client-7.X.XXXX.exe`, dove `X` è la sottoversione di Adobe Campaign e `XXXX` è il numero di build.

1. Copia e incolla questo pacchetto nella cartella di installazione di Adobe Campaign (sul server di marketing per le installazioni ibride), in **/datakit/nl/eng/jsp**.
1. Avvia il server Adobe Campaign.

Gli utenti di Campaign possono quindi scaricare il programma di installazione della console tramite un browser web grazie al seguente URL:

```
https://<your Adobe Campaign server>:>port number>/nl/jsp/logon.jsp
```

Questa pagina richiede un login e una password definiti nell&#39;applicazione.

Scopri come installare la console [in questa sezione](../../installation/using/installing-the-client-console.md).

## Proporre agli utenti finali di aggiornare la console client

Una volta che la console è disponibile nella cartella del server Campaign, gli utenti sono invitati a scaricare l’ultima versione della console client in una finestra di prompt dedicata. Adobe consiglia di lasciare l’opzione **[!UICONTROL No longer ask this question]** deselezionato per assicurarsi che tutti gli utenti vengano avvisati quando è disponibile una nuova versione della console.

Se selezioni questa opzione e scegli di non scaricare l’ultima versione, nessun altro utente verrà informato delle nuove versioni disponibili.

Se l’opzione è stata selezionata, puoi reimpostare questo prompt. Solo gli amministratori di sistema che hanno familiarità con la modifica del Registro di sistema di Windows possono apportare le seguenti modifiche:

1. Apri l’Editor del Registro di sistema utilizzando **regedit** comando da **[!UICONTROL Start > Run]** menu.
1. Cerca il nodo ed espandilo.

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. Elimina **confAdvisedUpgrade** e chiudere l&#39;Editor del Registro di sistema.
