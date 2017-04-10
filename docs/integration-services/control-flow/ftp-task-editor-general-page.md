---
title: "Редактор задачи &#171;FTP&#187; (страница &#171;Общие&#187;) | Microsoft Docs"
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
  - "sql13.dts.designer.ftptask.general.f1"
helpviewer_keywords: 
  - "редактор задачи FTP"
ms.assetid: 28b46fdd-b04a-4f97-a99f-883f5735a6d9
caps.latest.revision: 29
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 29
---
# Редактор задачи &#171;FTP&#187; (страница &#171;Общие&#187;)
  Используйте страницу **Общие** диалогового окна **Редактор задачи «FTP»** для задания диспетчера FTP-соединений, выполняющего соединение с FTP-сервером, с которым задача обменивается данными. Также здесь можно указать имя и описание задачи «FTP».  
  
 Дополнительные сведения об этой задаче см. в разделе [Задача FTP](../../integration-services/control-flow/ftp-task.md).  
  
## Параметры  
 **FtpConnection**  
 Выберите существующий диспетчер подключений FTP или щелкните \<**Создать соединение...**>, чтобы создать его.  
  
> [!IMPORTANT]  
>  Диспетчер FTP-соединений поддерживает только анонимную проверку подлинности и обычную проверку подлинности. Проверка подлинности Windows не поддерживается.  
  
 **См. также**: [FTP Connection Manager](../../integration-services/connection-manager/ftp-connection-manager.md), [FTP Connection Manager Editor](../../integration-services/connection-manager/ftp-connection-manager-editor.md)  
  
 **StopOnFailure**  
 Укажите, следует ли завершить задачу «FTP» в случае ошибки операции с FTP.  
  
 **Название**  
 Задайте уникальное имя задачи «FTP». Это имя используется в качестве метки для значка задачи.  
  
> [!NOTE]  
>  Имена задач в пределах пакета должны быть уникальными.  
  
 **Description**  
 Введите описание задачи «FTP».  
  
## См. также  
 [Справочник по сообщениям об ошибках служб Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Редактор задачи "FTP" (страница "Передача файлов")](../../integration-services/control-flow/ftp-task-editor-file-transfer-page.md)   
 [Страница «Выражения»](../../integration-services/expressions/expressions-page.md)  
  
  