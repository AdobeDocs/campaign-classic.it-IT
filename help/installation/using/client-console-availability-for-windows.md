---
title: Disponibilità della console client per Windows
seo-title: Disponibilità della console client per Windows
description: Disponibilità della console client per Windows
seo-description: null
page-status-flag: never-activated
uuid: d1cbb34e-87e0-481b-a78b-3616047eb5cb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
discoiquuid: 4fa2e8c1-33d1-4d14-941b-ca528b8ceabb
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 46f5bfb41bfe9c938ac0ffa767ead3e47a32047d

---


# Disponibilità della console client per Windows{#client-console-availability-for-windows}

Affinché gli utenti di Adobe Campaign possano accedere all&#39;istanza creata e configurata, devono utilizzare la console client.

Quando il computer utilizzato per avviare un server applicazioni Adobe Campaign (**server web**) riceve connessioni utente dalla console client, puoi configurarlo per rendere disponibile il programma di configurazione per il client avanzato Adobe Campaign tramite un&#39;interfaccia HTML.

A tal fine, è necessario:

1. Recuperare il pacchetto che contiene il programma di installazione della console.

   Questo file viene chiamato `setup-client-7.X.XXXX.exe` per v7 o `setup-client-6.X.XXXX.exe` per v6.1, dove `X` è la versione secondaria di Adobe Campaign ed `XXXX` è il numero di build.

1. Copia e incolla il pacchetto nella cartella di installazione di Adobe Campaign, in **/datakit/nl/eng/jsp**.
1. Avvia il server Adobe Campaign.

Gli utenti finali possono quindi scaricare il programma di installazione della console tramite un browser Web grazie al seguente URL:

```
https://<your Adobe Campaign server>:>port number>/nl/jsp/logon.jsp
```

Questa pagina richiede un login e una password definiti nell&#39;applicazione.

Per scaricare e installare la console, vedere [Installazione della console](../../installation/using/installing-the-client-console.md)client.

Ogni volta che è disponibile una nuova versione della console client, si invita a scaricarla.

>[!NOTE]
>
>Nel prompt visualizzato, Adobe consiglia di lasciare l’opzione **[!UICONTROL No longer ask this question]** deselezionata per fare in modo che tutti gli utenti siano avvisati quando è disponibile una nuova versione della console.\
>Se selezionate questa opzione e scegliete di non scaricare la versione più recente, nessun altro utente verrà informato delle nuove versioni disponibili.

Per ripristinare questo prompt, attenetevi alla procedura seguente (solo gli amministratori di sistema che hanno familiarità con la modifica del Registro di sistema devono effettuare le seguenti modifiche):

1. Aprite l&#39;Editor del Registro di sistema utilizzando il comando **regedit** del **[!UICONTROL Start > Run]** menu.
1. Cercare il nodo ed espanderlo.

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. Eliminate la voce **confAdvisorUpgrade** e chiudete l&#39;Editor del Registro di sistema.

