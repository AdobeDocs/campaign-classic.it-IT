---
solution: Campaign Classic
product: campaign
title: Disponibilità della console del client per Windows
description: Disponibilità della console del client per Windows
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
translation-type: tm+mt
source-git-commit: c625b4109e2cb47446331cd009ff9827c8267c93
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 5%

---


# Disponibilità della console del client per Windows{#client-console-availability-for-windows}

Affinché  utenti Adobe Campaign possano accedere all’istanza creata e configurata, devono utilizzare la console client.

Quando il computer utilizzato per avviare un  server applicazioni Adobe Campaign (**nlserver web**) riceve connessioni utente dalla console client, potete configurarlo per rendere disponibile il programma di configurazione per il client Adobe Campaign  tramite un&#39;interfaccia HTML.

A tal fine, è necessario:

1. Recuperare il pacchetto che contiene il programma di installazione della console.

   Questo file è denominato `setup-client-7.X.XXXX.exe` per v7 o `setup-client-6.X.XXXX.exe` per v6.1, dove `X` è la versione secondaria di  Adobe Campaign e `XXXX` è il numero di build.

1. Copiate e incollate il pacchetto nella cartella di installazione  Adobe Campaign, in **/datakit/nl/eng/jsp**.
1. Avviate il server Adobe Campaign .

Gli utenti finali possono quindi scaricare il programma di installazione della console tramite un browser Web grazie al seguente URL:

```
https://<your Adobe Campaign server>:>port number>/nl/jsp/logon.jsp
```

Questa pagina richiede un login e una password definiti nell&#39;applicazione.

Per scaricare e installare la console, fare riferimento a [Installazione della console client](../../installation/using/installing-the-client-console.md).

Ogni volta che è disponibile una nuova versione della console client, si invita a scaricarla.

>[!NOTE]
>
>Nel prompt visualizzato,  Adobe consiglia di lasciare l&#39;opzione **[!UICONTROL No longer ask this question]** deselezionata per fare in modo che tutti gli utenti siano avvisati quando è disponibile una nuova versione della console.\
>Se selezionate questa opzione e scegliete di non scaricare la versione più recente, nessun altro utente verrà informato delle nuove versioni disponibili.

Per ripristinare questo prompt, attenetevi alla procedura seguente (solo gli amministratori di sistema che hanno familiarità con la modifica del Registro di sistema devono effettuare le seguenti modifiche):

1. Aprire l&#39;Editor del Registro di sistema utilizzando il comando **regedit** dal menu **[!UICONTROL Start > Run]**.
1. Cercare il nodo ed espanderlo.

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. Eliminare la voce **confAdvisorUpgrade** e chiudere l&#39;Editor del Registro di sistema.

