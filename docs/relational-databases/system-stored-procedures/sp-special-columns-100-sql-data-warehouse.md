---
title: sp_special_columns_100 (хранилище данных SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-objects
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 5774fadc-77cc-46f8-8f9f-a0f9efe95e21
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 618b2e1a0fafdec18b1e040d255f636640e8acf1
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38015054"
---
# <a name="spspecialcolumns100-sql-data-warehouse"></a>sp_special_columns_100 (хранилище данных SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Возвращает оптимальный набор столбцов, уникально идентифицирующих строку таблицы. Также возвращает столбцы, автоматически обновляемые, когда любое значение в строке обновляется транзакцией.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL (Transact-SQL)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_special_columns_100 [ @table_name = ] 'table_name'     
     [ , [ @table_owner = ] 'table_owner' ]   
     [ , [ @qualifier = ] 'qualifier' ]   
     [ , [ @col_type = ] 'col_type' ]   
     [ , [ @scope = ] 'scope' ]  
     [ , [ @nullable = ] 'nullable' ]   
     [ , [ @ODBCVer = ] 'ODBCVer' ]   
[ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @table_name=] '*table_name*"  
 Название таблицы, используемой для возврата сведений о каталоге. *имя* — **sysname**, не имеет значения по умолчанию. Сопоставление по шаблону не поддерживается.  
  
 [ @table_owner=] '*table_owner*"  
 Владелец таблицы, используемой для возврата сведений о каталоге. *владелец* — **sysname**, значение по умолчанию NULL. Сопоставление по шаблону не поддерживается. Если *владельца* не указан, применяются правила видимости таблиц по умолчанию базовой СУБД.  
  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], если текущий пользователь является владельцем таблицы с указанным именем, возвращаются ее столбцы. Если *владельца* не задан и текущий пользователь не является владельцем указанной таблицы *имя*, эта процедура ищет таблицу указанного *имя* владельцем базы данных владелец. Если таблица существует, возвращаются ее столбцы.  
  
 [ @qualifier=] '*квалификатор*"  
 Имя квалификатора таблицы. *квалификатор* — **sysname**, значение по умолчанию NULL. Различные продукты СУБД поддерживают трехкомпонентные имена таблиц (*qualifier.owner.name*). В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] этот столбец представляет имя базы данных. В некоторых СУБД он представляет имя сервера в среде базы данных, в которой находится таблица.  
  
 [ @col_type=] '*col_type*"  
 Тип — Column. *col_type* — **char (** 1 **)**, значение по умолчанию R. тип R возвращает оптимальный столбец или набор столбцов, получая значения из столбца или столбцов, позволяет любую строку в указанном Таблица для однозначной идентификации. Столбец может быть либо псевдостолбцом, специально созданным для этой цели, либо столбцом или столбцами любого уникального индекса таблицы. Тип V возвращает столбец или столбцы в указанной таблице, которые источник данных обновляет автоматически, когда любое значение в строке обновляется транзакцией.  
  
 [ @scope=] '*область*"  
 Минимально требуемая область ROWID. *область* — **char (** 1 **)**, значение по умолчанию T. область c Указывает, что ROWID действителен только в том случае, если располагается в этой строке. Область T указывает, что ROWID действителен для транзакции.  
  
 [ @nullable=] '*допускает значения NULL*"  
 Определяет, допускают ли специальные столбцы значение NULL. *допускает значения NULL* — **char (** 1 **)**, значение по умолчанию U. O указывает специальные столбцы, которые не допускают значения null. U указывает столбцы, частично допускающие значения NULL.  
  
 [ @ODBCVer=] '*Аргумент ODBCVer*"  
 Используемая версия ODBC. *Аргумент ODBCVer* — **int (** 4 **)**, значение по умолчанию 2. Это значение соответствует версии ODBC 2.0. Дополнительные сведения о различиях между ODBC версии 2.0 и ODBC версии 3.0 см. в спецификации ODBC SQLSpecialColumns для ODBC версии 3.0.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 None  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|SCOPE|**smallint**|Фактическая область идентификатора строки. Возможны следующие варианты: 0, 1 или 2. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] всегда возвращает значение 0. Это поле всегда возвращает значение.<br /><br /> 0 = SQL_SCOPE_CURROW. Идентификатор строки гарантированно действителен до тех пор, пока он расположен на этой строке. Проведенная позднее повторная выборка с использованием идентификатора строки может не вернуть строку, если строка была обновлена или удалена другой транзакцией.<br /><br /> 1 = SQL_SCOPE_TRANSACTION. Идентификатор строки гарантированно допустимым в течение текущей транзакции.<br /><br /> 2 = SQL_SCOPE_SESSION. Идентификатор строки гарантированно действителен на протяжении сеанса (несмотря на границы транзакций).|  
|COLUMN_NAME|**sysname**|Имя столбца для каждого столбца *таблицы*возвращается. Это поле всегда возвращает значение.|  
|DATA_TYPE|**smallint**|Тип данных ODBC SQL.|  
|TYPE_NAME|**sysname**|Имя типа данных зависит от источника данных; например **char**, **varchar**, **деньги**, или **текст**.|  
|PRECISION|**Int**|Точность столбца на источнике данных. Это поле всегда возвращает значение.|  
|LENGTH|**Int**|Длина в байтах, необходимый для типа данных в двоичной форме в источнике данных, например, 10 для **char (** 10 **)**, 4 для **целое число**и 2 для **smallint** .|  
|SCALE|**smallint**|Масштаб столбца в источнике данных. Для тех типов данных, для которых масштаб не применим, возвращается значение NULL.|  
|PSEUDO_COLUMN|**smallint**|Указывает, является ли столбец псевдостолбцом. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] всегда возвращает 1:<br /><br /> 0 = SQL_PC_UNKNOWN<br /><br /> 1 = SQL_PC_NOT_PSEUDO<br /><br /> 2 = SQL_PC_PSEUDO|  
  
## <a name="remarks"></a>Примечания  
 sp_special_columns эквивалентна SQLSpecialColumns в ODBC. Возвращенные результаты сортируются по столбцу SCOPE.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение SELECT для схемы.  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Следующий пример возвращает данные о столбце, которые уникально идентифицируют строки в таблице `FactFinance`.  
  
```  
-- Uses AdventureWorks  
  
EXEC sp_special_columns_100 @table_name = 'FactFinance';  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры хранилища данных SQL](../../relational-databases/system-stored-procedures/sql-data-warehouse-stored-procedures.md)  
  
  

