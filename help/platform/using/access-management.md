---
product: campaign
title: Introduzione alle autorizzazioni
description: Scopri come concedere l’accesso alle funzionalità di Campaign
badge: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
feature: Access Management, Permissions
exl-id: 9b616715-33cd-43ba-8548-8d96a179408e
source-git-commit: e1a085384fb27ec165c487c112fbc70fe9738d9e
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 5%

---

# Introduzione alle autorizzazioni{#access-management}


>[!CAUTION]
>
>A partire da Campaign Classic v7.3.1, tutti gli operatori devono utilizzare [Sistema Adobe Identity Management (IMS)](https://helpx.adobe.com/it/enterprise/using/users.html){target="_blank"} per connettersi a Campaign.
>
>Come parte degli sforzi per rafforzare la sicurezza e il processo di autenticazione, Adobe Campaign consiglia vivamente di migrare tutte le modalità di autenticazione degli operatori esistenti dall’autenticazione nativa di login/password ad Adobe Identity Management System (IMS). Scopri come eseguire la migrazione degli operatori in [questa pagina](../../technotes/using/migrate-users-to-ims.md).
> 
>Dopo questa migrazione, la sezione seguente non è più applicabile.  Scopri come impostare le autorizzazioni con Adobe IMS in [Documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/gs-permissions.html?lang=it){target="_blank"}.


Adobe Campaign ti consente di definire e gestire i diritti assegnati ai vari operatori. Si tratta di una serie di diritti e restrizioni che autorizzano o negano:

* Accesso a determinate funzionalità (tramite i diritti denominati),
* Accesso a determinati documenti,
* Creazione, modifica e/o eliminazione di record (azioni, contatti, campagne, gruppi, ecc.).

Le autorizzazioni si applicano ai profili o ai gruppi di operatori.

Sono completati da parametri di sicurezza collegati alla modalità di connessione dell’operatore ad Adobe Campaign. Per ulteriori informazioni sulle aree di protezione in [questa pagina](../../installation/using/security-zones.md).

Esistono due tipi di autorizzazioni che è possibile concedere a un utente:

* È possibile definire gruppi di operatori a cui si attribuiscono diritti, quindi associare gli operatori a uno o più gruppi. Questo consente di riutilizzare i diritti e rendere più coerenti i profili dell’operatore. Inoltre, facilita la gestione e la manutenzione dei profili. La creazione e la gestione dei gruppi sono presentate in [questa sezione](access-management-groups.md).

* Puoi attribuire i diritti denominati direttamente agli utenti, in alcuni casi per sovraccaricare i diritti allocati tramite i gruppi. Questi diritti sono presentati in [questa pagina](access-management-named-rights.md).

>[!NOTE]
>
>Prima di iniziare a definire le autorizzazioni, l’Adobe consiglia di leggere [Elenco di controllo per la configurazione della sicurezza](https://helpx.adobe.com/it/campaign/kb/acc-security.html).

Scopri come concedere l’accesso e impostare le autorizzazioni in queste sezioni:

* [Creare operatori](access-management-operators.md)

* [Definire i gruppi](access-management-groups.md)

* [Aggiungi diritti denominati](access-management-named-rights.md)

* [Gestire l’accesso alla cartella Campaign](access-management-folders.md)

* [Matrice dei diritti di accesso](access-management-named-rights.md#access-rights-matrix)


Vedi anche:

* [Gestire le autorizzazioni per i flussi di lavoro](../../workflow/using/managing-rights.md)
* [Gestire le autorizzazioni per il marketing distribuito](../../distributed/using/about-distributed-marketing.md#operators-and-entities)
* [Gestire le autorizzazioni per il modulo di interazione](../../interaction/using/operator-profiles.md)
* [Filtrare l’accesso agli schemi](../../configuration/using/filtering-schemas.md)
* [Limitazione della visualizzazione delle informazioni personali](../../configuration/using/restricting-pii-view.md)
