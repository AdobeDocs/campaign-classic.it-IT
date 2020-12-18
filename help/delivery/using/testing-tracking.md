---
solution: Campaign Classic
product: campaign
title: Test del tracking
description: Test del tracking
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 3%

---


# Test del tracking{#testing-tracking}

Potete testare il tracciamento su pagine mirror, registri e collegamenti e-mail. Per eseguire questa operazione:

1. Create una nuova consegna e-mail da utilizzare per il test.
1. Specificate l’utente che riceverà l’e-mail. Poiché l&#39;utente dovrà aprire l&#39;e-mail e fare clic sui collegamenti in essa contenuti, accertatevi di selezionare l&#39;indirizzo del destinatario di prova controllato.
1. Aggiungi un blocco di personalizzazione pagina mirror (MirrorPage) nel contenuto dell&#39;e-mail.
1. Inviate la consegna contenente un collegamento alla pagina mirror.
1. Dopo aver ricevuto l’e-mail, apritela e fate clic sul collegamento della pagina mirror.
1. Dopo aver eseguito correttamente il reindirizzamento alla pagina mirror, accedere alla cartella **Amministrazione > Flussi di lavoro tecnici** e aprire il flusso di lavoro **Tracciamento**.
1. Avviare il flusso di lavoro, fare clic con il pulsante destro del mouse sull&#39;attività **Scheduler** e selezionare **Esegui attività in sospeso ora**.
1. Attendi circa 30 secondi, quindi seleziona la scheda **Audit**. Verificare che sia trovato almeno un record di registro di tracciamento.

   Fare clic su **Aggiorna** se non vengono visualizzati nuovi registri.

1. Andate alla pagina del profilo del destinatario utilizzato per il test, quindi selezionate la scheda **Tracking**. Alcuni record devono essere visualizzati con il valore **Mirror Page** nella colonna **Type**.

   >[!NOTE]
   >
   >Per impostazione predefinita, la pagina del profilo del destinatario si trova nella cartella **Profili e destinazioni > Destinatari**.

   Per controllare il tracciamento del registro e-mail, cercare i valori **Open** e **[!UICONTROL Email click]** nella colonna **Type**.

   Se i registri aperti non vengono visualizzati, andate alla consegna e accedete alle relative **Proprietà** per verificare che siano selezionate entrambe le opzioni **Attiva tracciamento** e **[!UICONTROL Opens tracking]**.

