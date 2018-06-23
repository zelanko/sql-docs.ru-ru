---
title: Задача "Выполнение инструкции T-SQL" | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.executetsqlstatementtask.f1
helpviewer_keywords:
- Transact-SQL statements, SSIS
- statements [Integration Services]
- Execute T-SQL Statement task [Integration Services]
ms.assetid: 7e9086ca-d27e-46c0-bfad-d61333ebd55e
caps.latest.revision: 34
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 74be247e47e50b61dfea84863a5969008f160ff0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36099319"
---
# <a name="execute-t-sql-statement-task"></a>Задача «Выполнение инструкции T-SQL»
  Задача «Выполнение инструкции T-SQL» запускает инструкции Transact-SQL. Дополнительные сведения см. в разделах [Справочник по Transact-SQL (компонент Database Engine)](/sql/t-sql/language-reference) и [Запросы в службах Integration Services (SSIS)](../integration-services-ssis-queries.md).  
  
 Эта задача аналогична задаче «Выполнение SQL». Тем не менее задача «Выполнение инструкции T-SQL» поддерживает только версию Transact-SQL языка SQL, и недопустимо использовать эту задачу для запуска инструкций на серверах, использующих другие разновидности языка SQL. Для запуска параметризованных запросов, сохранения результатов запроса в переменную или использования выражений свойств необходимо использовать задачу «Выполнение SQL» вместо задачи «Выполнение инструкций T-SQL». Дополнительные сведения см. в разделе [Execute SQL Task](execute-sql-task.md).  
  
## <a name="configuration-of-the-execute-t-sql-task"></a>Настройка задачи «Выполнение T-SQL»  
 Свойства задаются с помощью конструктора служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] . Эта задача находится в разделе **Задачи плана обслуживания** **области элементов** в конструкторе служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] .  
  
 Дополнительные сведения о свойствах, которые можно задать в конструкторе служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] , см. в следующем разделе:  
  
-   [Задача "Выполнение инструкции T-SQL" (план обслуживания)](../../relational-databases/maintenance-plans/execute-t-sql-statement-task-maintenance-plan.md)  
  
 Дополнительные сведения об установке этих свойств в конструкторе служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] см. в следующем разделе:  
  
-   [Задание свойств задач или контейнеров](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a>См. также  
 [Задачи служб Integration Services](integration-services-tasks.md)   
 [Поток управления](control-flow.md)   
 [Предложение MERGE в пакетах служб Integration Services](merge-in-integration-services-packages.md)  
  
  
