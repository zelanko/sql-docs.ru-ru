---
title: sys.sensitivity_classifications (Transact-SQL) | Документы Microsoft
ms.date: 06/17/2018
ms.reviewer: ''
ms.prod: sql
ms.prod_service: sql-database
ms.service: sql-database
ms.technology: t-sql
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.custom: ''
ms.manager: craigg
ms.author: giladm
author: giladmit
f1_keywords:
- 'sys.sensitivity_classifications '
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sensitivity_classifications statement
- dropping labels
- drop labels
- removing labels
- remove labels
- classification [SQL]
- labels [SQL]
- information types
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: d0adbbeb82c06d6a44f3a7439bcbf479d7358401
ms.sourcegitcommit: 70882926439a63ab9d812809429c63040eb9a41b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36262893"
---
# <a name="syssensitivityclassifications-transact-sql"></a>sys.sensitivity_classifications (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

Возвращает строку для каждого элемента, классифицированные в базе данных.

|Имя столбца|Тип данных|Описание|
|-----------------|---------------|-----------------|  
|**class**|**int**|Идентифицирует класс элемента, на котором существует классификации|  
|**class_desc**|**varchar(16)**|Описание класса элемента, на котором существует классификации|  
|**major_id**|**int**|Идентификатор элемента, на котором существует классификации. < br \>< br \>Если класс является 0, major_id всегда равно 0.<br>Если столбец class равен 1, 2 или 7, то столбец major_id равен столбцу object_id.|  
|**то столбец minor_id**|**int**|Вторичный идентификатор элемента, на который существует классификации, интерпретируемый в соответствии с его классом.<br><br>Если класс = 1, то столбец minor_id равен столбцу column_id (если столбец), в противном случае 0 (если объект).<br>Если столбец class = 2, то столбец minor_id равен столбцу parameter_id.<br>Если класс = 7, то столбец minor_id равен столбцу index_id. |  
|**label**|**sysname**|Метка (читаемого), назначенный для классификации чувствительности|  
|**label_id**|**sysname**|Идентификатор, связанный с меткой, который может использоваться системой защиты информации например защиты информации Azure (Административной)|  
|**information_type**|**sysname**|Тип сведений (читаемого), назначенный для классификации чувствительности|  
|**information_type_id**|**sysname**|Идентификатор, связанный с типом сведения, который может использоваться системой защиты информации например защиты информации Azure (Административной)|  
| &nbsp; | &nbsp; | &nbsp; |

## <a name="remarks"></a>Примечания  

- Это представление обеспечивает видимость классификации состояние базы данных. Он может использоваться для управления классификации базы данных, а также для создания отчетов.
- Поддерживается в настоящее время единственным классификации столбцов базы данных. Таким образом:
    - **Класс** -всегда будет иметь значение 1 (представляющий столбец)
    - **class_desc** -всегда будет иметь значение *OBJECT_OR_COLUMN*
    - **major_id** -представляет идентификатор таблицы, содержащей классифицированного столбца, соответствующего sys.all_objects.object_id
    - **то столбец minor_id** -представляет идентификатор столбца, на который классификации существует, соответствующий sys.all_columns.column_id

## <a name="examples"></a>Примеры

### <a name="a-listing-all-classified-columns-and-their-corresponding-classification"></a>A. Список всех классифицированные столбцы и их соответствующие классификации

Следующий пример возвращает таблицу со списком Имя таблицы, имя столбца, метки, метка идентификатора типа данных идентификатор типа сведения для каждого классифицированного столбца в базе данных.

```sql
SELECT
    sys.all_objects.name AS TableName, sys.all_columns.name As ColumnName,
    Label, Label_ID, Information_Type, Information_Type_ID
FROM
          sys.sensitivity_classifications
left join sys.all_objects on sys.sensitivity_classifications.major_id = sys.all_objects.object_id
left join sys.all_columns on sys.sensitivity_classifications.major_id = sys.all_columns.object_id
                         and sys.sensitivity_classifications.minor_id = sys.all_columns.column_id
```

## <a name="see-also"></a>См. также  

[ДОБАВИТЬ CLASSIFICTION ЧУВСТВИТЕЛЬНОСТИ (Transact-SQL)](../../t-sql/statements/add-sensitivity-classification-transact-sql.md)

[УДАЛИТЬ CLASSIFICTION ЧУВСТВИТЕЛЬНОСТИ (Transact-SQL)](../../t-sql/statements/drop-sensitivity-classification-transact-sql.md)

[Приступая к работе с SQL Information Protection](http://aka.ms/sqlip)
