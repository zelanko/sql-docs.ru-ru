---
title: sp_pkeys (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_pkeys
- sp_pkeys_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_pkeys
ms.assetid: e614c75d-847b-4726-8f6f-cd18de688eda
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: da9b788e69decf1c209eec846fbeccc811e70374
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/18/2018
ms.locfileid: "53589768"
---
# <a name="sppkeys-transact-sql"></a>sp_pkeys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает сведения о первичном ключе заданной таблицы в текущей среде.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
sp_pkeys [ @table_name = ] 'name'       
    [ , [ @table_owner = ] 'owner' ]   
    [ , [ @table_qualifier = ] 'qualifier' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @table_name=] '*имя*"  
 — Таблица, для которой возвращаются сведения. *имя* — **sysname**, не имеет значения по умолчанию. Сопоставление по шаблону не поддерживается.  
  
 [ @table_owner=] '*владельца*"  
 Задает владельца указанной таблицы. *владелец* — **sysname**, значение по умолчанию NULL. Сопоставление по шаблону не поддерживается. Если *владельца* не указан, применяются правила видимости таблиц по умолчанию базовой СУБД.  
  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], если текущий пользователь является владельцем таблицы с указанным именем, возвращаются ее столбцы. Если *владельца* не задан и текущий пользователь не является владельцем таблицы с указанным *имя*, эта процедура ищет таблицу с указанным *имя* владельцем Владелец базы данных. Если такая таблица существует, возвращаются ее столбцы.  
  
 [ @table_qualifier=] '*квалификатор*"  
 Квалификатор таблицы. *квалификатор* — **sysname**, значение по умолчанию NULL. Различные продукты СУБД поддерживают трехкомпонентные имена таблиц (_квалификатор_**.** _владельца_**.** _имя_). В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] этот столбец представляет имя базы данных. В некоторых СУБД он представляет имя сервера в среде базы данных, в которой находится таблица.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 None  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|TABLE_QUALIFIER|**sysname**|Имя квалификатора таблицы. Это поле может иметь значение NULL.|  
|TABLE_OWNER|**sysname**|Имя владельца таблицы. Это поле всегда возвращает значение.|  
|TABLE_NAME|**sysname**|Имя таблицы. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] этот столбец представляет имя таблицы, отображаемое в таблице sysobjects. Это поле всегда возвращает значение.|  
|COLUMN_NAME|**sysname**|Возвращаются имена всех столбцов в таблице TABLE_NAME. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] этот столбец представляет имя столбца, отображаемое в таблице sys.columns. Это поле всегда возвращает значение.|  
|KEY_SEQ|**smallint**|Порядковый номер столбца в первичном ключе, состоящем из нескольких столбцов.|  
|PK_NAME|**sysname**|Идентификатор первичного ключа. Возвращает NULL, если не применим к источнику данных.|  
  
## <a name="remarks"></a>Примечания  
 Процедура sp_pkeys возвращает сведения о столбцах, явно указанных в ограничении ПЕРВИЧНЫЙ КЛЮЧ. Так как не все системы поддерживают явно именованные первичные ключи, средство реализации шлюза зависит от составляющих первичный ключ. Обратите внимание на то, что под первичным ключом понимается логический первичный ключ таблицы. Предполагается, что для каждого логического первичного ключа определен уникальный индекс. Этот уникальный индекс возвращает хранимая процедура sp_statistics.  
  
 Хранимая процедура sp_pkeys эквивалентна SQLPrimaryKeys в ODBC. Результаты упорядочиваются по столбцам TABLE_QUALIFIER, TABLE_OWNER, TABLE_NAME и KEY_SEQ.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение SELECT для схемы.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается первичный ключ таблицы `HumanResources.Department` в базе данных `AdventureWorks2012`.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_pkeys @table_name = N'Department'  
    ,@table_owner = N'HumanResources';  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 В следующем примере возвращается первичный ключ таблицы `DimAccount` в базе данных `AdventureWorksPDW2012`. Он возвращает нулевые строки, указывающее, что в таблице нет первичного ключа.  
  
```  
-- Uses AdventureWorks  
  
EXEC sp_pkeys @table_name = N'DimAccount;  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры каталога &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/catalog-stored-procedures-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

