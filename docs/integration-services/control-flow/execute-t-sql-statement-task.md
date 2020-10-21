---
description: Задача «Выполнение инструкции T-SQL»
title: Задача "Выполнение инструкции T-SQL" | Документы Майкрософт
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.executetsqlstatementtask.f1
helpviewer_keywords:
- Transact-SQL statements, SSIS
- statements [Integration Services]
- Execute T-SQL Statement task [Integration Services]
ms.assetid: 7e9086ca-d27e-46c0-bfad-d61333ebd55e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 060fa6ad9faae0fa6159eba2591623af57a41c5b
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2020
ms.locfileid: "92196555"
---
# <a name="execute-t-sql-statement-task"></a>Задача «Выполнение инструкции T-SQL»

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Задача «Выполнение инструкции T-SQL» запускает инструкции Transact-SQL. Дополнительные сведения см. в разделах [Справочник по Transact-SQL (компонент Database Engine)](../../t-sql/language-reference.md) и [Запросы в службах Integration Services (SSIS)](../../integration-services/integration-services-ssis-queries.md).  
  
 Эта задача аналогична задаче «Выполнение SQL». Тем не менее задача «Выполнение инструкции T-SQL» поддерживает только версию Transact-SQL языка SQL, и недопустимо использовать эту задачу для запуска инструкций на серверах, использующих другие разновидности языка SQL. Для запуска параметризованных запросов, сохранения результатов запроса в переменную или использования выражений свойств необходимо использовать задачу «Выполнение SQL» вместо задачи «Выполнение инструкций T-SQL». Дополнительные сведения см. в разделе [Execute SQL Task](../../integration-services/control-flow/execute-sql-task.md).  
  
## <a name="configuration-of-the-execute-t-sql-task"></a>Настройка задачи «Выполнение T-SQL»  
 Свойства задаются с помощью конструктора служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] . Эта задача находится в разделе **Задачи плана обслуживания****области элементов** в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 Дополнительные сведения о свойствах, которые можно задать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в следующем разделе:  
  
-   [Задача "Выполнение инструкции T-SQL" (план обслуживания)](../../relational-databases/maintenance-plans/execute-t-sql-statement-task-maintenance-plan.md)  
  
 Дополнительные сведения об установке этих свойств в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] см. в следующем разделе:  
  
-   [Задание свойств задач или контейнеров](./add-or-delete-a-task-or-a-container-in-a-control-flow.md)  
  
## <a name="see-also"></a>См. также:  
 [Задачи служб Integration Services](../../integration-services/control-flow/integration-services-tasks.md)   
 [Поток управления](../../integration-services/control-flow/control-flow.md)   
 [Предложение MERGE в пакетах служб Integration Services](../../integration-services/control-flow/merge-in-integration-services-packages.md)  
  
