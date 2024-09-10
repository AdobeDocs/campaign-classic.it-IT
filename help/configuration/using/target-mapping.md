---
product: campaign
title: Mappatura del target
description: Scopri come creare una mappatura di destinazione
feature: Application Settings
role: Data Engineer, Developer
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
exl-id: 38333669-5598-4811-a121-b677c1413f56
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 2%

---

# Mappatura del target{#target-mapping}



La creazione della mappatura target è necessaria in due casi:

* se utilizzi una tabella dei destinatari diversa da quella fornita da Adobe Campaign,
* se configuri una dimensione di filtro diversa dalla dimensione di targeting standard nella schermata mappatura target.

L’assistente alla creazione della mappatura di destinazione ti aiuterà a creare tutti gli schemi necessari per utilizzare la tabella personalizzata.

## Creazione e configurazione di schemi collegati alla tabella personalizzata {#creating-and-configuring-schemas-linked-to-the-custom-table}

Prima di creare una mappatura di destinazione, sono necessarie diverse configurazioni affinché Adobe Campaign possa funzionare con un nuovo schema di dati del destinatario.

A questo scopo, esegui i seguenti passaggi:

1. Crea un nuovo schema di dati che integra i campi della tabella personalizzata che desideri utilizzare.

   Per ulteriori informazioni, consultare [Riferimento schema (xtk:srcSchema)](../../configuration/using/about-schema-reference.md).

   Nel nostro esempio, creeremo uno schema cliente, una tabella molto semplice contenente i seguenti campi: ID, nome, cognome, indirizzo e-mail, numero di telefono cellulare. L’obiettivo è quello di poter inviare avvisi e-mail o SMS alle persone memorizzate in questa tabella.

   Schema di esempio (cus:individual)

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

1. Dichiara lo schema come vista esterna utilizzando l’attributo =&quot;true&quot;. Fare riferimento a [Attributo visualizzazione](../../configuration/using/schema-characteristics.md#the-view-attribute).

   ```
    <srcSchema desc="External recipient table" namespace="cus" view="true"....>
      ...
    </srcSchema>
   ```

1. Se devi aggiungere un indirizzo di direct mailing, usa il seguente tipo di struttura:

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

1. Fare clic sul nodo **[!UICONTROL Administration > Campaign management > Target mappings]**.
1. Fai clic sul pulsante **Nuovo** per aprire l&#39;assistente alla creazione della mappatura di destinazione.
1. Immetti il campo **Label** e seleziona lo schema appena creato nel campo **Targeting dimension**.

   ![](assets/mapping_diffusion_wizard_1.png)

1. Nella finestra **Modifica moduli indirizzo**, seleziona i campi dello schema che corrispondono ai vari indirizzi di consegna. Qui è possibile mappare i campi **@email** e **@mobile**.

   ![](assets/mapping_diffusion_wizard_2.png)

1. Nella seguente finestra di **Archiviazione**, immetti il campo **Suffisso degli schemi di estensione** per differenziare i nuovi schemi dagli schemi predefiniti forniti da Adobe Campaign.

   Fai clic su **[!UICONTROL Define new additional fields]** per selezionare la dimensione di destinazione nella consegna.

   Per impostazione predefinita, la gestione delle esclusioni viene memorizzata nella stessa tabella dei messaggi.

   Se desideri configurare l&#39;archiviazione per il tracciamento collegato alla mappatura di destinazione, seleziona la casella **Genera uno schema di archiviazione per il tracciamento**.

   ![](assets/mapping_diffusion_wizard_3.png)

   >[!IMPORTANT]
   >
   >Adobe Campaign non supporta più schemi di destinatari, noti come schemi di targeting, collegati agli stessi schemi broadlog e/o trackinglog. In caso contrario, potrebbero verificarsi anomalie nella riconciliazione dei dati in seguito. Per ulteriori informazioni, consulta la pagina [Consigli e limitazioni](../../configuration/using/about-custom-recipient-table.md).

1. Nella finestra **Estensioni**, seleziona gli schemi facoltativi che desideri generare (l&#39;elenco degli schemi disponibili dipende dai moduli installati sulla piattaforma Adobe Campaign).

   ![](assets/mapping_diffusion_wizard_4.png)

1. Fai clic sul pulsante **Salva** per chiudere l&#39;assistente.

   L’assistente utilizza lo schema di inizio per creare tutti gli altri schemi necessari per il funzionamento della nuova mappatura di destinazione.

   ![](assets/mapping_schema_list.png)

## Utilizzo della mappatura target {#using-target-mapping}

Esistono due modi per utilizzare il nuovo schema come destinazione di una consegna:

* Creare uno o più modelli di consegna in base alla mappatura
* Seleziona la mappatura direttamente durante la selezione del target durante la creazione di una consegna, come illustrato di seguito:

![](assets/mapping_selection_ciblage.png)
