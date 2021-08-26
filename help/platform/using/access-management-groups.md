---
product: campaign
title: Creare e gestire gruppi di operatori
description: Scopri come concedere l’accesso ai gruppi di operatori
feature: Access Management
role: User, Admin
level: Beginner
exl-id: d5833d3d-e8ef-4f2b-8084-4ba825c79525
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---

# Creare e gestire gruppi di operatori {#operator-groups}

![](../../assets/common.svg)

I gruppi di operatori vengono creati tramite il nodo **[!UICONTROL Administration > Access management > Operator groups]** nella struttura.

## Crea un nuovo gruppo di operatori {#creating-a-new-operator-group}

Per creare un nuovo gruppo di operatori, effettua le seguenti operazioni:

1. Fai clic sul pulsante **[!UICONTROL New]** a destra dell’elenco dei gruppi oppure fai clic con il pulsante destro del mouse sull’elenco e scegli **[!UICONTROL New]**.
1. Nella finestra inferiore della sezione, dalla scheda **[!UICONTROL General]**, immetti il nome e una descrizione per questo gruppo nei campi corrispondenti.

   ![](assets/s_ncs_user_create_operator_gp.png)

1. Fai clic sulla scheda **[!UICONTROL Content]** per definire le autorizzazioni per questo gruppo.
1. Fai clic sul pulsante **[!UICONTROL Add]** per selezionare un diritto designato o un operatore da associare al gruppo.
1. Fai clic sull&#39;elenco a discesa o sulla cartella a destra del campo **[!UICONTROL Folder]** per individuare i diritti o gli operatori nominati da associare a questo gruppo.
1. Seleziona i diritti o gli operatori da aggiungere e fai clic su **[!UICONTROL OK]** per convalidare.

   ![](assets/s_ncs_user_create_operator_gp03.png)

   Ripeti questa operazione per aggiungere altri diritti o operatori.

1. Fai clic sul pulsante **[!UICONTROL Save]** per aggiungere il gruppo all’elenco.

## Gruppi predefiniti {#default-groups}

I gruppi di operatori predefiniti sono:

1. **[!UICONTROL Administrator]**

   Gli operatori di questo gruppo hanno pieno accesso all’istanza. Gli amministratori sono utenti che possono accedere alle parti più tecniche dell’interfaccia. Hanno il ruolo **[!UICONTROL Administration]** e si accertano che la piattaforma sia configurata completamente.

   Questo gruppo contiene il seguente diritto denominato:

   * **[!UICONTROL ADMINISTRATION]**: diritto di eseguire/creare/modificare/eliminare qualsiasi oggetto come flusso di lavoro, consegna, script, ecc.

1. **[!UICONTROL Delivery operators]**

   Gli operatori di questo gruppo sono responsabili della gestione delle consegne: consentono di accedere alle risorse principali necessarie per creare e preparare le consegne (tipologie di campagne, mappature di consegna, modelli predefiniti, blocchi di personalizzazione, ecc.).

   Questo gruppo contiene i seguenti diritti denominati:

   * **[!UICONTROL PREPARE DELIVERIES]**: diritto di creare, modificare e avviare l’analisi della consegna,
   * **[!UICONTROL START DELIVERIES]**: diritto di approvare le consegne analizzate in precedenza.

1. **[!UICONTROL Campaign managers]**

   Gli operatori di questo gruppo possono gestire le campagne di marketing: ti consente di accedere agli oggetti collegati alle campagne (piani, programmi, flussi di lavoro, budget, ecc.) nel framework di **[!UICONTROL Campaign]** (modulo Adobe Campaign opzionale).

   Questo gruppo contiene i seguenti diritti denominati:

   * **[!UICONTROL INSERT FOLDERS]**: diritto di inserire cartelle nell’albero di Adobe Campaign (purché si disponga dei diritti di modifica per i rami interessati),
   * **[!UICONTROL WORKFLOW]**: diritto di utilizzare i flussi di lavoro.
   >[!NOTE]
   >
   >Questo gruppo non consente agli operatori di avviare le consegne.

1. **[!UICONTROL Content contributors]**

   Gli operatori di questo gruppo possono accedere alle cartelle Contenuto nel framework di **[!UICONTROL Content management]** (modulo Adobe Campaign opzionale). Questo gruppo non concede diritti aggiuntivi.

1. **[!UICONTROL Access to reports]**

   Questo gruppo è riservato agli operatori esterni per accedere ai report di consegna tramite un accesso Web.

1. **[!UICONTROL Workflow execution]**

   Questo gruppo ti consente di assegnare agli operatori il diritto di gestire flussi di lavoro non correlati alle campagne.

1. **[!UICONTROL Workflow supervisors]**

   Gli operatori di questo gruppo ricevono una notifica e-mail in caso di avvisi relativi ai flussi di lavoro delle campagne.

1. Gestione locale/centrale

   Questi gruppi consentono di utilizzare **[!UICONTROL Distributed marketing]** (modulo Adobe Campaign opzionale).

1. **[!UICONTROL Offer managers]**

   Gli operatori di questo gruppo possono creare e gestire le offerte. Per ulteriori informazioni, consulta questa [pagina](../../interaction/using/operator-profiles.md).
Questo gruppo contiene i seguenti diritti denominati:

   * **[!UICONTROL INSERT FOLDERS]**: Diritto di inserire cartelle nell&#39;albero di Adobe Campaign (purché si disponga dei diritti di modifica per i rami interessati),
   * **[!UICONTROL EDIT FOLDERS]**: Diritto di modificare le proprietà della cartella come nome interno, etichetta, immagine associata, ordine delle sottocartelle, ecc.
