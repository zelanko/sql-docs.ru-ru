---
title: Категория событий "Ошибки и предупреждения" (ядро СУБД) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
topic_type:
- apiref
helpviewer_keywords:
- Errors and Warnings event category [SQL Server]
- SQL Server event classes, Errors and Warnings event category
- event classes [SQL Server], Errors and Warnings event category
ms.assetid: 249c19b5-af68-4433-80f6-337395176641
caps.latest.revision: 28
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2a91599ccb601c1072ad05e1294c176f30d63a26
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36098649"
---
# <a name="errors-and-warnings-event-category-database-engine"></a>Категория событий Errors and Warnings (компонент Database Engine)
  В категорию событий **Ошибки и предупреждения** входят общие события ошибок и предупреждений.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Класс событий Attention](attention-event-class.md)|Указывает, что произошло событие **Внимание** .|  
|[Класс событий Background Job Error](background-job-error-event-class.md)|Указывает, что фоновое задание завершилось ненормально.|  
|[Класс событий Bitmap Warning](bitmap-warning-event-class.md)|Указывает, что в запросе отключена фильтрация по битовым картам.|  
|[Класс событий Blocked Process Report](blocked-process-report-event-class.md)|Указывает, что задача заблокирована дольше указанного времени.|  
|[Класс событий CPU Threshold Exceeded](cpu-threshold-exceeded-event-class.md)|Указывает, что регулятор ресурсов обнаружил запрос, превышающий заданное пороговое значение загрузки ЦП.|  
|[Класс событий ErrorLog](errorlog-event-class.md)|Показывает, что связанные с ошибками события были записаны в журнал ошибок сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[Класс событий EventLog](eventlog-event-class.md)|Указывает, что события были записаны в журнал событий Windows.|  
|[Класс событий Exception](exception-event-class.md)|Указывает, что в сервере [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]произошло исключение.|  
|[Класс событий Exchange Spill](exchange-spill-event-class.md)|Указывает, что буферы связи в параллельном плане запроса были записаны в базу данных tempdb.|  
|[Класс событий Execution Warnings](execution-warnings-event-class.md)|Указывает, что за время выполнения инструкции или хранимой процедуры сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] были выданы предупреждения предоставления памяти.|  
|[Класс событий Hash Warning](hash-warning-event-class.md)|Указывает, что во время операции хэширования произошли рекурсия или аварийное хэширование.|  
|[Класс событий Missing Column Statistics](missing-column-statistics-event-class.md)|Указывает, что статистические данные столбцов, которые были бы полезны оптимизатору, недоступны.|  
|[Класс событий Missing Join Predicate](missing-join-predicate-event-class.md)|Указывает, что выполняется запрос, не имеющий предиката соединения.|  
|[Класс событий Sort Warnings](sort-warnings-event-class.md)|Указывает, что операциям сортировки не хватает памяти.|  
|[Класс событий User Error Message](user-error-message-event-class.md)|Отображаются сообщения об ошибках, видимые пользователю.|  
  
## <a name="see-also"></a>См. также  
 [Хранимая процедура sp_trace_setevent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
