---
title: "sys.masked_columns (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 02/25/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.masked_columns
- masked_columns_tsql
- sys.masked_columns_tsql
- masked_columns
helpviewer_keywords:
- sys.masked_columns catalog view
ms.assetid: 671577e4-d757-4b8d-9aa9-0fc8d51ea9ca
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7855e2d4ccf46977138cff813d27266d90e0fa86
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="sysmaskedcolumns-transact-sql"></a>sys.masked_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Используйте **sys.masked_columns** представление для выполнения запросов для столбцов таблицы, имеющие динамического применена функция маскирования данных. Это представление наследуется из представления **sys.columns** . Оно возвращает все столбцы в представлении **sys.columns** , а также столбцы **is_masked** и **masking_function** , указывающие, маскирован ли столбец, и если да, то какая функция маскирования определена. В этом представлении отображаются только столбцы, к которым применена функция маскирования.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|object_id|**int**|Идентификатор объекта, которому принадлежит этот столбец.|  
|имя|**sysname**|Имя столбца. Уникален в пределах объекта.|  
|column_id|**int**|Идентификатор столбца. Уникален в пределах объекта.<br /><br /> Идентификаторы столбца могут быть непоследовательными.|  
|**sys.masked_columns** возвращает многие дополнительные столбцы, наследуемые от **sys.columns**.|различные|В разделе [sys.columns &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md) для определения дополнительных столбцов.|  
|is_masked|**bit**|Указывает, если столбец скрыт. 1 означает скрытый.|  
|masking_function|**nvarchar(4000)**|Функция маскирования для столбца.|  
  
## <a name="remarks"></a>Замечания  
  
## <a name="permissions"></a>Permissions  
 Это представление возвращает сведения о таблицах, где пользователь, есть разрешения на таблицу или если пользователь имеет разрешение VIEW ANY DEFINITION.  
  
## <a name="example"></a>Пример  
 В следующем запросе соединения **sys.masked_columns** для **sys.tables** для возврата сведений обо всех маскированные столбцы.  
  
```  
SELECT tbl.name as table_name, c.name AS column_name, c.is_masked, c.masking_function  
FROM sys.masked_columns AS c  
JOIN sys.tables AS tbl   
    ON c.object_id = tbl.object_id  
WHERE is_masked = 1;  
```  
  
## <a name="see-also"></a>См. также:  
 [Маскирование динамических данных](../../relational-databases/security/dynamic-data-masking.md)   
 [sys.columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)  
  
  
