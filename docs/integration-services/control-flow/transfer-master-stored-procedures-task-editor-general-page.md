---
title: "Редактор задачи &#171;Передача главных хранимых процедур&#187; (страница &#171;Общие&#187;) | Microsoft Docs"
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
  - "sql13.dts.designer.transferstoredprocedurestask.general.f1"
helpviewer_keywords: 
  - "редактор задачи «Передача хранимых процедур»"
ms.assetid: fa1abd4c-e2be-427f-be53-860e49c97227
caps.latest.revision: 25
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 25
---
# Редактор задачи &#171;Передача главных хранимых процедур&#187; (страница &#171;Общие&#187;)
  Используйте страницу **Общие** в диалоговом окне **Редактор задачи «Передача главных хранимых процедур»** , чтобы назвать и описать задачу переноса главных хранимых процедур. Дополнительные сведения об этой задаче см. в разделе [Transfer Master Stored Procedures Task](../../integration-services/control-flow/transfer-master-stored-procedures-task.md).  
  
> [!NOTE]  
>  Эта задача передает только пользовательские хранимые процедуры, принадлежащие **dbo**, из базы данных **master** на исходном сервере в базу данных **master** на целевом сервере. Пользователям должно быть предоставлено разрешение CREATE PROCEDURE в базе данных **master** на целевом сервере, или они должны быть членами предопределенной роли сервера **sysadmin** на целевом сервере, чтобы создавать на нем хранимые процедуры.  
  
## Параметры  
 **Название**  
 Введите уникальное имя для задачи «Передача главных хранимых процедур». Это имя используется в качестве метки для значка задачи.  
  
> [!NOTE]  
>  Имена задач в пределах пакета должны быть уникальными.  
  
 **Description**  
 Введите описание для задачи «Передача главных хранимых процедур».  
  
## См. также  
 [Справочник по сообщениям об ошибках служб Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Задачи служб Integration Services](../../integration-services/control-flow/integration-services-tasks.md)   
 [Редактор задачи "Передача главных хранимых процедур" (страница "Хранимые процедуры")](../../integration-services/control-flow/transfer-master-stored-procedures-task-editor-stored-procedures-page.md)   
 [Страница «Выражения»](../../integration-services/expressions/expressions-page.md)  
  
  