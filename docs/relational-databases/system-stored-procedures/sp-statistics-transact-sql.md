---
title: sp_statistics (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_statistics_TSQL
- sp_statistics
dev_langs:
- TSQL
helpviewer_keywords:
- sp_statistics
ms.assetid: 0bb6495f-258a-47ec-9f74-fd16671d23b8
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d72e2c9f79e2029e26275be46e200d476dbf621a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47704552"
---
# <a name="spstatistics-transact-sql"></a>sp_statistics (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает список всех индексов и статистику для указанной таблицы или индексированного представления.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
sp_statistics [ @table_name = ] 'table_name'    
     [ , [ @table_owner = ] 'owner' ]   
     [ , [ @table_qualifier = ] 'qualifier' ]   
     [ , [ @index_name = ] 'index_name' ]   
     [ , [ @is_unique = ] 'is_unique' ]  
     [ , [ @accuracy = ] 'accuracy' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@table_name=** ] **"***table_name***"**  
 Указывает таблицу, используемую для возврата сведений о каталоге. *TABLE_NAME* — **sysname**, не имеет значения по умолчанию. Сопоставление по шаблону не поддерживается.  
  
 [  **@table_owner=** ] **"***владельца***"**  
 Имя владельца таблицы, используемой для возврата сведений о каталоге. *TABLE_OWNER* — **sysname**, значение по умолчанию NULL. Сопоставление по шаблону не поддерживается. Если *владельца* не указан, применяются правила видимости таблиц по умолчанию базовой СУБД.  
  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], если текущий пользователь является владельцем таблицы с указанным именем, возвращаются индексы таблицы. Если *владельца* не задан и текущий пользователь не является владельцем таблицы с указанным *имя*, эта процедура ищет таблицу с указанным *имя* владельцем Владелец базы данных. Если владелец существует, возвращаются индексы этой таблицы.  
  
 [  **@table_qualifier=** ] **"***квалификатор***"**  
 Имя квалификатора таблицы. *квалификатор* — **sysname**, значение по умолчанию NULL. Различные продукты СУБД поддерживают трехкомпонентные имена таблиц (*квалификатор ***.*** владелец ***.*** имя*). В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] этот аргумент представляет имя базы данных. В некоторых СУБД он представляет имя сервера в среде базы данных, где находится таблица.  
  
 [  **@index_name=** ] **"***index_name***"**  
 Имя индекса. *index_name* — **sysname**, значение по умолчанию %. Поиск совпадений по шаблону поддерживается.  
  
 [  **@is_unique=** ] **"***is_unique***"**  
 Является ли только уникальные индексы (если **Y**) должны быть возвращены. *is_unique* — **char(1)**, значение по умолчанию **N**.  
  
 [  **@accuracy=** ] **"***точность***"**  
 Уровень количества элементов и точность на страницах для статистики. *точность* — **char(1)**, значение по умолчанию **Q**. Укажите **E** чтобы убедиться в том, что статистика обновляется таким образом, количество элементов и страницах являются точными.  
  
 Значение **E** (SQL_ENSURE) запрашивает драйверу безусловно.  
  
 Значение **Q** (SQL_QUICK) драйверу для получения количества элементов и страницах только в том случае, если они доступны с сервера. В этом случае драйвер не гарантирует актуальность значений. Приложения, написанные в соответствии со стандартом Open Group, всегда получают значение SQL_QUICK из драйверов, совместимых с ODBC 3.x.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**TABLE_QUALIFIER**|**sysname**|Имя квалификатора таблицы. Этот столбец может принимать значение NULL.|  
|**TABLE_OWNER**|**sysname**|Имя владельца таблицы. Этот столбец всегда возвращает значение.|  
|**ИМЯ_ТАБЛИЦЫ**|**sysname**|Имя таблицы. Этот столбец всегда возвращает значение.|  
|**NON_UNIQUE**|**smallint**|NOT NULL<br /><br /> 0 = уникальное<br /><br /> 1 = неуникальное|  
|**INDEX_QUALIFIER**|**sysname**|Имя владельца индекса. В некоторых СУБД пользователям, не являющимся владельцами таблицы, разрешено создавать индексы. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], этот столбец всегда является таким же, как **TABLE_NAME**.|  
|**INDEX_NAME**|**sysname**|Имя индекса. Этот столбец всегда возвращает значение.|  
|**TYPE**|**smallint**|Этот столбец всегда возвращает значение:<br /><br /> 0 = статистика по таблице<br /><br /> 1 = кластеризованный<br /><br /> 2 = хэшированный<br /><br /> 3 = некластеризованный|  
|**SEQ_IN_INDEX**|**smallint**|Позиция столбца в индексе.|  
|**COLUMN_NAME**|**sysname**|Имя столбца для каждого столбца **TABLE_NAME** возвращается. Этот столбец всегда возвращает значение.|  
|**COLLATION**|**char(1)**|Порядок сортировки. Возможны следующие варианты:<br /><br /> A = по возрастанию<br /><br /> D = по убыванию<br /><br /> NULL = неприменимо|  
|**КОЛИЧЕСТВО ЭЛЕМЕНТОВ**|**int**|Число строк в таблице или уникальных значений в индексе.|  
|**СТРАНИЦЫ**|**int**|Число страниц для хранения индекса или таблицы.|  
|**УСЛОВИЕ_ФИЛЬТРАЦИИ**|**varchar(128)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не возвращает значение.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 None  
  
## <a name="remarks"></a>Примечания  
 Индексы в результирующем наборе отображаются в порядке возрастания по столбцам **NON_UNIQUE**, **тип**, **INDEX_NAME**, и **SEQ_IN_INDEX**.  
  
 Кластеризованный индекс — это индекс, при котором физический порядок хранения данных таблицы соответствует последовательности индекса. Это соответствует [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] кластеризованных индексов.  
  
 Хешированный индекс обеспечивает поиск по полному совпадению или диапазону. Для поиска по шаблону он не используется.  
  
 **sp_statistics** эквивалентен **SQLStatistics** в ODBC. Возвращенные результаты сортируются по **NON_UNIQUE**, **тип**, **INDEX_QUALIFIER**, **INDEX_NAME**, и **SEQ_IN_ Индекс**. Дополнительные сведения см. в разделе [Справочник по API ODBC](http://go.microsoft.com/fwlink/?LinkId=68323).  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение SELECT для схемы.  
  
## <a name="example-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Пример: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 В следующем примере возвращаются сведения о `DimEmployee` таблицы.  
  
```  
-- Uses AdventureWorks  
  
EXEC sp_statistics DimEmployee;  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры каталога &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/catalog-stored-procedures-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

