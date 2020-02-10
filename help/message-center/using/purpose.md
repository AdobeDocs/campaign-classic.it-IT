---
title: Finalità
seo-title: Finalità
description: Finalità
seo-description: null
page-status-flag: never-activated
uuid: 4452d839-318a-49d8-8abb-4ba04c803e9f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: use-case
discoiquuid: 7b8ab9d6-e47e-46d8-99df-da793486654c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Finalità{#purpose}

Lo scopo di questo caso d’uso è quello di aggiungere al volo allegati e-mail a messaggi in uscita.

In questo scenario, vedremo come inviare e-mail transazionali con allegati individuali e personalizzati. Gli allegati non verranno precaricati sul server di messaggistica transazionali ma generati al momento.

Quando acquisite informazioni sui clienti o informazioni dettagliate, potrebbe essere necessario inviarle nuovamente al cliente al termine del processo, ad esempio in un file PDF allegato a un messaggio e-mail. Di seguito sono riportati i passaggi generali di questo scenario.

1. Il cliente accede al sito Web e trova un prodotto che desidera acquistare.
1. Il cliente seleziona il prodotto e personalizza alcune opzioni.
1. Il cliente completa la transazione.
1. Al cliente viene inviato un messaggio e-mail di conferma della transazione. Non vogliamo inviare informazioni PII (Personally Identifiable Information) nell&#39;e-mail per generare un PDF protetto e allegarlo all&#39;e-mail.
1. Il cliente riceve l&#39;e-mail e il relativo allegato contenente tutti i dati necessari.

In questo scenario, gli allegati non vengono pre-creati ma aggiunti al momento dell&#39;invio delle e-mail in uscita. Consente inoltre di personalizzare il contenuto dell&#39;allegato. Inoltre, se l&#39;allegato è associato a una transazione (come nell&#39;esempio precedente), potrebbe essere necessario che contenga dati dinamici generati durante il processo del cliente. In questo modo, anche i PDF allegati possono essere protetti in modo ottimale e possono essere cifrati e inviati tramite HTTPS.
