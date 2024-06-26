---
title: Migrazione degli utenti tecnici alla console Adobe Developer
description: Scopri come migrare gli operatori tecnici di Campaign all’account tecnico nella console Adobe Developer
feature: Technote
role: Admin
exl-id: 1a409daf-57be-43c9-a3d9-b8ab54c88068
source-git-commit: af811b2df325efcaee38a967252b6952e67680d1
workflow-type: tm+mt
source-wordcount: '1775'
ht-degree: 0%

---

# Migrazione degli operatori tecnici di Campaign alla console Adobe Developer {#migrate-tech-users-to-ims}

Nell’ambito del rafforzamento della sicurezza e del processo di autenticazione, a partire da Campaign Classic v7.3.5, è stato migliorato il processo di autenticazione in Campaign Classic. Ora gli operatori tecnici devono utilizzare il [Sistema Adobe Identity Management (IMS)](https://helpx.adobe.com/it/enterprise/using/users.html){target="_blank"} per connettersi a Campaign. Ulteriori informazioni sul nuovo processo di autenticazione server-to-server in [Documentazione della console Adobe Developer](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/){target="_blank"}. **L’Adobe consiglia di eseguire questa migrazione nella versione v7 per eseguire in modo fluido la migrazione a Campaign v8.**

Un operatore tecnico è un profilo utente di Campaign creato esplicitamente per l’integrazione API. Questo articolo descrive i passaggi necessari per migrare un operatore tecnico a un account tecnico tramite la console Adobe Developer.

## Sei interessato?{#ims-impacts}

Se effettui chiamate API da un sistema esterno a Campaign all’istanza Campaign Marketing o al Centro messaggi in tempo reale, l’Adobe ti consiglia vivamente di migrare gli operatori tecnici agli account tecnici tramite la console Adobe Developer come descritto di seguito.

Questa modifica è applicabile a partire da Campaign Classic v7.3.5 (e più recente [Versioni compatibili con la migrazione IMS](ac-ims.md#ims-versions)) ed è **obbligatorio** per passare ad Adobe Campaign v8.

## Processo di migrazione {#ims-migration-procedure}

Segui i passaggi seguenti per creare account tecnici nella console Adobe Developer, quindi utilizza gli account appena creati per poter modificare i metodi di autenticazione per tutti i sistemi esterni che effettuano chiamate API in Adobe Campaign.

Ecco una panoramica dei passaggi:

* Creare un progetto nella console Adobe Developer
* Assegna le API appropriate al progetto appena creato
* Concedere i profili di prodotto di Campaign necessari al progetto
* Aggiorna le API per utilizzare le credenziali dell’account tecnico appena create
* Rimuovere gli operatori tecnici legacy dall’istanza Campaign


### Prerequisiti per la migrazione{#ims-migration-prerequisites}

<!--To be able to create the technical accounts which replace the technical operators, the prerequisite that the proper Campaign Product Profiles exist within the Admin Console for all Campaign instances need to be validated. You can learn more about Product Profiles within the Adobe Console in [Adobe Developer Console documentation](https://developer.adobe.com/developer-console/docs/guides/projects/){target="_blank"}.-->

* Clienti Campaign in hosting e Managed Services

  Per le chiamate API nelle istanze del Centro messaggi, il profilo di prodotto (indicato di seguito) deve essere creato durante l’aggiornamento a Campaign v7.4.1 (o altro) [Versione compatibile con migrazione IMS](ac-ims.md#ims-versions)) o durante il provisioning dell’istanza. Se non trovi il profilo di prodotto, contatta il tuo Transition Manager o l’Assistenza clienti per creare il profilo di prodotto prima di avviare la migrazione IMS. Questo profilo di prodotto è denominato:

  `campaign - <your campaign marketing instance> - messagecenter`

  Se utilizzi già l’autenticazione basata su IMS per l’accesso utente a Campaign, i profili di prodotto necessari per le chiamate API dovrebbero già esistere all’interno dell’Admin Console. Se utilizzi un gruppo di operatori personalizzato all’interno di Campaign per le chiamate API all’istanza Marketing, devi creare tale profilo di prodotto nell’Admin Console.

  Per gli altri casi, devi contattare il tuo Adobe Transition Manager (per gli utenti di Managed Services) o l’Assistenza clienti di Adobe (per gli altri utenti in hosting), in modo che i team tecnici di Adobe possano migrare i gruppi di operatori e i diritti denominati esistenti ai profili di prodotto all’interno dell’Admin Console.

* Clienti Campaign on-premise e ibridi

  Per le chiamate API nelle istanze del Centro messaggi, devi creare un profilo di prodotto denominato:

  `campaign - <your campaign instance> - messagecenter`

  Se utilizzi già l’autenticazione basata su IMS per l’accesso utente a Campaign, i profili di prodotto necessari per le chiamate API dovrebbero già esistere all’interno dell’Admin Console. Se utilizzi un gruppo di operatori personalizzato all’interno di Campaign per le chiamate API all’istanza Marketing, devi creare tale profilo di prodotto nell’Admin Console.

  Per ulteriori informazioni sui profili di prodotto, consulta la console Adobe in [Documentazione della console Adobe Developer](https://developer.adobe.com/developer-console/docs/guides/projects/){target="_blank"}


### Passaggio 1: creare il progetto Campaign all’interno della console Adobe Developer {#ims-migration-step-1}

Le integrazioni vengono create come parte di un **Progetto** nella console Adobe Developer. Ulteriori informazioni sui progetti in [Documentazione della console Adobe Developer](https://developer.adobe.com/developer-console/docs/guides/projects/){target="_blank"}.

Puoi utilizzare qualsiasi progetto creato in precedenza da te oppure creare un nuovo progetto. I passaggi per creare un progetto sono descritti in [Documentazione della console Adobe Developer](https://developer.adobe.com/developer-console/docs/guides/getting-started/){target="_blank"}. Di seguito sono riportati i passaggi chiave

<!--
For this migration, you must add below APIs in your project: **I/O Management API** and **Adobe Campaign**.

![](assets/do-not-localize/ims-products-and-services.png)-->

Per creare un nuovo progetto, fai clic su **Crea nuovo progetto** dalla schermata principale nella console Adobe Developer.

![](assets/New-Project.png)

È possibile utilizzare **Modifica progetto** per rinominare il progetto.


### Passaggio 2: aggiungere API al progetto {#ims-migration-step-2}

Dalla schermata del progetto appena creato, aggiungi nelle API necessarie per poter utilizzare questo progetto come account tecnico per le chiamate API ad Adobe Campaign.

Per aggiungere API al progetto, effettua le seguenti operazioni:

1. Fai clic su **Aggiungi API** per selezionare le API da aggiungere al progetto.
   ![](assets/do-not-translate/ims-updates-01.png)
1. Seleziona e aggiungi l’API Adobe Campaign al progetto selezionando la casella nell’angolo superiore destro della scheda Adobe Campaign che viene visualizzata quando passi il mouse sulla scheda
   ![](assets/do-not-translate/ims-updates-02.png)
1. Clic **Successivo** nella parte inferiore dello schermo.

### Passaggio 3: selezionare il tipo di autenticazione  {#ims-migration-step-3}

In **Configurare API** , seleziona il tipo di autenticazione necessario. **OAuth Server-to-Server** Per questo progetto è necessaria l’autenticazione. Assicurati che sia selezionato e fai clic su **Successivo** nella parte inferiore dello schermo.

![](assets/do-not-translate/ims-updates-03.png)

<!--
Once your project is created in the Adobe Developer Console, add an API that uses Server-to-Server authentication. Learn how to set up the OAuth Server-to-Server credential in [Adobe Developer Console documentation](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/){target="_blank"}.

When the API has been successfully connected, you can access the newly generated credentials including Client ID and Client Secret, as well as generate an access token.-->

### Passaggio 4: selezionare i profili di prodotto {#ims-migration-step-4}

Come descritto nella sezione prerequisiti, è necessario assegnare i profili di prodotto appropriati da utilizzare per il progetto. In questo passaggio, devi selezionare il profilo o i profili di prodotto da utilizzare per l’account tecnico creato.

Se questo account tecnico viene utilizzato per effettuare chiamate API all’istanza del Centro messaggi, assicurati di selezionare il profilo di prodotto di Adobe, che termina con messagecenter, per l’istanza di marketing associata al Centro messaggi.

Per le chiamate API alle istanze Marketing, seleziona il profilo di prodotto corrispondente all’istanza e al gruppo di operatori, ad esempio `campaign - <your campaign marketing instance> - Admin`.

Una volta selezionati i profili di prodotto necessari, fai clic su **Salva API configurata** nella parte inferiore dello schermo.

<!--
You can now add your Campaign product profile to the project, as detailed below:

1. Open the Adobe Campaign API.
1. Click the **Edit product profiles** button

    ![](assets/do-not-localize/ims-edit-api.png)

1. Assign all the relevant Product Profiles to the API, for example 'messagecenter', and save your changes.
1. Browse to the **Credential details** tab of your project, and copy the **Technical Account Email** value.-->

### Passaggio 5: aggiungi l’API di gestione I/O al progetto {#ims-migration-step-5}


Dalla schermata del progetto, fai clic su **[!UICONTROL + Add to Project]** e scegli **[!UICONTROL API]** in alto a sinistra per poter aggiungere l’API di gestione I/O a questo progetto.

![](assets/do-not-translate/ims-updates-04.png)

In **Aggiungere un’API** scorri verso il basso per trovare la **API di gestione I/O** Card. Selezionala facendo clic sulla casella di controllo che compare quando passi il cursore del mouse sulla scheda. Quindi fai clic su **Successivo** nella parte inferiore dello schermo.

![](assets/do-not-translate/ims-updates-05.png)


In **Configurare API** , l&#39;autenticazione server-to-server OAuth è già esistente. Clic **Salva API configurata** nella parte inferiore dello schermo.


![](assets/do-not-translate/ims-updates-06.png)

Viene visualizzata di nuovo la schermata Progetto nell’API di gestione I/O del progetto appena creato. Fai clic sul nome del progetto nelle breadcrumb nella parte superiore dello schermo per tornare alla pagina principale dei Dettagli del progetto.


### Passaggio 6: verificare la configurazione del progetto {#ims-migration-step-6}

Rivedi il progetto per assicurarti che sia simile a quello riportato di seguito con **API di gestione I/O** e **API ADOBE CAMPAIGN** visibile nella sezione Prodotti e servizi e **OAuth Server-to-Server** nella sezione Credenziali.

![](assets/do-not-translate/ims-updates-07.png)


### Passaggio 7: convalidare la configurazione {#ims-migration-step-7}

Per provare la connessione, segui i passaggi descritti in [Guida alle credenziali della console Adobe Developer](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/#generate-access-tokens){target="_blank"} per generare un token di accesso e copiare il comando cURL di esempio fornito. Puoi creare una chiamata soap utilizzando queste credenziali per verificare di poter autenticare e connettersi correttamente alle istanze di Adobe Campaign. È consigliabile eseguire questa convalida prima di apportare tutte le modifiche alle integrazioni API di terze parti.

### Passaggio 8: aggiornare le integrazioni API di terze parti {#ims-migration-step-8}

Ora devi aggiornare tutte le integrazioni API che effettuano chiamate ad Adobe Campaign per utilizzare l’account tecnico appena creato.

Per informazioni dettagliate sui passaggi di integrazione API, consulta gli esempi di codice seguenti.

Quando si utilizza l’autenticazione Adobe Identity Management System (IMS), per generare un file WSDL è necessario aggiungere Authorization: Bearer &lt;ims_technical_token_token> nella chiamata al postino:

```
curl --location --request POST 'https://<instance_url>/nl/jsp/schemawsdl.jsp?schema=nms:rtEvent' \--header 'Authorization: Bearer <Technical account access token>'
```

>[!BEGINTABS]

>[!TAB Chiamata SOAP]

```
curl --location --request POST 'https://<instance_name>.campaign.adobe.com/nl/jsp/soaprouter.jsp' \
--header 'Content-Type: text/xml; charset=utf-8' \
--header 'SOAPAction: xtk:queryDef#ExecuteQuery' \
--header 'Authorization: Bearer eyJhw' \
--data-raw '<?xml version="1.0" encoding="utf-8"?>
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
  <soap:Body>
    <ExecuteQuery xmlns="urn:xtk:queryDef">
            <sessiontoken></sessiontoken>
            <entity>
                <queryDef schema="nms:recipient" operation="select">
                    <!-- fields to retrieve -->
                    <select>
                        <node expr="@lastName"/>
                        <node expr="@email"/>
                        <node expr="@firstName"/>
                    </select>
                    <!-- condition on email -->
                    <!-- <where><condition expr="@email= '\''joh@com.com'\''"/>
                </where> -->
                </queryDef>
            </entity>
        </ExecuteQuery>
  </soap:Body>
</soap:Envelope>
'
```

>[!TAB  Java SampleCode]

```javascript
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;
import com.google.gson.Gson;
import com.google.gson.JsonObject;
 
import com.google.gson.JsonSyntaxException;
import org.apache.hc.client5.http.classic.methods.HttpPost;
import org.apache.hc.client5.http.impl.classic.CloseableHttpClient;
import org.apache.hc.client5.http.impl.classic.CloseableHttpResponse;
import org.apache.hc.client5.http.impl.classic.HttpClients;
import org.apache.hc.core5.http.HttpEntity;
import org.apache.hc.core5.http.io.entity.StringEntity;
 
 
public class TAAccessToken {
    public static void main(String[] args) throws IOException {
        String accessToken = null;
        CloseableHttpClient httpClient = HttpClients.createDefault();
        try {
            HttpPost httpPost = new HttpPost("https://ims-na1.adobelogin.com/ims/token/v3");
 
            // Request headers
            httpPost.addHeader("Content-Type", "application/x-www-form-urlencoded");
 
            String clientId = "<client_id>";
            String clientSecret = "<client_secret>";
            String scopes = "<scopes>";
 
            // Define the request body
            String requestBody = "client_id="+clientId+"&client_secret="+clientSecret+"&grant_type=client_credentials&scope="+scopes+"";
            StringEntity requestEntity = new StringEntity(requestBody);
            httpPost.setEntity(requestEntity);
 
            // Execute the request
            CloseableHttpResponse response = httpClient.execute(httpPost);
            try {
                // Get the response entity
                HttpEntity entity = response.getEntity();
                int responseCode = response.getCode();
 
                // Print the response
                if (entity != null) {
                    BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(entity.getContent()));
                    String lineImsToken;
                    StringBuilder responseImsToken = new StringBuilder();
                    while ((lineImsToken = bufferedReader.readLine()) != null) {
                        responseImsToken.append(lineImsToken);
                    }
 
                    String jsonString = responseImsToken.toString();
 
                    try {
                        Gson gson = new Gson();
                        JsonObject jsonObject = gson.fromJson(jsonString, JsonObject.class);
 
                        // Get the value of a specific key
                        accessToken = jsonObject.get("access_token").getAsString();
                    }
                    catch (JsonSyntaxException | NullPointerException e) {
                        System.err.println("Error parsing JSON: " + e.getMessage());
                        e.printStackTrace();
                    }
                    System.out.println("Response Code: " + responseCode);
                    System.out.println("Response Body: " + accessToken);
                }
            } catch (IOException e) {
                e.printStackTrace();
            } finally {
                response.close();
            }
        } finally {
            httpClient.close();
        }
 
        CloseableHttpClient httpClientSoap = HttpClients.createDefault();
        try {
            HttpPost httpPostSoap = new HttpPost("https://<instance_name>.campaign.adobe.com/nl/jsp/soaprouter.jsp");
 
            // Request headers
            httpPostSoap.addHeader("Content-Type", "text/xml; charset=utf-8");
            httpPostSoap.addHeader("SOAPAction", "xtk:queryDef#ExecuteQuery");
            httpPostSoap.addHeader("Authorization", "Bearer "+accessToken);
 
            // Request body
            String xmlData = "<?xml version=\"1.0\" encoding=\"utf-8\"?>\n" +
                    "<soap:Envelope xmlns:soap=\"http://schemas.xmlsoap.org/soap/envelope/\">\n" +
                    "  <soap:Body>\n" +
                    "    <ExecuteQuery xmlns=\"urn:xtk:queryDef\">\n" +
                    "            <sessiontoken></sessiontoken>\n" +
                    "            <entity>\n" +
                    "                <queryDef schema=\"nms:recipient\" operation=\"select\">\n" +
                    "                    <!-- fields to retrieve -->\n" +
                    "                    <select>\n" +
                    "                        <node expr=\"@lastName\"/>\n" +
                    "                        <node expr=\"@email\"/>\n" +
                    "                        <node expr=\"@firstName\"/>\n" +
                    "                    </select>\n" +
                    "                    <!-- condition on email -->\n" +
                    "                    <!-- <where><condition expr=\"@email= '\''joh@com.com'\''\"/>\n" +
                    "                </where> -->\n" +
                    "                </queryDef>\n" +
                    "            </entity>\n" +
                    "        </ExecuteQuery>\n" +
                    "  </soap:Body>\n" +
                    "</soap:Envelope>";
            StringEntity requestEntity = new StringEntity(xmlData);
            httpPostSoap.setEntity(requestEntity);
 
            // Execute the request
            CloseableHttpResponse response = httpClientSoap.execute(httpPostSoap);
            try {
                // Get the response entity
                HttpEntity entity = response.getEntity();
 
                // Print the response
                if (entity != null) {
                    BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(entity.getContent()));
                    String line;
                    while ((line = bufferedReader.readLine()) != null) {
                        System.out.println(line);
                    }
                }
            } catch (IOException e) {
                e.printStackTrace();
            } finally {
                response.close();
            }
        } finally {
            httpClientSoap.close();
        }
 
    }
}
```

>[!TAB SampleCodePython]

```python
import requests
 
oauth_url = 'https://ims-na1.adobelogin.com/ims/token/v3'
data = {
    'grant_type': 'client_credentials',
    'scope': '<scopes>',
    'client_id': '<client_id>',
    'client_secret': '<client_secret>'
}
 
headers = {
    'Content-Type': 'application/x-www-form-urlencoded',
    'Accept': 'application/json'
}
response = requests.post(oauth_url, data=data, headers=headers)
response = response.json()
access_token = response['access_token']
 
 
url = 'https://<instance_name>.campaign.adobe.com/nl/jsp/soaprouter.jsp'
headers = {
    'Content-Type': 'text/xml; charset=utf-8',
    'SOAPAction': 'xtk:queryDef#ExecuteQuery',
    'Authorization': 'Bearer '+access_token
}
xml_data = '''<?xml version="1.0" encoding="utf-8"?>
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
  <soap:Body>
    <ExecuteQuery xmlns="urn:xtk:queryDef">
            <sessiontoken></sessiontoken>
            <entity>
                <queryDef schema="nms:recipient" operation="select">
                    <!-- fields to retrieve -->
                    <select>
                        <node expr="@lastName"/>
                        <node expr="@email"/>
                        <node expr="@firstName"/>
                    </select>
                    <!-- condition on email -->
                    <!-- <where><condition expr="@email= '\''joh@com.com'\''"/>
                </where> -->
                </queryDef>
            </entity>
        </ExecuteQuery>
  </soap:Body>
</soap:Envelope>
'''
response = requests.post(url, headers=headers, data=xml_data)
```

>[!ENDTABS]

Per ulteriori informazioni, consulta [Documentazione sull’autenticazione della console Adobe Developer](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/){target="_blank"}.

Di seguito sono riportati alcuni esempi di chiamate SOAP che mostrano le chiamate prima e dopo la migrazione per i sistemi di terze parti.

Una volta completato e convalidato il processo di migrazione, le chiamate Soap vengono aggiornate come segue:

* Prima della migrazione: non era disponibile il supporto per il token di accesso dell’account tecnico.

  ```sql
  POST /nl/jsp/soaprouter.jsp HTTP/1.1
  Host: localhost:8080
  Content-Type: application/soap+xml;
  SOAPAction: "nms:rtEvent#PushEvent"
  charset=utf-8
  
  <?xml version="1.0" encoding="utf-8"?>  <soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:nms:rtEvent">
  <soapenv:Header/>
  <soapenv:Body>
      <urn:PushEvent>
          <urn:sessiontoken>SESSION_TOKEN</urn:sessiontoken>
          <urn:domEvent>
              <!--You may enter ANY elements at this point-->
              <rtEvent type="type" email="name@domain.com"/>
          </urn:domEvent>
      </urn:PushEvent>
  </soapenv:Body>
  </soapenv:Envelope>
  ```

* Dopo la migrazione: è disponibile il supporto per il token di accesso dell’account tecnico. Il token di accesso deve essere fornito in `Authorization` intestazione come token Bearer. L’utilizzo del token di sessione deve essere ignorato qui, come mostrato nell’esempio di chiamata soap seguente.

  ```sql
  POST /nl/jsp/soaprouter.jsp HTTP/1.1
  Host: localhost:8080
  Content-Type: application/soap+xml;
  SOAPAction: "nms:rtEvent#PushEvent"
  charset=utf-8
  Authorization: Bearer <IMS_Technical_Token_Token>
  
  <?xml version="1.0" encoding="utf-8"?>  <soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:nms:rtEvent">
  <soapenv:Header/>
  <soapenv:Body>
      <urn:PushEvent>
          <urn:sessiontoken></urn:sessiontoken>
          <urn:domEvent>
              <!--You may enter ANY elements at this point-->
              <rtEvent type="type" email="name@domain.com"/>
          </urn:domEvent>
      </urn:PushEvent>
  </soapenv:Body>
  </soapenv:Envelope>
  ```



### Passaggio 9: (facoltativo) aggiorna l’operatore dell’account tecnico nella console client di Campaign {#ims-migration-step-9}

Questo passaggio è facoltativo e disponibile solo all’interno delle istanze Marketing, non all’interno di alcuna istanza del Centro messaggi. Se sono state definite autorizzazioni di cartelle specifiche o diritti denominati per l’operatore tecnico non tramite i gruppi di operatori assegnati. Ora è necessario aggiornare l’utente dell’account tecnico appena creato nell’Admin Console per concedere le autorizzazioni della cartella o i diritti denominati richiesti.

L’utente dell’account tecnico NON esisterà in Adobe Campaign finché non verrà effettuata almeno una chiamata API all’istanza di Campaign, momento in cui IMS creerà l’utente all’interno di Campaign. Se non riesci a individuare gli utenti tecnici all’interno di Campaign, assicurati di aver inviato correttamente una chiamata API come descritto [nel passaggio 7](#ims-migration-step-7).

1. Per applicare le modifiche necessarie per il nuovo utente account tecnico, individuale nella console client di Campaign per indirizzo e-mail. Questo indirizzo e-mail è stato creato durante i passaggi di creazione e autenticazione del progetto descritti sopra.

   Puoi individuare questo indirizzo e-mail facendo clic sul pulsante **OAuth Server-to-Server** intestazione nel **Credenziali** sezione del progetto.

   ![](assets/do-not-translate/ims-updates-07.png)

   In **Dettagli delle credenziali** , scorri verso il basso per individuare **E-mail account tecnico** e fai clic su **Copia** pulsante.

   ![](assets/do-not-translate/ims-updates-08.png)

1. Ora devi aggiornare l’operatore tecnico appena creato nella console client di Adobe Campaign. È necessario applicare al nuovo operatore tecnico le autorizzazioni esistenti per la cartella dell’operatore tecnico.

   Per aggiornare questo operatore, effettua le seguenti operazioni:

   1. Dall’Explorer della console client di Campaign, passa alla **Amministrazione > Gestione degli accessi > Operatori**.
   1. Accedi all’operatore tecnico esistente utilizzato per le API.
   1. Individua le autorizzazioni della cartella e controlla i diritti.
   1. Applica le stesse autorizzazioni all’operatore tecnico appena creato. L’e-mail di questo operatore è **E-mail account tecnico** valore copiato in precedenza.
   1. Salva le modifiche.


>[!CAUTION]
>
>Il nuovo operatore tecnico deve aver effettuato almeno una chiamata API per essere aggiunto alla console client di Campaign.
>

### Passaggio 10 - Rimuovere il vecchio operatore tecnico da Adobe Campaign {#ims-migration-step-10}

Dopo aver migrato tutti i sistemi di terze parti per utilizzare il nuovo account tecnico con autenticazione IMS, puoi eliminare il vecchio operatore tecnico dalla console client di Campaign.

A tale scopo, accedi alla console client di Campaign e vai a **Amministrazione > Gestione degli accessi > Operatori** e individuare i vecchi utenti tecnici ed eliminarli.


>[!MORELIKETHIS]
>
>* [Migrazione degli utenti finali a IMS](migrate-users-to-ims.md)
>* [Aggiornare l’interfaccia di Campaign dopo la migrazione IMS](impact-ims-migration.md)
>* [Note sulla versione più recente di Adobe Campaign Classic v7](../../rn/using/latest-release.md)
>* [Che cos’è Adobe Identity Management System (IMS)](https://helpx.adobe.com/it/enterprise/using/users.html){target="_blank"}

