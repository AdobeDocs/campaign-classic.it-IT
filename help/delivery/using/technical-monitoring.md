---
title: Monitoraggio tecnico
seo-title: Monitoraggio tecnico
description: Monitoraggio tecnico
seo-description: null
page-status-flag: never-activated
uuid: 44ac7cf0-1d44-4656-b137-f3008be32e1d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 008d6a63-68cd-4e87-8adb-9642e2f9bb2a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 38700b79aeb19c75d10d2f5eb60c1efdb12e62e3

---


# Monitoraggio tecnico{#technical-monitoring}

## Rapporto di monitoraggio sulla realizzazione tecnica {#technical-deliverability-monitoring}

Il rapporto di monitoraggio della recapito tecnico viene aggiornato ogni giorno e disponibile accedendo a **[!UICONTROL Monitoring]** > **[!UICONTROL Overview]** e facendo clic sul **[!UICONTROL Technical monitoring]** collegamento dalla scheda Adobe Campaign **[!UICONTROL Home]** . Include una serie di indicatori di qualità della distribuzione per la piattaforma.

Questi indicatori vengono aggiornati ogni giorno alle 9.

>[!NOTE]
>
>Inoltre, potete ricevere un rapporto giornaliero via e-mail all&#39;indirizzo specificato. Inviaci l&#39;indirizzo e-mail richiesto tramite e-mail o tramite Adobe Campaign Extranet.

![](assets/s_tn_del_monitoring.png)

Nella relazione sono utilizzati i seguenti indicatori:

* **[!UICONTROL Reverse DNS]** :Adobe Campaign verifica se per un indirizzo IP è stato specificato un DNS inverso e che questo indichi correttamente l&#39;IP.

* **[!UICONTROL SPF]** (Framework per i criteri di invio): Meccanismo di autenticazione che consente agli ISP e ai fornitori di cassette postali di verificare se il mittente e-mail è autorizzato nel dominio di invio.

   <!--
    >[!NOTE]
    >
    >The SPF may look **[!UICONTROL Acceptable]** (instead of **[!UICONTROL Good]**) since the report is currently unable to detect the presence of a “redirect” or “include” mechanism. This bug has been submitted to Adobe Campaign R&D to be fixed. In the meantime, please feel free to add 15 points to your global score to obtain your real rating (a **[!UICONTROL Good]** one corresponds to 96 points or higher).
    -->

* **[!UICONTROL DomainKeys]** : Un servizio sviluppato da Yahoo e destinato a certificare l&#39;identità di un mittente di posta elettronica.

* **[!UICONTROL IP and RBL domain]** (Elenco buchi neri in tempo reale): Un elenco di indirizzi IP e domini contrassegnati da organizzazioni blocklist per cattiva reputazione. Questi elenchi sono gestiti da organizzazioni dedicate come Spamhaus, Spampoliziotto, SURBL/URIBL, ecc. Adobe Campaign elabora attualmente controlli rispetto agli URL che hanno un impatto significativo sulla recapito. Questi URL riflettono la reputazione dell&#39;invio e possono essere citati dagli ISP prima di accettare di ricevere le tue e-mail.

* **[!UICONTROL SNDS]** (Smart Network Data Services): Un servizio [Windows Live Hotmail anti-spam](https://sendersupport.olc.protection.outlook.com/snds/FAQ.aspx). Hotmail è l&#39;unico ISP che fornisce questo tipo di informazioni. I punteggi di riferimento sono un risultato di filtro verde, un tasso di reclamo inferiore allo 0,1% e zero spam trap.

<!--
* **[!UICONTROL Reputation Authority]**: This WatchGuard’s score is calculated in real time according to the feedback received from their network worldwide, and also from the different users who use their software.

    Administrators can use such tools to apply a first level filter on their messaging servers.
    If you click on the IP link within the technical report, it will lead you to reputationauthority.org, where you will have the possibility to clean the IP history and get a neutral score again.
    Nevertheless, this action is limited to a number of times per month.
    Please also be aware there is no support provided by WatchGuard‘s Reputation Authority (sending delisting requests is therefore useless). Otherwise, this scoring is based on the following: 
    * Message content (for example: presence of spam words). 
    * IP/Domains reputation (for example: your IPs are listed on an RBL). 
    * IP configuration (for example: IPs associated to different domains). 
    * Volumes sent by IP (for example: presence of peaks or significant variations).
    
    * **[!UICONTROL Sender Score]** : A database of reputed servers ([https://www.senderscore.org/](https://www.senderscore.org/)) issuing a score created by Return Path about your reputation. Think of it like a credit score, but for email senders.-->

<!--## Delivery Reports - Broadcast Statistics {#delivery-reports-broadcast-statistics}

Each delivery will generate a broadcast statistics report when you open a delivery in the “Deliveries List”, which includes some reputation metrics that may impact your deliverability:

![](assets/s_tn_del_monitoring.png)-->
