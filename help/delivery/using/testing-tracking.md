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
1. Dopo essere stato correttamente reindirizzato alla pagina speculare, accedi al **Amministrazione > Flussi di lavoro tecnici** e aprire la **Tracciamento** flusso di lavoro.
1. Avvia il flusso di lavoro, fai clic con il pulsante destro del mouse su **Scheduler** attività e selezione **Esegui attività in sospeso**.
1. Attendere circa 30 secondi, quindi selezionare **Audit** scheda. Verifica che sia stato trovato almeno un record del registro di tracciamento.

   Clic **Aggiorna** se non vengono visualizzati nuovi registri.

1. Vai alla pagina del profilo del destinatario utilizzato per il test e seleziona la **Tracciamento** scheda. Alcuni record devono essere visualizzati con **Pagina mirror** valore in **Tipo** colonna.

   >[!NOTE]
   >
   >La pagina del profilo del destinatario si trova in **Profili e destinazioni > Destinatari** cartella per impostazione predefinita.

   Per verificare il tracciamento del registro e-mail, cerca i valori **Apri** e **[!UICONTROL Email click]** nel **Tipo** colonna.

   Se i registri aperti non vengono visualizzati, vai alla consegna e accedi ai relativi **Proprietà** per assicurarsi che entrambi **Attiva tracciamento** e **[!UICONTROL Opens tracking]** sono selezionate.
