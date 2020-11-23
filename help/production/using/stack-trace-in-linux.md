---
solution: Campaign Classic
product: campaign
title: Stack trace in Linux
description: Stack trace in Linux
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 11%

---


# Stack trace in Linux{#stack-trace-in-linux}

Una traccia **** dello stack rappresenta una traccia contenuta in un file di tipo **core** . Questo file viene generato in caso di errore del computer. Può identificare l’origine dell’errore.

>[!NOTE]
>
>* Un file **di base** è denominato **core.`<num>`**.
>* **gdb - Il debugger** GNU deve essere installato nel computer.

>



 supporto tecnico Adobe Campaign può richiedere questa traccia **** dello stack. Per ottenerlo, immettete i seguenti comandi in Linux:

```
su - neolane
gdb nlserver <coreFile>
//You get lots of output but the stack trace (or Back trace) can be obtained with : 
(gdb) bt
// and forward all the output : 
#0 0x0836c189 in ObjectValue::SetPropertyTarget ()
#1 0x082623b3 in CXtkScriptProperty::VDeclareProperties ()
#2 0x0826a835 in CXtkScriptContext::OnGetProperty ()
#3 0x08370b3d in JavaScriptGetProperty ()
#4 0x557b8aa7 in js_Interpret () from /usr/local/neolane/nl6/lib/libmozjs.so
#5 0x557afb97 in js_Execute () from /usr/local/neolane/nl6/lib/libmozjs.so
#6 0x5578921f in JS_ExecuteScript () from /usr/local/neolane/nl6/lib/libmozjs.so
#7 0x08370468 in JavaScriptSource::Evaluate ()
#8 0x0848fa03 in JSTDeliveryContext::ProcessScript ()
#9 0x0848fcb6 in JSTDeliveryContext::ProcessTemplate ()
#10 0x08460d2b in CDeliveryToolbox::CreateMailMessage ()
#11 0x080d51fe in CMtaQueue::PrepareMessages ()
#12 0x080d2b07 in CMtaQueue::Prepare ()
#13 0x080dca38 in CMtaChild::OnRun ()
#14 0x0814792c in ThreadStartRoutine ()
#15 0x55575b63 in start_thread () from /lib/tls/libpthread.so.0
#16 0x5565918a in clone () from /lib/tls/libc.so.6
```

 supporto tecnico Adobe Campaign potrebbe chiedere di eseguire questo comando utilizzando un file eseguibile specifico (fornito da noi).

In questo caso, eseguite semplicemente il comando seguente sostituendo **nlserver** con l&#39;eseguibile fornito da  Adobe Campaign:

```
gdb nlserver <coreFile>
```

Ad esempio:

```
gdb nlserver.1823 <coreFile>
```

