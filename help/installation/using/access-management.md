---
product: campaign
title: Gestione degli accessi
description: Ulteriori informazioni sulle best practice per la gestione degli accessi.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: af88e4e7-0ee3-48b4-9db4-7dd390d9d46a
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 8%

---

# Gestione degli accessi {#access-management}

![](../../assets/v7-only.svg)

## Operatore Webapp

L’operatore webApp è un amministratore. Per migliorare la sicurezza, segui queste linee guida:

* Sostituisci l’amministratore denominato a destra da questo operatore con un nuovo (può essere denominato &quot;webapp&quot;). Per ulteriori informazioni, consulta [questa pagina](../../platform/using/access-management.md).

* Aggiungi l’operatore webApp nelle cartelle (principalmente nelle cartelle dei destinatari) per concedere l’accesso in lettura/scrittura ai destinatari. Per ulteriori informazioni, consulta [questa pagina](../../platform/using/access-management.md).

* Se utilizzi un’istanza multi-brand (o multi-geo), puoi dividere l’accesso alle applicazioni web in diverse cartelle dei destinatari. Per eseguire questa operazione:

   1. Duplica l’operatore webApp

   1. Immetti un nome per ogni duplicato. Ad esempio: webapp_brand, webapp_brand2, ecc.

   1. Duplica un modello di applicazione web per avere un modello per marchio e modifica le proprietà per modificare l’operatore selezionando Usa un account specifico.  Per ulteriori informazioni, consulta [questa pagina](../../web/using/defining-web-forms-properties.md).

## Gruppi di sicurezza e operatori di amministrazione

Crea abbastanza gruppi di sicurezza per dare solo abbastanza diritti ai tuoi operatori per consentire loro di fare ciò di cui hanno bisogno, e non di più.

Non utilizzare l&#39;operatore amministratore (o non condividerlo). Crea un operatore per utente fisico (per avere un controllo/registrazione accurati). Aggiungi i nuovi amministratori al gruppo di amministratori. Se non utilizzi l’operatore amministratore, non eliminarlo e non disattivarlo: questo operatore viene utilizzato internamente per eseguire l’elaborazione. Tuttavia, puoi vietarne l&#39; [accesso alla console client](../../platform/using/access-management.md) e limitarne la zona di sicurezza (a localhost).

Evita di aggiungere troppi operatori nel gruppo di amministrazione (o con diritti di amministratore). Sono operatori molto potenti (possono eseguire tutte le istruzioni SQL, eseguire comandi sul server, ecc.).

Adobe Campaign fornisce tre privilegi di alto livello tramite [diritti denominati](../../platform/using/access-management.md#named-rights):

* **AMMINISTRAZIONE**  (amministratore): consente l&#39;accesso a tutto e consente di eseguire tutte le operazioni, bypassando tutti i controlli dei diritti denominati, in modo da includere l&#39;ESECUZIONE PROGRAM (createProcess) e i diritti denominati SQL

* **ESECUZIONE PROGRAMMA**  (createProcess): consente l&#39;esecuzione di programmi esterni (sul server)

* **SQL**: consente l&#39;esecuzione di script SQL nel database (in modo da poter ignorare il modello di sicurezza). Nota: se è necessario eseguire calcoli complessi (ad esempio il filtro), è possibile chiedere all&#39;amministratore del database di creare una funzione SQL e aggiungerla all&#39;elenco consentiti. Per ulteriori informazioni, consulta [questa pagina](../../installation/using/scripting-coding-guidelines.md).

* **Concedili a pochi operatori (e affidabili)**
