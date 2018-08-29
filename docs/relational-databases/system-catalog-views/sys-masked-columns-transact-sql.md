---
title: sys.masked_columns (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 02/25/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.masked_columns
- masked_columns_tsql
- sys.masked_columns_tsql
- masked_columns
helpviewer_keywords:
- sys.masked_columns catalog view
ms.assetid: 671577e4-d757-4b8d-9aa9-0fc8d51ea9ca
caps.latest.revision: 9
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 3a4c0fec8610dbc38c039428823e35d116889843
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43110818"
---
# <a name="sysmaskedcolumns-transact-sql"></a>sys.masked_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Используйте **sys.masked_columns** представление для запроса для столбцов таблицы, имеющие динамического применена функция маскирования данных. Это представление наследуется из представления **sys.columns** . Оно возвращает все столбцы в представлении **sys.columns** , а также столбцы **is_masked** и **masking_function** , указывающие, маскирован ли столбец, и если да, то какая функция маскирования определена. В этом представлении отображаются только столбцы, к которым применена функция маскирования.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|object_id|**int**|Идентификатор объекта, которому принадлежит этот столбец.|  
|name|**sysname**|Имя столбца. Уникален в пределах объекта.|  
|column_id|**int**|Идентификатор столбца. Уникален в пределах объекта.<br /><br /> Идентификаторы столбца могут быть непоследовательными.|  
|**sys.masked_columns** возвращает многие дополнительные столбцы, наследуемые от **sys.columns**.|различные|См. в разделе [sys.columns &#40;Transact-SQL&#41; ](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md) для Дополнительные определения столбцов.|  
|is_masked|**bit**|Указывает, если столбец скрыт. 1 указывает маской.|  
|masking_function|**nvarchar(4000)**|Функция маскирования для столбца.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="permissions"></a>Разрешения  
 Это представление возвращает сведения о таблицах, в которых пользователь имеет какую-либо разрешений на таблицу или если у пользователя есть разрешение VIEW ANY DEFINITION.  
  
## <a name="example"></a>Пример  
 В следующем запросе соединения **sys.masked_columns** для **sys.tables** для возврата сведений обо всех маскируются столбцов.  
  
```  
SELECT tbl.name as table_name, c.name AS column_name, c.is_masked, c.masking_function  
FROM sys.masked_columns AS c  
JOIN sys.tables AS tbl   
    ON c.object_id = tbl.object_id  
WHERE is_masked = 1;  
```  
  
## <a name="see-also"></a>См. также  
 [Динамическое маскирование данных](../../relational-databases/security/dynamic-data-masking.md)   
 [sys.columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)  
  
  
