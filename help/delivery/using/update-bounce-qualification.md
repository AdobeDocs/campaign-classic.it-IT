---
product: campaign
title: Aggiornare la qualifica di mancato recapito dopo un’interruzione del servizio dell’ISP
description: Scopri come aggiornare la qualifica del mancato recapito dopo un'interruzione dell'ISP.
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
hidefromtoc: true
exl-id: 34be23f7-17fa-475e-9663-2e353d76b172
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 3%

---

# Aggiorna i messaggi non corretti dopo l&#39;interruzione Apple {#update-bounce-qualification.md}

## Contesto

Il 26 aprile 2021, a causa di un problema globale ad Apple, alcuni messaggi e-mail inviati a indirizzi e-mail Apple validi venivano inseriti erroneamente come indirizzi e-mail non validi dai server Apple con la seguente risposta non recapitata:  &quot;550 5.1.1 &#39;indirizzo email&#39;: ricerca utente riuscita ma nessun record utente trovato.&quot;

Questo problema si è verificato il 26/4 e è durato 7.00 - 13.00 EST.

>[!NOTE]
>
>È possibile controllare il dashboard di stato del sistema Apple su [questa pagina](https://www.apple.com/support/systemstatus/).

In caso di interruzione di un ISP, le e-mail inviate tramite Campaign non possono essere recapitate correttamente al destinatario: queste e-mail verranno erroneamente contrassegnate come messaggi non recapitati.

Per logica standard di gestione dei messaggi non recapitati, Adobe Campaign ha aggiunto automaticamente questi destinatari all’elenco di quarantena con un’impostazione **[!UICONTROL Status]** di **[!UICONTROL Quarantine]**. Per correggere questo problema, devi aggiornare la tabella di quarantena in Campaign individuando e rimuovendo questi destinatari o modificando i relativi **[!UICONTROL Status]** in **[!UICONTROL Valid]** in modo che il flusso di lavoro di pulizia notturna li rimuova.

Per trovare i destinatari interessati da questo problema o nel caso in cui questo si verifichi nuovamente con un altro ISP, consulta le istruzioni riportate di seguito.

## Processo di aggiornamento

Sarà necessario eseguire una query sulla tabella di quarantena per filtrare tutti i destinatari Apple - tra cui @icloud.com, @me.com, @mac.com - che sono stati potenzialmente interessati dall’interruzione in modo che possano essere rimossi dall’elenco di quarantena e inclusi nelle future consegne e-mail di Campaign.

In base al calendario dell’incidente, di seguito sono riportate le linee guida consigliate per questa query.

>[!IMPORTANT]
>
>Queste date/ore si basano sul fuso orario standard orientale (EST). Modifica il fuso orario dell’istanza.

* Per le istanze Campaign con informazioni sulla risposta non recapitata SMTP nel campo **[!UICONTROL Error text]** dell’elenco di quarantena:

   * **Il testo di errore (testo di quarantena)** contiene &quot;user lookup success but no user record found&quot; E il testo di  **errore (testo di quarantena)** contiene &quot;support.apple.com&quot;
   * **Stato dell&#39;aggiornamento (@lastModified)** il o dopo il 26/04/2021 07:00:00
   * **Stato dell&#39;aggiornamento (@lastModified)** il 26/04/2021 01:00:00 PM

* Per le istanze Campaign con informazioni sulla regola e-mail in entrata nel campo **[!UICONTROL Error text]** dell’elenco di quarantena:

   * **Testo di errore (testo di quarantena)** contiene &quot;Momen_Code10_InvalidRecipient&quot;
   * **Dominio e-mail (@dominio)** uguale a icloud.com OR Dominio  **e-mail (@dominio)** uguale a me.com OR Dominio  **E-mail (@dominio)** uguale a mac.com
   * **Stato dell&#39;aggiornamento (@lastModified)** il o dopo il 26/04/2021 07:00:00
   * **Stato dell&#39;aggiornamento (@lastModified)** il 26/04/2021 01:00:00 PM

Una volta visualizzato l’elenco dei destinatari interessati, puoi impostarli su uno stato **[!UICONTROL Valid]** in modo che vengano rimossi dall’elenco di quarantena dal flusso di lavoro **[!UICONTROL Database cleanup]** oppure eliminarli dalla tabella.

**Argomenti correlati:**
* [Comprendere gli errori di consegna](../../delivery/using/understanding-delivery-failures.md)
* [Qualificazione di mail non recapitate](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification)
