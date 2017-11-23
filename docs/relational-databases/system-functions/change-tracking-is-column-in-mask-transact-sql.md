---
title: "CHANGE_TRACKING_IS_COLUMN_IN_MASK (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/08/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CHANGE_TRACKING_IS_COLUMN_IN_MASK_TSQL
- CHANGE_TRACKING_IS_COLUMN_IN_MASK
dev_langs: TSQL
helpviewer_keywords:
- change tracking [SQL Server], CHANGE_TRACKING_IS_COLUMN_IN_MASK
- CHANGE_TRACKING_IS_COLUMN_IN_MASK
ms.assetid: 649b370b-da54-4915-919d-1b597a39d505
caps.latest.revision: "15"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a75d56944852d39d083bd1a8c075c3efb6aaa723
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="changetrackingiscolumninmask-transact-sql"></a>CHANGE_TRACKING_IS_COLUMN_IN_MASK (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Интерпретирует значение SYS_CHANGE_COLUMNS, возвращаемое функцией CHANGETABLE(CHANGES …). Это позволяет приложению определить, включается ли указанный столбец в набор значений, возвращаемых в качестве значения SYS_CHANGE_COLUMNS.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
CHANGE_TRACKING_IS_COLUMN_IN_MASK ( column_id , change_columns )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Идентификатор column_id*  
 Идентификатор проверяемого столбца. Идентификатор можно получить с помощью столбца [COLUMNPROPERTY](../../t-sql/functions/columnproperty-transact-sql.md) функции.  
  
 *change_columns*  
 Двоичные данные из столбца SYS_CHANGE_COLUMNS [CHANGETABLE](../../relational-databases/system-functions/changetable-transact-sql.md) данных.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 **bit**  
  
## <a name="return-values"></a>Возвращаемые значения  
 Функция CHANGE_TRACKING_IS_COLUMN_IN_MASK возвращает следующие значения.  
  
|Возвращаемое значение|Description|  
|------------------|-----------------|  
|0|Указанный столбец не включен в *change_columns* списка.|  
|1|Указанный столбец включен в *change_columns* списка.|  
  
## <a name="remarks"></a>Замечания  
 CHANGE_TRACKING_IS_COLUMN_IN_MASK не выполняет каких-либо проверок для проверки *column_id* значение или, *change_columns* параметра были получены из таблицы, из которой  *Идентификатор column_id* был получен.  
  
## <a name="examples"></a>Примеры  
 В следующем примере определяется, был ли обновлен столбец `Salary` таблицы `Employees`. `COLUMNPROPERTY` Функция возвращает идентификатор столбца `Salary` столбца. Локальной переменной `@change_columns` должны быть присвоены результаты запроса с использованием результатов функции CHANGETABLE в качестве источника данных.  
  
```tsql  
SET @SalaryChanged = CHANGE_TRACKING_IS_COLUMN_IN_MASK  
    (COLUMNPROPERTY(OBJECT_ID('Employees'), 'Salary', 'ColumnId')  
    ,@change_columns);  
```  
  
## <a name="see-also"></a>См. также:  
 [Функции отслеживания изменений (Transact-SQL)](../../relational-databases/system-functions/change-tracking-functions-transact-sql.md)   
 [CHANGETABLE (Transact-SQL)](../../relational-databases/system-functions/changetable-transact-sql.md)   
 [Отслеживание измененных данных (SQL Server)](../../relational-databases/track-changes/track-data-changes-sql-server.md)  
  
  
