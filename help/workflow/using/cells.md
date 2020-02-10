---
title: Celle
seo-title: Celle
description: Celle
seo-description: null
page-status-flag: never-activated
uuid: 1b18928f-04e1-4268-ab8e-ff74d78599de
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: f7187d42-56e9-4681-b172-22abd43ecd29
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Celle{#cells}

L&#39; **[!UICONTROL Cells]** attività fornisce una visualizzazione dei vari sottoinsiemi sotto forma di colonne di dati. Facilita la manipolazione di sottoinsiemi ed è anche progettato per incoraggiare le possibilità di personalizzazione.

![](assets/wf_split_cells.png)

Questa attività può essere configurata per immettere parametri specifici in base alle esigenze dell&#39;utente. Per impostazione predefinita, il dettaglio di ciascun sottoinsieme è dettagliato in una finestra dedicata tramite le **[!UICONTROL Selection]** e **[!UICONTROL Advanced]** le schede. Nell&#39;esempio seguente, il modulo è stato modificato: è stata aggiunta una **[!UICONTROL Data]** scheda per abilitare l&#39;associazione di un&#39;offerta e un livello di priorità per ciascun sottoinsieme.

![](assets/wf_split_cells_with_customization.png)

Per questa configurazione, al modulo del flusso di lavoro (nel **[!UICONTROL Administration > Configurations > Input forms]** nodo della struttura di Adobe Campaign) sono state aggiunte le seguenti informazioni:

```
<container img="nms:miniatures/mini-enrich.png" label="Data">
                <input xpath="@code"/>
                <container xpath="select/node[@alias='@numTest']">
                  <input alwaysActive="true" expr="'long'" type="expr" xpath="@type"/>
                  <input alwaysActive="true" expr="'Priority'" type="expr" xpath="@label"/>
                  <input label="Priority" maxValue="12" minValue="0" type="number"
                         xpath="@value" xpathEditFromType="@type"/>
                </container>
                <container xpath="select/node[@alias='@test']">
                  <input alwaysActive="true" expr="'string'" type="expr" xpath="@type"/>
                  <input alwaysActive="true" expr="'Identifier'" type="expr" xpath="@label"/>
                  <input label="Cell identifier" xpath="@value"/>
                </container>
                <container xpath="select/node[@alias='linkTest']">
                  <input alwaysActive="true" expr="'link'" type="expr" xpath="@type"/>
                  <input alwaysActive="true" expr="'nms:offer'" type="expr" xpath="@dataType"/>
                  <input alwaysActive="true" expr="'Offre'" type="expr" xpath="@label"/>
                  <input computeStringAlias="@valueLabel" label="Offers" notifyPathList="@_cs|@valueLabel"
                         schema="nms:offer" type="linkEdit" xpath="@value"/>
                </container>
```

La personalizzazione dei moduli di partecipazione in Adobe Campaign è riservata agli utenti esperti. For more on this, refer to this [section](../../configuration/using/identifying-a-form.md).
