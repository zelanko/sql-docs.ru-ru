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
- rank
monikerRange: '>= sql-server-ver15 || = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 4ee73a840be6ec29e3ac34c4c43fe0c8e87185f6
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "77903913"
---
# <a name="syssensitivity_classifications-transact-sql"></a>sys.sensitivity_classifications (Transact-SQL)
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

Возвращает строку для каждого классифицированного элемента в базе данных.

|Имя столбца|Тип данных|Описание|
|-----------------|---------------|-----------------|  
|**class**|**int**|Определяет класс элемента, для которого существует классификация. Всегда будет иметь значение 1 (представляет столбец)|  
|**class_desc**|**varchar (16)**|Описание класса элемента, для которого существует классификация. всегда будет иметь значение *OBJECT_OR_COLUMN*|  
|**major_id**|**int**|Представляет идентификатор таблицы, содержащей классифицированный столбец, соответствующий sys. all_objects. object_id|  
|**minor_id**|**int**|Представляет идентификатор столбца, на котором существует классификация, соответствующая sys. all_columns. column_id|   
|**label**|**sysname**|Метка (удобное для чтения), назначенная для классификации чувствительности|  
|**label_id**|**sysname**|Идентификатор, связанный с меткой, который может использоваться системой защиты информации, например Azure Information Protection (точка административного установки).|  
|**information_type**|**sysname**|Тип сведений (для человека), назначенный для классификации чувствительности|  
|**information_type_id**|**sysname**|Идентификатор, связанный с типом данных, который может использоваться системой защиты информации, например Azure Information Protection (точка административного ввода).|  
|**Рейтинг**|**int**|Числовое значение ранга: <br><br>0 для NONE<br>10 для низкого уровня<br>20 для средних<br>30 для HIGH<br>40 для КРИТИЧЕСКИх| 
|**rank_desc**|**sysname**|Текстовое представление ранга:  <br><br>НЕТ, НИЗКИЙ, СРЕДНИЙ, ВЫСОКИЙ, КРИТИЧЕСКИЙ|  
| &nbsp; | &nbsp; | &nbsp; |

## <a name="remarks"></a>Remarks  

- Это представление позволяет видеть состояние классификации базы данных. Его можно использовать для управления классификациями баз данных, а также для создания отчетов.
- В настоящее время поддерживается только классификация столбцов базы данных.
 
## <a name="examples"></a>Примеры

### <a name="a-listing-all-classified-columns-and-their-corresponding-classification"></a>A. Составление списка всех классифицированных столбцов и соответствующих им классификаций

В следующем примере возвращается таблица с перечнем имени таблицы, имени столбца, метки, идентификатора метки, типа сведений, идентификатора информационного типа для каждого классифицированного столбца в базе данных.

> [!NOTE]
> Метка — это ключевое слово для хранилища данных SQL Azure.

```sql
SELECT
    SCHEMA_NAME(sys.all_objects.schema_id) as SchemaName,
    sys.all_objects.name AS [TableName], sys.all_columns.name As [ColumnName],
    [Label], [Label_ID], [Information_Type], [Information_Type_ID], [Rank], [Rank_Desc]
FROM
          sys.sensitivity_classifications
left join sys.all_objects on sys.sensitivity_classifications.major_id = sys.all_objects.object_id
left join sys.all_columns on sys.sensitivity_classifications.major_id = sys.all_columns.object_id
                         and sys.sensitivity_classifications.minor_id = sys.all_columns.column_id
```

## <a name="permissions"></a>Разрешения  
 Требует разрешения на **Просмотр любого чувствительности** . 
 
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  

## <a name="see-also"></a>См. также:  

[ADD SENSITIVITY CLASSIFICATION (Transact-SQL)](../../t-sql/statements/add-sensitivity-classification-transact-sql.md)

[DROP SENSITIVITY CLASSIFICATION (Transact-SQL)](../../t-sql/statements/drop-sensitivity-classification-transact-sql.md)

[Начало работы с SQL Information Protection](https://aka.ms/sqlip)
