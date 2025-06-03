---
product: campaign
title: Introduzione alle autorizzazioni
description: Scopri come concedere l’accesso alle funzionalità di Campaign
badge: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
feature: Access Management, Permissions
exl-id: 9b616715-33cd-43ba-8548-8d96a179408e
source-git-commit: 42cec0e9bede94a2995a5ad442822512bda14f2b
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 6%

---

# Introduzione alle autorizzazioni{#access-management}


>[!CAUTION]
>
>A partire da Campaign Classic v7.3.1, tutti gli operatori devono utilizzare [Adobe Identity Management System (IMS)](https://helpx.adobe.com/it/enterprise/using/identity.html){target="_blank"} per connettersi a Campaign.
>
>Per rafforzare la sicurezza e il processo di autenticazione, Adobe Campaign consiglia vivamente di migrare tutte le modalità di autenticazione degli operatori esistenti dall’autenticazione nativa di login/password ad Adobe Identity Management System (IMS). Scopri come eseguire la migrazione degli operatori in [questa pagina](../../technotes/using/migrate-users-to-ims.md).
> 
>Dopo questa migrazione, tieni presente che la sezione seguente non è più applicabile.  Scopri come impostare le autorizzazioni con Adobe IMS nella [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/gs-permissions.html?lang=it){target="_blank"}.


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
> * Prima di iniziare a definire le autorizzazioni, Adobe consiglia di leggere l&#39;[elenco di controllo per la configurazione della sicurezza](https://helpx.adobe.com/it/campaign/kb/acc-security.html).
> * Per ulteriori informazioni sulle autorizzazioni, consulta la spiegazione dettagliata nella [documentazione di Campaign v8](https://experienceleague.adobe.com/it/docs/campaign/campaign-v8/admin/permissions/gs-permissions){target=_blank}.

<!--

Learn how to grant access and set up permissions in these sections:

* [Create operators](access-management-operators.md)

* [Define groups](access-management-groups.md)

* [Add Named rights](access-management-named-rights.md)

* [Manage Campaign folder access](access-management-folders.md)

* [Access rights matrix](access-management-named-rights.md#access-rights-matrix)


See also:

* [Manage permissions for workflows](../../workflow/using/managing-rights.md)
* [Manage permissions for distributed marketing](../../distributed/using/about-distributed-marketing.md#operators-and-entities)
* [Manage permissions for the interaction module](../../interaction/using/operator-profiles.md)
* [Filter access to schemas](../../configuration/using/filtering-schemas.md)
* [Restricting PI view](../../configuration/using/restricting-pii-view.md)
-->