---
product: campaign
title: Aggiornare la qualifica di mancato recapito dopo l’interruzione di Apple 2021
description: Scopri come aggiornare la qualifica di mancato recapito dopo l’interruzione di Apple 2021
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Deliverability
exl-id: 34be23f7-17fa-475e-9663-2e353d76b172
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# Aggiornare mancati recapiti erronei dopo l&#39;interruzione di Apple {#update-bounce-qualification.md}

## Contesto

Il 26 aprile 2021, un problema globale in Apple ha causato la mancata ricezione di alcuni messaggi e-mail inviati a indirizzi e-mail validi di Apple come indirizzi e-mail non validi da parte dei server Apple, con la seguente risposta di mancato recapito: &quot;550 5.1.1 &#39;indirizzo e-mail&#39;: ricerca utente riuscita, ma nessun record utente trovato.&quot;

Questo problema si è verificato il 26/4 e si è protratto dalle 7.00 alle 13.00 CET.

>[!NOTE]
>
>Puoi controllare il dashboard di stato del sistema di Apple in [questa pagina](https://www.apple.com/support/systemstatus/).

In caso di interruzione di un ISP, le e-mail inviate tramite Campaign non possono essere consegnate correttamente al destinatario: verranno contrassegnate erroneamente come mancate consegne.

In base alla logica standard di gestione dei mancati recapiti, Adobe Campaign ha aggiunto automaticamente questi destinatari all&#39;elenco di quarantena con un&#39;impostazione **[!UICONTROL Status]** di **[!UICONTROL Quarantine]**. Per risolvere questo problema, devi aggiornare la tabella di quarantena in Campaign trovando e rimuovendo questi destinatari o modificando i loro **[!UICONTROL Status]** in **[!UICONTROL Valid]** in modo che il flusso di lavoro di pulizia notturna li rimuova.

Per trovare i destinatari interessati da questo problema o nel caso in cui questo si verifichi nuovamente con un altro ISP, consulta le istruzioni di seguito.

## Processo di aggiornamento

Dovrai eseguire una query sulla tabella di quarantena per filtrare tutti i destinatari di Apple - inclusi, @icloud.com, @me.com, @mac.com - che sono stati potenzialmente interessati dall’interruzione, in modo che possano essere rimossi dall’elenco di quarantena e inclusi nelle consegne e-mail future di Campaign.

In base alla tempistica dell’incidente, di seguito sono riportate le linee guida consigliate per questa query.

>[!IMPORTANT]
>
>Queste date/ore si basano sul fuso orario standard orientale (EST). Effettua le regolazioni in base al fuso orario dell’istanza.

* Per le istanze di Campaign con informazioni di risposta SMTP non recapitate nel campo **[!UICONTROL Error text]** dell’elenco di quarantena:

   * **Testo di errore (testo di quarantena)** contiene &quot;ricerca utente completata ma nessun record utente trovato&quot; E **Testo di errore (testo di quarantena)** contiene &quot;support.apple.com&quot;
   * **Aggiorna stato (@lastModified)** il 4/26/2021 o dopo il 07:00:00 AM
   * **Aggiorna stato (@lastModified)** entro il 4/26/2021 01:00:00 PM

* Per le istanze di Campaign con informazioni sulle regole e-mail in entrata nel campo **[!UICONTROL Error text]** dell’elenco di quarantena:

   * **Testo di errore (testo di quarantena)** contiene &quot;Momen_Code10_InvalidRecipient&quot;
   * **Dominio e-mail (@domain)** uguale a icloud.com OPPURE **Dominio e-mail (@domain)** uguale a me.com OPPURE **Dominio e-mail (@domain)** uguale a mac.com
   * **Aggiorna stato (@lastModified)** il 4/26/2021 o dopo il 07:00:00 AM
   * **Aggiorna stato (@lastModified)** entro il 4/26/2021 01:00:00 PM

Una volta ottenuto l&#39;elenco dei destinatari interessati, è possibile impostarli sullo stato **[!UICONTROL Valid]** in modo che vengano rimossi dall&#39;elenco di quarantena dal flusso di lavoro **[!UICONTROL Database cleanup]** oppure eliminarli dalla tabella.

**Argomenti correlati:**
* [Errori di consegna](understanding-delivery-failures.md)
* [Qualificazione di mail non recapitate](understanding-delivery-failures.md#bounce-mail-qualification)
