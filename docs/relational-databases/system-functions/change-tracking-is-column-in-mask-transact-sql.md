---
title: CHANGE_TRACKING_IS_COLUMN_IN_MASK (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/08/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- CHANGE_TRACKING_IS_COLUMN_IN_MASK_TSQL
- CHANGE_TRACKING_IS_COLUMN_IN_MASK
dev_langs:
- TSQL
helpviewer_keywords:
- change tracking [SQL Server], CHANGE_TRACKING_IS_COLUMN_IN_MASK
- CHANGE_TRACKING_IS_COLUMN_IN_MASK
ms.assetid: 649b370b-da54-4915-919d-1b597a39d505
author: rothja
ms.author: jroth
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: a6f7e9d8d9ab99ebe4a7c5749033eacf85b8feb5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68042994"
---
# <a name="change_tracking_is_column_in_mask-transact-sql"></a>CHANGE_TRACKING_IS_COLUMN_IN_MASK (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Интерпретирует значение SYS_CHANGE_COLUMNS, возвращаемое функцией CHANGETABLE (CHANGEs...). Это позволяет приложению определить, включается ли указанный столбец в набор значений, возвращаемых в качестве значения SYS_CHANGE_COLUMNS.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
CHANGE_TRACKING_IS_COLUMN_IN_MASK ( column_id , change_columns )  
```  
  
## <a name="arguments"></a>Аргументы  
 *column_id*  
 Идентификатор проверяемого столбца. Идентификатор столбца можно получить с помощью функции [COLUMNPROPERTY](../../t-sql/functions/columnproperty-transact-sql.md) .  
  
 *change_columns*  
 Двоичные данные из столбца SYS_CHANGE_COLUMNS данных [CHANGETABLE](../../relational-databases/system-functions/changetable-transact-sql.md) .  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 **bit**  
  
## <a name="return-values"></a>Возвращаемые значения  
 Функция CHANGE_TRACKING_IS_COLUMN_IN_MASK возвращает следующие значения.  
  
|Возвращаемое значение|Описание|  
|------------------|-----------------|  
|0|Указанный столбец отсутствует в списке *change_columns* .|  
|1|Указанный столбец находится в списке *change_columns* .|  
  
## <a name="remarks"></a>Remarks  
 CHANGE_TRACKING_IS_COLUMN_IN_MASK не выполняет никаких проверок для проверки значения *column_id* или того, что параметр *change_columns* был получен из таблицы, из которой было получено *column_id* .  
  
## <a name="examples"></a>Примеры  
 В следующем примере определяется, был ли обновлен столбец `Salary` таблицы `Employees`. `COLUMNPROPERTY` Функция возвращает идентификатор `Salary` столбца. Локальной переменной `@change_columns` должны быть присвоены результаты запроса с использованием результатов функции CHANGETABLE в качестве источника данных.  
  
```sql  
SET @SalaryChanged = CHANGE_TRACKING_IS_COLUMN_IN_MASK  
    (COLUMNPROPERTY(OBJECT_ID('Employees'), 'Salary', 'ColumnId')  
    ,@change_columns);  
```  
  
## <a name="see-also"></a>См. также:  
 [Функции Отслеживание изменений &#40;Transact-SQL&#41;](../../relational-databases/system-functions/change-tracking-functions-transact-sql.md)   
 [&#40;"CHANGETABLE" Transact-SQL&#41;](../../relational-databases/system-functions/changetable-transact-sql.md)   
 [Отслеживание измененных данных (SQL Server)](../../relational-databases/track-changes/track-data-changes-sql-server.md)  
  
  
