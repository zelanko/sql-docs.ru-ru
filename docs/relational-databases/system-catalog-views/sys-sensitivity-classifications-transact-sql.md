---
title: sys.sensitivity_classifications (Transact-SQL) | Документация Майкрософт
ms.date: 06/17/2018
ms.reviewer: ''
ms.prod: sql
ms.technology: t-sql
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
ms.openlocfilehash: 0fb7b7719ce53fe4f20863cb3f44c9483bc6b472
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51660353"
---
# <a name="syssensitivityclassifications-transact-sql"></a>sys.sensitivity_classifications (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

Возвращает строку для каждого элемента, классифицированные в базе данных.

|Имя столбца|Тип данных|Описание|
|-----------------|---------------|-----------------|  
|**class**|**int**|Идентифицирует класс элемента, на котором существует классификации|  
|**class_desc**|**varchar(16)**|Описание класса элемента, на котором существует классификации|  
|**major_id**|**int**|Идентификатор элемента, на котором существует классификации. < br \>< br \>Если класс является 0, major_id всегда равно 0.<br>Если столбец class равен 1, 2 или 7, то столбец major_id равен столбцу object_id.|  
|**minor_id**|**int**|Вторичный идентификатор элемента, на который существует классификацию, интерпретируемый в соответствии с его классом.<br><br>Если класс = 1, то столбец minor_id равен столбцу column_id (если столбец), в противном случае 0 (если объект).<br>Если столбец class = 2, то столбец minor_id равен столбцу parameter_id.<br>Если класс = 7, то столбец minor_id равен столбцу index_id. |  
|**label**|**sysname**|Метка (удобным для чтения), назначенный для классификации конфиденциальности|  
|**label_id**|**sysname**|Идентификатор, связанный с меткой, который может использоваться, например Azure Information Protection (AIP) системы защиты информации|  
|**information_type**|**sysname**|Тип сведений (удобным для чтения), назначенный для классификации конфиденциальности|  
|**information_type_id**|**sysname**|Идентификатор, связанный с типом сведений, который может использоваться, например Azure Information Protection (AIP) системы защиты информации|  
| &nbsp; | &nbsp; | &nbsp; |

## <a name="remarks"></a>Примечания  

- Это представление позволяет просматривать состояние классификации базы данных. Его можно использовать для управления классификации базы данных, а также для создания отчетов.
- Сейчас только классификации столбцов базы данных поддерживается. Таким образом:
    - **Класс** -всегда будет иметь значение 1 (представляющий столбец)
    - **class_desc** -всегда будет иметь значение *OBJECT_OR_COLUMN*
    - **major_id** -представляет идентификатор таблицы, содержащей классифицированного столбца, соответствующего sys.all_objects.object_id
    - **minor_id** -представляет идентификатор столбца, на который классификации существует, соответствующий sys.all_columns.column_id

## <a name="examples"></a>Примеры

### <a name="a-listing-all-classified-columns-and-their-corresponding-classification"></a>A. Список всех классифицированных столбцов и их соответствующие классификации

В следующем примере возвращаются таблицы со списком Имя таблицы, имя столбца, метку, метка идентификатор, тип данных, идентификатор типа информации для каждого классифицированного столбца в базе данных.

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

[ADD SENSITIVITY CLASSIFICTION (Transact-SQL)](../../t-sql/statements/add-sensitivity-classification-transact-sql.md)

[DROP SENSITIVITY CLASSIFICTION (Transact-SQL)](../../t-sql/statements/drop-sensitivity-classification-transact-sql.md)

[Начало работы с SQL Information Protection](https://aka.ms/sqlip)
