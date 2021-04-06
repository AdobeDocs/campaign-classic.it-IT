---
solution: Campaign Classic
product: campaign
title: Aggiornare la qualifica di mancato recapito dopo un'interruzione dell'ISP
description: Scopri come aggiornare la qualifica del mancato recapito dopo un'interruzione dell'ISP.
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
hidefromtoc: true
translation-type: tm+mt
source-git-commit: 0c93193ff30737870803f9fb25019f3162dcc96d
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 1%

---


# Aggiornare la qualifica del mancato recapito dopo un&#39;interruzione dell&#39;ISP {#update-bounce-qualification.md}

## Contesto

In caso di interruzione di un ISP, le e-mail inviate tramite Campaign non possono essere recapitate correttamente al destinatario: queste e-mail verranno erroneamente contrassegnate come messaggi non recapitati.

Nel dicembre 2020, un problema globale a Gmail causava l’invio errato di alcuni messaggi e-mail a indirizzi e-mail Gmail validi, in quanto gli indirizzi e-mail non validi da parte dei server Gmail con la seguente risposta non recapitata: *&quot;550-5.1.1 L&#39;account e-mail che si è tentato di raggiungere non esiste.&quot;*

Google ha dichiarato che le interruzioni e le interruzioni di Gmail che hanno causato questo problema sono iniziate il 14 dicembre alle 6:55 del mattino e si sono concluse alle 6:09 del pomeriggio EST il 15 dicembre. La nostra analisi dei dati ha anche mostrato un picco molto breve in Gmail rimbalzi alle 2:06AM EST il 16 dicembre, con la maggior parte che si verifica il 15 dicembre tra le 2:00 EST e le 6:30 pm EST.

>[!NOTE]
>
>Puoi controllare il dashboard di stato di Google Workspace in [questa pagina](https://www.google.com/appsstatus#hl=en&amp;v=status).


Per logica standard di gestione dei messaggi non recapitati, Adobe Campaign ha aggiunto automaticamente questi destinatari all’elenco di quarantena con un’impostazione **[!UICONTROL Status]** di **[!UICONTROL Quarantine]**. Per correggere questo problema, devi aggiornare la tabella di quarantena in Campaign individuando e rimuovendo questi destinatari o modificando i relativi **[!UICONTROL Status]** in **[!UICONTROL Valid]** in modo che il flusso di lavoro di pulizia notturna li rimuova.

Per trovare i destinatari interessati da questo problema Gmail o nel caso in cui questo si verifichi nuovamente con un altro ISP, consulta le istruzioni riportate di seguito.

## Processo di aggiornamento

Sarà necessario eseguire una query sulla tabella di quarantena per filtrare tutti i destinatari Gmail (o altri ISP) potenzialmente interessati dall’interruzione, in modo che possano essere rimossi dall’elenco di quarantena e inclusi nelle future consegne e-mail di Campaign.

In base al calendario dell’incidente, di seguito sono riportate le linee guida consigliate per questa query.

>[!IMPORTANT]
>
>Queste date/ore si basano sul fuso orario standard orientale (EST). Modifica il fuso orario dell’istanza.

* Per le istanze Campaign con informazioni sulla risposta non recapitata SMTP nel campo **[!UICONTROL Error text]** dell’elenco di quarantena:

   * **Testo di errore (testo di quarantena)** contiene &quot;550-5.1.1 L&#39;account e-mail che hai cercato di raggiungere non esiste&quot; E il testo di  **errore (testo di quarantena)** contiene &quot;support.google.com&quot; **
   * **Stato dell&#39;aggiornamento (@lastModified)** il o dopo il 14/12/2020 6:55:00
   * **Stato dell&#39;aggiornamento (@lastModified)** il 16/12/2020 6:00:00

* Per le istanze Campaign con informazioni sulla regola e-mail in entrata nel campo **[!UICONTROL Error text]** dell’elenco di quarantena:

   * **Testo di errore (testo di quarantena)** contiene &quot;Momen_Code10_InvalidRecipient&quot;
   * **Dominio e-mail (@dominio)** uguale a &quot;gmail.com&quot; O Dominio e-mail (@dominio) uguale a &quot;googlemail.com&quot;
   * **Stato dell&#39;aggiornamento (@lastModified)** il o dopo il 14/12/2020 6:55:00
   * **Stato dell&#39;aggiornamento (@lastModified)** il 16/12/2020 6:00:00

Una volta visualizzato l’elenco dei destinatari interessati, puoi impostarli su uno stato **[!UICONTROL Valid]** in modo che vengano rimossi dall’elenco di quarantena dal flusso di lavoro **[!UICONTROL Database cleanup]** oppure eliminarli dalla tabella.

**Argomenti correlati:**
* [Comprendere gli errori di consegna](../../delivery/using/understanding-delivery-failures.md)
* [Qualificazione di mail non recapitate](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification)

