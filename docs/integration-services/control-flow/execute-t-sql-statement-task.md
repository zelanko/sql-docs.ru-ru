---
title: "«Выполнение инструкции T-SQL» | Документы Microsoft"
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.executetsqlstatementtask.f1
helpviewer_keywords:
- Transact-SQL statements, SSIS
- statements [Integration Services]
- Execute T-SQL Statement task [Integration Services]
ms.assetid: 7e9086ca-d27e-46c0-bfad-d61333ebd55e
caps.latest.revision: 35
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 94fd411504f1781041e8d36f3f1cf41f6082aa09
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="execute-t-sql-statement-task"></a>Задача «Выполнение инструкции T-SQL»
  Задача «Выполнение инструкции T-SQL» запускает инструкции Transact-SQL. Дополнительные сведения см. в разделах [Справочник по Transact-SQL (компонент Database Engine)](../../t-sql/transact-sql-reference-database-engine.md) и [Запросы в службах Integration Services (SSIS)](../../integration-services/integration-services-ssis-queries.md).  
  
 Эта задача аналогична задаче «Выполнение SQL». Тем не менее задача «Выполнение инструкции T-SQL» поддерживает только версию Transact-SQL языка SQL, и недопустимо использовать эту задачу для запуска инструкций на серверах, использующих другие разновидности языка SQL. Для запуска параметризованных запросов, сохранения результатов запроса в переменную или использования выражений свойств необходимо использовать задачу «Выполнение SQL» вместо задачи «Выполнение инструкций T-SQL». Дополнительные сведения см. в разделе [Execute SQL Task](../../integration-services/control-flow/execute-sql-task.md).  
  
## <a name="configuration-of-the-execute-t-sql-task"></a>Настройка задачи «Выполнение T-SQL»  
 Свойства задаются с помощью конструктора служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] . Эта задача находится в разделе **Задачи плана обслуживания** **области элементов** в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 Дополнительные сведения о свойствах, которые можно задать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в следующем разделе:  
  
-   [Задача "Выполнение инструкции T-SQL" (план обслуживания)](../../relational-databases/maintenance-plans/execute-t-sql-statement-task-maintenance-plan.md)  
  
 Дополнительные сведения об установке этих свойств в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] см. в следующем разделе:  
  
-   [Задание свойств задач или контейнеров](http://msdn.microsoft.com/library/52d47ca4-fb8c-493d-8b2b-48bb269f859b)  
  
## <a name="see-also"></a>См. также  
 [Задачи служб Integration Services](../../integration-services/control-flow/integration-services-tasks.md)   
 [Поток управления](../../integration-services/control-flow/control-flow.md)   
 [ОБЪЕДИНЕНИЕ пакетов в службах Integration Services](../../integration-services/control-flow/merge-in-integration-services-packages.md)  
  
  

