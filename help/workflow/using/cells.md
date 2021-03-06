---
product: campaign
title: Celle
description: Celle
feature: Workflows, Targeting Activity
exl-id: 7b562dba-7e4b-40a7-91db-7b9379de44ca
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 8%

---

# Celle{#cells}

![](../../assets/v7-only.svg)

La **[!UICONTROL Cells]** L’attività fornisce una visualizzazione dei vari sottoinsiemi sotto forma di colonne di dati. Semplifica la manipolazione dei sottoinsiemi ed è anche progettato per incoraggiare le possibilità di personalizzazione.

![](assets/wf_split_cells.png)

Puoi configurare questa attività per immettere parametri specifici in base alle esigenze degli utenti. Per impostazione predefinita, il dettaglio di ciascun sottoinsieme è descritto in una finestra dedicata tramite la **[!UICONTROL Selection]** e **[!UICONTROL Advanced]** schede. Nell’esempio seguente, il modulo è stato modificato: a **[!UICONTROL Data]** è stata aggiunta una scheda per abilitare l’associazione di un’offerta e un livello di priorità per ciascun sottoinsieme.

![](assets/wf_split_cells_with_customization.png)

Per questa configurazione, sono state aggiunte le seguenti informazioni al modulo del flusso di lavoro (nel **[!UICONTROL Administration > Configurations > Input forms]** nodo della struttura di Adobe Campaign):

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

La personalizzazione dei moduli di ingresso in Adobe Campaign è riservata agli utenti esperti. Per ulteriori informazioni, consulta questa [sezione](../../configuration/using/identifying-a-form.md).
