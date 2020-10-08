---
title: Disponibilità della console del client per Windows
seo-title: Disponibilità della console del client per Windows
description: Disponibilità della console del client per Windows
seo-description: null
page-status-flag: never-activated
uuid: d1cbb34e-87e0-481b-a78b-3616047eb5cb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
discoiquuid: 4fa2e8c1-33d1-4d14-941b-ca528b8ceabb
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 6%

---


# Disponibilità della console del client per Windows{#client-console-availability-for-windows}

Affinché  utenti Adobe Campaign possano accedere all’istanza creata e configurata, devono utilizzare la console client.

Quando il computer utilizzato per avviare un  server applicazioni Adobe Campaign (Web **** nlserver) riceve le connessioni utente dalla console client, potete configurarlo per rendere disponibile il programma di configurazione per il client Adobe Campaign  tramite un&#39;interfaccia HTML.

A tal fine, è necessario:

1. Recuperare il pacchetto che contiene il programma di installazione della console.

   Questo file viene chiamato `setup-client-7.X.XXXX.exe` per v7 o `setup-client-6.X.XXXX.exe` per v6.1, dove `X` è la sub-versione di  Adobe Campaign e `XXXX` è il numero di build.

1. Copiate e incollate il pacchetto nella cartella di installazione  Adobe Campaign, in **/datakit/nl/eng/jsp**.
1. Avviate il server Adobe Campaign .

Gli utenti finali possono quindi scaricare il programma di installazione della console tramite un browser Web grazie al seguente URL:

```
https://<your Adobe Campaign server>:>port number>/nl/jsp/logon.jsp
```

Questa pagina richiede un login e una password definiti nell&#39;applicazione.

Per scaricare e installare la console, vedere [Installazione della console](../../installation/using/installing-the-client-console.md)client.

Ogni volta che è disponibile una nuova versione della console client, si invita a scaricarla.

>[!NOTE]
>
>Nel prompt visualizzato,  Adobe consiglia di lasciare l&#39;opzione **[!UICONTROL No longer ask this question]** deselezionata per fare in modo che tutti gli utenti ricevano avvisi quando è disponibile una nuova versione della console.\
>Se selezionate questa opzione e scegliete di non scaricare la versione più recente, nessun altro utente verrà informato delle nuove versioni disponibili.

Per ripristinare questo prompt, attenetevi alla procedura seguente (solo gli amministratori di sistema che hanno familiarità con la modifica del Registro di sistema devono effettuare le seguenti modifiche):

1. Aprite l&#39;Editor del Registro di sistema utilizzando il comando **regedit** del **[!UICONTROL Start > Run]** menu.
1. Cercare il nodo ed espanderlo.

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. Eliminate la voce **confAdvisorUpgrade** e chiudete l&#39;Editor del Registro di sistema.

