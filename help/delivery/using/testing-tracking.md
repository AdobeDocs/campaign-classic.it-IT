---
product: campaign
title: Verifica tracciamento dei messaggi
description: Scopri come verificare il tracciamento dei messaggi
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Monitoring
role: User
exl-id: 16ad36b7-c13e-4b77-86ca-41c9ef174172
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 1%

---

# Verifica tracciamento dei messaggi{#testing-tracking}

Puoi verificare il tracciamento su pagine mirror, registri e collegamenti e-mail. Per eseguire questa operazione:

1. Crea una nuova consegna e-mail da utilizzare per il test.
1. Specifica l’utente che riceverà l’e-mail. Poiché questo utente dovrà aprire l’e-mail e fare clic sui collegamenti in essa contenuti, assicurati di selezionare un indirizzo del destinatario di prova che controlli.
1. Aggiungi un blocco di personalizzazione pagina speculare (MirrorPage) nel contenuto dell’e-mail.
1. Invia la consegna contenente un collegamento alla pagina speculare.
1. Una volta ricevuta l’e-mail, aprila e fai clic sul collegamento della pagina speculare.
1. Dopo essere stato reindirizzato correttamente alla pagina mirror, accedere alla cartella **Amministrazione > Flussi di lavoro tecnici** e aprire il flusso di lavoro **Tracciamento**.
1. Avvia il flusso di lavoro, fai clic con il pulsante destro del mouse sull&#39;attività **Scheduler** e seleziona **Esegui attività in sospeso ora**.
1. Attendi circa 30 secondi, quindi seleziona la scheda **Audit**. Verifica che sia stato trovato almeno un record del registro di tracciamento.

   Fare clic su **Aggiorna** se non vengono visualizzati nuovi registri.

1. Vai alla pagina del profilo del destinatario utilizzato per il test e seleziona la scheda **Verifica**. Alcuni record devono essere visualizzati con il valore **Pagina mirror** nella colonna **Tipo**.

   >[!NOTE]
   >
   >Per impostazione predefinita, la pagina del profilo del destinatario si trova nella cartella **Profili e destinazioni > Destinatari**.

   Per controllare il tracciamento del registro e-mail, cerca i valori **Apri** e **[!UICONTROL Email click]** nella colonna **Tipo**.

   Se i registri aperti non vengono visualizzati, vai alla consegna e accedi alle relative **Proprietà** per assicurarti che siano verificate sia le opzioni **Attiva tracciamento** che le opzioni **[!UICONTROL Opens tracking]**.
