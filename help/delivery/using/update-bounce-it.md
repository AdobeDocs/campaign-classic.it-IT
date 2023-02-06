---
product: campaign
title: Aggiornamento qualificazione rimbalzo dopo l'interruzione online di Italia
description: Scopri come aggiornare la qualifica di rimbalzo dopo Italia Online outage
feature: Deliverability
hide: true
hidefromtow: true
source-git-commit: 3cf6ffb2b69d44b56615492dd9db8965ae3cf4e1
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# Aggiorna non corretti rimbalzi hard dopo l&#39;interruzione online di Italia {#update-bounce-italia}

![](../../assets/common.svg)

## Contesto{#outage-context}

Dal 22 gennaio (ora locale), Italia Online ha subito un&#39;interruzione che ha causato diversi ritardi e ha rifiutato le e-mail. Il servizio ha iniziato a riprendere con capacità limitata il 26 gennaio.

I domini interessati sono: **libero.it**, **virgilio.it**, **inwind.it**, **iol.it** e **blu.it**.

Questo problema si è verificato dal 22/01/2023 al 26/1/2023, ma la maggior parte delle quarantene erroneamente è avvenuta il 26 gennaio.

Ulteriori informazioni nella comunicazione ufficiale [qui](https://tecnologia.libero.it/avviato-il-ritorno-online-di-libero-mail-e-virgilio-mail-66832){_blank}.


## Impatto{#outage-impact}

In caso di interruzione di un ISP, le e-mail inviate tramite Campaign non possono essere recapitate correttamente al destinatario: queste e-mail verranno erroneamente contrassegnate come messaggi non recapitati. Questo non ha solo un impatto sull&#39;Adobe, ma tutti quelli che cercano di ottenere email inviate a Italia Online.

I sintomi sono:

* **Rimbalzi differiti** con il messaggio `452 requested action aborted: try again later` vengono osservati, vengono automaticamente ritentati e non sono necessarie azioni. Dovrebbero migliorare man mano che l&#39;ISP recupera la piena capacità.

* **Rimbalzi netti** con il messaggio `550 <email address> recipient rejected` sono stati restituiti dal provider di servizi Internet il 26 gennaio, tra le 8.00 e le 2.00 ora locale, per impedire ai mittenti di continuare a sovraccaricare i propri server. Come confermato dal postmaster online Italia, questi non sono veri e propri rimbalzi duri, quindi si consiglia di non mettere in quarantena tutti gli indirizzi e-mail che sono stati esclusi il 26 gennaio 2023 a causa di quel messaggio.

## Processo di aggiornamento{#outage-update}

Per logica standard di gestione dei messaggi non recapitati, Adobe Campaign ha aggiunto automaticamente questi destinatari all’elenco di quarantena con un **[!UICONTROL Status]** definizione **[!UICONTROL Quarantine]**. Per correggere questo problema, devi aggiornare la tabella di quarantena in Campaign trovando e rimuovendo questi destinatari o modificando i relativi **[!UICONTROL Status]** a **[!UICONTROL Valid]** in modo che il flusso di lavoro di pulizia notturna li rimuova.

Per trovare i destinatari interessati da questo problema, o nel caso in cui si verifichi di nuovo con un altro ISP, consulta le istruzioni [in questa pagina](../../delivery/using/understanding-quarantine-management.md#unquarantine-bulk).
