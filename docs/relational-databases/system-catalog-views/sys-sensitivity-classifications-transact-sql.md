---
title: sys. sensitivity_classifications (Transact-SQL) | Документация Майкрософт
ms.date: 03/25/2019
ms.reviewer: ''
ms.prod: sql
ms.technology: t-sql
ms.topic: language-reference
ms.custom: ''
ms.author: mibar
author: barmichal
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
ms.openlocfilehash: a9d14cd93b08c0094ad984a6469b433e0b266479
ms.sourcegitcommit: 77293fb1f303ccfd236db9c9041d2fb2f64bce42
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929782"
---
# <a name="syssensitivity_classifications-transact-sql"></a>sys. sensitivity_classifications (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

Возвращает строку для каждого классифицированного элемента в базе данных.

|Имя столбца|Тип данных|Описание|
|-----------------|---------------|-----------------|  
|**class**|**int**|Определяет класс элемента, для которого существует классификация|  
|**class_desc**|**varchar (16)**|Описание класса элемента, для которого существует классификация|  
|**major_id**|**int**|Идентификатор элемента, для которого существует классификация. < br \>< br \>если класс равен 0, major_id всегда имеет значение 0.<br>Если столбец class равен 1, 2 или 7, то столбец major_id равен столбцу object_id.|  
|**minor_id**|**int**|Вторичный идентификатор элемента, для которого существует классификация, интерпретируемый в соответствии с ее классом.<br><br>Если Class = 1, minor_id является column_id (если столбец), в противном случае — 0 (если объект).<br>Если столбец class = 2, то столбец minor_id равен столбцу parameter_id.<br>Если Class = 7, minor_id является значением index_id. |  
|**label**|**sysname**|Метка (удобное для чтения), назначенная для классификации чувствительности|  
|**label_id**|**sysname**|Идентификатор, связанный с меткой, который может использоваться системой защиты информации, например Azure Information Protection (точка административного установки).|  
|**information_type**|**sysname**|Тип сведений (для человека), назначенный для классификации чувствительности|  
|**information_type_id**|**sysname**|Идентификатор, связанный с типом данных, который может использоваться системой защиты информации, например Azure Information Protection (точка административного ввода).|  
| &nbsp; | &nbsp; | &nbsp; |

## <a name="remarks"></a>Примечания  

- Это представление позволяет видеть состояние классификации базы данных. Его можно использовать для управления классификациями баз данных, а также для создания отчетов.
- В настоящее время поддерживается только классификация столбцов базы данных. Результате
    - **класс** — всегда будет иметь значение 1 (представляет столбец)
    - **class_desc** — всегда будет иметь значение *OBJECT_OR_COLUMN*
    - **major_id** — представляет идентификатор таблицы, содержащей классифицированный столбец, соответствующий sys. ALL _objects. object_id
    - **minor_id** — представляет идентификатор столбца, на котором существует классификация, соответствующий sys. ALL _columns. column_id

## <a name="examples"></a>Примеры

### <a name="a-listing-all-classified-columns-and-their-corresponding-classification"></a>A. Составление списка всех классифицированных столбцов и соответствующих им классификаций

В следующем примере возвращается таблица с перечнем имени таблицы, имени столбца, метки, идентификатора метки, типа сведений, идентификатора информационного типа для каждого классифицированного столбца в базе данных.

> [!NOTE]
> Метка — это ключевое слово для хранилища данных SQL Azure.

```sql
SELECT
    SCHEMA_NAME(sys.all_objects.schema_id) as SchemaName,
    sys.all_objects.name AS [TableName], sys.all_columns.name As [ColumnName],
    [Label], [Label_ID], [Information_Type], [Information_Type_ID]
FROM
          sys.sensitivity_classifications
left join sys.all_objects on sys.sensitivity_classifications.major_id = sys.all_objects.object_id
left join sys.all_columns on sys.sensitivity_classifications.major_id = sys.all_columns.object_id
                         and sys.sensitivity_classifications.minor_id = sys.all_columns.column_id
```

## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  

## <a name="see-also"></a>См. также  

[ADD SENSITIVITY CLASSIFICATION (Transact-SQL)](../../t-sql/statements/add-sensitivity-classification-transact-sql.md)

[DROP SENSITIVITY CLASSIFICATION (Transact-SQL)](../../t-sql/statements/drop-sensitivity-classification-transact-sql.md)

[Начало работы с SQL Information Protection](https://aka.ms/sqlip)
