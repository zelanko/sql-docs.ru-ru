---
title: "Редактор задачи &#171;Очередь сообщений&#187; (страница &#171;Общие&#187;) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.msgqueuetask.general.f1"
helpviewer_keywords: 
  - "редактор задачи «Очередь сообщений»"
ms.assetid: 09368b18-37a5-4321-a173-7cfe5d42d2a2
caps.latest.revision: 25
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 25
---
# Редактор задачи &#171;Очередь сообщений&#187; (страница &#171;Общие&#187;)
   **Страница «Общие»** диалогового окна **Редактор задачи «Очередь сообщений»** позволяет задавать имя и описывать задачу «Очередь сообщений», определять формат сообщений, а также указывать, будет ли задача отправлять или получать сообщения.  
  
 Дополнительные сведения об этой задаче см. в разделе [Message Queue Task](../../integration-services/control-flow/message-queue-task.md).  
  
## Параметры  
 **Название**  
 Задайте уникальное имя задаче «Очередь сообщений». Это имя используется в качестве метки для значка задачи.  
  
> [!NOTE]  
>  Имена задач в пределах пакета должны быть уникальными.  
  
 **Description**  
 Введите описание задачи «Очередь сообщений».  
  
 **Use2000Format**  
 Укажите, нужно ли использовать формат 2000 службы очередей сообщений (MSMQ). По умолчанию **False**.  
  
 **MSMQConnection**  
 Выберите существующий диспетчер подключений MSMQ или щелкните \<**Создать соединение...**>, чтобы создать диспетчер.  
  
 **См. также**: [Диспетчер FTP-соединений](../../integration-services/connection-manager/msmq-connection-manager.md), [Редактор диспетчера FTP-соединений](../../integration-services/connection-manager/msmq-connection-manager-editor.md)  
  
 **Сообщение**  
 Указывает, будет ли задача «Очередь сообщений» отправлять или получать сообщения. При выборе режима **Отправить сообщение**на левой панели диалогового окна появляется страница «Отправка», при выборе режима **Получить сообщение**появляется страница «Получение». По умолчанию, устанавливается режим **Отправить сообщение**.  
  
## См. также  
 [Справочник по сообщениям об ошибках служб Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Редактор задачи "Очередь сообщений" (страница "Получение")](../../integration-services/control-flow/message-queue-task-editor-receive-page.md)   
 [Редактор задачи "Очередь сообщений" (страница "Отправка")](../../integration-services/control-flow/message-queue-task-editor-send-page.md)   
 [Страница «Выражения»](../../integration-services/expressions/expressions-page.md)  
  
  