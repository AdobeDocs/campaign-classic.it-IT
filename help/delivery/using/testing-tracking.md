---
product: campaign
title: Test del tracking
description: Test del tracking
audience: delivery
content-type: reference
topic-tags: tracking-messages
exl-id: 16ad36b7-c13e-4b77-86ca-41c9ef174172
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 3%

---

# Test del tracking{#testing-tracking}

![](../../assets/common.svg)

Puoi testare il tracciamento su pagine mirror, registri e-mail e collegamenti. Per eseguire questa operazione:

1. Crea una nuova consegna e-mail da utilizzare per il test.
1. Specifica l’utente che riceverà l’e-mail. Poiché l’utente dovrà aprire l’e-mail e fare clic sui collegamenti in essa contenuti, assicurati di selezionare un indirizzo del destinatario di prova controllato.
1. Aggiungi un blocco di personalizzazione della pagina speculare (MirrorPage) nel contenuto dell’e-mail.
1. Invia la consegna contenente un collegamento alla pagina speculare.
1. Dopo aver ricevuto l’e-mail, aprilo e fai clic sul collegamento della pagina speculare.
1. Dopo aver eseguito correttamente il reindirizzamento alla pagina speculare, accedi alla cartella **Amministrazione > Flussi di lavoro tecnici** e apri il flusso di lavoro **Tracking** .
1. Avvia il flusso di lavoro, fai clic con il pulsante destro del mouse sull&#39;attività **Scheduler** e seleziona **Esegui attività in sospeso ora**.
1. Attendi circa 30 secondi, quindi seleziona la scheda **Audit** . Assicurati che sia trovato almeno un record di registro di tracciamento.

   Fai clic su **Aggiorna** se non vengono visualizzati nuovi registri.

1. Vai alla pagina del profilo del destinatario utilizzato per il test e seleziona la scheda **Tracking** . Alcuni record devono essere visualizzati con il valore **Pagina speculare** nella colonna **Tipo**.

   >[!NOTE]
   >
   >Per impostazione predefinita, la pagina del profilo del destinatario si trova nella cartella **Profili e destinazioni > Destinatari** .

   Per controllare il tracciamento del registro e-mail, cerca i valori **Apri** e **[!UICONTROL Email click]** nella colonna **Tipo** .

   Se i registri aperti non vengono visualizzati, vai alla consegna e accedi alle relative **Proprietà** per assicurarti che siano selezionate entrambe le opzioni **Attiva tracciamento** e **[!UICONTROL Opens tracking]** .
