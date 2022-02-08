---
product: campaign
title: Aggiornare la qualifica di mancato recapito dopo un’interruzione del servizio ISP
description: Scopri come aggiornare la qualificazione dei messaggi non recapitati dopo un’interruzione dell’ISP
exl-id: 34be23f7-17fa-475e-9663-2e353d76b172
source-git-commit: 1e11b7419388698f5de366cbeddf2be88ef12873
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 3%

---

# Aggiorna i messaggi non corretti dopo l&#39;interruzione di Apple {#update-bounce-qualification.md}

![](../../assets/common.svg)

## Contesto

Il 26 aprile 2021, a causa di un problema globale di Apple, alcuni messaggi e-mail inviati a indirizzi e-mail Apple validi non venivano inseriti correttamente come indirizzi e-mail non validi dai server Apple con la seguente risposta non recapitata: &quot;550 5.1.1 &#39;indirizzo email&#39;: ricerca utente riuscita ma nessun record utente trovato.&quot;

Questo problema si è verificato il 26/4 e è durato 7.00 - 13.00 EST.

>[!NOTE]
>
>Puoi controllare il dashboard di stato del sistema di Apple su [questa pagina](https://www.apple.com/support/systemstatus/).

In caso di interruzione di un ISP, le e-mail inviate tramite Campaign non possono essere recapitate correttamente al destinatario: queste e-mail verranno erroneamente contrassegnate come messaggi non recapitati.

Per logica standard di gestione dei messaggi non recapitati, Adobe Campaign ha aggiunto automaticamente questi destinatari all’elenco di quarantena con un **[!UICONTROL Status]** definizione **[!UICONTROL Quarantine]**. Per correggere questo problema, devi aggiornare la tabella di quarantena in Campaign trovando e rimuovendo questi destinatari o modificando i relativi **[!UICONTROL Status]** a **[!UICONTROL Valid]** in modo che il flusso di lavoro di pulizia notturna li rimuova.

Per trovare i destinatari interessati da questo problema o nel caso in cui questo si verifichi nuovamente con un altro ISP, consulta le istruzioni riportate di seguito.

## Processo di aggiornamento

Sarà necessario eseguire una query sulla tabella di quarantena per filtrare tutti i destinatari di Apple - tra cui @icloud.com, @me.com, @mac.com - che sono stati potenzialmente interessati dall’interruzione, in modo che possano essere rimossi dall’elenco di quarantena e inclusi nelle future consegne e-mail di Campaign.

In base al calendario dell’incidente, di seguito sono riportate le linee guida consigliate per questa query.

>[!IMPORTANT]
>
>Queste date/ore si basano sul fuso orario standard orientale (EST). Modifica il fuso orario dell’istanza.

* Per le istanze Campaign con le informazioni di risposta non recapitata SMTP nel **[!UICONTROL Error text]** campo dell’elenco di quarantena:

   * **Testo di errore (testo di quarantena)** contiene &quot;user lookup success but no user record found&quot; AND **Testo di errore (testo di quarantena)** contiene &quot;support.apple.com&quot;
   * **Stato aggiornamento (@lastModified)** il 26/04/2021 07 o successivo:00:00
   * **Stato aggiornamento (@lastModified)** il 26/04/2021 01 o versione precedente:00:10:00

* Per le istanze Campaign con informazioni sulla regola e-mail in entrata nel **[!UICONTROL Error text]** campo dell’elenco di quarantena:

   * **Testo di errore (testo di quarantena)** contiene &quot;Momen_Code10_InvalidRecipient&quot;
   * **Dominio e-mail (@dominio)** uguale a icloud.com OR **Dominio e-mail (@dominio)** uguale a me.com OR **Dominio e-mail (@dominio)** uguale a mac.com
   * **Stato aggiornamento (@lastModified)** il 26/04/2021 07 o successivo:00:00
   * **Stato aggiornamento (@lastModified)** il 26/04/2021 01 o versione precedente:00:10:00

Una volta visualizzato l’elenco dei destinatari interessati, puoi impostarli su uno stato **[!UICONTROL Valid]** in modo che vengano rimosse dall&#39;elenco di quarantena **[!UICONTROL Database cleanup]** oppure eliminali dalla tabella.

**Argomenti correlati:**
* [Comprendere gli errori di consegna](understanding-delivery-failures.md)
* [Qualificazione di mail non recapitate](understanding-delivery-failures.md#bounce-mail-qualification)
