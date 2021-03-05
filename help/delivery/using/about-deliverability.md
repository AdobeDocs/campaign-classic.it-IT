---
solution: Campaign Classic
product: campaign
title: Informazioni sul recapito messaggi in Campaign
description: Scopri le best practice per il recapito messaggi
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 87028ec81a8cae6793d45d7c840511b59cd0287c
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---


# Informazioni sul recapito messaggi{#about-deliverability}

**** Il recapito messaggi consiste nel misurare il successo delle campagne che raggiungono la casella in entrata dei destinatari senza rimbalzare o contrassegnare come spam.

Adobe Campaign offre un certo numero di strumenti per monitorare le prestazioni di recapito messaggi della piattaforma. Questa sezione evidenzia anche i principi principali da tenere a mente durante la gestione e l’ottimizzazione del recapito messaggi.

## Configurazione {#configuration}

Questa funzione è disponibile tramite un pacchetto dedicato in Adobe Campaign. Per utilizzarlo, è necessario installare questo pacchetto. Al termine, riavvia il server per tenere conto del pacchetto.
* Per i client in hosting e ibridi, il **monitoraggio del recapito** è configurato nella tua istanza dal supporto tecnico e dai consulenti Adobe. Per ulteriori informazioni, contatta il tuo account executive di Adobe.

* Per le installazioni on-premise, devi installare il pacchetto **[!UICONTROL Deliverability monitoring (Email Deliverability)]** tramite il menu **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** . Per ulteriori informazioni, consulta [Installazione dei pacchetti incorporati di Campaign](../../installation/using/installing-campaign-standard-packages.md).

In Adobe Campaign, il **monitoraggio del recapito** è gestito dal flusso di lavoro **[!UICONTROL Refresh for deliverability]**. È installato per impostazione predefinita su tutte le istanze e ti consente di inizializzare l’elenco delle regole di qualifica della posta non recapitata, l’elenco dei domini e l’elenco delle MX. Una volta installato il pacchetto **[!UICONTROL Deliverability monitoring (Email Deliverability)]**, questo flusso di lavoro viene eseguito ogni notte per aggiornare regolarmente l’elenco delle regole e consente di gestire attivamente il recapito messaggi della piattaforma.

## Sfondo {#background}

La consegna delle e-mail rappresenta una sfida importante per gli addetti al marketing, che inviino poche migliaia di messaggi o diversi miliardi. Un messaggio su cinque non raggiunge mai la casella in entrata o il destinatario desiderato.

Una volta relegata come &quot;problema tecnico&quot; per il reparto IT, il recapito messaggi e-mail continua a crescere nell’agenda di marketing. Questo perché gli esperti di marketing esperti riconoscono che, sebbene molti dei suoi elementi siano di natura tecnica, il recapito messaggi è in definitiva un problema aziendale con implicazioni significative sul fatturato.

Considera il funnel di e-mail marketing. Il recapito di messaggi determina il numero di messaggi ricevuti, che a sua volta influisce su ogni fase successiva del funnel. Il minor numero di e-mail ricevute si traduce in meno aperture, meno clic e meno conversioni. **Per le aziende con un grande database, la differenza tra la media e la grande consegna potrebbe letteralmente significare tra centinaia di migliaia e milioni di dollari di ricavi.**

![](assets/deliverability_overview_1.png)

Impostando la consegna media (80%), gli addetti al marketing stanno lasciando sul tavolo conversioni significative - e dollari -.

Cos’è esattamente il recapito messaggi e-mail? E in che modo gli esperti di marketing possono migliorare i tassi di consegna per ampliare la bocca del funnel e ottenere più risultati dalle loro campagne e-mail?

Il recapito messaggi e-mail si riferisce al set di caratteristiche che determinano la capacità di un messaggio di raggiungere la destinazione, tramite un indirizzo e-mail personale, in un breve periodo di tempo e con la qualità prevista in termini di contenuto e formato. Queste caratteristiche rientrano in quattro categorie principali: qualità dei dati, messaggi e contenuti, infrastruttura di invio e reputazione. Insieme, costituiscono la base di un programma di recapito messaggi e-mail di successo. Questa panoramica illustra i quattro principi fondamentali del successo della consegna delle e-mail e offre le best practice per raggiungere la casella in entrata e incrementare i ricavi derivanti dai programmi di marketing per e-mail.

<!--![](assets/deliverability_overview_2.png)-->
