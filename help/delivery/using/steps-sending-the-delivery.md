---
product: campaign
title: Configurare e inviare la consegna
description: Scopri come configurare e inviare la consegna
feature: Channel Configuration
role: User
hide: true
exl-id: 0411686e-4f13-401e-9333-e14b05ebe9cd
TQID: 'https://experienceleague.adobe.com/-Wh-pHFGE1kTId3t6g7wVJFfSvh2W5ERHi2K5-0Ohdw'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
    internal-label: Campaigns
  - id: b631758a-142d-425f-b9aa-f756d85cb979
    internal-label: Campaign Email Designer
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
    internal-label: Prepare and test messages
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
    internal-label: Email messaging
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
    internal-label: Email design
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
    internal-label: A/B testing
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
    internal-label: Manage deliverability
  - id: b4ecd69f-2adf-4219-bc47-c9cd9a53c118
    internal-label: Channel configuration
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
source-git-commit: d7e5f68c0d2e0b94fd5cfdf2981bed29f33d9f62
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 24%
---
# Configurare e inviare la consegna {#configuring-and-sending-the-delivery}

Questa pagina descrive le impostazioni di invio della consegna specifiche per le installazioni on-premise e ibride di Campaign Classic v7.

Nell’ambito della transizione da Campaign v7 a v8, il set di documentazione di Campaign Classic è stato razionalizzato e riorganizzato. Le funzioni comuni sono ora disponibili esclusivamente nel set di documentazione di Campaign v8. Per ulteriori informazioni sulle impostazioni di invio della consegna, consulta la [documentazione di Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/validate/configure-and-send){target=_blank}.

[![immagine](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/validate/configure-and-send){target=_blank}

## Parametri aggiuntivi della consegna {#delivery-additiona-parameters}

Prima di inviare la consegna, puoi definire i parametri di invio nelle proprietà di consegna tramite la scheda **[!UICONTROL Delivery]**.

* **[!UICONTROL Test SMTP delivery]**: utilizzare questa opzione per verificare l&#39;invio tramite SMTP. La consegna viene elaborata fino alla connessione al server SMTP, ma non viene inviata: per ogni destinatario della consegna, Campaign si connette al server del provider SMTP, esegue il comando SMTP RCPT TO e chiude la connessione prima del comando SMTP DATA.

  >[!NOTE]
  >
  >* Questa opzione non deve essere impostata nel mid-sourcing.
  >
  >* Ulteriori informazioni sulla configurazione del server SMTP, in [questa sezione](../../installation/using/configure-delivery-settings.md).

## Configurare nuovi tentativi {#configuring-retries}

>[!IMPORTANT]
>
>Per le installazioni in hosting o ibride, se hai eseguito l&#39;aggiornamento all&#39;[MTA avanzato](sending-with-enhanced-mta.md), le impostazioni dei nuovi tentativi nella consegna non vengono più utilizzate da Campaign. I nuovi tentativi di mancato recapito non permanenti e il periodo di tempo che intercorre tra di essi sono determinati dall’MTA avanzato in base al tipo e alla gravità delle risposte di mancato recapito provenienti dal dominio e-mail del messaggio.

Per le installazioni on-premise e le installazioni in hosting/ibride che utilizzano l’MTA di Campaign legacy, la sezione centrale della scheda **[!UICONTROL Delivery]** per i parametri di consegna indica quanti tentativi devono essere eseguiti il giorno successivo alla consegna e il ritardo minimo tra i nuovi tentativi.

![](assets/s_ncs_user_wizard_retry_param.png)

Per impostazione predefinita, per il primo giorno della consegna sono pianificati cinque nuovi tentativi con un intervallo minimo di un’ora distribuiti nelle 24 ore del giorno. Un nuovo tentativo al giorno è programmato dopo tale e fino alla scadenza della consegna, definita nella scheda **[!UICONTROL Validity]**. Consulta [Definire il periodo di validità](#defining-validity-period).

## Definire il periodo di validità {#defining-validity-period}

Una volta avviata la consegna, i messaggi (ed eventuali nuovi tentativi) possono essere inviati fino alla scadenza della consegna. Questo è indicato nelle proprietà di consegna tramite la scheda **[!UICONTROL Validity]**.

![](assets/s_ncs_user_email_del_valid_period.png)

* Il campo **[!UICONTROL Delivery duration]** consente di immettere il limite per i nuovi tentativi di consegna globali. Questo significa che Adobe Campaign invia i messaggi a partire dalla data di inizio e quindi, per i messaggi che restituiscono un errore, vengono eseguiti nuovi tentativi regolari e configurabili fino al raggiungimento del limite di validità.

  >[!IMPORTANT]
  >
  >Per le installazioni in hosting o ibride, se hai effettuato l&#39;aggiornamento all&#39;[MTA avanzato](sending-with-enhanced-mta.md), l&#39;impostazione **[!UICONTROL Delivery duration]** nelle consegne e-mail di Campaign verrà utilizzata solo se impostata su **3,5 giorni o meno**. Se definisci un valore superiore a 3,5 giorni, questo non verrà preso in considerazione.

* **Limite di validità delle risorse**: il campo **[!UICONTROL Validity limit]** viene utilizzato per le risorse caricate, principalmente per la pagina speculare e per le immagini. Le risorse presenti in questa pagina sono valide per un periodo di tempo limitato (per risparmiare spazio su disco).

  I valori in questo campo possono essere espressi nelle seguenti unità: **s** per secondi, **m** per minuti, **h** per ore, **d** per giorni (impostazione predefinita), **y** per anni.
