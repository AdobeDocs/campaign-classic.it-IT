---
product: campaign
title: Creare e gestire gruppi di operatori
description: Scopri come concedere l’accesso ai gruppi di operatori
badge: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
feature: Access Management, Permissions
role: User, Admin
level: Beginner
exl-id: d5833d3d-e8ef-4f2b-8084-4ba825c79525
TQID: https://experienceleague.adobe.com/FZhH7zDL3g3tG8Ar40XJQWE-2O9Rs5-KD-NliQ6wH3M
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616aid: c5474392-5419-4296-9e41-f6f4ce4f6e9b
subfeature_v2: id: e3988c18-3cfa-4f16-b812-ac2d2b1056faid: efa38731-2723-4334-8d8b-a778af834835
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
level_v2: id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: e0eb8757-182f-49f3-94a4-1587d16f5094id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 589
ht-degree: 4%

---

# Creare e gestire gruppi di operatori {#operator-groups}

>[!NOTE]
>
>Queste procedure si applicano solo agli operatori che si connettono a Campaign con l&#39;**autenticazione nativa legacy**. A partire da Campaign Classic v7.3.1, tutti gli operatori devono utilizzare [Adobe Identity Management System (IMS)](https://helpx.adobe.com/it/enterprise/using/identity.html){target="_blank"} per connettersi a Campaign. [Ulteriori informazioni](../../technotes/using/migrate-users-to-ims.md)
>
>Quando ci si connette a Campaign con il tuo Adobe ID, la seguente sezione non è più applicabile. Scopri come impostare le autorizzazioni con Adobe IMS nella [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/gs-permissions.html?lang=it){target="_blank"}.

I gruppi di operatori vengono creati tramite il nodo **[!UICONTROL Administration > Access management > Operator groups]** nella struttura.

## Crea un nuovo gruppo di operatori {#creating-a-new-operator-group}

Per creare un nuovo gruppo di operatori, attieniti alla seguente procedura:

1. Fare clic sul pulsante **[!UICONTROL New]** a destra dell&#39;elenco dei gruppi oppure fare clic con il pulsante destro del mouse sull&#39;elenco e scegliere **[!UICONTROL New]**.
1. Nella finestra inferiore della sezione, dalla scheda **[!UICONTROL General]**, immettere il nome e la descrizione del gruppo nei campi corrispondenti.

   ![](assets/s_ncs_user_create_operator_gp.png)

1. Fare clic sulla scheda **[!UICONTROL Content]** per definire le autorizzazioni per questo gruppo.
1. Fare clic sul pulsante **[!UICONTROL Add]** per selezionare un diritto designato o un operatore da associare al gruppo.
1. Fare clic sull&#39;elenco a discesa o sulla cartella a destra del campo **[!UICONTROL Folder]** per individuare i diritti o gli operatori designati da associare al gruppo.
1. Selezionare i diritti o gli operatori da aggiungere e fare clic su **[!UICONTROL OK]** per convalidare.

   ![](assets/s_ncs_user_create_operator_gp03.png)

   Ripeti questa operazione per aggiungere altri diritti o operatori.

1. Fare clic sul pulsante **[!UICONTROL Save]** per aggiungere il gruppo all&#39;elenco.

## Gruppi predefiniti {#default-groups}

I gruppi di operatori predefiniti sono:

1. **[!UICONTROL Administrator]**

   Gli operatori di questo gruppo hanno accesso completo all’istanza. Gli amministratori sono utenti che possono accedere alle parti più tecniche dell’interfaccia. Hanno il ruolo **[!UICONTROL Administration]** e si accertano che la piattaforma sia configurata.

   Questo gruppo contiene i seguenti diritti denominati:

   * **[!UICONTROL ADMINISTRATION]**: diritto di eseguire/creare/modificare/eliminare qualsiasi oggetto come flusso di lavoro, consegna, script e così via.

1. **[!UICONTROL Delivery operators]**

   Gli operatori di questo gruppo sono responsabili della gestione delle consegne: consentono l’accesso alle risorse principali necessarie per la creazione e la preparazione delle consegne (tipologie di campagne, mappature di consegna, modelli predefiniti, blocchi di personalizzazione, ecc.).

   Questo gruppo contiene i seguenti diritti denominati:

   * **[!UICONTROL PREPARE DELIVERIES]**: diritto di creare, modificare e avviare l&#39;analisi della consegna,
   * **[!UICONTROL START DELIVERIES]**: diritto di approvare le consegne analizzate in precedenza.

1. **[!UICONTROL Campaign managers]**

   Gli operatori di questo gruppo possono gestire le campagne di marketing: ti consente di accedere agli oggetti collegati alle campagne (piani, programmi, flussi di lavoro, budget, ecc.) nel framework di **[!UICONTROL Campaign]** (modulo Adobe Campaign opzionale).

   Questo gruppo contiene i seguenti diritti denominati:

   * **[!UICONTROL INSERT FOLDERS]**: diritto di inserire cartelle nella struttura Adobe Campaign (a condizione di disporre dei diritti di modifica per i rami interessati),
   * **[!UICONTROL WORKFLOW]**: diritto di utilizzare i flussi di lavoro.

   >[!NOTE]
   >
   >Questo gruppo non consente agli operatori di avviare le consegne.

1. **[!UICONTROL Content contributors]**

   Gli operatori di questo gruppo possono accedere alle cartelle dei contenuti nel framework di **[!UICONTROL Content management]** (modulo Adobe Campaign facoltativo). Questo gruppo non concede alcun diritto aggiuntivo.

1. **[!UICONTROL Access to reports]**

   Questo gruppo è riservato agli operatori esterni, per abilitare le icone Report, Schedule e Forum nel Dashboard di Campaign per un operatore specifico.

1. **[!UICONTROL Workflow execution]**

   Questo gruppo ti consente di assegnare agli operatori il diritto di gestire flussi di lavoro non correlati alle campagne.

1. **[!UICONTROL Workflow supervisors]**

   Gli operatori di questo gruppo ricevono una notifica e-mail in caso di avvisi relativi ai flussi di lavoro delle campagne.

1. Gestione locale/centrale

   Questi gruppi ti consentono di utilizzare **[!UICONTROL Distributed marketing]** (modulo Adobe Campaign facoltativo).

1. **[!UICONTROL Offer managers]**

   Gli operatori di questo gruppo possono creare e gestire le offerte. Per ulteriori informazioni, consulta questa [pagina](../../interaction/using/operator-profiles.md).
Questo gruppo contiene i seguenti diritti denominati:

   * **[!UICONTROL INSERT FOLDERS]**: diritto di inserire cartelle nella struttura Adobe Campaign (a condizione di disporre dei diritti di modifica per i rami interessati),
   * **[!UICONTROL EDIT FOLDERS]**: diritto di modificare le proprietà della cartella come nome interno, etichetta, immagine associata, ordine delle sottocartelle e così via.
