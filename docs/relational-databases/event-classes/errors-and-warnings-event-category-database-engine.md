---
title: Категория событий "Ошибки и предупреждения" (ядро СУБД) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: event-classes
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Errors and Warnings event category [SQL Server]
- SQL Server event classes, Errors and Warnings event category
- event classes [SQL Server], Errors and Warnings event category
ms.assetid: 249c19b5-af68-4433-80f6-337395176641
caps.latest.revision: 28
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 277f15df25b78ee3ff0fa38351b2fcc3a839f5fd
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="errors-and-warnings-event-category-database-engine"></a>Категория событий Errors and Warnings (компонент Database Engine)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  В категорию событий **Ошибки и предупреждения** входят общие события ошибок и предупреждений.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Класс событий Attention](../../relational-databases/event-classes/attention-event-class.md)|Указывает, что произошло событие **Внимание** .|  
|[Класс событий Background Job Error](../../relational-databases/event-classes/background-job-error-event-class.md)|Указывает, что фоновое задание завершилось ненормально.|  
|[Класс событий Bitmap Warning](../../relational-databases/event-classes/bitmap-warning-event-class.md)|Указывает, что в запросе отключена фильтрация по битовым картам.|  
|[Класс событий Blocked Process Report](../../relational-databases/event-classes/blocked-process-report-event-class.md)|Указывает, что задача заблокирована дольше указанного времени.|  
|[Класс событий CPU Threshold Exceeded](../../relational-databases/event-classes/cpu-threshold-exceeded-event-class.md)|Указывает, что регулятор ресурсов обнаружил запрос, превышающий заданное пороговое значение загрузки ЦП.|  
|[Класс событий ErrorLog](../../relational-databases/event-classes/errorlog-event-class.md)|Показывает, что связанные с ошибками события были записаны в журнал ошибок сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[Класс событий EventLog](../../relational-databases/event-classes/eventlog-event-class.md)|Указывает, что события были записаны в журнал событий Windows.|  
|[Класс событий Exception](../../relational-databases/event-classes/exception-event-class.md)|Указывает, что в сервере [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]произошло исключение.|  
|[Класс событий Exchange Spill](../../relational-databases/event-classes/exchange-spill-event-class.md)|Указывает, что буферы связи в параллельном плане запроса были записаны в базу данных tempdb.|  
|[Класс событий Execution Warnings](../../relational-databases/event-classes/execution-warnings-event-class.md)|Указывает, что за время выполнения инструкции или хранимой процедуры сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] были выданы предупреждения предоставления памяти.|  
|[Класс событий Hash Warning](../../relational-databases/event-classes/hash-warning-event-class.md)|Указывает, что во время операции хэширования произошли рекурсия или аварийное хэширование.|  
|[Класс событий Missing Column Statistics](../../relational-databases/event-classes/missing-column-statistics-event-class.md)|Указывает, что статистические данные столбцов, которые были бы полезны оптимизатору, недоступны.|  
|[Класс событий Missing Join Predicate](../../relational-databases/event-classes/missing-join-predicate-event-class.md)|Указывает, что выполняется запрос, не имеющий предиката соединения.|  
|[Класс событий Sort Warnings](../../relational-databases/event-classes/sort-warnings-event-class.md)|Указывает, что операциям сортировки не хватает памяти.|  
|[Класс событий User Error Message](../../relational-databases/event-classes/user-error-message-event-class.md)|Отображаются сообщения об ошибках, видимые пользователю.|  
  
## <a name="see-also"></a>См. также:  
 [Хранимая процедура sp_trace_setevent (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
  
