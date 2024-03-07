---
product: campaign
title: Aggiornare la qualifica di mancato recapito dopo un’interruzione del servizio ISP
description: Scopri come aggiornare la qualifica di mancato recapito dopo un’interruzione del servizio ISP
badge-v7: label="v7" type="Informative" tooltip="Applicabile a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Deliverability
hide: true
hidefromtoc: true
exl-id: 7a9afe0a-0219-40f1-9fe2-6374db8d555c
source-git-commit: 209ccbcac20052826dad0c55b35173be20b10114
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 3%

---

# Aggiornare i mancati recapiti permanenti errati dopo un’interruzione del servizio ISP {#update-bounces}



## Contesto{#update-bounce-context}

In caso di interruzione di un ISP, le e-mail inviate tramite Campaign non possono essere consegnate correttamente al destinatario: verranno contrassegnate erroneamente come mancate consegne.

Ad esempio, in caso di problemi globali in Apple o Gmail, alcuni messaggi e-mail inviati a indirizzi e-mail Apple o Gmail validi possono essere erroneamente inseriti come indirizzi e-mail non validi dai server ISP, con le seguenti risposte di mancato recapito:

* &quot;550 5.1.1 &#39;indirizzo e-mail&#39;: ricerca utente completata, ma nessun record utente trovato.&quot;

* &quot;Destinatario 550 &#39;indirizzo e-mail&#39; rifiutato&quot;

Tieni presente che se si verificano dei mancati recapiti differiti con il messaggio &quot;452 richiesta azione interrotta: riprova più tardi&quot;, questi vengono ritentati automaticamente e non è necessaria alcuna azione. Dovrebbero migliorare man mano che l&#39;ISP recupera la piena capacità.

>[!NOTE]
>
>Puoi controllare il dashboard di stato del sistema di Apple su [questa pagina](https://www.apple.com/support/systemstatus/){_blank}.
>
>Puoi controllare il dashboard di stato dell’area di lavoro di Google su [questa pagina](https://www.google.com/appsstatus#hl=en&amp;v=status){_blank}.
>

## Impatto{#update-bounce-impact}

In caso di interruzione di un ISP, le e-mail inviate tramite Campaign non possono essere consegnate correttamente al destinatario: verranno contrassegnate erroneamente come mancate consegne.

In base alla logica standard di gestione dei mancati recapiti, Adobe Campaign ha aggiunto automaticamente questi destinatari all’elenco di quarantena con una **[!UICONTROL Status]** impostazione di **[!UICONTROL Quarantine]**. Per risolvere questo problema, aggiorna la tabella di quarantena in Campaign trovando e rimuovendo questi destinatari o modificando i **[!UICONTROL Status]** a **[!UICONTROL Valid]** in modo che il flusso di lavoro di pulizia notturna li rimuova.

Per trovare i destinatari interessati da questo problema, consulta le istruzioni di seguito.

## Processo di aggiornamento{#update-bounce-update}

È necessario eseguire una query sulla tabella di quarantena per filtrare tutti i destinatari interessati, ad esempio Apple, gli indirizzi che includono, @icloud.com, @me.com, @mac.com, che sono stati potenzialmente interessati dall’interruzione in modo che possano essere rimossi dall’elenco di quarantena e inclusi nelle consegne e-mail future di Campaign.

Di seguito sono riportate le linee guida consigliate per questa query in base alla tempistica dell’incidente e all’ISP.

* Per gli ambienti Campaign con informazioni sulle regole e-mail in entrata in **[!UICONTROL Error text]** campo dell’elenco di quarantena:

   * **Testo di errore (testo di quarantena)** contiene &quot;Momen_Code10_InvalidRecipient&quot;
   * **Dominio e-mail (@domain)** uguale a domain1.com OR **Dominio e-mail (@domain)** uguale a domain2.com OR **Dominio e-mail (@domain)** uguale a domain3.com
   * **Stato aggiornamento (@lastModified)** il o dopo il `MM/DD/YYYY HH:MM:SS AM`
   * **Stato aggiornamento (@lastModified)** il o prima del `MM/DD/YYYY HH:MM:SS PM`

* Per gli ambienti Campaign con informazioni sulla risposta SMTP non recapitate nella **[!UICONTROL Error text]** campo dell’elenco di quarantena:

   * **Testo di errore (testo di quarantena)** contiene &quot;550-5.1.1&quot; E **Testo di errore (testo di quarantena)** contiene &quot;support.ISP.com&quot;

     dove &quot;support.ISP.com&quot; può essere: &quot;support.apple.com&quot; o &quot;support.google.com&quot;, ad esempio

   * **Stato aggiornamento (@lastModified)** il o dopo il `MM/DD/YYYY HH:MM:SS AM`
   * **Stato aggiornamento (@lastModified)** il o prima del  `MM/DD/YYYY HH:MM:SS PM`


Dopo aver visualizzato l’elenco dei destinatari interessati, puoi impostarli sullo stato **[!UICONTROL Valid]** in modo che vengano rimossi dall’elenco di quarantena dal **[!UICONTROL Database cleanup]** oppure eliminarli dalla tabella.

**Argomenti correlati:**
* [Errori di consegna](understanding-delivery-failures.md)
* [Qualificazione di mail non recapitate](understanding-delivery-failures.md#bounce-mail-qualification)
