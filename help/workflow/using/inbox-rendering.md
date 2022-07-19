---
product: campaign
title: Casella in entrata - Flusso di lavoro tecnico di rendering
description: Questa sezione descrive il flusso di lavoro tecnico installato con il pacchetto di rendering della casella in entrata
feature: Workflows, Inbox Rendering
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '75'
ht-degree: 2%

---


# Rendering della casella in entrata (IR){#inbox-rendering}

![](../../assets/v7-only.svg)

Il flusso di lavoro descritto di seguito è installato con **Rendering della casella in entrata (IR)** modulo per impostazione predefinita. Per ulteriori informazioni sul rendering della casella in entrata, consulta questo [sezione](../../delivery/using/inbox-rendering.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etichetta</strong><br /> </td> 
   <td> <strong>Nome interno</strong><br /> </td> 
   <td> <strong>Descrizione</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Aggiorna la rete di seed per il rendering della casella in entrata</strong><br /> </td> 
   <td> <span class="uicontrol">updateRenderingSeeds</span> <br /> </td> 
   <td> Questo flusso di lavoro aggiorna gli indirizzi e-mail utilizzati per il rendering della casella in entrata e funziona solo se la porta HTTPS è aperta per <strong>https://deliverability-app.neolane.net/deliverability</strong>.<br /> </td> 
  </tr> 
 </tbody> 
</table>

