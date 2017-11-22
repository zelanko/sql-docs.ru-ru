---
title: "sys.fn_validate_plan_guide (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.fn_validate_plan_guide
- sys.fn_validate_plan_guide_TSQL
- fn_validate_plan_guide
- fn_validate_plan_guide_TSQL
dev_langs: TSQL
helpviewer_keywords:
- fn_validate_plan_guide function
- sys.fn_validate_plan_guide function
ms.assetid: 3af8b47a-936d-4411-91d1-d2d16dda5623
caps.latest.revision: "19"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: fbca0ca02e994a3c286cea445965edd9cd53bfcf
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysfnvalidateplanguide-transact-sql"></a>sys.fn_validate_plan_guide (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Проверяет допустимость указанного руководства плана. Функция sys.fn_validate_plan_guide возвращает первое сообщение об ошибке, выдаваемое при применении структуры плана к запросу. Если структура плана допустима, возвращается пустой набор строк. Структуры планов могут стать недопустимыми после внесения изменений в физическую структуру базы данных. Например, если в структуре плана указан конкретный индекс, который впоследствии удаляется, данная структура плана больше не может быть использована для запроса.  
  
 С помощью проверки допустимости структуры плана можно определить, возможно ли ее использование оптимизатором без изменения. Основываясь на результатах выполнения функции, можно принять решение об удалении структуры плана и повторной настройке запроса или об изменении структуры базы данных, например с помощью повторного создания индекса, указанного в структуре плана.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
sys.fn_validate_plan_guide ( plan_guide_id )  
```  
  
## <a name="arguments"></a>Аргументы  
 *plan_guide_id*  
 Представляет собой идентификатор структуры плана, указанная в [sys.plan_guides](../../relational-databases/system-catalog-views/sys-plan-guides-transact-sql.md) представления каталога. *plan_guide_id* — **int** без значения по умолчанию.  
  
## <a name="table-returned"></a>Возвращаемая таблица  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|msgnum|**int**|Идентификатор сообщения об ошибке.|  
|severity|**tinyint**|Степень серьезности сообщения, от 1 до 25.|  
|state|**smallint**|Номер состояния ошибки, отмеченной точкой в коде, в котором она произошла.|  
|message|**nvarchar(2048)**|Текст сообщения ошибки.|  
  
## <a name="permissions"></a>Permissions  
 Для руководств планов области OBJECT требуются разрешения VIEW DEFINITION или ALTER на соответствующий объект и разрешения на компиляцию запроса или пакета, представленного в структуре плана. Например, если пакет содержит инструкции SELECT, необходимы разрешения SELECT на соответствующие объекты.  
  
 Для структур планов области SQL или TEMPLATE требуются разрешение ALTER на базу данных и разрешения на компиляцию запроса или пакета, представленного в структуре плана. Например, если пакет содержит инструкции SELECT, необходимы разрешения SELECT на соответствующие объекты.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-validating-all-plan-guides-in-a-database"></a>A. Проверка допустимости всех руководств планов в базе данных  
 В следующем примере выполняется проверка допустимости всех структур планов в текущей базе данных. Если возвращается пустой результирующий набор строк, значит все структуры планов допустимы.  
  
```tsql  
USE AdventureWorks2012;  
GO  
SELECT plan_guide_id, msgnum, severity, state, message  
FROM sys.plan_guides  
CROSS APPLY fn_validate_plan_guide(plan_guide_id);  
GO  
```  
  
### <a name="b-testing-plan-guide-validation-before-implementing-a-change-to-the-database"></a>Б. Тестирование проверки руководства плана перед изменением базы данных  
 В следующем примере используется явная транзакция для удаления индекса. `sys.fn_validate_plan_guide` Выполняется функция, чтобы определить, является ли это действие сделает недействительными все руководства планов в базе данных. В зависимости от результатов выполнения этой функции инструкция `DROP INDEX` фиксируется либо выполняется откат транзакции, а индекс не удаляется.  
  
```tsql  
USE AdventureWorks2012;  
GO  
BEGIN TRANSACTION;  
DROP INDEX IX_SalesOrderHeader_CustomerID ON Sales.SalesOrderHeader;  
-- Check for invalid plan guides.  
IF EXISTS (SELECT plan_guide_id, msgnum, severity, state, message  
           FROM sys.plan_guides  
           CROSS APPLY sys.fn_validate_plan_guide(plan_guide_id))  
    ROLLBACK TRANSACTION;  
ELSE  
    COMMIT TRANSACTION;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Руководства планов](../../relational-databases/performance/plan-guides.md)   
 [sp_create_plan_guide (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)   
 [sp_create_plan_guide_from_handle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
  
