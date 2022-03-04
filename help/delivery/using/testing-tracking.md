---
product: campaign
title: Verifica del tracciamento dei messaggi
description: Scopri come verificare il tracciamento dei messaggi
feature: Monitoring
exl-id: 16ad36b7-c13e-4b77-86ca-41c9ef174172
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 1%

---

# Verifica del tracciamento dei messaggi{#testing-tracking}

![](../../assets/common.svg)

Puoi testare il tracciamento su pagine mirror, registri e-mail e collegamenti. Per eseguire questa operazione:

1. Crea una nuova consegna e-mail da utilizzare per il test.
1. Specifica l’utente che riceverà l’e-mail. Poiché l’utente dovrà aprire l’e-mail e fare clic sui collegamenti in essa contenuti, assicurati di selezionare un indirizzo del destinatario di prova controllato.
1. Aggiungi un blocco di personalizzazione della pagina speculare (MirrorPage) nel contenuto dell’e-mail.
1. Invia la consegna contenente un collegamento alla pagina speculare.
1. Dopo aver ricevuto l’e-mail, aprilo e fai clic sul collegamento della pagina speculare.
1. Dopo aver eseguito correttamente il reindirizzamento alla pagina speculare, accedi al **Amministrazione > Flussi di lavoro tecnici** e apri la **Tracking** workflow.
1. Avvia il flusso di lavoro, fai clic con il pulsante destro del mouse sul **Scheduler** e seleziona **Esegui attività in sospeso**.
1. Attendi circa 30 secondi, quindi seleziona il **Audit** scheda . Assicurati che sia trovato almeno un record di registro di tracciamento.

   Fai clic su **Aggiorna** se non vengono visualizzati nuovi registri.

1. Vai alla pagina del profilo del destinatario utilizzato per il test e seleziona il **Tracking** scheda . Alcuni record devono essere visualizzati con **Pagina speculare** nel **Tipo** colonna.

   >[!NOTE]
   >
   >La pagina del profilo del destinatario si trova nella **Profili e destinazioni > Destinatari** per impostazione predefinita.

   Per controllare il tracciamento del registro e-mail, cerca i valori **Apri** e **[!UICONTROL Email click]** in **Tipo** colonna.

   Se i registri aperti non vengono visualizzati, accedi alla consegna e accedi alle relative **Proprietà** per assicurarsi che **Attiva tracciamento** e **[!UICONTROL Opens tracking]** sono selezionate.
