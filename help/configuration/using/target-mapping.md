---
title: Mappatura del target
description: Scopri come creare una mappatura di destinazione
page-status-flag: never-activated
uuid: a7dad8eb-c191-4f10-b7d8-63e0699603b7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: ff7e6f72-7605-41ee-b25a-1e4618e674d7
translation-type: tm+mt
source-git-commit: 30eaabba8962c518c734cc4e9ad27065cfe9d467
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 1%

---


# Mappatura del target{#target-mapping}

La creazione del mapping di destinazione è necessaria in due casi:

* se utilizzi una tabella di destinatari diversa da quella fornita da  Adobe Campaign,
* se configurate una dimensione di filtro diversa dalla dimensione di targeting standard nella schermata di mappatura della destinazione.

La procedura guidata per la creazione del mapping di destinazione consente di creare tutti gli schemi necessari per utilizzare la tabella personalizzata.

## Creazione e configurazione di schemi collegati alla tabella personalizzata {#creating-and-configuring-schemas-linked-to-the-custom-table}

Prima di creare una mappatura di destinazione, sono necessarie diverse configurazioni affinché  Adobe Campaign possa funzionare con un nuovo schema di dati del destinatario.

A questo scopo, eseguire i seguenti passaggi:

1. Creare un nuovo schema dati che integri i campi della tabella personalizzata che si desidera utilizzare.

   Per ulteriori informazioni, fare riferimento a Riferimento [schema (xtk:srcSchema)](../../configuration/using/about-schema-reference.md).

   Nel nostro esempio, creeremo uno schema cliente, una tabella molto semplice contenente i seguenti campi: ID, nome, cognome, indirizzo e-mail, numero di telefono cellulare. L&#39;obiettivo è quello di poter inviare avvisi via e-mail o SMS alle persone memorizzate in questa tabella.

   Schema di esempio (cus:single)

   ```
   <srcSchema name="individual" namespace="cus" label="Individuals">
     <element name="individual">
       <key name="id" internal="true">
         <keyfield xpath="@id"/>
       </key>
       <attribute name="id" type="long" length="32"/>
       <attribute name="lastName" type="string" length="100"/>
       <attribute name="firstName" type="string" length="100"/>
       <attribute name="email" type="string" length="100"/>
       <attribute name="mobile" type="string" length="100"/>
     </element>
   </srcSchema>
   ```

1. Dichiarare lo schema come visualizzazione esterna utilizzando l&#39;attributo =&quot;true&quot;. Fare riferimento a [L&#39;attributo](../../configuration/using/schema-characteristics.md#the-view-attribute)view.

   ```
    <srcSchema desc="External recipient table" namespace="cus" view="true"....>
      ...
    </srcSchema>
   ```

1. Per aggiungere un indirizzo di posta diretta, utilizzare il seguente tipo di struttura:

   ```
   <element advanced="true" name="postalAddress" template="nms:common:postalAddress">
        <attribute expr="SubString(JuxtWords(Smart([../infos/@firstname]), Upper([../infos/@name])), 1, 80)"
                   name="line1"/>
        <attribute expr="Upper([../address/@line2])" name="line2"/>
        <attribute expr="Upper([../address/@line])" name="line3"/>
        <attribute expr="Upper([../address/@line])" name="line4"/>
        <attribute expr="Upper([../address/@line])" name="line5"/>
        <attribute expr="Upper([../address/@line])" name="line6"/>
        <attribute _operation="delete" name="line7"/>
        <attribute _operation="delete" name="addrErrorCount"/>
        <attribute _operation="delete" name="addrQuality"/>
        <attribute _operation="delete" name="addrLastCheck"/>
        <element expr="@line1+'n'+@line2+'n'+@line3+'n'+@line4+'n'+@line5+'n'+@line6"
                 name="serialized"/>
        <attribute expr="AllNonNull2([../address/@line], [../infos/@name])" name="addrDefined"/>
      </element>
   ```

1. Fare clic sul **[!UICONTROL Administration > Campaign management > Target mappings]** nodo.
1. Fate clic sul pulsante **Nuovo** per aprire la procedura guidata di creazione del mapping di destinazione.
1. Immettete il campo **Etichetta** e selezionate lo schema appena creato nel campo Dimensione **** targeting.

   ![](assets/mapping_diffusion_wizard_1.png)

1. Nella finestra **Modifica moduli** indirizzo, selezionare i campi dello schema che corrispondono ai vari indirizzi di consegna. Qui è possibile mappare i campi **@email** e **@mobile** .

   ![](assets/mapping_diffusion_wizard_2.png)

1. Nella finestra **Archiviazione** seguente, immettete il **suffisso del campo degli schemi** di estensione per distinguere i nuovi schemi dagli schemi forniti da  Adobe Campaign.

   Fate clic **[!UICONTROL Define new additional fields]** per selezionare la dimensione da destinare alla consegna.

   Per impostazione predefinita, la gestione dell&#39;esclusione è memorizzata nelle stesse tabelle dei messaggi. Per configurare la memorizzazione per il tracciamento collegato alla mappatura di destinazione, selezionare la casella **Genera uno schema di archiviazione per il tracciamento** .

   ![](assets/mapping_diffusion_wizard_3.png)

   >[!IMPORTANT]
   >
   > Adobe Campaign non supporta più schemi destinatari, noti come schemi di targeting, collegati agli stessi schemi di trasmissione e/o di trackinglog. In caso contrario si verificheranno successivamente delle anomalie nella riconciliazione dei dati. Per ulteriori informazioni, consultate la pagina [Raccomandazione e limitazioni](../../configuration/using/about-custom-recipient-table.md) .

1. Nella finestra **Estensioni** , selezionate gli schemi facoltativi da generare (l&#39;elenco degli schemi disponibili dipende dai moduli installati sulla piattaforma Adobe Campaign ).

   ![](assets/mapping_diffusion_wizard_4.png)

1. Fare clic sul pulsante **Salva** per chiudere la procedura guidata.

   La procedura guidata utilizza lo schema iniziale per creare tutti gli altri schemi necessari per il funzionamento del nuovo mapping di destinazione.

   ![](assets/mapping_schema_list.png)

## Utilizzo del mapping di destinazione {#using-target-mapping}

Esistono due modi per utilizzare il nuovo schema come destinazione di una consegna:

* Creare uno o più modelli di consegna basati sulla mappatura
* Selezionate la mappatura direttamente durante la selezione di destinazione durante la creazione di una consegna, come illustrato di seguito:

![](assets/mapping_selection_ciblage.png)

**Argomento correlato**

* [Rispondere rapidamente alle richieste dei clienti per accedere ai loro dati](https://helpx.adobe.com/campaign/kb/simplifying-campaign-management-acc.html#Quicklyrespondtocustomerrequeststoaccesstheirdata)