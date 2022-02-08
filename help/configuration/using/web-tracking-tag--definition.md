---
product: campaign
title: Definire il tag di web tracking
description: Definire il tag di web tracking
exl-id: 0b5575be-57e7-4eee-9c0a-e9ef4b0931bf
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 2%

---

# Tag di tracciamento web: definizione{#web-tracking-tag-definition}

![](../../assets/v7-only.svg)

Un tag di web tracking è semplicemente un URL costruito con i parametri appropriati, inviato al server di reindirizzamento tramite una query HTTP.

## Formato dei dati da inviare {#format-of-the-data-to-be-sent}

Il formato di un URL di web tracking è il seguente: **https://`<name_of_redirection_server>`:`<port>`/r/`<random_number>`?`<parameters>`**

>[!NOTE]
>
>Il numero casuale aggiunto all’URL evita i problemi causati dalla memorizzazione in cache delle pagine web da parte dei browser.

Nella tabella seguente è riportato un elenco di parametri speciali supportati dal server di reindirizzamento.

<table>
                     <thead>
                        <tr>
                           <th>Nome</th>
                           <th>Tipo</th>
                           <th>Descrizione</th> 
                        </tr> 
                     </thead>
                     <tbody>
                        <tr>
                           <td>
                              <p>ID</p> 
                           </td>
                           <td>
                              <p>Cookie di sessione</p> 
                           </td>
                           <td>
                              <p>Identificatore della consegna e identificatore del destinatario.</p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>uuid230</p> 
                           </td>
                           <td>
                              <p>Cookie permanente</p> 
                           </td>
                           <td>
                              <p>Identificatore del destinatario (utile se manca il cookie di sessione).</p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>tagid</p> 
                           </td>
                           <td>
                              <p>Parametro URL</p> 
                           </td>
                           <td>
                              <p>Identificatore della pagina web tracciata: questo è l’unico parametro obbligatorio.</p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>jobid</p> 
                           </td>
                           <td>
                              <p>Parametro URL</p> 
                           </td>
                           <td>
                              <p>Identificatore di consegna da utilizzare se non è presente un cookie di sessione. Questo valore deve essere espresso in esadecimale.
                              </p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>rcpid</p> 
                           </td>
                           <td>
                              <p>Parametro URL</p> 
                           </td>
                           <td>
                              <p>Parametro utilizzato per identificare l'utente Internet. Il formato di questo parametro è "name=value", dove il nome è un campo dello schema del destinatario. Questo parametro ha la priorità rispetto all’identificatore contenuto nel cookie di sessione.
                              </p> 
                           </td> 
                        </tr> 
                     </tbody>  
                  </table>

**Alcuni URL di web tracking**

* Visita a una pagina di identificazione &quot;home&quot;

   **https://myserver.adobe.com/r/9862?tagid=home**

* Raccolta di dati sul volume di business

   **https://myserver.adobe.com/r/4567?tagid=command&amp;amount=100&amp;article=2l**

* Specifica di un campo per trovare il destinatario

   **https://myserver.adobe.com/r/2353?tagid=home&amp;rcpid=saccount%3D10**

   Un destinatario il cui numero di account è 10 viene inviato alla home page.

* Utilizzo di una consegna predefinita

   **https://myserver.adobe.com/r/2456?tagid=home&amp;jobid=e6**

   Un destinatario viene inviato alla home page. Queste informazioni verranno memorizzate nella consegna con l’identificatore 230 (e6 nel database 16) a meno che questa query non invii un cookie di sessione contenente un identificatore di consegna.

>[!NOTE]
>
>Tutti i valori inviati al server di reindirizzamento tramite parametri URL devono essere codificati nell’URL. Negli esempi forniti, si noti che i caratteri &#39;=&#39; e &#39;|&#39; sono codificati rispettivamente come &#39;%3D&#39; e &#39;%7C&#39;.

## Metodi di trasmissione dei dati {#data-transmission-methods}

Sono possibili i seguenti metodi:

* Inserimento dell’URL nel **&quot;src&quot;** attributo di un HTML **`<img>`** tag incorporato nella pagina web da monitorare.
* Chiamata diretta al server di reindirizzamento quando viene generata la pagina web che desideri monitorare.
