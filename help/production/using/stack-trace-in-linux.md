---
product: campaign
title: Traccia dello stack in Linux
description: Traccia dello stack in Linux
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 91662d6d-2177-4440-b31f-7b031bd953cb
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 11%

---

# Traccia dello stack in Linux{#stack-trace-in-linux}

![](../../assets/v7-only.svg)

A **traccia stack** rappresenta una traccia contenuta in un **nucleo centrale** digitare file. Questo file viene generato in caso di errore del computer. Può identificare l’origine dell’errore.

>[!NOTE]
>
>* A **nucleo centrale** file denominato **core.`<num>`**.
>* **gdb - Debugger GNU** deve essere installato sul computer.
>


Il supporto tecnico Adobe Campaign può richiedere questo **traccia stack**. Per ottenerlo, immetti i seguenti comandi in Linux:

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

Il supporto tecnico di Adobe Campaign potrebbe chiederti di eseguire questo comando utilizzando un eseguibile specifico (da noi fornito).

In questo caso, è sufficiente eseguire il comando seguente sostituendo **nlserver** con l’eseguibile fornito da Adobe Campaign:

```
gdb nlserver <coreFile>
```

Ad esempio:

```
gdb nlserver.1823 <coreFile>
```
