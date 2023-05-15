---
product: campaign
title: Aggiornare la qualifica di mancato recapito dopo un’interruzione del servizio ISP
description: Scopri come aggiornare la qualificazione dei messaggi non recapitati dopo un’interruzione dell’ISP
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Deliverability
hide: true
hidefromtoc: true
exl-id: 7a9afe0a-0219-40f1-9fe2-6374db8d555c
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 4%

---

# Aggiornare i mancati recapiti permanenti errati dopo un’interruzione del servizio ISP {#update-bounces}



## Contesto{#update-bounce-context}

In caso di interruzione di un ISP, le e-mail inviate tramite Campaign non possono essere recapitate correttamente al destinatario: queste e-mail verranno erroneamente contrassegnate come messaggi non recapitati.

I problemi globali ad Apple o Gmail, ad esempio, possono causare il mancato recapito di alcuni messaggi e-mail inviati a indirizzi e-mail Apple o Gmail validi, in quanto gli indirizzi e-mail non validi dai server ISP con le seguenti risposte non recapitate:

* &quot;550 5.1.1 &#39;indirizzo email&#39;: ricerca utente riuscita ma nessun record utente trovato.&quot;

* &quot;550 destinatario &#39;email&#39; rifiutato&quot;

Nota che se il differimento viene rimbalzato con il messaggio &quot;452 azione richiesta interrotta: riprova più tardi&quot; vengono osservati, vengono automaticamente ritentati e non sono necessarie azioni. Dovrebbero migliorare man mano che l&#39;ISP recupera la piena capacità.

>[!NOTE]
>
>Puoi controllare il dashboard di stato del sistema di Apple su [questa pagina](https://www.apple.com/support/systemstatus/){_blank}.
>
>Puoi controllare il dashboard di stato di Google Workspace su [questa pagina](https://www.google.com/appsstatus#hl=en&amp;v=status){_blank}.

## Impatto{#update-bounce-impact}

In caso di interruzione di un ISP, le e-mail inviate tramite Campaign non possono essere recapitate correttamente al destinatario: queste e-mail verranno erroneamente contrassegnate come messaggi non recapitati.

Per logica standard di gestione dei messaggi non recapitati, Adobe Campaign ha aggiunto automaticamente questi destinatari all’elenco di quarantena con un **[!UICONTROL Status]** definizione **[!UICONTROL Quarantine]**. Per correggere questo problema, devi aggiornare la tabella di quarantena in Campaign trovando e rimuovendo questi destinatari o modificando i relativi **[!UICONTROL Status]** a **[!UICONTROL Valid]** in modo che il flusso di lavoro di pulizia notturna li rimuova.

Per trovare i destinatari interessati da questo problema, consulta le istruzioni riportate di seguito.

## Processo di aggiornamento{#update-bounce-update}

Devi eseguire una query sulla tabella di quarantena per filtrare tutti i destinatari interessati, ad esempio per Apple, gli indirizzi che includono @icloud.com, @me.com, @mac.com, che sono stati potenzialmente interessati dall’interruzione, in modo che possano essere rimossi dall’elenco di quarantena e inclusi nelle future consegne e-mail di Campaign.

In base al calendario dell&#39;incidente e dell&#39;ISP, di seguito sono riportate le linee guida consigliate per questa query.

* Per gli ambienti Campaign con informazioni sulla regola e-mail in entrata nel **[!UICONTROL Error text]** campo dell’elenco di quarantena:

   * **Testo di errore (testo di quarantena)** contiene &quot;Momen_Code10_InvalidRecipient&quot;
   * **Dominio e-mail (@dominio)** uguale a dominio1.com OR **Dominio e-mail (@dominio)** uguale a domain2.com OR **Dominio e-mail (@dominio)** uguale a domain3.com
   * **Stato aggiornamento (@lastModified)** su o dopo MM/GG/AAAA HH:MM:SS AM
   * **Stato aggiornamento (@lastModified)** su o prima MM/GG/AAAA HH:MM:PM SS

* Per gli ambienti Campaign con informazioni sulla risposta non recapitata SMTP nel **[!UICONTROL Error text]** campo dell’elenco di quarantena:

   * **Testo di errore (testo di quarantena)** contiene &quot;550-5.1.1&quot; E **Testo di errore (testo di quarantena)** contiene &quot;support.ISP.com&quot;

      dove &quot;support.ISP.com&quot; può essere: &quot;support.apple.com&quot; o &quot;support.google.com&quot; per esempio

   * **Stato aggiornamento (@lastModified)** su o dopo MM/GG/AAAA HH:MM:SS AM
   * **Stato aggiornamento (@lastModified)** su o prima MM/GG/AAAA HH:MM:PM SS


Una volta visualizzato l’elenco dei destinatari interessati, puoi impostarli su uno stato **[!UICONTROL Valid]** in modo che vengano rimosse dall&#39;elenco di quarantena **[!UICONTROL Database cleanup]** oppure eliminali dalla tabella.

**Argomenti correlati:**
* [Comprendere gli errori di consegna](understanding-delivery-failures.md)
* [Qualificazione di mail non recapitate](understanding-delivery-failures.md#bounce-mail-qualification)
