---
product: campaign
title: Gestione degli accessi
description: Ulteriori informazioni sulle best practice per la gestione degli accessi
feature: Installation, Access Management, Permissions
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
exl-id: af88e4e7-0ee3-48b4-9db4-7dd390d9d46a
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 10%

---

# Gestione degli accessi {#access-management}



## Operatore WebApp

L’operatore webApp è un amministratore. Per migliorare la sicurezza, segui queste linee guida:

* Sostituisci l’amministratore nominato direttamente da questo operatore con uno nuovo (può essere denominato &quot;webapp&quot;). Per ulteriori informazioni, consulta [questa pagina](../../platform/using/access-management.md).

* Aggiungi l’operatore webApp in cartelle (principalmente cartelle dei destinatari) per concedere l’accesso in lettura/scrittura ai destinatari. Per ulteriori informazioni, consulta [questa pagina](../../platform/using/access-management.md).

* Se utilizzi un’istanza multi-brand (o multi-geo), potrebbe essere utile suddividere l’accesso all’applicazione web in più cartelle di destinatari. Per eseguire questa operazione:

   1. Duplica l’operatore webApp.

   1. Immettere un nome per ogni duplicato. Ad esempio: webapp_brand, webapp_brand2, ecc.

   1. Duplica un modello di applicazione web in modo che abbia un modello per brand e modifica le proprietà per cambiare l’operatore selezionando Utilizza un account specifico.  Per ulteriori informazioni, consulta [questa pagina](../../web/using/defining-web-forms-properties.md).

## Gruppi di sicurezza e operatori amministratori

Crea un numero sufficiente di gruppi di sicurezza per assegnare agli operatori diritti sufficienti per consentire loro di fare ciò di cui hanno bisogno, e non di più.

Non utilizzare l’operatore admin (o non condividerlo). Crea un operatore per utente fisico (per avere un controllo/una registrazione accurati). Aggiungi gli amministratori appena denominati al gruppo di amministratori. Se non utilizzi l’operatore admin, non eliminarlo e non disattivarlo: questo operatore viene utilizzato internamente per eseguire l’elaborazione. Ma puoi vietare i [accedere alla console client](../../platform/using/access-management.md) e limitarne l’area di sicurezza (a localhost).

Evita di aggiungere troppi operatori nel gruppo di amministrazione (o con diritti denominati amministratore). Si tratta di operatori molto potenti (possono eseguire tutte le istruzioni SQL, eseguire comandi sul server, ecc.).

Adobe Campaign fornisce tre privilegi di alto livello tramite [diritti denominati](../../platform/using/access-management.md#named-rights):

* **AMMINISTRAZIONE** (admin): consente di accedere a tutto e di eseguire tutte le operazioni, ignorando tutti i controlli dei diritti denominati, in modo da includere i diritti denominati PROGRAM EXECUTION (createProcess) e SQL

* **ESECUZIONE DEL PROGRAMMA** (createProcess): consente l&#39;esecuzione di programmi esterni (sul server)

* **SQL**: consente l&#39;esecuzione di script SQL nel database (in modo che possa ignorare il modello di sicurezza). Nota: se è necessario eseguire calcoli complessi (ad esempio i filtri), è possibile chiedere all&#39;amministratore del database di creare una funzione SQL e aggiungerli al inserisco nell&#39;elenco Consentiti di. Per ulteriori informazioni, consulta [questa pagina](../../installation/using/scripting-coding-guidelines.md).

* **Concedi a pochissimi operatori (e attendibili)**
