---
product: campaign
title: Aggiornare la qualifica di mancato recapito dopo l’interruzione di Apple 2021
description: Scopri come aggiornare la qualifica di mancato recapito dopo l’interruzione di Apple 2021
badge-v7: label="v7" type="Informative" tooltip="Applicabile a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Deliverability
exl-id: 34be23f7-17fa-475e-9663-2e353d76b172
source-git-commit: d2f5f2a662c022e258fb3cc56c8502c4f4cb2849
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# Aggiornamento in caso di mancati recapiti erronei dovuti a interruzioni del servizio Apple {#update-bounce-qualification.md}

## Contesto

Il 26 aprile 2021, un problema globale in Apple ha causato la mancata ricezione di alcuni messaggi e-mail inviati a indirizzi e-mail validi di Apple come indirizzi e-mail non validi da parte dei server Apple, con la seguente risposta di mancato recapito: &quot;550 5.1.1 &#39;indirizzo e-mail&#39;: ricerca utente riuscita, ma nessun record utente trovato.&quot;

Questo problema si è verificato il 26/4 e si è protratto dalle 7.00 alle 13.00 CET.

>[!NOTE]
>
>Puoi controllare il dashboard di stato del sistema di Apple su [questa pagina](https://www.apple.com/support/systemstatus/).

In caso di interruzione di un ISP, le e-mail inviate tramite Campaign non possono essere consegnate correttamente al destinatario: verranno contrassegnate erroneamente come mancate consegne.

In base alla logica standard di gestione dei mancati recapiti, Adobe Campaign ha aggiunto automaticamente questi destinatari all’elenco di quarantena con una **[!UICONTROL Status]** impostazione di **[!UICONTROL Quarantine]**. Per risolvere questo problema, aggiorna la tabella di quarantena in Campaign trovando e rimuovendo questi destinatari o modificando i **[!UICONTROL Status]** a **[!UICONTROL Valid]** in modo che il flusso di lavoro di pulizia notturna li rimuova.

Per trovare i destinatari interessati da questo problema o nel caso in cui questo si verifichi nuovamente con un altro ISP, consulta le istruzioni di seguito.

## Processo di aggiornamento

Dovrai eseguire una query sulla tabella di quarantena per filtrare tutti i destinatari di Apple - inclusi, @icloud.com, @me.com, @mac.com - che sono stati potenzialmente interessati dall’interruzione, in modo che possano essere rimossi dall’elenco di quarantena e inclusi nelle consegne e-mail future di Campaign.

In base alla tempistica dell’incidente, di seguito sono riportate le linee guida consigliate per questa query.

>[!IMPORTANT]
>
>Queste date/ore si basano sul fuso orario standard orientale (EST). Effettua le regolazioni in base al fuso orario dell’istanza.

* Per le istanze di Campaign con informazioni di risposta SMTP non recapitate in **[!UICONTROL Error text]** campo dell’elenco di quarantena:

   * **Testo di errore (testo di quarantena)** contiene &quot;ricerca utente completata, ma nessun record utente trovato&quot; E **Testo di errore (testo di quarantena)** contiene &quot;support.apple.com&quot;
   * **Stato aggiornamento (@lastModified)** a partire dal 4/26/2021 07:00:00 AM
   * **Stato aggiornamento (@lastModified)** entro il 4/26/2021 01:00:19:00

* Per le istanze di Campaign con informazioni sulle regole e-mail in entrata in **[!UICONTROL Error text]** campo dell’elenco di quarantena:

   * **Testo di errore (testo di quarantena)** contiene &quot;Momen_Code10_InvalidRecipient&quot;
   * **Dominio e-mail (@domain)** uguale a icloud.com OR **Dominio e-mail (@domain)** uguale a me.com OR **Dominio e-mail (@domain)** uguale a mac.com
   * **Stato aggiornamento (@lastModified)** a partire dal 4/26/2021 07:00:00 AM
   * **Stato aggiornamento (@lastModified)** entro il 4/26/2021 01:00:19:00

Dopo aver visualizzato l’elenco dei destinatari interessati, puoi impostarli sullo stato **[!UICONTROL Valid]** in modo che vengano rimossi dall’elenco di quarantena dal **[!UICONTROL Database cleanup]** oppure eliminarli dalla tabella.

**Argomenti correlati:**
* [Errori di consegna](understanding-delivery-failures.md)
* [Qualificazione di mail non recapitate](understanding-delivery-failures.md#bounce-mail-qualification)
