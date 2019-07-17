---
title: sys.dm_sql_referencing_entities (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_sql_referencing_entities
- dm_sql_referencing_entities_TSQL
- sys.dm_sql_referencing_entities_TSQL
- dm_sql_referencing_entities
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_sql_referencing_entities dynamic management function
ms.assetid: c16f8f0a-483f-4feb-842e-da90426045ae
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: b5bd5257e06b784418625616c71cfb7d3e5510a8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68090665"
---
# <a name="sysdmsqlreferencingentities-transact-sql"></a>sys.dm_sql_referencing_entities (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает одну строку для каждой сущности текущей базы данных, которая ссылается на имя какой-либо другой определенной пользователем сущности. Зависимость между двумя сущностями создается в том случае, когда некоторой сущности, называемой *упоминаемая сущность*, отображается именем в материализованном выражении SQL другой сущности, называемой *ссылающейся сущностью*. Например, если в качестве упоминаемой сущности, выступает определяемый пользователем тип (UDT), то данная функция возвращает список всех определяемых пользователем сущностей, ссылающихся в своих определениях на имя указанного определяемого пользователем типа. Функция не возвращает список сущностей других баз данных, ссылающихся на указанную сущность. Данная функция предназначена для выполнения в контексте базы данных master и возвращает триггер DDL уровня сервера как ссылающаяся сущность.  
  
 Данная динамическая административная функция может быть использована для отображения списка сущностей текущей базы данных, ссылающихся на заданную сущность и имеющих следующие типы:  
  
-   сущности, как связанные со схемой, так и не связанные;  
  
-   триггеры DDL уровня базы данных;  
  
-   триггеры DDL уровня сервера.  
  
**Применимо к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] по [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]), [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
sys.dm_sql_referencing_entities (  
    ' schema_name.referenced_entity_name ' , ' <referenced_class> ' )  
  
<referenced_class> ::=  
{  
    OBJECT  
  | TYPE  
  | XML_SCHEMA_COLLECTION  
  | PARTITION_FUNCTION  
}  
```  
  
## <a name="arguments"></a>Аргументы  
 *schema_name.referenced*_*entity_name*  
 Имя упоминаемой сущности.  
  
 *schema_name* требуется за исключением случаев, когда упоминаемый класс относится к классу PARTITION_FUNCTION.  
  
 *schema_name.referenced_entity_name* — **nvarchar(517)** .  
  
 *< Referenced_class >* :: = {объект | ТИП | XML_SCHEMA_COLLECTION | PARTITION_FUNCTION}  
 Класс упоминаемой сущности. В одной инструкции может быть указан только один класс.  
  
 *< referenced_class >* — **nvarchar**(60).  
  
## <a name="table-returned"></a>Возвращаемая таблица  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|referencing_schema_name|**sysname**|Схема, которой принадлежит ссылающаяся сущность. Допускает значение NULL.<br /><br /> Значение NULL для триггеров DDL уровня базы данных или сервера.|  
|referencing_entity_name|**sysname**|Имя ссылающейся сущности. Не допускает значение NULL.|  
|referencing_id|**int**|Идентификатор ссылающейся сущности. Не допускает значение NULL.|  
|referencing_class|**tinyint**|Класс ссылающейся сущности. Не допускает значение NULL.<br /><br /> 1 = объект<br /><br /> 12 = триггер DDL уровня базы данных<br /><br /> 13 = триггер DDL уровня сервера|  
|referencing_class_desc|**nvarchar(60)**|Описание класса ссылающейся сущности.<br /><br /> OBJECT<br /><br /> DATABASE_DDL_TRIGGER<br /><br /> SERVER_DDL_TRIGGER|  
|is_caller_dependent|**bit**|Указывает разрешение идентификатора упоминаемой сущности, полученного во время выполнения (так как он зависит от схемы вызывающего объекта).<br /><br /> Значение 1 означает, что ссылающаяся сущность может ссылаться на данный объект. При этом разрешение упоминаемой сущности зависит от вызывающего объекта и не может быть определено. Данная ситуация возможна только при вызове в инструкции EXECUTE не связанной со схемой ссылки на хранимую процедуру, расширенную хранимую процедуру или определяемую пользователем функцию.<br /><br /> Значение 0 означает, что упоминаемая сущность не зависит от вызывающего объекта.|  
  
## <a name="exceptions"></a>Исключения  
 Возвращает пустой результирующий набор, если выполняется любое из следующих условий.  
  
-   Указан системный объект.  
  
-   Указанная сущность не существует в текущей базе данных.  
  
-   Указанная сущность не ссылается ни на какие сущности.  
  
-   Передан недопустимый параметр.  
  
 Возвращает ошибку, если заданная упоминаемая сущность является пронумерованной хранимой процедурой.  
  
## <a name="remarks"></a>Примечания  
 В следующей таблице перечислены типы сущностей, для которых созданы и обновляются данные о зависимостях. Данные о зависимостях не создаются и не обновляются для правил, значений по умолчанию, временных таблиц, временных хранимых процедур и системных объектов.  
  
|Тип сущности|Ссылающаяся сущность|Упоминаемая сущность|  
|-----------------|------------------------|-----------------------|  
|Таблица|Да*|Да|  
|Представление|Да|Да|  
|Хранимая процедура [!INCLUDE[tsql](../../includes/tsql-md.md)]**|Да|Да|  
|Хранимая процедура CLR|Нет|Да|  
|Определяемая пользователем функция [!INCLUDE[tsql](../../includes/tsql-md.md)]|Да|Да|  
|Определяемая пользователем функция CLR|Нет|Да|  
|Триггер CLR (DML и DDL)|Нет|Нет|  
|Триггер DML [!INCLUDE[tsql](../../includes/tsql-md.md)]|Да|Нет|  
|Триггер DDL [!INCLUDE[tsql](../../includes/tsql-md.md)] уровня базы данных|Да|Нет|  
|Триггер DDL [!INCLUDE[tsql](../../includes/tsql-md.md)] уровня сервера|Да|Нет|  
|Расширенные хранимые процедуры|Нет|Да|  
|Очередь|Нет|Да|  
|Синоним|Нет|Да|  
|Тип (псевдоним и определяемый пользователем тип данных CLR)|Нет|Да|  
|Коллекция схем XML|Нет|Да|  
|Функция секционирования|Нет|Да|  
  
 \* Таблица отслеживается как ссылающаяся сущность, только в том случае, если оно ссылается на [!INCLUDE[tsql](../../includes/tsql-md.md)] модуля, определяемый пользователем тип или коллекцию схем XML в определении вычисляемого столбца, ограничения CHECK или ограничении DEFAULT.  
  
 ** Пронумерованные хранимые процедуры с целочисленным значением больше 1 не отслеживаются в качестве ссылающихся или упоминаемых сущностей.  
  
## <a name="permissions"></a>Разрешения  
  
### <a name="includesskatmaiincludessskatmai-mdmd---includesssql11includessssql11-mdmd"></a>[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] - [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
  
-   Необходимо разрешение CONTROL для указанного объекта. Если упоминаемая сущность является функцией секционирования, необходимо разрешение CONTROL на базу данных.  
  
-   Необходимо разрешение SELECT на представление sys.dm_sql_referencing_entities. Разрешение SELECT по умолчанию предоставляется роли public.  
  
### <a name="includesssql14includessssql14-mdmd---includesscurrentincludessscurrent-mdmd"></a>[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] - [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
-   Не требуются какие-либо разрешения на указанный объект. Частичные результаты могут быть возвращены, если пользователь имеет разрешение VIEW DEFINITION лишь на некоторые из указываемых сущностей.  
  
-   Необходимо разрешение VIEW DEFINITION на объект, если ссылающаяся сущность является объектом.  
  
-   Необходимо разрешение VIEW DEFINITION на базу данных, если ссылающаяся сущность является триггером DDL уровня базы данных.  
  
-   Требуется разрешение VIEW ANY DEFINITION на уровне сервера, если ссылающаяся сущность является триггером DDL уровня сервера.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-returning-the-entities-that-refer-to-a-given-entity"></a>A. Получение списка сущностей, ссылающихся на заданную сущность  
 В следующем примере возвращается список сущностей текущей базы данных, которые ссылаются на указанную таблицу.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT referencing_schema_name, referencing_entity_name, referencing_id, referencing_class_desc, is_caller_dependent  
FROM sys.dm_sql_referencing_entities ('Production.Product', 'OBJECT');  
GO  
```  
  
### <a name="b-returning-the-entities-that-refer-to-a-given-type"></a>Б. Получение списка сущностей, ссылающихся на заданный тип  
 В следующем примере возвращается список сущностей, ссылающихся на псевдоним типа `dbo.Flag`. Результирующий набор показывает, что этот тип используется двумя хранимыми процедурами. `dbo.Flag` Тип также используется в определении некоторых столбцов `HumanResources.Employee` таблицы; тем не менее, поскольку тип не является в определении вычисляемого столбца, ПРОВЕРОЧНОЕ ограничение или ограничение по умолчанию в таблице, строки не возвращаются для `HumanResources.Employee`таблицы.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT referencing_schema_name, referencing_entity_name, referencing_id, referencing_class_desc, is_caller_dependent  
FROM sys.dm_sql_referencing_entities ('dbo.Flag', 'TYPE');  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 referencing_schema_name referencing_entity_name   referencing_id referencing_class_desc is_caller_dependent  
 ----------------------- -------------------------  ------------- ---------------------- -------------------  
 HumanResources          uspUpdateEmployeeHireInfo  1803153469    OBJECT_OR_COLUMN       0  
 HumanResources          uspUpdateEmployeeLogin     1819153526    OBJECT_OR_COLUMN       0  
 (2 row(s) affected)`  
 ``` 
 
## <a name="see-also"></a>См. также  
 [sys.dm_sql_referenced_entities (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql.md)   
 [sys.sql_expression_dependencies (Transact-SQL)](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md)  
  
  
