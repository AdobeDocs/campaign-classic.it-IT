---
solution: Campaign Classic
product: campaign
title: Disponibilità della console del client per Windows
description: Disponibilità della console del client per Windows
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
translation-type: tm+mt
source-git-commit: 1b02c3870ddc01705f01ea992e734cf0810e003a
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 4%

---


# Disponibilità della console del client per Windows{#client-console-availability-for-windows}

Affinché gli utenti di Adobe Campaign possano accedere all’istanza creata e configurata, devono utilizzare la console client.

## Rendi disponibile la console client

Quando il computer utilizzato per avviare un server applicazioni Adobe Campaign (**nlserver web**) riceve connessioni utente dalla console client, puoi configurarlo per rendere disponibile il programma di configurazione per il client avanzato Adobe Campaign tramite un’interfaccia HTML. Ogni volta che è disponibile una nuova versione della console client, gli utenti vengono invitati a scaricarla all’avvio della console client.

A questo scopo, devi:

1. Selezionare il pacchetto contenente il programma di installazione della console.

   Questo file si chiama `setup-client-7.X.XXXX.exe` per v7 o `setup-client-6.X.XXXX.exe` per v6.1, dove `X` è la versione secondaria di Adobe Campaign e `XXXX` è il numero di build.

1. Copia e incolla questo pacchetto nella cartella di installazione di Adobe Campaign (sul server di marketing per le installazioni ibride), alla voce **/datakit/nl/eng/jsp**.
1. Avvia il server Adobe Campaign.

Gli utenti di Campaign possono quindi scaricare il programma di installazione della console tramite un browser web grazie al seguente URL:

```
https://<your Adobe Campaign server>:>port number>/nl/jsp/logon.jsp
```

Questa pagina richiede un login e una password definiti nell&#39;applicazione.

Scopri come installare la console [in questa sezione](../../installation/using/installing-the-client-console.md).

## Proporre agli utenti finali di aggiornare la propria console client

Una volta che la console è disponibile nella cartella del server Campaign, gli utenti sono invitati a scaricare l’ultima versione della console client in una finestra dedicata al prompt. Adobe consiglia di deselezionare l’opzione **[!UICONTROL No longer ask this question]** per fare in modo che tutti gli utenti vengano avvisati quando è disponibile una nuova versione della console.

Se selezioni questa opzione e scegli di non scaricare la versione più recente, nessun altro utente verrà informato delle nuove versioni disponibili.

Se l’opzione è stata selezionata, è possibile reimpostare questo prompt. Solo gli amministratori di sistema che possono modificare il Registro di sistema di Windows devono apportare le seguenti modifiche:

1. Apri l&#39;Editor del Registro di sistema utilizzando il comando **regedit** dal menu **[!UICONTROL Start > Run]**.
1. Cercare il nodo ed espanderlo.

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. Elimina la voce **confAdvisorUpgrade** e chiudi l&#39;Editor del Registro di sistema.

