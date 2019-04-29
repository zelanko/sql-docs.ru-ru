---
title: sp_special_columns (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_special_columns_TSQL
- sp_special_columns
dev_langs:
- TSQL
helpviewer_keywords:
- sp_special_columns
ms.assetid: 0b0993f8-73e0-402b-8c6c-1b0963956f5d
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d96c8565a8d908518504cf86eb253fc5913f1a85
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63004161"
---
# <a name="spspecialcolumns-transact-sql"></a>sp_special_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает оптимальный набор столбцов, уникально идентифицирующих строку таблицы. Также возвращает столбцы, автоматически обновляемые, когда любое значение в строке обновляется транзакцией.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
sp_special_columns [ @table_name = ] 'table_name'     
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
  
 [ @col_type=] '*col_type*'  
 Тип — Column. *col_type* — **char (** 1 **)**, значение по умолчанию R. тип R возвращает оптимальный столбец или набор столбцов, получая значения из столбца или столбцов, позволяет любую строку в указанном Таблица для однозначной идентификации. Столбец может быть либо псевдостолбцом, специально созданным для этой цели, либо столбцом или столбцами любого уникального индекса таблицы. Тип V возвращает столбец или столбцы в указанной таблице, которые источник данных обновляет автоматически, когда любое значение в строке обновляется транзакцией.  
  
 [ @scope=] '*область*"  
 Минимально требуемая область ROWID. *область* — **char (** 1 **)**, значение по умолчанию T. область c Указывает, что ROWID действителен только в том случае, если располагается в этой строке. Область T указывает, что ROWID действителен для транзакции.  
  
 [ @nullable=] '*допускает значения NULL*"  
 Определяет, допускают ли специальные столбцы значение NULL. *допускает значения NULL* — **char (** 1 **)**, значение по умолчанию U. O указывает специальные столбцы, которые не допускают значения null. U указывает столбцы, частично допускающие значения NULL.  
  
 [ @ODBCVer=] '*ODBCVer*'  
 Используемая версия ODBC. *Аргумент ODBCVer* — **int (** 4 **)**, значение по умолчанию 2. Это значение соответствует версии ODBC 2.0. Дополнительные сведения о различиях между ODBC версии 2.0 и ODBC версии 3.0 см. в спецификации ODBC SQLSpecialColumns для ODBC версии 3.0.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 None  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|SCOPE|**smallint**|Фактическая область идентификатора строки. Возможны следующие варианты: 0, 1 или 2. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Всегда возвращает значение 0. Это поле всегда возвращает значение.<br /><br /> 0 = SQL_SCOPE_CURROW. Идентификатор строки гарантированно действителен до тех пор, пока он расположен на этой строке. Проведенная позднее повторная выборка с использованием идентификатора строки может не вернуть строку, если строка была обновлена или удалена другой транзакцией.<br /><br /> 1 = SQL_SCOPE_TRANSACTION. Идентификатор строки гарантированно допустимым в течение текущей транзакции.<br /><br /> 2 = SQL_SCOPE_SESSION. Идентификатор строки гарантированно действителен на протяжении сеанса (несмотря на границы транзакций).|  
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
  
## <a name="examples"></a>Примеры  
 Следующий пример возвращает данные о столбце, которые уникально идентифицируют строки в таблице `HumanResources.Department`.  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_special_columns @table_name = 'Department'   
    ,@table_owner = 'HumanResources';  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры каталога &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/catalog-stored-procedures-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
