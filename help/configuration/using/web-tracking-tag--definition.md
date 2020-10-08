---
title: '"Etichetta di web tracking: definizione"'
seo-title: '"Etichetta di web tracking: definizione"'
description: '"Etichetta di web tracking: definizione"'
seo-description: null
page-status-flag: never-activated
uuid: 915ddfd8-ad1b-41ac-96ed-f7fae687c09f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: b8996508-7173-4225-95e7-b51209aae1f1
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 5%

---


# Etichetta di web tracking: definizione{#web-tracking-tag-definition}

Un tag di tracciamento Web è semplicemente un URL costruito con i parametri appropriati, inviato al server di reindirizzamento tramite una query HTTP.

## Formato dei dati da inviare {#format-of-the-data-to-be-sent}

Il formato di un URL di tracciamento Web è il seguente: **https://`<name_of_redirection_server>`:`<port>`/r/`<random_number>`?`<parameters>`**

>[!NOTE]
>
>Il numero casuale aggiunto all’URL evita i problemi causati dal caching delle pagine Web da parte dei browser.

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
                              <p>Identificatore di consegna e identificatore del destinatario.</p> 
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
                              <p>Identificatore della pagina Web tracciata: questo è l'unico parametro obbligatorio.</p> 
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
                              <p>Identificatore di consegna da utilizzare in assenza di cookie di sessione. Questo valore deve essere espresso in esadecimale.
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
                              <p>Parametro utilizzato per identificare l’utente Internet. Il formato di questo parametro è "name=value", dove il nome è un campo dello schema del destinatario. Questo parametro ha la priorità rispetto all’identificatore contenuto nel cookie di sessione.
                              </p> 
                           </td> 
                        </tr> 
                     </tbody>  
                  </table>

**Alcuni URL di tracciamento Web**

* Visita a una pagina di identificatore &#39;home&#39;

   **https://myserver.adobe.com/r/9862?tagid=home**

* Raccolta dei dati sul volume di business

   **https://myserver.adobe.com/r/4567?tagid=command&amp;amount=100&amp;article=2l**

* Specifica di un campo per trovare il destinatario

   **https://myserver.adobe.com/r/2353?tagid=home&amp;rcpid=saccount%3D10**

   Destinatario il cui numero di account è 10 viene inviato alla home page.

* Utilizzo di una consegna predefinita

   **https://myserver.adobe.com/r/2456?tagid=home&amp;jobid=e6**

   Un destinatario viene inviato alla home page. Queste informazioni verranno memorizzate nella consegna con l&#39;identificatore 230 (e6 nel database 16), a meno che non venga inviato un cookie di sessione contenente un identificatore di consegna con questa query.

>[!NOTE]
>
>Tutti i valori inviati al server di reindirizzamento tramite parametri URL devono essere codificati nell’URL. Negli esempi forniti, i caratteri &#39;=&#39; e &#39;|&#39; sono codificati rispettivamente come &#39;%3D&#39; e &#39;%7C&#39;.

## Metodi di trasmissione dei dati {#data-transmission-methods}

Sono possibili i seguenti metodi:

* Inserimento dell’URL nell’attributo **&quot;src&quot;** di un **`<img>`** tag HTML incorporato nella pagina Web da monitorare.
* Chiamata diretta al server di reindirizzamento quando viene generata la pagina Web da tracciare.

