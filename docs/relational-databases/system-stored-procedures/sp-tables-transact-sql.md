---
title: sp_tables (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_tables
- sp_tables_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_tables
ms.assetid: 787a2fa5-87a1-49bd-938b-6043c245f46b
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 71aaa9e52cfca8435501695a4ebf60b2a6aa6ee4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68096049"
---
# <a name="sptables-transact-sql"></a>sp_tables (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает список объектов, к которым можно выполнять запросы в текущем окружении. Это означает применение любой таблицы или представления, кроме объектов-синонимов.  
  
> [!NOTE]  
>  Чтобы определить имя базового объекта синонима, запросите [sys.synonyms](../../relational-databases/system-catalog-views/sys-synonyms-transact-sql.md) представления каталога.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
sp_tables [ [ @table_name = ] 'name' ]   
     [ , [ @table_owner = ] 'owner' ]   
     [ , [ @table_qualifier = ] 'qualifier' ]   
     [ , [ @table_type = ] "type" ]   
     [ , [@fUsePattern = ] 'fUsePattern'];  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @table_name = ] 'name'` Таблица, используемая для возврата сведений о каталоге. *имя* — **nvarchar(384)** , значение по умолчанию NULL. Поиск совпадений по шаблону поддерживается.  
  
`[ @table_owner = ] 'owner'` Является владельцем таблицы, таблицы, используемой для возврата сведений о каталоге. *владелец* — **nvarchar(384)** , значение по умолчанию NULL. Поиск совпадений по шаблону поддерживается. Если владелец не указан, применяются правила видимости таблиц по умолчанию базовой СУБД.  
  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], если текущий пользователь является владельцем таблицы с указанным именем, возвращаются ее столбцы. Если пользователь не указан, а текущий пользователь не является владельцем таблицы с заданным именем, процедура ищет таблицу с заданным именем, которая принадлежит владельцу базы данных. Если такая таблица существует, возвращаются ее столбцы.  
  
`[ @table_qualifier = ] 'qualifier'` — Имя квалификатора таблицы. *квалификатор* — **sysname**, значение по умолчанию NULL. Различные продукты СУБД поддерживают трехкомпонентные имена таблиц (_квалификатор_ **.** _владельца_ **.** _имя_). В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] этот столбец представляет имя базы данных. В некоторых СУБД он представляет имя сервера в среде базы данных, где находится таблица.  
  
``[ , [ @table_type = ] "'type', 'type'" ]`` Приведен список значений, разделенных запятыми, который предоставляет сведения обо всех таблицах табличными типами, которые указаны. К ним относятся **таблицы**, **SYSTEMTABLE**, и **ПРЕДСТАВЛЕНИЕ**. *Тип* — **varchar(100)** , значение по умолчанию NULL.  
  
> [!NOTE]  
>  Каждый табличный тип должен быть заключен в одиночные кавычки, а весь параметр должен быть заключен в двойные кавычки. Типы таблиц должны указываться в верхнем регистре. Если настройка SET QUOTED_IDENTIFIER установлена в ON, то каждый тип таблицы должен быть заключен в двойные кавычки, а весь параметр должен быть заключен в одинарные кавычки.  
  
`[ @fUsePattern = ] 'fUsePattern'` Определяет, следует ли рассматривать подчеркивание (_), процента (%) и скобок ([и]) символы как символы-шаблоны. Допустимые значения: 0 (сопоставление с шаблоном отключено) и 1 (сопоставление с шаблоном включено). *Шаблонов* — **бит**, значение по умолчанию 1.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 None  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**TABLE_QUALIFIER**|**sysname**|Имя квалификатора таблицы. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] этот столбец представляет имя базы данных. Это поле может иметь значение NULL.|  
|**TABLE_OWNER**|**sysname**|Имя владельца таблицы. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] этот столбец представляет имя пользователя базы данных, создавшего таблицу. Это поле всегда возвращает значение.|  
|**ИМЯ_ТАБЛИЦЫ**|**sysname**|Имя таблицы. Это поле всегда возвращает значение.|  
|**TABLE_TYPE**|**varchar(32)**|Таблица, системная таблица или представление.|  
|**"ПРИМЕЧАНИЯ"**|**varchar(254)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не возвращает значение для этого столбца.|  
  
## <a name="remarks"></a>Примечания  
 Для максимальной совместимости клиент шлюза должен принимать только сопоставление шаблонов стандарта SQL-92 (символы-шаблоны «%» и «_»).  
  
 Данные о правах доступа текущего пользователя на чтение и запись в конкретную таблицу не всегда проверяются. Поэтому доступ не гарантируется. Этот результирующий набор включает не только таблицы и представления, но и синонимы, и псевдонимы для шлюзов к СУБД, поддерживающим эти типы. Если атрибут сервера **ACCESSIBLE_TABLES** указано значение Y в результирующем наборе для **sp_server_info**, возвращаются только те таблицы, доступных для текущего пользователя.  
  
 **sp_tables** эквивалентен **SQLTables** в ODBC. Возвращенные результаты сортируются по **TABLE_TYPE**, **TABLE_QUALIFIER**, **TABLE_OWNER**, и **TABLE_NAME**.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение SELECT для схемы.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-returning-a-list-of-objects-that-can-be-queried-in-the-current-environment"></a>A. Возврат списка объектов, к которым можно выполнять запросы в текущем окружении  
 Следующий пример возвращает список объектов, которые могут быть запросами в текущем окружении.  
  
```  
EXEC sp_tables ;  
```  
  
### <a name="b-returning-information-about-the-tables-in-a-specified-schema"></a>Б. Возврат сведений о таблицах в указанной схеме  
 В следующем примере возвращаются сведения о таблицах, принадлежащих схеме `Person` в базе данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_tables   
   @table_name = '%',  
   @table_owner = 'Person',  
   @table_qualifier = 'AdventureWorks2012';  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-returning-a-list-of-objects-that-can-be-queried-in-the-current-environment"></a>В. Возврат списка объектов, к которым можно выполнять запросы в текущем окружении  
 Следующий пример возвращает список объектов, которые могут быть запросами в текущем окружении.  
  
```  
EXEC sp_tables ;  
```  
  
### <a name="d-returning-information-about-the-tables-in-a-specified-schema"></a>Г. Возврат сведений о таблицах в указанной схеме  
 Следующий пример возвращает сведения о таблицах измерений в `AdventureWorksPDW201` базы данных.  
  
```  
-- Uses AdventureWorks  
  
EXEC sp_tables   
   @table_name = 'Dim%',  
   @table_owner = 'dbo',  
   @table_qualifier = 'AdventureWorksPDW2012';  
```  
  
## <a name="see-also"></a>См. также  
 [sys.synonyms &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-synonyms-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

